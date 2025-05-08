---
beschreibung: Dokumentation für das BaSyx Security Rule Management UI (Security.vue)
icon: lock-keyhole
---

# Sicherheitsregelverwaltung (Security.vue)

## BaSyx Security Plugin Frontend – Dokumentation

### 1. Einführung

Das BaSyx Security Plugin Frontend ist eine auf Vue.js basierende Benutzeroberfläche, die in das BaSyx Web UI integriert ist. Es ermöglicht die Verwaltung von Sicherheitsregeln für BaSyx-Komponenten über eine intuitive grafische Oberfläche. Das Plugin kommuniziert mit dem BaSyx-Backend, um Regeln aus dem Security Submodel zu lesen und zu ändern.

#### 1.1 Hauptfunktionen

* **Vorhandene Sicherheitsregeln anzeigen**: Tabellenansicht aller definierten Regeln im System
* **Neue Regeln erstellen**: Benutzerfreundliches Formular zur Definition von Zugriffsregeln
* **Vorhandene Regeln bearbeiten**: Aktualisierung von Regelparametern ohne Neuerstellung
* **Regeln löschen**: Entfernen veralteter Regeln mit Bestätigungsdialog
* **Suchen und filtern**: Suchen und Filtern von Regeln nach verschiedenen Kriterien
* **API-Protokollierung**: Detaillierte Protokollierung aller API-Aufrufe zur Fehleranalyse

### 2. Benutzeroberfläche

#### 2.1 Hauptansicht

Die Hauptansicht des Security Plugins besteht aus:

* **Kopfbereich**: Titel, Informationstext und Links zur Dokumentation sowie zur Keycloak-Admin-Oberfläche
* **Regelübersicht**: Tabelle mit allen definierten Sicherheitsregeln und Such-/Filteroptionen
* **Aktionsschaltflächen**: Schaltflächen zum Hinzufügen, Bearbeiten und Löschen von Regeln
* **API-Protokoll**: Ausklappbarer Bereich mit Protokollen der API-Kommunikation

#### Screenshots

<figure><img src="../.gitbook/assets/ui.png" alt=""><figcaption><p>Hauptansicht des Plugins im Dark- und Light-Mode</p></figcaption></figure>

#### 2.2 Such- und Filterfunktionen

Die Regelübersicht bietet folgende Filteroptionen:

* **Textsuche**: Freitextsuche in allen Regelfeldern
* **Target Type Filter**: Filtern nach Ressourcentyp (AAS, Submodel, etc.)
* **Action Filter**: Filtern nach erlaubten Aktionen (READ, WRITE, etc.)
* **Zurücksetzen**: Zurücksetzen aller Filterkriterien

#### 2.3 Fehleranzeige in der UI

Das Frontend zeigt Fehler an mehreren Stellen an:

* **Fehler auf der Hauptseite**: Oben in der UI für allgemeine Probleme
* **Dialogfehler**: Im jeweiligen Dialogfenster
* **API-Protokolleinträge**: Detaillierte Informationen zu jedem API-Aufruf

#### 2.4 Dialoge

Das Plugin enthält drei Hauptdialoge:

1. **Neuer-Regel-Dialog**: Formular zum Erstellen einer neuen Sicherheitsregel
2. **Bearbeiten-Dialog**: Formular zum Aktualisieren einer bestehenden Regel
3. **Löschbestätigungsdialog**: Dialog zur Bestätigung des Löschens einer Regel

<figure><img src="../.gitbook/assets/Screenshot 2025-04-25 at 14-23-43 AAS UI.png" alt=""><figcaption><p>Popup zur Definition einer neuen Sicherheitsregel</p></figcaption></figure>

### 3. Funktionalität

#### 3.1 Regeln anzeigen

Das Plugin lädt automatisch alle bestehenden Sicherheitsregeln aus dem Security Submodel und zeigt sie in einer Tabelle an:

* **Regel-ID Short**: Automatisch generierte ID (Base64-codiert)
* **Zielrolle**: Die Rolle, für die die Regel gilt
* **Aktionen**: Erlaubte Aktionen (READ, WRITE, DELETE, EXECUTE)
* **Zieltyp**: Typ der Zielressource (AAS, Submodel, etc.)
* **Verwaltungsoptionen**: Schaltflächen zum Bearbeiten und Löschen von Regeln

#### 3.2 Regeln erstellen

Beim Erstellen neuer Regeln bietet das System:

* Automatische Generierung der Regel-ID basierend auf Rolle, erster Aktion und Zieltyp
* Validierung der Eingabefelder mit Fehlermeldungen
* Multi-Select für Aktionen (READ, WRITE, DELETE, EXECUTE)
* Unterstützung für mehrere Ziel-IDs (eine pro Zeile)
* Wildcard-Unterstützung mit "*" für alle Instanzen eines Typs

#### 3.3 Regeln bearbeiten

Das Plugin ermöglicht das Bearbeiten bestehender Regeln:

* Änderung von Zielrolle, Aktionen und Ziel-IDs
* Beibehaltung der ursprünglichen Regel-ID für Kontinuität
* Validierung aller Eingabefelder vor dem Speichern

#### 3.4 API-Protokolle

Das Frontend protokolliert alle API-Interaktionen im API-Protokollbereich:

* Zeitstempel der Aktion
* Art der Operation (Fetch, Create, Update, Delete)
* HTTP-Methode und Endpunkt
* Payload (bei POST/PUT-Anfragen)
* Ergebnis (Erfolg/Fehler mit Statuscode)
* Etwaige Fehlermeldungen
* Farbige Kennzeichnung für erfolgreiche und fehlgeschlagene Operationen

### 4. Technische Details

#### 4.1 Technologien

* **Vue.js**: JavaScript-Framework für die UI
* **TypeScript**: Für typsicheres Programmieren
* **Vuetify**: UI-Komponentenframework für Material Design
* **REST API**: Kommunikation mit dem BaSyx-Backend

#### 4.2 Regel-Datenstruktur

Eine Sicherheitsregel wird im Frontend als Vue-Objekt dargestellt, bevor sie in die AAS-Struktur umgewandelt wird:

```typescript
interface FormData {
  idShort: string;
  role: string;
  actions: string[];
  targetType: string;
  targetIds: string;
  targetElementPaths: string;
}
```

#### 4.3 Zieltyp-Mapping

Das Frontend ordnet benutzerfreundliche Typen Anzeigennamen für die UI und zur Generierung der Regel-ID zu:

```typescript
const targetInformationClassMap: Record<TargetType, string> = {
  'aas-registry': 'AAS-Registry',
  'aas': 'Asset Administration Shell',
  'submodel-registry': 'Submodel-Registry',
  'submodel': 'Submodel'
};
```

#### 4.4 Automatische ID-Generierung

Die Regel-ID Short wird automatisch generiert, indem eine Kombination aus:

```
Base64(Rolle + ErsteAktion + Zieltyp)
```

Base64-codiert wird. Dies stellt eindeutige, reproduzierbare IDs für jede Regelkonfiguration sicher.

#### 4.5 API-Endpunkte

Das Frontend interagiert mit folgenden API-Endpunkten:

* **GET** `/submodels/{SECURITY_SUBMODEL_B64_ID}`: Security Submodel abrufen
* **POST** `/submodels/{SECURITY_SUBMODEL_B64_ID}/submodel-elements`: Neue Regel erstellen
* **PUT** `/submodels/{SECURITY_SUBMODEL_B64_ID}/submodel-elements/{ruleIdShort}`: Regel aktualisieren
* **DELETE** `/submodels/{SECURITY_SUBMODEL_B64_ID}/submodel-elements/{ruleIdShort}`: Regel löschen

***

### Weitere Informationen

* Projekt-Repository: [https://github.com/DHBW-TINF23F/Team1-BaSyx-Security-Plugin](https://github.com/DHBW-TINF23F/Team1-BaSyx-Security-Plugin)
