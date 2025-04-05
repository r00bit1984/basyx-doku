---
description: >-
  Eine der Anforderungen an unser Projekt ist ein funktionelles Hosting, das die
  Möglichkeiten unseres  Plugins präsentiert.
icon: microsoft
---

# Funktionelles Hosting

{% hint style="info" %}
Verantwortlicher: Robert L.
{% endhint %}

Diese Seite soll ein wenig technischen Hintergrund geben, wie wir ein funktionelles Hosting erreicht haben. Für das Hosten der BaSyx-UI haben wir uns für eine VM auf Microsofts Cloud-Anbieter [Azure](https://azure.microsoft.com/en-us) entschieden, da dieser ein Kontingent von 100$ für Studenten bereitstellt.&#x20;

## Erste Versuche und Tests

### Azure VM Setup

1. **Erstellen der VM**: Ich habe mich bei meinem Azure-Konto angemeldet und eine neue virtuelle Maschine erstellt. Dabei habe ich mich für eine Ubuntu und erstmal 1gb RAM entschieden,.

### DNS-Konfiguration mit Cloudflare

1. Ich habe mich bei Cloudflare angemeldet und meine Domain hinzugefügt.
2. Dort wurde dann ein `A` Eintrag mit der öffentlichen IPv4 meiner VM erstellt.
3. Die Ports `443` und `80` wurden in der Azure WebUI geöffnet. Diese müssen offen sein, damit Caddy ein SSL Zertifikat bei _Let's Encrypt_ erfolgreich anfordern kann.

### TLS-Zertifikate mit Caddy

1. Ich habe mich in meine VM eingeloggt und Caddy installiert. Dazu bin ich den Anweisungen auf [dieser Seite gefolgt.](https://caddyserver.com/docs/install#debian-ubuntu-raspbian)
2. Caddyfile schreiben:

{% code lineNumbers="true" %}
```json
basichs.goofyboxd.space {
	reverse_proxy localhost:3000
	log {
		output file /var/log/caddy/access.log
	}
	tls <meine-email@example.com>
}
```
{% endcode %}

* Der lokale Dienst (die BaSyx WebUI) läuft auf Port 3000
* Caddy dient als [Reverse Proxy](https://en.wikipedia.org/wiki/Reverse_proxy) und stellt mir ein SSL Zertifikat für HTTPS zur Verfügung
* Caddy liefert den content auf Port 443 (HTTPS)
* In Azure muss Port 443 offen sein, nicht Port 3000

{% hint style="info" %}
Durch die Kombination aus Azure, Cloudflare und Caddy habe ich eine stabile Base mit der ich Seiten mit HTTPS-Unterstützung hosten kann.&#x20;
{% endhint %}

### Probleme

* Erste Tests zeigten, dass 1gb an RAM absolut nicht ausreichend sind. Sobald die Website [basichs.goofyboxd.space](https://basichs.goofyboxd.space) in einem Webbrowser aufgerufen wurde, ist die Azure VM gecrashed.
* In der Azure WebUI habe ich den RAM + die CPU geupgradet, jedoch sind die monatlichen Kosten nun etwa **35$**
  * Das hat zur Folge, dass der Server nun die meinste Zeit offline ist, um Kosten zu sparen



