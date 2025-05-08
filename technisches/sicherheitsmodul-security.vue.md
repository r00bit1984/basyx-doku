---
description: Dokumentation über das BaSyx-Modul 'Security'
icon: lock-keyhole
---

# Sicherheitsmodul (MOCK)

## BaSyx Security Plugin Frontend - Dokumentation

### 1. Einführung

Das BaSyx Security Plugin Frontend ist eine Vue.js-basierte Benutzeroberfläche, die in das BaSyx Web UI integriert wird. Es ermöglicht die Verwaltung von Sicherheitsregeln für BaSyx-Komponenten über eine intuitive grafische Oberfläche. Das Plugin kommuniziert mit dem BaSyx-Backend, um Regeln aus dem Security Submodel zu lesen und zu modifizieren.

#### 1.1 Hauptfunktionen

* **Anzeige bestehender Sicherheitsregeln**: Übersichtliche Darstellung aller im System definierten Regeln
* **Erstellung neuer Regeln**: Benutzerfreundliches Formular zur Definition von Zugriffsregeln
* **Bearbeitung bestehender Regeln**: Aktualisierung von Regelparametern ohne Neuanlage
* **Löschung von Regeln**: Entfernen nicht mehr benötigter Regeln mit Bestätigungsdialog
* **Suche und Filterung**: Durchsuchen und Filtern von Regeln nach verschiedenen Kriterien
* **API-Logging**: Detaillierte Protokollierung aller API-Aufrufe für Debugging-Zwecke

### 2. Benutzeroberfläche

#### 2.1 Hauptansicht

Die Hauptansicht des Security Plugins besteht aus folgenden Elementen:

* **Header-Bereich**: Titel, Informationstext und Links zur Dokumentation und Keycloak-Admin-Interface
* **Regelübersicht**: Tabelle mit allen definierten Sicherheitsregeln und Such-/Filteroptionen
* **Aktion-Buttons**: Schaltflächen zum Hinzufügen, Bearbeiten und Löschen von Regeln
* **API-Log**: Aufklappbarer Bereich mit Protokollen der API-Kommunikation

#### Screenshots

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption><p>Die Hauptansicht der (MOCK)-UI</p></figcaption></figure>

#### 2.2 Such- und Filterfunktionen

Die Regelübersicht bietet folgende Filtermöglichkeiten:

* **Textsuche**: Durchsuchen aller Regelfelder nach Freitext
* **Target Type Filter**: Filterung nach Ressourcentyp (AAS, Submodel, etc.)
* **Action Filter**: Filterung nach erlaubten Aktionen (READ, WRITE, etc.)
* **Reset-Funktion**: Zurücksetzen aller Filterkriterien

#### 2.3 UI-Fehleranzeigen

Das Frontend zeigt Fehler an mehreren Stellen an:

* **Hauptseiten-Fehler**: Werden oben in der UI angezeigt und betreffen allgemeine Probleme
* **Dialog-Fehler**: Werden in den jeweiligen Dialogen angezeigt
* **API-Log-Einträge**: Detaillierte Informationen zu jedem API-Aufruf

#### 2.4 Dialoge

Das Plugin enthält drei Hauptdialoge:

1. **Neuer-Regel-Dialog**: Formular zur Erstellung einer neuen Sicherheitsregel
2. **Bearbeiten-Dialog**: Formular zur Aktualisierung einer bestehenden Regel
3. **Löschen-Bestätigungs-Dialog**: Dialog zur Bestätigung des Löschvorgangs einer Regel

<figure><img src="../.gitbook/assets/Screenshot 2025-04-25 at 14-23-43 AAS UI.png" alt=""><figcaption><p>Popup, wenn eine neue Security Regel definiert werden soll</p></figcaption></figure>

### 3. Funktionalitäten

#### 3.1 Regeln anzeigen

Das Plugin lädt automatisch alle vorhandenen Sicherheitsregeln aus dem Security Submodel und zeigt sie in einer übersichtlichen Tabelle an:

* **Rule ID Short**: Automatisch generierte ID (Base64-kodiert)
* **Target Role**: Die Zielrolle, für die die Regel gilt
* **Actions**: Erlaubte Aktionen (READ, WRITE, DELETE, EXECUTE)
* **Target Type**: Typ der Zielressource (AAS, Submodel, etc.)
* **Verwaltungsoptionen**: Buttons zum Bearbeiten und Löschen von Regeln

#### 3.2 Regeln erstellen

Beim Erstellen neuer Regeln bietet das System:

* Automatische Generierung der Rule ID auf Basis von Role, Action und TargetType
* Validierung der Eingabefelder mit Fehlermeldungen
* Mehrfachauswahl von Aktionen (READ, WRITE, DELETE, EXECUTE)
* Unterstützung für mehrere Target-IDs (eine pro Zeile)
* Wildcard-Unterstützung mit "\*" für alle Instanzen eines Typs

#### 3.3 Regeln bearbeiten

Das Plugin ermöglicht die Bearbeitung bestehender Regeln:

* Änderungen der Zielrolle, Aktionen und Target-IDs
* Beibehaltung der ursprünglichen Rule ID für Kontinuität
* Validierung aller Eingabefelder vor dem Speichern

#### 3.4 API-Logs

Das Frontend protokolliert alle API-Interaktionen im API-Log-Bereich:

* Timestamp der Aktion
* Art der Operation (Fetch, Create, Update, Delete)
* HTTP-Methode und Endpunkt
* Payload (bei POST/PUT-Anfragen)
* Ergebnis (Erfolg/Fehler mit Statuscode)
* Eventuelle Fehlermeldungen
* Farbliche Kennzeichnung für erfolgreiche und fehlgeschlagene Operationen

### 4. Technische Details

#### 4.1 Technologien

* **Vue.js**: JavaScript-Framework für die UI
* **TypeScript**: Für typsichere Programmierung
* **Vuetify**: UI-Komponenten-Framework für Material Design
* **REST API**: Kommunikation mit dem BaSyx Backend

#### 4.2 Datenstruktur einer Regel

Eine Sicherheitsregel wird im Frontend als Vue-Objekt repräsentiert, bevor sie in die AAS-Struktur umgewandelt wird:

```typescript
interface NewRuleData {
  role: string;            // Zielrolle
  actions: string[];       // Erlaubte Aktionen
  targetType: TargetType;  // Ressourcentyp als typensicherer Wert
  targetIds: string;       // Ziel-IDs (mehrzeilig)
}
```

#### 4.3 Target Type Mapping

Das Frontend mappt benutzerfreundliche Typen auf Java-Klassennamen für die Generierung der Rule ID:

```typescript
const targetInformationClassMap = {
  'aas-registry': 'org.eclipse.digitaltwin.basyx.aasregistry.feature.authorization.AasRegistryTargetInformation',
  'aas': 'org.eclipse.digitaltwin.basyx.aasrepository.feature.authorization.AasTargetInformation',
  'submodel-registry': 'org.eclipse.digitaltwin.basyx.submodelregistry.feature.authorization.SubmodelRegistryTargetInformation',
  'submodel': 'org.eclipse.digitaltwin.basyx.submodelrepository.feature.authorization.SubmodelTargetInformation',
  'concept-description': 'org.eclipse.digitaltwin.basyx.conceptdescriptionrepository.feature.authorization.ConceptDescriptionTargetInformation',
  'aas-environment': 'org.eclipse.digitaltwin.basyx.aasenvironment.feature.authorization.AasEnvironmentTargetInformation',
  'aas-discovery': 'org.eclipse.digitaltwin.basyx.aasdiscoveryservice.feature.authorization.AasDiscoveryServiceTargetInformation',
};
```

#### 4.4 Automatische ID-Generierung

Die Rule ID Short wird automatisch generiert durch Base64-Kodierung einer Kombination aus:

```
Base64(Role + FirstAction + TargetInfoClass)
```

Dies gewährleistet eindeutige, reproduzierbare IDs für jede Regelkonfiguration.

#### 4.5 API-Endpunkte

Das Frontend interagiert mit folgenden API-Endpunkten:

* **GET** `{submodelRepositoryUrl}/{SECURITY_SUBMODEL_B64_ID}`: Abrufen des Security Submodels
* **POST** `{submodelRepositoryUrl}/{SECURITY_SUBMODEL_B64_ID}/submodel-elements`: Erstellen einer neuen Regel
* **PUT** `{submodelRepositoryUrl}/{SECURITY_SUBMODEL_B64_ID}/submodel-elements/{ruleIdShort}`: Aktualisieren einer Regel
* **DELETE** `{submodelRepositoryUrl}/{SECURITY_SUBMODEL_B64_ID}/submodel-elements/{ruleIdShort}`: Löschen einer Regel

***

### Weiterführende Informationen

* Projektrepository: [https://github.com/DHBW-TINF23F/Team1-BaSyx-Security-Plugin](https://github.com/DHBW-TINF23F/Team1-BaSyx-Security-Plugin)
