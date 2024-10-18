# Lastenheft

## Lastenheft

Verantwortlich: Lukas

...

### Changelog

| _Version_ | _Date_     | _Author_              | _Comment_                                                                           |
| --------- | ---------- | --------------------- | ----------------------------------------------------------------------------------- |
| 0.1       | 04.10.2024 | Felix, Moritz, Jannik | Created, first draft                                                                |
| 0.2       | 17.10.2024 | Lukas, Jannik         | Goal, Product Usage, Business Processes, Use Case, Requirements, Product Data added |

### Goal

Ziel dieses Projekts ist die Entwicklung eines Security-Plugins für das BaSyx-UI. Dieses soll mit Unterstützung von rollenbasierten Zugriffssteuerungen zur Verwaltung von Zugangsrichtlinien für einzelne AAS-Elemente erfolgen.

### Product Environment

BaSyx-Umgebung beschreiben: Zweck --> von BaSyx auf die Verwaltungsschale überleiten und erklären

### Product Usage

Die folgenden Business Processes und Use Cases beschreiben die Funktionen die das System unterstützen soll.

### Business Processes

#### \<BP.001>: Rollen neu vergeben, verwalten und konfigurieren

| Auslösendes Ereignis: | Der Administrator möchte Rollen neu vergeben, konfigurieren und verwalten                                                   |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator kann in einem speziellen Bereich die Rollen für sämtliche Benutzer vergeben, konfigurieren und verwalten. |
| Involvierte Rollen:   | Administrator                                                                                                               |

#### \<BP.002>: Rechtezuweisungen konfigurieren

| Auslösendes Ereignis: | Der Administrator möchte den Rollen Berechtigungen zuweisen                                                            |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator kann in einem speziellen Bereich die Berechtigungen für sämtliche Rollen vergeben und konfigurieren. |
| Involvierte Rollen:   | Administrator                                                                                                          |

#### \<BP.003>: Identitäten verwalten und zu Rollen zuordnen

| Auslösendes Ereignis: | Der Administrator möchte den Rollen Berechtigungen zuweisen                                                             |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator kann in einem speziellen Bereich die Berechtigungen für sämtliche Rollen vergeben, und konfigurieren. |
| Involvierte Rollen:   | Administrator                                                                                                           |

#### \<BP.004>: Import/Export von Zugangsrichtlinien

| Auslösendes Ereignis: | Der Administrator möchte Zugangsrichtlinien in Keycloak importieren oder exportieren                                        |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Resultat:             | Der Administrator über eine Schnittstelle im Keycloak die aktuelle Zugangsrichtline exportieren oder eine neue importieren. |
| Involvierte Rollen:   | Administrator                                                                                                               |

### Use Cases

#### \<UC.001>: Rollen neu vergeben

| Verwandter Business Process: | \<BP.001>: Rollen neu vergeben, verwalten und konfigurieren                                                                             |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Der Administrator möchte einem neuen Benutzer eine neue Rolle zuweisen.                                                                 |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                                        |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen.                       |
| Erfolgskriterium:            | Die neu vergebene Rolle ist in Keycloak hinterlegt und der betroffene Benutzer kann auf die entsprechenden Berechtigungen zurückgreifen |
| Involvierte Benutzer:        | Administrator und ein Benutzer.                                                                                                         |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf "neue Rolle vergeben" klickt.                                         |

#### \<UC.002>: Rollen konfigurieren

| Verwandter Business Process: | \<BP.001>: Rollen neu vergeben, verwalten und konfigurieren                                                       |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Der Administrator möchte eine neue Rolle konfigurieren.                                                           |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                  |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium:            | Die neu konfigurierte Rolle ist in Keycloak hinterlegt und die Änderungen an der Rolle wurden wirksam.            |
| Involvierte Benutzer:        | Administrator.                                                                                                    |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf " Rolle konfigurieren" klickt.                  |
|                              |                                                                                                                   |

#### \<UC.003>: Rollen verwalten

| Verwandter Business Process: | \<BP.001>: Rollen neu vergeben, verwalten und konfigurieren                                                       |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Eintrittsfall:               | Der Administrator möchte eine bestehende Rolle verwalten.                                                         |
| Systemgrenzen:               | Die Konfigurationen in Keycloak.                                                                                  |
| Vorbedingung:                | Der konfigurierende Benutzer muss im System authentifiziert sein und über administrative Berechtigungen verfügen. |
| Erfolgskriterium:            | Die bearbeitete Rolle ist in Keycloak hinterlegt und die Änderungen wurden wirksam.                               |
| Involvierte Benutzer:        | Ein Administrator und ein Benutzer.                                                                               |
| Auslösendes Ereignis:        | Wenn der Administrator auf der Webseite im Bereich "Security" auf "neue Rolle vergeben" klickt.                   |
|                              |                                                                                                                   |

* **Rollen konfigurieren**: Verwaltung von Rollen für verschiedene Nutzergruppen.
* **Rechtezuordnungen konfigurieren**: Zugriffskontrollen auf AAS-, Submodell- und Attributebene festlegen.
* **Identitäten zuordnen und verwalten**: Verwaltung von Nutzeridentitäten und Zuweisung von Rollen.
* **Import/Export von Zugangsrichtlinien**: Schnittstellen zu Authorisierungs-Servern (z.B. Keycloak) ermöglichen.

### Requirements

#### /REQ10/ Import server

The webpage should be able to import a server by its URL and display its content.

#### /REQ20/ Server validation

The system shall be able to detect false server-URLs when adding a new server and throw an error to the user.

#### /REQ30/ Error handling

The system shall be able to handle errors (no entries found, unexpected errors, false server-ULR, ...)

and throw an error to the user.

#### /REQ40/ Display content in a clear way

The entries including the digital twins are shown in a clear and readable way as a list one entry under the other while more information can be seen when clicking on the asset.

#### /REQ50/ Display digital twin

The user should be able to see more information about the digital twin.

#### /REQ60/ Sort by year

The user should be able to sort the displayed assets by manufacturing year.

#### /REQ70/ Filter for manufacturer

The user should be able to filter the assets by manufacturer.

#### /REQ80/ Search for digital twin

The user should be able to search for digital twins by entering the name of the asset.

### Product Data

### /LD10/ Data

The data displayed in the webpage is delivered through an AAS-Server with REST-Calls. There is no functionality to export data or import other data than an AAS-Server by its URL.

### Other Product Characteristics

This section describes the already known non-functional requirements for the product.

#### /NF10/ Intuitive GUI

The webpage shall display a graphical user interface (GUI) to the user. This GUI must display every function provided to the user in a simple and intuitive way. It will be the only way to interact with the application.

#### /NF20/ Browser

The webpage shall work in every Browser supporting the HTML 5 standard.

#### /NF30/ Efficiency

The webpage shall add servers and apply filters in the fastest way possible as well as the user being able to find desired results with the lowest possible amount of steps.

#### /NF40/ Usability

A user searching a specific product shall find that product as fast as possible, intuitively know how the webpage works and there shall be enough online documentation for new users. No further training or experience is required.
