---
icon: js
cover: ../.gitbook/assets/Untitled.png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# WebUI für die Entwicklung aufsetzen

## Installation

### Windows (WSL)

{% hint style="info" %}
Für diese Anleitung muss das Windows Subsystem for Linux (WSL) aktiviert sein
{% endhint %}

{% hint style="info" %}
Falls die Installation von Nodejs mit dieser Methode nicht funktioniert:  [https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl)
{% endhint %}

1. WSL mit Ubuntu als Distro installieren (im Windows Terminal):\
   `wsl --install -d Ubuntu`
2. In Ubuntu alle Packages updaten:\
   `sudo apt update && sudo apt upgrade -y`
3. Über den Package-Manager nodejs und npm installieren:\
   `sudo apt install nodejs npm -y`
4. Über npm yarn installieren:\
   `npm install --global yarn`
5. Mit Hilfe von git das benötigte Repo klonen (in Ubuntu WSL):\
   `git clone https://github.com/eclipse-basyx/basyx-aas-web-ui`
6. In das geklonte Repo navigieren:\
   `cd basyx-aas-web-ui`
7. Das Bootstrap Shell-Skript ausführen:\
   `sh bootstrap.sh`
8. Die erste Frage mit `y` und die zweite mit `n` beantworten&#x20;
9. Visual Studio Code öffnen
10. `STRG + SHIFT + P`
11. `Connect to WSL using Distro > Ubuntu`
12. `Open Folder...`
13. `aas-web-ui` auswählen
14. Die WebUI sollte auf [http://localhost:3000/aasviewer](http://localhost:3000/aasviewer) laufen
15. Zum Schließen: <kbd>CTRL + C</kbd>&#x20;
16. Um WSL in VSCode zu schließen: Unten Links auf `WSL:Ubuntu` und dann `Close Remote Connection`

### macOS

{% hint style="info" %}
Es wird davon ausgegangen, dass homebrew ([https://brew.sh/](https://brew.sh/)) bereits installiert ist
{% endhint %}

1. Node und npm mit Hilfe von homebrew installieren:\
   `brew install nodejs`&#x20;
2. Über npm yarn installieren:\
   `npm install --global yarn`
3. Mit Hilfe von git das benötigte Repo klonen:\
   `git clone`[`https://github.com/eclipse-basyx/basyx-aas-web-ui.git`](https://github.com/eclipse-basyx/basyx-aas-web-ui.git)
4. In das geklonte Repo navigieren:\
   `cd basyx-aas-web-ui`
5. Das Bootstrap Shell-Skript ausführen:\
   `sh bootstrap.sh`
6. Die erste Frage mit `y` und die zweite mit `n` beantworten&#x20;
7. Die WebUI sollte auf [http://localhost:3000/aasviewer](http://localhost:3000/aasviewer) laufen
8. Zum Schließen: <kbd>CTRL + C</kbd> in Ubuntu WSL

### Linux

{% hint style="info" %}
Mehr Infos zur Installation: [https://nodejs.org/en/download/package-manager/current](https://nodejs.org/en/download/package-manager/current)
{% endhint %}

1. Node und npm über den Paketmanager der verwendeten Distribution installieren, Beispiel für apt:\
   `sudo apt install nodejs npm -y`
2. Über npm yarn installieren:\
   `npm install --global yarn`
3. Mit Hilfe von git das benötigte Repo klonen:\
   `git clone`[`https://github.com/eclipse-basyx/basyx-aas-web-ui.git`](https://github.com/eclipse-basyx/basyx-aas-web-ui.git)
4. In das geklonte Repo navigieren:\
   `cd basyx-aas-web-ui`
5. Das Bootstrap Shell-Skript ausführen:\
   `sh bootstrap.sh`
6. Die erste Frage mit `y` und die zweite mit `n` beantworten&#x20;
7. Die WebUI sollte auf [http://localhost:3000/aasviewer](http://localhost:3000/aasviewer) laufen
8. Zum Schließen: <kbd>CTRL + C</kbd>&#x20;

## WebUI erneut starten

Um die WebUI wieder zu starten muss wieder das Skript mit

```
sh bootstrap.sh
```

ausgeführt werden.

Hierbei jedoch beide Fragen mit `n` beantworten.&#x20;
