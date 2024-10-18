---
icon: folder-grid
---

# Lastenheft

## Lastenheft

Verantwortlich: Lukas

...

### Changelog

| _Version_ | _Date_     | _Author_      | _Comment_                                                                           |
| --------- | ---------- | ------------- | ----------------------------------------------------------------------------------- |
| 0.1       | 04.10.2024 | Felix         | Created, first draft                                                                |
| 0.2       | 17.10.2024 | Lukas, Jannik | Goal, Product Usage, Business Processes, Use Case, Requirements, Product Data added |

### Ziel

Ziel dieses Projekts ist die Entwicklung eines Security-Plugins für das BaSyx-UI. Dieses soll mit Unterstützung von rollenbasierten Zugriffssteuerungen zur Verwaltung von Zugangsrichtlinien für einzelne AAS-Elemente erfolgen.

### Produktumgebung

BaSyx-Umgebung beschreiben: Zweck --> von BaSyx auf die Verwaltungsschale überleiten und erklären

### Produktverwendung

Die folgenden Business Processes und Use Cases beschreiben die Funktionen die das System unterstützen soll.

### Geschäftsprozesse

#### \<BP.001>: Verwaltung und Konfiguration von Rollen

| Auslösendes Ereignis: | Der Administrator möchte Rollen konfigurieren und verwalten                                                                 |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator kann in einem speziellen Bereich die Rollen für sämtliche Benutzer vergeben, konfigurieren und verwalten. |
| Involvierte Rollen:   | Administrator                                                                                                               |

#### \<BP.002>: Konfiguration von Zugriffsrechten und Berechtigungsstrukturen

| Auslösendes Ereignis: | Der Administrator möchte den Rollen Berechtigungen zuweisen                                                            |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator kann in einem speziellen Bereich die Berechtigungen für sämtliche Rollen vergeben und konfigurieren. |
| Involvierte Rollen:   | Administrator                                                                                                          |

#### \<BP.003>: Verwaltung von Benutzeridentitäten und Rollenbasierter Zugriffssteuerung

| Auslösendes Ereignis: | Ein Benutzer soll nach dem Login automatisch die für seine Rolle vorgesehenen Berechtigungen erhalten    |
| --------------------- | -------------------------------------------------------------------------------------------------------- |
| Resultat:             | Das System vergibt nach der Authentifizierung des Benutzers automatisch die vorgesehenen Berechtigungen. |
| Involvierte Rollen:   | Administrator                                                                                            |

#### \<BP.004>: Verwaltung von Zugangsrichtlinien durch Import und Export

| Auslösendes Ereignis: | Der Administrator möchte Zugangsrichtlinien in Keycloak importieren oder exportieren                                        |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator über eine Schnittstelle im Keycloak die aktuelle Zugangsrichtline exportieren oder eine neue importieren. |
| Involvierte Rollen:   | Administrator                                                                                                               |

### Anwendungsfälle

#### \<UC.001>: Rollen konfigurieren

| Verwandter Business Process: | \<BP.001>: Verwaltung und Konfiguration von Rollen                                                                |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Der Administrator möchte eine neue Rolle konfigurieren.                                                           |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                  |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium:            | Die neu konfigurierte Rolle ist in Keycloak hinterlegt und die Änderungen an der Rolle wurden wirksam.            |
| Involvierte Benutzer:        | Administrator                                                                                                     |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf " Rolle konfigurieren" klickt.                  |
|                              |                                                                                                                   |

#### \<UC.002>: Rollen verwalten

| Verwandter Business Process: | \<BP.001>: Verwaltung und Konfiguration von Rollen                                                                |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Der Administrator möchte eine bestehende Rolle verwalten.                                                         |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                  |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium:            | Die bearbeitete Rolle ist in Keycloak hinterlegt und die Änderungen wurden wirksam.                               |
| Involvierte Benutzer:        | Administrator und Benutzer                                                                                        |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf "neue Rolle vergeben" klickt.                   |
|                              |                                                                                                                   |

#### \<UC.003>: Zugriffsrechte zuweisen

| Verwandter Business Process: | \<BP.002>: Konfiguration von Zugriffsrechten und Berechtigungsstrukturen                                          |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Der Administrator möchte einer Rolle Zugriffsrechte zuweisen.                                                     |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                  |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium:            | Die konfigurierten Rechte für die Rolle sind wirksam.                                                             |
| Involvierte Benutzer:        | Administrator                                                                                                     |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Berechtigungen konfigurieren" klickt.          |
|                              |                                                                                                                   |

#### \<UC.004>: Rollen für Identitäten zuweisen

| Verwandter Business Process: | \<BP.003>: Verwaltung von Benutzeridentitäten und Rollenbasierter Zugriffssteuerung                                                                                                                                                               |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Das Identitätsmanagement wird von einem Identitätsanbieter (Keycloak) durchgeführt. Der IdP stellt ein Access Token zur Verfügung, das für den AAS-Server relevante Angaben enthält. Das Token (JWT, JSON Web Token) wird vom IdP signiert. Jeder |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                                                                                                                                                  |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen.                                                                                                                                 |
| Erfolgskriterium:            | Die Benutzer bekommen nach dem Einloggen die vorgesehenen Berechtigungen.                                                                                                                                                                         |
| Involvierte Benutzer:        | Benutzer                                                                                                                                                                                                                                          |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Berechtigungen konfigurieren" klickt.                                                                                                                                          |
|                              |                                                                                                                                                                                                                                                   |

#### \<UC.005>: Zugangsrichtlinien exportieren und importieren

| Verwandter Business Process: | \<BP.004>: Verwaltung von Zugangsrichtlinien durch Import und Export                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Eintrittsfall:               | Der Administrator möchte aktuelle Zugriffsrichtlinien exportieren oder neue importieren .                                                        |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                                                 |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen.                                |
| Erfolgskriterium:            | Die Zugangsrichtlinien wurden vollständig und richtig importiert oder exportiert .                                                               |
| Involvierte Benutzer:        | Administrator                                                                                                                                    |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Zugangsrichtlinien importieren" oder "Zugangsrichtlinien exportieren" klickt. |
|                              |                                                                                                                                                  |

### Voraussetzungen

#### /REQ10/ Policy-Speicherung

Die Policy-Speicherung muss eine effiziente und zuverlässige Verwaltung von Zugangsrichtlinien gewährleisten.

#### /REQ20/ Policy-Abbildung

Die Policy-Abbildung muss sicherstellen, dass Zugangsrichtlinien klar und konsistent auf die entsprechenden Ressourcen, Benutzer und Rollen im System abgebildet werden.

#### /REQ30/ Policy-Entscheidung

Die Policy-Entscheidung muss sicherstellen, dass das System auf Basis vordefinierter Zugangsrichtlinien automatisch Entscheidungen über den Zugriff auf Ressourcen trifft.

### Nicht-funktionale Voraussetzungen

Dieser Abschnitt beschreibt die bereits bekannten nicht-funktionalen Anforderungen an das Produkt.

#### /NF10/ Intuitive Konfiguration von Rollen und Rechten

Die intuitive Konfiguration von Rollen und Rechten erfordert, dass das System eine leicht verständliche Benutzeroberfläche bereitstellt, die es Administratoren und anderen befugten Benutzern ermöglicht, Zugriffsrechte und Rollen ohne tiefgehende technische Kenntnisse zu verwalten.

#### /NF20/ Benutzerfreundliche Oberfläche zur Verwaltung von Identitäten

Das System muss eine benutzerfreundliche Oberfläche zur Verwaltung von Identitäten bereitstellen, die es Administratoren und befugten Benutzern ermöglicht, Identitäten einfach zu erstellen, zu bearbeiten, zu deaktivieren oder zu löschen. Die Oberfläche soll klar strukturiert und intuitiv zu bedienen sein, sodass auch Benutzer ohne technische Expertise die Identitätsverwaltung effizient durchführen können.

#### /NF30/ Einfacher Import/Export von Zugangsrichtlinien.

Das System muss die Möglichkeit bieten, Zugangsrichtlinien einfach und effizient zu importieren und zu exportieren. Dieser Vorgang sollte über eine benutzerfreundliche Oberfläche erfolgen, die klar strukturierte Schritte zur Auswahl und Durchführung des Imports oder Exports bietet. Es muss sichergestellt sein, dass Administratoren ohne umfangreiche technische Kenntnisse diese Funktion nutzen können.
