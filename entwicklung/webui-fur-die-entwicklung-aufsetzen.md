---
icon: brackets-curly
---

# WebUI für die Entwicklung aufsetzen

## Windows (WSL)

{% hint style="info" %}
Für diese Anleitung muss das Windows Subsystem for Linux (WSL) aktiviert sein
{% endhint %}

1. Ubuntu installieren über WSL (Windows Terminal):\
   `wsl --install -d Ubuntu`
2. In Ubuntu alle Packages updaten:\
   `sudo apt update && sudo apt upgrade -y`
3. Über den Package-Manager nodejs und npm installieren:\
   `sudo apt install nodejs npm -y`
4. Über npm yarn installieren:\
   `npm install --global yarn`
5. Mit Hilfe von git das benötigte Repo klonen (in Ubuntu WSL):\
   `git clone` [`https://github.com/eclipse-basyx/basyx-aas-web-ui.git`](https://github.com/eclipse-basyx/basyx-aas-web-ui.git)
6. In das geklonte Repo navigieren:\
   `cd basyx-aas-web-ui`
7. Das Bootstrap Shell-Skript ausführen:\
   `sh bootstrap.sh`
8. Die erste Frage mit `y` und die zweite mit `n` beantworten&#x20;
9. Visual Studio Code öffnen
10. `STRG + SHIFT + P`
11. `Connect to WSL using Distro > Ubuntu`
12. `aas-web-ui` auswählen
13. Die WebUI sollte auf [http://localhost:3000/aasviewer](http://localhost:3000/aasviewer) laufen
