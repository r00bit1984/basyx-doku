---
description: >-
  Am 11.11.2024 wurde ein Meeting mit zwei Mitarbeitern des Fraunhofer Instituts
  gehalten. In diesem wurden Fragen geklärt und grundlegend etabliert, wie die
  Umsetzung des Plugins technisch erfolgt.
icon: info
---

# Informationen zur Umsetzung

## Informationen für die Umsetzung

* **RBAC** (Role Based Access Control) ist auf zwei Wegen umsetzbar
* Konfigurationsdateien aktueller Weg (JSON, für Rollen, welche Rollen gibt es und welche Rechte haben diese)
* BaSyxSecure setup wichtig um RBAC zu verstehen (dort gibt es beispielhafte Rules)\
  &#x20;[repo](https://github.com/eclipse-basyx/basyx-java-server-sdk/tree/main/examples/BaSyxSecured)
* Voraussetzung: Rollenkofigurationen dynamisch und grafisch anpassen können
* In den **nächsten zwei Wochen wird ein Beispiel** für die Umsetzung von RBAC in BaSyx bereitsgestellt.
* **Plugin im Frontend**, greift auf Submodel zu und aktualisert, editiert und löscht dort Eigenschaften
* So eine [Art von Plugin](https://ibb.co/zG95s3Y) wird benötigt.
* Keycloak bereits im upstream BaSyx eingebunden -> alles schon gemacht
* wenn Keycloak über Environment aktiviert, passiert automatisch Redirect auf Keycloak
  * wenn angemeldet dann über UI in BaSyx
* Basyx Datenbanken im Backend sind bereits vorkonfiguriert
* Security Plugin bekommt eigene semanticID

### &#x20;Nützliche Links/Grafiken

* [Dokumentation für die API](http://localhost:8081/swagger-ui/index.html)
* [RBAC Wiki](https://wiki.basyx.org/en/latest/content/user_documentation/basyx_components/v2/submodel_repository/features/authorization.html)

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Schema des RBAC in Basyx</p></figcaption></figure>

### JSON configs in ein Submodel übersetzen

1. Leeres Plugin anlegen (statische Daten)
2. Wenn das funktioniert, Möglichkeit des Bearbeiten des Submodels implementieren
