# Sicherheitsmodul (Security.vue)

## BaSyx Security Plugin Frontend - Dokumentation

### 1. Einführung

Das BaSyx Security Plugin Frontend ist eine Vue.js-basierte Benutzeroberfläche, die in das BaSyx Web UI integriert wird. Es ermöglicht die Verwaltung von Sicherheitsregeln für BaSyx-Komponenten über eine intuitive grafische Oberfläche. Durch diese Komponente können Administratoren granulare Zugriffsberechtigungen für verschiedene Rollen und Ressourcen definieren und verwalten.

#### 1.1 Hauptfunktionen

* **Anzeige bestehender Sicherheitsregeln**: Tabellarische Übersicht aller im System definierten Sicherheitsregeln
* **Filterung und Suche**: Möglichkeit zur Filterung nach Zieltyp und Aktion sowie Volltextsuche
* **Erstellung neuer Regeln**: Formular zur Definition neuer Zugriffsregeln mit rollenbasierter Berechtigung
* **Bearbeitung von Regeln**: Anpassung existierender Regeln über ein benutzerfreundliches Formular
* **Löschung von Regeln**: Entfernen nicht mehr benötigter Regeln mit Bestätigungsdialog
* **API-Logging**: Detaillierte Protokollierung aller API-Aufrufe für Debugging und Nachverfolgung

### 2. Benutzeroberfläche

#### 2.1 Hauptansicht

Die Hauptansicht des Security Plugins besteht aus folgenden Elementen:

* **Header-Bereich**: Titel, Informationstext und Warnhinweis zur sorgfältigen Prüfung von Änderungen
* **Dokumentations- und Keycloak-Links**: Schnellzugriff auf externe Ressourcen
* **Filter- und Suchbereich**: Eingabefeld für Suchbegriffe und Dropdown-Menüs für Typ- und Aktionsfilter
* **Regelübersicht**: Tabelle mit allen definierten Sicherheitsregeln und deren Haupteigenschaften
* **API-Log**: Aufklappbarer Bereich mit chronologischen Protokollen der API-Kommunikation

#### 2.2 Dialoge

Das Plugin enthält drei Hauptdialoge:

1. **Neuer-Regel-Dialog**: Formular zur Erstellung einer neuen Sicherheitsregel mit automatischer ID-Generierung
2. **Bearbeiten-Dialog**: Formular zur Änderung einer bestehenden Sicherheitsregel
3. **Löschen-Bestätigungs-Dialog**: Dialog zur Bestätigung des Löschvorgangs mit Anzeige der betroffenen Regeldaten

#### 2.3 Fehlerbehandlung

Das Frontend zeigt Fehler an mehreren Stellen an:

* **Hauptseiten-Fehler**: Werden als Alert in der Hauptansicht angezeigt, mit möglichen Fehlerursachen
* **Dialog-Fehler**: Werden innerhalb der entsprechenden Dialoge angezeigt
* **API-Log-Einträge**: Farblich gekennzeichnete Erfolgs- und Fehlermeldungen mit detaillierten Informationen

### 3. Funktionalitäten

#### 3.1 Regelverwaltung

Das Plugin ermöglicht die vollständige CRUD-Funktionalität für Sicherheitsregeln:

* **Anzeigen**: Automatisches Laden aller Regeln aus dem Security Submodel
* **Erstellen**: Definition neuer Regeln mit Rolle, Aktionen, Zieltyp und Ziel-IDs
* **Bearbeiten**: Änderung bestehender Regelparameter (Rolle, Aktionen, Ziele)
* **Löschen**: Entfernen von Regeln mit Sicherheitsabfrage

#### 3.2 Regelkomponenten

Eine Sicherheitsregel besteht aus folgenden Hauptkomponenten:

* **Rule ID Short**: Automatisch generierte Base64-ID (Role + FirstAction + TargetType)
* **Target Role**: Die Zielrolle aus dem Authentifizierungssystem (z.B. Keycloak)
* **Actions**: Erlaubte Aktionen (READ, WRITE, DELETE, EXECUTE)
* **Target Type**: Ressourcentyp (aas, submodel, aas-registry, submodel-registry)
* **Target IDs**: Spezifische Ressourcen-IDs oder Wildcard (*) für alle Instanzen

#### 3.3 Filterung und Suche

Das Plugin bietet verschiedene Filtermöglichkeiten:

* **Textsuche**: Durchsucht alle Felder nach dem eingegebenen Text
* **Target Type Filter**: Filtert nach dem spezifischen Ressourcentyp
* **Action Filter**: Filtert nach einer bestimmten Aktion

#### 3.4 API-Logs

Das Frontend protokolliert alle API-Interaktionen für Debugging-Zwecke:

* **Zeitstempel**: Datum und Uhrzeit der Aktion
* **Aktion**: Art der Operation (Fetch, Create, Update, Delete)
* **HTTP-Details**: Methode, Endpunkt und Status
* **Payload**: Bei POST/PUT-Anfragen 
* **Ergebnis**: Erfolgs- oder Fehlerinformationen mit Statuscode

### 4. Technische Details

#### 4.1 Technologien und Komponenten

* **Vue 3**: JavaScript-Framework mit Composition API
* **TypeScript**: Für typsichere Programmierung
* **Vuetify**: UI-Komponenten-Framework
* **RequestHandling Composable**: Zentrale Komponente für API-Kommunikation

#### 4.2 Datenmodell

Die Security.vue Komponente definiert folgende Hauptinterfaces:

```typescript
// BaSyx Model Interfaces
interface SecurityRule {
  modelType: 'SubmodelElementCollection';
  idShort: string;
  value: [
    BaSyxProperty<string>,                      // Role Property
    BaSyxSubmodelElementList<BaSyxProperty<string>>,  // Actions List
    BaSyxTargetInformation                      // TargetInformation Collection
  ];
}

// Formular-Datenmodell
interface FormData {
  idShort: string;
  role: string;
  actions: string[];
  targetType: string;
  targetIds: string;
  targetElementPaths: string;
}
```

#### 4.3 Konstanten und Konfiguration

Das Plugin verwendet folgende wichtige Konstanten:

```typescript
// Submodel-Identifikatoren
const SECURITY_SUBMODEL_ID = 'SecuritySubmodel';
const SECURITY_SUBMODEL_B64_ID = 'U2VjdXJpdHlTdWJtb2RlbA==';

// API-Endpunkte
const submodelUrl = `/submodels/${SECURITY_SUBMODEL_B64_ID}`;
const submodelElementsUrl = `/submodels/${SECURITY_SUBMODEL_B64_ID}/submodel-elements`;

// Verfügbare Aktionen und Zieltypen
const availableActions = ['READ', 'WRITE', 'DELETE', 'EXECUTE'];

const targetInformationClassMap = {
  'aas-registry': 'AAS Registry',
  'aas': 'Asset Administration Shell',
  'submodel-registry': 'Submodel Registry',
  'submodel': 'Submodel'
};
```

#### 4.4 Zuständigkeiten im Code

Die Komponente ist nach klaren Verantwortlichkeiten aufgeteilt:

* **UI-Komponenten und Design**: Moritz (UI-Architekt)
  - Gestaltung der Benutzeroberfläche, Komponentenstruktur, UI-Konsistenz, Barrierefreiheit, Responsivität und visuelle Elemente

* **Logik und Funktionalität**: Felix (Entwickler)
  - API-Integration, Datenverarbeitung, Nutzerverwaltung, RBAC-Implementierung, Formularvalidierung und State-Management

#### 4.5 API-Endpunkte

Das Frontend interagiert mit folgenden API-Endpunkten:

* **GET** `/submodels/${SECURITY_SUBMODEL_B64_ID}`: Abrufen des Security Submodels
* **POST** `/submodels/${SECURITY_SUBMODEL_B64_ID}/submodel-elements`: Erstellen einer neuen Regel
* **PUT** `/submodels/${SECURITY_SUBMODEL_B64_ID}/submodel-elements/{ruleIdShort}`: Aktualisieren einer Regel
* **DELETE** `/submodels/${SECURITY_SUBMODEL_B64_ID}/submodel-elements/{ruleIdShort}`: Löschen einer Regel

### 5. Integration mit externen Systemen

Das Security-Modul integriert sich mit:

* **Keycloak**: Für Rollen- und Benutzerinformationen (Link zur Admin-Oberfläche im Header)
* **BaSyx Security Submodel**: Speicherort der Sicherheitsregeln
* **BaSyx API**: Für CRUD-Operationen auf dem Security Submodel

***

### Weiterführende Informationen

* **Projektrepository**: [https://github.com/DHBW-TINF23F/Team1-BaSyx-Security-Plugin](https://github.com/DHBW-TINF23F/Team1-BaSyx-Security-Plugin)
* **Dokumentation**: [https://basyx-security-plugin.gitbook.io/basyx-security](https://basyx-security-plugin.gitbook.io/basyx-security)
* **Keycloak Admin**: Typischerweise erreichbar unter `http://localhost:9097/admin/master/console/#/BaSyx`
