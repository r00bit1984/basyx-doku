---
icon: route-interstate
---

# SIR Systemintegrationsreport

{% hint style="info" %}
Verantwortlicher: Robert L.
{% endhint %}

{% hint style="info" %}
Dieser Report bezieht sich auf die PROD Variante des Plugins. Mehr dazu [hier.](../entwicklung/finales-plugin-starten-mock-vs-prod.md)
{% endhint %}

### 1. Systemarchitektur

Das BaSyx Security Plugin ist als Erweiterungsmodul für die BaSyx-UI konzipiert und folgt einer modularen Architektur. Die Hauptkomponente ist die Security.vue, die als Frontend-Interface zur Verwaltung von Sicherheitsregeln dient. Die Architektur umfasst:

* **Frontend**: Vue.js basierte Benutzeroberfläche mit Vuetify-Komponenten
* **Backend**: REST-API zur Kommunikation mit dem BaSyx Submodel Repository
* **Authentifizierungsdienst**: Externe Authentifizierungskomponente (Keycloak)
* **Sicherheitssubmodell**: Spezialisiertes BaSyx-Submodell zur Speicherung von Zugriffsregeln

### 2. Integrationskomponenten

Das Plugin integriert sich nahtlos in die bestehende BaSyx-Umgebung durch folgende Komponenten:

* **Security Submodel**: Ein dediziertes Submodell (`SecuritySubmodel`) zur Speicherung von Zugriffsregeln
* **UI-Komponenten**: Integration in das bestehende UI-Framework durch wiederverwendbare Komponenten
* **API-Anbindung**: RequestHandling-Composable für API-Kommunikation
* **Logging-Mechanismus**: Integrierte API-Call-Protokollierung für Audit-Zwecke

### 3. Funktionsumfang

Das Security Plugin bietet folgende Kernfunktionalitäten:

* **Regelbasierte Zugriffskontrolle**: Definition von Zugriffsregeln basierend auf Rollen
* **CRUD-Operationen**: Erstellen, Anzeigen, Bearbeiten und Löschen von Sicherheitsregeln
* **Filterung und Suche**: Erweiterte Such- und Filterfunktionen für Sicherheitsregeln
* **Zielgenaue Rechtevergabe**: Definition von Zugriffsrechten für spezifische Komponenten:
  * Asset Administration Shells
  * Submodelle
  * AAS-Registry
  * Submodell-Registry
* **Granulare Aktionsdefinition**: Feingranulare Rechtevergabe für READ, WRITE, DELETE und EXECUTE Operationen
* **Audit-Logging**: Protokollierung aller API-Aufrufe für Nachvollziehbarkeit

### 4. Schnittstellen

Das Plugin kommuniziert über folgende Schnittstellen:

#### 4.1 Backend-API

* **Submodell-Endpunkte**:
  * GET `/submodels/{SECURITY_SUBMODEL_B64_ID}` zum Abrufen aller Regeln
  * POST `/submodels/{SECURITY_SUBMODEL_B64_ID}/submodel-elements` zum Erstellen neuer Regeln
  * PUT/DELETE für Aktualisierung und Löschung

#### 4.2 Authentifizierungsdienst

* Integration mit externem Authentifizierungsdienst (URL: http://localhost:9097/admin/master/console/#/BaSyx)
* Regelbasierter Zugriff auf Systemressourcen

#### 4.3 UI-Komponenten

* Verwendung von UI-Header und API-Log Komponenten
* Integration in das bestehende Modul-System der BaSyx-UI

### 5. Datenfluss

Der Datenfluss innerhalb des Security Plugins folgt diesem Muster:

1. **Initialisierung**: Beim Laden der Komponente werden bestehende Sicherheitsregeln vom Backend abgerufen
2. **Benutzereingabe**: Benutzer erstellen oder modifizieren Sicherheitsregeln über die UI
3. **Validierung**: Eingaben werden clientseitig validiert (erforderliche Felder, Formatierung)
4. **API-Kommunikation**: Validierte Daten werden an das Backend gesendet
5. **Rückmeldung**: Erfolgs- oder Fehlermeldungen werden dem Benutzer angezeigt
6. **Aktualisierung**: Bei erfolgreicher Operation wird die Anzeige aktualisiert

### 6. Authentifizierung und Autorisierung

Das Plugin implementiert ein umfassendes RBAC-System (Role-Based Access Control):

* **Rollenbasierter Zugriff**: Zugriffsrechte werden anhand von Benutzerrollen definiert
* **Zielspezifische Regeln**: Regeln können für spezifische Komponententypen definiert werden
* **ID-basierte Einschränkung**: Zugriffsrechte können auf bestimmte IDs beschränkt werden
* **Aktionsbasierte Kontrolle**: Separate Berechtigungen für READ, WRITE, DELETE und EXECUTE
* **Wildcard-Unterstützung**: Verwendung von "\*" für umfassende Rechte auf allen Instanzen eines Typs

### 7. Implementierungsdetails

Die Implementierung folgt bewährten Entwicklungspraktiken:

* **Komponentenbasierte Architektur**: Modularisierung durch Vue-Komponenten
* **Reactive State Management**: Verwendung von Vue 3 Composition API für reaktive Zustandsverwaltung
* **Typsicherheit**: TypeScript-Interfaces für BaSyx-Datenmodelle
* **UX-Optimierung**: Benutzerfreundliche Dialoge, Validierungsfeedback und visuelle Hinweise
* **Fehlerbehandlung**: Umfassende Fehlerbehandlung mit spezifischen Fehlermeldungen
* **Dokumentation**: Inline-Kommentare und Typendefinitionen

**Besondere technische Merkmale:**

* Automatische ID-Generierung für neue Regeln mittels Base64-Kodierung
* Dynamische Formularvalidierung
* Reaktive Filterung und Suche
* API-Logging für Audit-Zwecke
* Responsives Design durch Vuetify-Komponenten

### 8. Fazit

Das BaSyx Security Plugin stellt eine robuste Erweiterung der BaSyx-UI dar, die eine feingranulare Zugriffskontrolle für verschiedene Systemkomponenten ermöglicht. Durch die nahtlose Integration in die bestehende UI und die Verwendung standardisierter BaSyx-Submodelle wird die Administration von Zugriffsrechten erheblich vereinfacht.
