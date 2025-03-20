---
description: Eine kurze Übersicht über häufig aufkommende HTTP Response Codes
icon: browser
---

# HTTP Response Codes

#### **1xx - Informational**

* **100 Continue**: Die Anfrage wurde empfangen, der Client kann fortfahren
* **101 Switching Protocols**: Der Server akzeptiert den Protokollwechsel

***

#### **2xx - Success**

* **200 OK**: Die Anfrage war erfolgreich
* **201 Created**: Eine Ressource wurde erfolgreich erstellt
* **202 Accepted**: Die Anfrage wurde akzeptiert, aber noch nicht verarbeitet
* **204 No Content**: Erfolgreich, aber es gibt keine Rückgabe

***

#### **3xx - Redirection**

* **301 Moved Permanently**: Die Ressource wurde dauerhaft verschoben
* **302 Found**: Die Ressource wurde vorübergehend umgeleitet
* **304 Not Modified**: Die Ressource wurde nicht geändert

***

#### **4xx - Client Error**

* **400 Bad Request**: Fehlerhafte Anfrage des Clients
* **401 Unauthorized**: Authentifizierung erforderlich
* **403 Forbidden**: Zugriff verweigert, obwohl authentifiziert
* **404 Not Found**: Ressource nicht gefunden
* **405 Method Not Allowed**: HTTP-Methode wird nicht unterstützt

***

#### **5xx - Server Error**

* **500 Internal Server Error**: Allgemeiner Serverfehler
* **501 Not Implemented**: Funktionalität wird vom Server nicht unterstützt
* **502 Bad Gateway**: Ungültige Antwort vom Upstream-Server
* **503 Service Unavailable**: Server ist vorübergehend nicht verfügbar
