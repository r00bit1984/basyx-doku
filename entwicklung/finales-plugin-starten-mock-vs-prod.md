---
icon: puzzle-piece-simple
---

# Finales Plugin starten (MOCK vs PROD)

## Setup-Anleitung

Diese Anleitung beschreibt, wie man das Projekt für Mock- und Produktionsumgebungen einrichtet und startet.

### Übersicht der Umgebungen

#### **Mockup-Umgebung**

Die Mockup-Umgebung wird für Demonstrations- und Entwicklungszwecke genutzt. In dieser Umgebung werden **keine API-Calls** an externe Server durchgeführt. Stattdessen werden gemockte Daten lokal in einem Array gespeichert und verwendet. Dies ermöglicht eine einfache und schnelle Simulation ohne Abhängigkeit von einer Backend-API.

{% hint style="info" %}
Die API-Calls können aufgrund eines BaSyx-Bugs nicht gemacht werden.

Dazu wurde bereits ein [Issue](https://github.com/eclipse-basyx/basyx-java-server-sdk/issues/707) auf dem passenden Repository erstellt.
{% endhint %}

#### **Produktionsumgebung**

Die Produktionsumgebung ist für den realen Einsatz vorgesehen. In dieser Umgebung werden echte **API-Calls** an das Backend durchgeführt, um mit echten Daten zu arbeiten. Diese Umgebung ist für Live-Betrieb und praxisnahe Tests gedacht. Durch den erwähnten Bug wird hier jedoch eine Fehlermeldung angezeigt.

***

### Setup und Start

Unabhängig von der Umgebung können beide Umgebungen über den Ordner `03_Entwicklung/dev` gestartet werden. Es stehen zwei Methoden zur Verfügung:

#### **1. Starten mit `yarn`**

1.  **In den Ordner wechseln:**\
    Navigiere in das Verzeichnis `03_Entwicklung/dev`:

    ```bash
    cd dev
    ```
2.  **Abhängigkeiten installieren:**\
    Falls noch nicht geschehen, installiere die notwendigen Pakete:

    ```bash
    yarn
    ```
3.  **Entsprechende Umgebung starten:**

    Umgebung starten:

    ```bash
    yarn dev
    ```

#### 2. Starten mit bootstrap.sh (Nur Linux/macOS oder WSL)

**In** `03_Entwicklung/dev` **wechseln:**

```
sh bootstrap.sh
```
