---
description: >-
  Überarbeitete Version des Systemtestplans mit Erklärungen und Schritt für
  Schritt Anleitungen für die einzelnen Tests.
icon: flask-vial
---

# Systemtestplan mit Erklärungen

> Verantwortlich: Francesco + Robert

Dieser Testplan beschreibt die Systemtests für das UI-Element `Security.vue`. Ziel ist es, die Funktionalität, Benutzerfreundlichkeit, Sicherheit und Qualität dieses UI-Elements zu überprüfen. Dieser Plan wurde so erstellt, dass auch Personen ohne technischen Hintergrund die Tests einfach durchführen können.

***

### 1. Testumgebung

Die Tests müssen auf verschiedenen Plattformen durchgeführt werden, um sicherzustellen, dass die Anwendung korrekt funktioniert und ein breites Spektrum an Benutzeranforderungen abdeckt.

* **Betriebssysteme**: Windows (10 und höher), macOS, Linux
* **Browser**: Chrome, Firefox, Edge, Safari
* **Bildschirmauflösungen**: 1920x1080 (Desktop), 1366x768 (Laptop), 1280x720 (Tablet und kleinere Bildschirme)
* **Benutzte Frameworks**: Vue.js (Version 3.2.x)

**Hinweis**: Für die Tests benötigen Sie Zugriff auf die Anwendung. Dafür müssen Sie der [Installationsanleitung](https://basyx-security-plugin.gitbook.io/basyx-security/entwicklung/webui-fur-die-entwicklung-aufsetzen) folgen.

***

### 2. Testfälle

#### 3.1 UI-Ladefähigkeit

**Beschreibung:** Sicherstellen, dass die `Security.vue`-Komponente korrekt geladen wird und keine Fehlermeldungen angezeigt werden.

**Schritte:**

1. Öffnen Sie die Anwendung in einem Webbrowser, indem Sie die bereitgestellte URL (meist `localhost:3000`) in die Adresszeile eingeben und die Seite aufrufen.
2. Navigieren Sie zu der Ansicht, die die Komponente `Security.vue` enthält (Oben Links auf `AAS Viewer` —> `Modules` —> `Security`).
3. Prüfen Sie, ob die Seite ohne sichtbare Ladeprobleme (ohne weiße Seite oder Fehlermeldungen) dargestellt wird.

**Kontrolle:**

* Die Seite wird vollständig geladen.
* Es gibt keine Fehlermeldungen (z. B. „Fehler beim Laden der Seite“ oder „Komponente nicht gefunden“).
* Alle sichtbaren Elemente wie Überschriften, Buttons und Formulare sind auf der Seite sichtbar.

***

#### 3.2 Navigation und Benutzerinteraktion

**Beschreibung:** Testen der Funktionalität von Buttons, Links und anderen interaktiven Elementen.

**Schritte:**

1. Klicken Sie auf jede sichtbare Schaltfläche auf der Seite. Beobachten Sie, was passiert (z. B. ob ein neues Fenster geöffnet wird, ob ein Formular abgeschickt wird usw.).
2. Klicken Sie auf alle vorhandenen Links, die auf der Seite `Security.vue` dargestellt werden.
3. Prüfen Sie, ob Dropdown-Menüs oder andere interaktive Elemente (falls vorhanden) wie erwartet reagieren.

**Kontrolle:**

* Jede Schaltfläche führt die beabsichtigte Aktion aus. Beispielsweise sollte „Speichern“ die Eingaben speichern oder „Abbrechen“ das Formular zurücksetzen.
* Links führen Sie zu den erwarteten Seiten ohne Fehlermeldungen.
* Dropdowns oder andere interaktive Elemente reagieren korrekt und ohne Verzögerungen.

***

#### 3.3 Formulareingaben und Validierung

**Beschreibung:** Überprüfen Sie, ob Formulareingabefelder korrekte Daten annehmen und ungültige Eingaben sinnvoll validieren.

**Schritte:**

1. Geben Sie in jedes Eingabefeld absichtlich ungültige Daten ein, z. B. Buchstaben in einem Feld, das nur Zahlen akzeptiert, oder lassen Sie ein Pflichtfeld leer.
2. Klicken Sie auf den „Speichern“-Knopf (oder eine ähnliche Schaltfläche, die das Formular absendet).
3. Beobachten Sie, ob Fehlermeldungen angezeigt werden (z. B. in einem roten Hinweis unter oder über dem Eingabefeld).
4. Geben Sie korrekte Daten in alle Felder ein und senden Sie das Formular erneut ab.
5. Prüfen Sie, ob eine Erfolgsmeldung angezeigt wird oder die erwartete Aktion ausgelöst wird.

**Kontrolle:**

* Fehlerhafte Eingaben führen zu deutlich erkennbaren Fehlermeldungen.
* Korrekte Eingaben werden ohne Fehler angenommen, und die Daten werden verarbeitet.

Beispiel: Wenn ein Feld nur Zahlen akzeptiert und Sie „abc“ eingeben, sollte der Hinweis „Bitte eine Zahl eingeben“ erscheinen.

***

#### 3.4 Responsivität (Anpassung an verschiedene Bildschirmgrößen)

**Beschreibung:** Sicherstellen, dass die Benutzeroberfläche auf verschiedenen Geräten und Bildschirmgrößen optimal angezeigt wird.

**Schritte:**

1. Öffnen Sie die Anwendung auf einem großen Bildschirm (1920x1080), z. B. einem Desktop oder Laptop.
2. Prüfen Sie, ob alle Elemente klar strukturiert sind und nichts abgeschnitten oder verschoben ist.
3. Wiederholen Sie den Test auf einem Gerät mit einer kleineren Bildschirmauflösung (1366x768).
4. Öffnen Sie die Anwendung auf einem Tablet oder Smartphone und prüfen Sie dieselbe Seite.
5. Wenn kein Smartphone/Tablett zur Verfügung steht: Ändern Sie die Größe des Browserfensters auf eine kleine Breite und beobachten Sie die Änderungen.
6. Prüfen Sie, ob die Navigation weiterhin nutzbar ist (z. B. ein Menü als „☰“ umgestellt wird).

**Kontrolle:**

* Auf allen Bildschirmgrößen sind die Inhalte klar lesbar und vollständig sichtbar.
* Es gibt keine abgeschnittenen Texte, falsche Abstände oder Fehlanpassungen.
* Die Navigation, einschließlich Schaltflächen und Links, bleibt auf allen Bildschirmgrößen funktionsfähig.

***

#### 3.5 Sicherheit

**Beschreibung:** Überprüfen, ob Eingaben in Formularen korrekt vor schädlichem Code geschützt sind.

**Schritte:**

1. Geben Sie Test-Daten ein, die potenziell schädlich sein könnten. Beispiele:
   * `<script>alert('Test')</script>`
   * Ungültige Zeichen wie `'` oder `"` in Textfeldern.
2. Klicken Sie auf „Speichern“ oder eine entsprechende Schaltfläche, um diese Daten zu senden.
3. Beobachten Sie, ob die Anwendung darauf richtig reagiert (Fehlermeldung oder Ignorieren der Eingabe).

**Kontrolle:**

* Potenziell gefährliche Eingaben wie Code oder unzulässige Sonderzeichen werden nicht verarbeitet.
* Die Anwendung bleibt stabil und zeigt keine Fehler an, die den Benutzer betreffen könnten.
* Es wird kein Code oder JavaScript auf der Seite ausgeführt.

***

### 3. Dokumentation der Ergebnisse

Für jeden Testschritt sollten Sie die Ergebnisse dokumentieren, indem Sie bestätigen, ob der Test erfolgreich war oder Fehler aufgetreten sind.

**Beispieleinträge:**

* Testfall 3.1 (UI-Ladefähigkeit): ✔️ Seite lädt fehlerfrei.
* Testfall 3.3 (Formulareingaben): ❌ Fehlermeldung bei falschen Eingaben wurde nicht angezeigt.

Falls Fehler auftreten, notieren Sie die genauen Schritte, um das Problem erneut zu verursachen, und leiten Sie diese Informationen an die Entwickler weiter
