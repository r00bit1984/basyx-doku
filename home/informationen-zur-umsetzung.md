---
description: >-
  Am 11.11.2024 wurde ein Meeting mit zwei Mitarbeitern des Fraunhofer Instituts
  gehaltten. Bei diesem wurden Fragen geklärt und grundlegend etabliert, wie die
  Umsetzung des Plugins technisch erfolgt.
icon: info
---

# Informationen zur Umsetzung

## Informationen für Umsetzung

* **RBAC** (Role Based Access Control) ist auf zwei Wege umsetzbar
* Konfigurationsdateien aktueller Weg (JSON, Für Rollen, Welche Rollen gibt es und welche Rechte haben diese)
* basyxSecure setup wichtig um RBAC zu verstehen (dort gibt es beispielhafte Rules)\
  &#x20;[repo](https://github.com/eclipse-basyx/basyx-java-server-sdk/tree/main/examples/BaSyxSecured)
* Voraussetzung: Rollenkofigurationen dynamisch und grafisch anpassen können
* In den **nächsten zwei Wochen wird ein Beispiel** für die Umsetzung von RBAC in Basyx bereitsgestellt.
* **Wir machen Plugin im Frontend**, greift zu auf Submodel und aktualisert und editiert und löscht dort Eigenschaften
* So eine [Art von Plugin brauchen](https://ibb.co/zG95s3Y) wird benötigt.
* Keycloak bereits im upstream Basyx eingebunden -> alles schon gemacht, wir müssen nix machen wenn keylcoak über environment aktiviert, passiert automatisch redirect auf keycloak, wennn angemeldet dann über UI in basyx
* Basyx Datenbanken im Backend sind bereits vorkonfiguriert
* Security Plugin bekommt eigenen semanticID http

### &#x20;Nützliche Links/Grafiken

* [Dokumentation für die API](http://localhost:8081/swagger-ui/index.html)
* [RBAC Wiki](https://wiki.basyx.org/en/latest/content/user\_documentation/basyx\_components/v2/submodel\_repository/features/authorization.html)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Schema des RBAC in Basyx</p></figcaption></figure>

### JSON configs in ein Submodel übersetzen

1. Leeres plugin ankegen (statische Daten)
2. Wenn das funktioniert, möglichkeit des bearbeiten des submodels implementieren
