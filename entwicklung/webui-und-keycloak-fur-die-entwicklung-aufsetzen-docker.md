---
icon: docker
cover: >-
  https://images.unsplash.com/photo-1697058149199-bc6d94639a82?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxkb2NrZXJ8ZW58MHx8fHwxNzI5Nzk4OTIyfDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# WebUI und Keycloak für die Entwicklung aufsetzen (Docker)

1. Die benötigten Repos (lokal klonen mit `git clone`):\
   [https://github.com/eclipse-basyx/basyx-aas-web-ui](https://github.com/eclipse-basyx/basyx-aas-web-ui)\
   [https://github.com/eclipse-basyx/basyx-java-server-sdk.git](https://github.com/eclipse-basyx/basyx-java-server-sdk.git)
2. In dem korrekten Verzeichnis (basyx-aas-web-ui/aas-web-ui) `docker build` machen:\
   `docker build aas-web-ui -t eclipsebasyx/aas-ui:latest`
3. Die Container starten: (in basyx-java-server-sdk/examples/BaSyxSecured)\
   `docker compose up -d`
4. Die UI läuft auf Port `3000`, Keycloak auf `9097`
5. Wenn Änderungen an der WebUI vorgenommen werden:\
   &#xNAN;_(In basyx-java-server-sdk/examples/BaSyxSecured):_\
   `docker compose down`\
   &#xNAN;_(In basyx-aas-web-ui/aas-web-ui):_\
   `docker build aas-web-ui -t eclipsebasyx/aas-ui:latest`    \
   &#xNAN;_(In basyx-java-server-sdk/examples/BaSyxSecured):_\
   `docker compose up -d`
