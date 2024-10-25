---
icon: docker
cover: >-
  https://images.unsplash.com/photo-1697058149199-bc6d94639a82?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxkb2NrZXJ8ZW58MHx8fHwxNzI5Nzk4OTIyfDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# WebUI für die Entwicklung aufsetzen (Docker)

1. Das benötigte Repo der [https://github.com/eclipse-basyx/basyx-aas-web-ui](https://github.com/eclipse-basyx/basyx-aas-web-ui)
2. In dem korrekten Verzeichnis (basyx-aas-web-ui/aas-web-ui) `docker build` machen:\
   `docker build aas-web-ui -t eclipsebasyx/aas-ui:latest`
3. Die Container starten:\
   `docker compose up -d`
4.
