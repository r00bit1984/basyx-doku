---
icon: puzzle-piece-simple
---

# Finales Plugin starten (MOCK vs PROD)

## Setup-Anleitung

Diese Anleitung beschreibt, wie man das Projekt für Mock- und Produktionsumgebungen einrichtet und startet.

### Übersicht der Umgebungen

#### **Mockup-Umgebung (/mock)**

Die Mockup-Umgebung wird für Demonstrations- und Entwicklungszwecke genutzt. In dieser Umgebung werden **keine API-Calls** an externe Server durchgeführt. Stattdessen werden gemockte Daten lokal in einem Array gespeichert und verwendet. Dies ermöglicht eine einfache und schnelle Simulation ohne Abhängigkeit von einer Backend-API.

{% hint style="info" %}
Die API-Calls können aufgrund eines BaSyx-Bugs nicht gemacht werden.

Dazu wurde bereits ein [Issue](https://github.com/eclipse-basyx/basyx-java-server-sdk/issues/707) auf dem passenden Repository erstellt.
{% endhint %}

#### **Produktionsumgebung (/production)**

Die Produktionsumgebung ist für den realen Einsatz vorgesehen. In dieser Umgebung werden echte **API-Calls** an das Backend durchgeführt, um mit echten Daten zu arbeiten. Diese Umgebung ist für Live-Betrieb und praxisnahe Tests gedacht.

***

### Setup und Start

Unabhängig von der Umgebung können beide Umgebungen über den Ordner `/aas-web-ui` gestartet werden. Es stehen zwei Methoden zur Verfügung:

#### **1. Starten mit `yarn`**

1.  **In den Ordner wechseln:**\
    Navigiere in das Verzeichnis `/aas-web-ui`:

    ```bash
    cd aas-web-ui
    ```
2.  **Abhängigkeiten installieren:**\
    Falls noch nicht geschehen, installiere die notwendigen Pakete:

    ```bash
    yarn install
    ```
3.  **Entsprechende Umgebung starten:**

    Umgebung starten:

    ```bash
    yarn dev
    ```

#### 2. Starten mit bootstrap.sh

**In `/mock` bzw. `/production` wechseln:**

```
sh bootstrap.sh
```
