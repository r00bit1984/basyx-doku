---
icon: folder-grid
---

# Lastenheft

## Lastenheft

**Verantwortlich**: Lukas G.

...

[Link zum Lastenheft](https://basyx.mausserver.xyz/analyse/lastenheft#lastenheft)

### Changelog

| **Version** | **Datum**  | **Autor** | **Kommentar**                                                                                                                  |
| ----------- | ---------- | --------- | ------------------------------------------------------------------------------------------------------------------------------ |
| 0.1         | 04.10.2024 | Felix     | Erstellt, erster Entwurf                                                                                                       |
| 0.2         | 17.10.2024 | Lukas     | Ziel, Produktverwendung, Geschäftsprozesse, Anwendungsfälle, Voraussetzungen und nicht-funktionale Voraussetzungen hinzugefügt |
| 0.3         | 18.10.2024 | Lukas     | Produktumgebung, Abgrenzung und Risiken hinzugefügt                                                                            |

### Inhaltsverzeichnis

* [Ziel](https://basyx.mausserver.xyz/analyse/lastenheft#ziel)
* [Produktumgebung](https://basyx.mausserver.xyz/analyse/lastenheft#produktumgebung)
* [Produktverwendung](https://basyx.mausserver.xyz/analyse/lastenheft#produktverwendung)
  * [Geschäftsprozesse](https://basyx.mausserver.xyz/analyse/lastenheft#geschaftsprozesse)
    * \[\<BP.001>: Verwaltung und Konfiguration von Rollen]
    * \[\<BP.002>: Konfiguration von Zugriffsrechten und Berechtigungsstrukturen]
    * \[\<BP.003>: Verwaltung von Benutzeridentitäten und rollenbasierter Zugriffssteuerung]
    * \[\<BP.004>: Verwaltung von Zugangsrichtlinien durch Import und Export]
  * [Anwendungsfälle](https://basyx.mausserver.xyz/analyse/lastenheft#anwendungsfalle)
    * \[\<UC.001>: Rollen konfigurieren]
    * \[\<UC.002>: Rollen verwalten]
    * \[\<UC.003>: Zugriffsrechte zuweisen]
    * \[\<UC.004>: Zugangsrichtlinien exportieren und importieren]
  * [Voraussetzungen](https://basyx.mausserver.xyz/analyse/lastenheft#voraussetzungen)
    * \[/REQ10/ Policy-Speicherung]
    * \[/REQ20/ Policy-Abbildung]
    * \[/REQ30/ Policy-Entscheidung]
* [Nicht-funktionale Voraussetzungen](https://basyx.mausserver.xyz/analyse/lastenheft#nicht-funktionale-voraussetzungen)
  * \[/NF10/ Intuitive Konfiguration von Rollen und Rechten]
  * \[/NF20/ Benutzerfreundliche Oberfläche zur Verwaltung von Identitäten]
  * \[/NF30/ Einfacher Import/Export von Zugangsrichtlinien]

### Ziel

[Link zum Ziel](https://basyx.mausserver.xyz/analyse/lastenheft#ziel)

Das Ziel dieses Projekts ist die Entwicklung eines Security-Plugins für das BaSyx-UI, das rollenbasierte Zugriffssteuerungen zur Verwaltung von Zugangsrichtlinien für einzelne AAS-Elemente unterstützt.

### Produktumgebung

[Link zur Produktumgebung](https://basyx.mausserver.xyz/analyse/lastenheft#produktumgebung)

BaSyx ist ein Open-Source-Projekt der Plattform Industrie 4.0, das die Verwaltung von Industriekomponenten durch digitale Zwillinge unterstützt und standardisierte Schnittstellen sowie Beispielmodellierungen bereitstellt. Das Ziel von BaSyx ist es, die Interoperabilität und Flexibilität von Produktionsketten zu fördern, indem es eine offene Plattform zur Verwaltung und Integration von Industrie-4.0-kompatiblen Lösungen bietet. Innerhalb dieser BaSyx-Umgebung soll ein Security-Plugin entwickelt werden, das ein gemeinsames Verständnis von Security in der Verwaltungsschale ermöglicht.

### Produktverwendung

[Link zur Produktverwendung](https://basyx.mausserver.xyz/analyse/lastenheft#produktverwendung)

Die folgenden Geschäftsprozesse und Anwendungsfälle beschreiben die vom System zu unterstützenden Funktionen.

### Geschäftsprozesse

[Link zu den Geschäftsprozessen](https://basyx.mausserver.xyz/analyse/lastenheft#geschaftsprozesse)

#### \<BP.001>: Verwaltung und Konfiguration von Rollen

| **Feld**             | **Beschreibung**                                                                                                 |
| -------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Auslösendes Ereignis | Der Administrator möchte Rollen konfigurieren und verwalten                                                      |
| Resultat             | Der Administrator kann im entsprechenden Bereich Rollen für alle Benutzer vergeben, konfigurieren und verwalten. |
| Involvierte Rollen   | Administrator                                                                                                    |

#### \<BP.002>: Konfiguration von Zugriffsrechten und Berechtigungsstrukturen

| **Feld**             | **Beschreibung**                                                                                            |
| -------------------- | ----------------------------------------------------------------------------------------------------------- |
| Auslösendes Ereignis | Der Administrator möchte den Rollen Berechtigungen zuweisen                                                 |
| Resultat             | Der Administrator kann im entsprechenden Bereich Berechtigungen für alle Rollen vergeben und konfigurieren. |
| Involvierte Rollen   | Administrator                                                                                               |

#### \<BP.003>: Verwaltung von Benutzeridentitäten und rollenbasierter Zugriffssteuerung

| **Feld**             | **Beschreibung**                                                                                         |
| -------------------- | -------------------------------------------------------------------------------------------------------- |
| Auslösendes Ereignis | Ein Benutzer soll nach dem Login automatisch die für seine Rolle vorgesehenen Berechtigungen erhalten    |
| Resultat             | Das System vergibt nach der Authentifizierung des Benutzers automatisch die vorgesehenen Berechtigungen. |
| Involvierte Rollen   | Administrator                                                                                            |

### Anwendungsfälle

#### \<UC.001>: Rollen konfigurieren

[Link zu den Anwendungsfällen](https://basyx.mausserver.xyz/analyse/lastenheft#anwendungsfalle)

| **Feld**             | **Beschreibung**                                                                                       |
| -------------------- | ------------------------------------------------------------------------------------------------------ |
| Verwandter Prozess   | \<BP.001>: Verwaltung und Konfiguration von Rollen                                                     |
| Eintrittsfall        | Der Administrator möchte eine neue Rolle konfigurieren.                                                |
| Systemgrenzen        | Die Konfigurationen in Keycloak.                                                                       |
| Vorbedingung         | Der Administrator muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium     | Die neu konfigurierte Rolle ist in Keycloak hinterlegt und die Änderungen wurden wirksam.              |
| Involvierte Benutzer | Administrator                                                                                          |
| Auslösendes Ereignis | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Rolle konfigurieren" klickt.        |

#### \<UC.002>: Rollen verwalten

| **Feld**             | **Beschreibung**                                                                                       |
| -------------------- | ------------------------------------------------------------------------------------------------------ |
| Verwandter Prozess   | \<BP.001>: Verwaltung und Konfiguration von Rollen                                                     |
| Eintrittsfall        | Der Administrator möchte eine bestehende Rolle verwalten.                                              |
| Systemgrenzen        | Die Konfigurationen in Keycloak.                                                                       |
| Vorbedingung         | Der Administrator muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium     | Die bearbeitete Rolle ist in Keycloak hinterlegt und die Änderungen wurden wirksam.                    |
| Involvierte Benutzer | Administrator, Benutzer                                                                                |
| Auslösendes Ereignis | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Neue Rolle vergeben" klickt.        |

#### \<UC.003>: Zugriffsrechte zuweisen

| **Feld**             | **Beschreibung**                                                                                         |
| -------------------- | -------------------------------------------------------------------------------------------------------- |
| Verwandter Prozess   | \<BP.002>: Konfiguration von Zugriffsrechten und Berechtigungsstrukturen                                 |
| Eintrittsfall        | Der Administrator möchte einer Rolle Zugriffsrechte zuweisen.                                            |
| Systemgrenzen        | Die Konfigurationen in Keycloak.                                                                         |
| Vorbedingung         | Der Administrator muss im System authentifiziert sein und über administrative Berechtigungen verfügen.   |
| Erfolgskriterium     | Die konfigurierten Rechte für die Rolle sind wirksam.                                                    |
| Involvierte Benutzer | Administrator                                                                                            |
| Auslösendes Ereignis | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Berechtigungen konfigurieren" klickt. |

#### \<UC.004>: Zugangsrichtlinien exportieren und importieren

| **Feld**             | **Beschreibung**                                                                                                                                 |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Verwandter Prozess   | \<BP.004>: Verwaltung von Zugangsrichtlinien durch Import und Export                                                                             |
| Eintrittsfall        | Der Administrator möchte aktuelle Zugriffsrichtlinien exportieren oder neue importieren.                                                         |
| Systemgrenzen        | Die Konfigurationen in Keycloak.                                                                                                                 |
| Vorbedingung         | Der Administrator muss im System authentifiziert sein und über administrative Berechtigungen verfügen.                                           |
| Erfolgskriterium     | Die Zugangsrichtlinien wurden vollständig und korrekt importiert oder exportiert.                                                                |
| Involvierte Benutzer | Administrator                                                                                                                                    |
| Auslösendes Ereignis | Wenn der Administrator auf der Webseite im Bereich "Security" auf "Zugangsrichtlinien importieren" oder "Zugangsrichtlinien exportieren" klickt. |

### Voraussetzungen

[Link zu den Voraussetzungen](https://basyx.mausserver.xyz/analyse/lastenheft#voraussetzungen)

#### /REQ10/ Policy-Speicherung

Die Policy-Speicherung muss eine effiziente und zuverlässige Verwaltung von Zugangsrichtlinien gewährleisten.

#### /REQ20/ Policy-Abbildung

Die Policy-Abbildung muss sicherstellen, dass Zugangsrichtlinien klar und konsistent auf die entsprechenden Ressourcen, Benutzer und Rollen im System abgebildet werden.

#### /REQ30/ Policy-Entscheidung

Die Policy-Entscheidung muss sicherstellen, dass das System auf Basis vordefinierter Zugangsrichtlinien automatisch Entscheidungen über den Zugriff auf Ressourcen trifft.

### Nicht-funktionale Voraussetzungen

[Link zu den nicht funktionalen Voraussetzungen](https://basyx.mausserver.xyz/analyse/lastenheft#nicht-funktionale-voraussetzungen)

#### /NF10/ Intuitive Konfiguration von Rollen und Rechten

Die intuitive Konfiguration von Rollen und Rechten erfordert, dass das System eine leicht verständliche Benutzeroberfläche bereitstellt, die es Administratoren und anderen befugten Benutzern ermöglicht, Zugriffsrechte und Rollen ohne tiefgehende technische Kenntnisse zu verwalten.

#### /NF20/ Benutzerfreundliche Oberfläche zur Verwaltung von Identitäten

Das System muss eine benutzerfreundliche Oberfläche zur Verwaltung von Identitäten bereitstellen, die es Administratoren ermöglicht, Identitäten einfach zu erstellen, zu bearbeiten, zu deaktivieren oder zu löschen. Die Oberfläche soll klar strukturiert und intuitiv zu bedienen sein, sodass auch Benutzer ohne technische Expertise die Identitätsverwaltung effizient durchführen können.

#### /NF30/ Einfacher Import/Export von Zugangsrichtlinien

Das System muss die Möglichkeit bieten, Zugangsrichtlinien einfach und effizient zu importieren und zu exportieren. Dieser Vorgang sollte über eine benutzerfreundliche Oberfläche erfolgen, die klar strukturierte Schritte zur Auswahl und Durchführung des Imports oder Exports bietet. Es muss sichergestellt sein, dass Administratoren ohne umfangreiche technische Kenntnisse diese Funktion nutzen können.

### Abgrenzung

Das Plugin wird ausschließlich in der BaSyx-Umgebung und zur Verwaltung von Zugangsrichtlinien für AAS-Elemente verwendet. Es wird keine universelle IAM-Lösung entwickelt, sondern nur ein spezifisches Plugin zur Ergänzung des bestehenden BaSyx-Frameworks. Externe Schnittstellen wie andere Identity-Provider (z. B. LDAP) werden nicht implementiert.

### Risiken

1. **Komplexität der Integration**: Die Integration in das bestehende BaSyx-UI könnte durch technische Schwierigkeiten oder unvollständige Dokumentationen problematisch werden
2. **Benutzerakzeptanz**: Die Komplexität der Benutzeroberfläche könnte zu Akzeptanzproblemen bei den Administratoren führen
3. **Performance**: Die Echtzeitverarbeitung von Zugriffsentscheidungen muss mit den anderen Komponenten im System koordiniert werden, um Performance-Probleme zu vermeiden
4. **Sicherheitsrisiken**: Unsachgemäß konfigurierte Rollen und Rechte können Sicherheitslücken im System verursachen
