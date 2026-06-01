# 🛒 Playmobil Warenkorb-Helfer

Ein Tool zum automatischen Befüllen des Playmobil-Warenkorbs anhand einer Artikelliste.

## 📋 Inhaltsverzeichnis

- [Überblick](#überblick)
- [Voraussetzungen](#voraussetzungen)
- [Installation](#installation)
- [Verwendung](#verwendung)
- [Eingabeformat](#eingabeformat)
- [Browser-Konsole öffnen](#browser-konsole-öffnen)
- [Paste-Protection deaktivieren](#paste-protection-deaktivieren)
- [Tipps & Tricks](#tipps--tricks)
- [Fehlerbehebung](#fehlerbehebung)
- [Technische Details](#technische-details)

---

## Überblick

Dieses Tool generiert ein JavaScript, das du in der Browser-Konsole auf [playmobil.com](https://www.playmobil.com) ausführen kannst. Es fügt automatisch mehrere Artikel mit gewünschter Menge zum Warenkorb hinzu – ohne jeden Artikel einzeln suchen und anklicken zu müssen.

### Warum ein Browser-Script?

Die Playmobil-Website verwendet verschiedene Sicherheitsmechanismen:

- **Session-Cookies** – Du musst auf der Website eingeloggt sein
- **CSRF-Protection** – Anfragen von externen Quellen werden blockiert
- **Rate-Limiting** – Zu schnelle Anfragen werden abgelehnt

Das generierte Script läuft **direkt im Browser** und nutzt deine bestehende Session, wodurch diese Einschränkungen umgangen werden.

---

## Voraussetzungen

- **Moderner Browser** (Chrome, Firefox, Edge)
- **Playmobil-Konto** (optional, aber empfohlen)

---

## Installation

1. Lade die Datei `index.html` von GitHub herunter:
   - Öffne die [GitHub-Repository-Seite](https://github.com/)
   - Klicke auf `index.html`
   - Klicke oben rechts auf **"Download raw file"** (Pfeil-nach-unten-Symbol)

2. Öffne die heruntergeladene `index.html` Datei in deinem Browser (Doppelklick oder Rechtsklick → "Öffnen mit")

---

## Verwendung

### Schritt 1: Tool öffnen

Öffne die `index.html` Datei in deinem Browser.

### Schritt 2: Artikelliste eingeben

Gib deine Artikel im Format `Artikelnummer, Menge` ein (eine Zeile pro Artikel).

### Schritt 3: Script generieren

Klicke auf **"🚀 Script generieren"**.

### Schritt 4: Script kopieren

Klicke auf **"📋 Script kopieren"**.

### Schritt 5: Playmobil-Website öffnen

Öffne [playmobil.com](https://www.playmobil.com) in einem neuen Tab und melde dich ggf. an.

### Schritt 6: Browser-Konsole öffnen

Siehe [Browser-Konsole öffnen](#browser-konsole-öffnen).

### Schritt 7: Konsole leeren (empfohlen)

> ⚠️ **Wichtig:** Es ist einfacher, die Konsole vor dem Einfügen des Scripts zu leeren. So siehst du nur die Ausgaben des Scripts und keine vorherigen Meldungen.

- **Rechtsklick** in der Konsole → **"Clear console"** / **"Konsole leeren"**
- Oder: Tastenkürzel **Strg + L** (Windows/Linux) bzw. **Cmd + K** (Mac)

### Schritt 8: Script einfügen und ausführen

Füge das kopierte Script in die Konsole ein und drücke **Enter**.

### Schritt 9: Warten

Das Script arbeitet die Liste ab. Du siehst den Fortschritt in der Konsole.

### Schritt 10: Seite aktualisieren

Nach Abschluss die Seite neu laden, um den gefüllten Warenkorb zu sehen.

---

## Eingabeformat

### Grundformat

```text
Artikelnummer, Menge
```

### Beispiele

```text
30238993, 2
30123456, 1
30987654, 5
```

### Unterstützte Formate

| Format               | Beispiel      | Ergebnis            |
|----------------------|---------------|---------------------|
| Komma-getrennt       | `30238993, 2` | 2x Artikel 30238993 |
| Leerzeichen-getrennt | `30238993 2`  | 2x Artikel 30238993 |
| Semikolon-getrennt   | `30238993;2`  | 2x Artikel 30238993 |
| Nur Artikelnummer    | `30238993`    | 1x Artikel 30238993 |

### Kommentare

Zeilen, die mit `#` oder `//` beginnen, werden ignoriert:

```text
# Ersatzteile für Set 70190
30238993, 2
30123456, 1

# Figuren
30987654, 3
```

---

## Browser-Konsole öffnen

### Google Chrome

1. **F12** drücken oder **Strg + Shift + J** (Windows) / **Cmd + Option + J** (Mac)
2. Auf den Tab **"Console"** / **"Konsole"** klicken

### Mozilla Firefox

1. **F12** drücken oder **Strg + Shift + K** (Windows) / **Cmd + Option + K** (Mac)
2. Auf den Tab **"Konsole"** klicken

### Microsoft Edge

1. **F12** drücken oder **Strg + Shift + J**
2. Auf den Tab **"Console"** / **"Konsole"** klicken

---

## Paste-Protection deaktivieren

> ⚠️ **Wichtig:** Moderne Browser haben eine **Paste-Protection** (Einfügeschutz), die verhindert, dass Code in die Konsole eingefügt wird. Dies ist eine Sicherheitsmaßnahme gegen sogenannte "Self-XSS"-Angriffe.

### Google Chrome Paste-Protection

Beim ersten Versuch, Code einzufügen, erscheint eine Warnung:

```text
Warning: Don't paste code into the DevTools Console that you don't understand or haven't reviewed yourself. This could allow attackers to steal your identity or take control of your computer.
```

**Lösung:**

1. Tippe `allow pasting` in die Konsole und drücke **Enter**
2. Jetzt kannst du das Script einfügen

### Mozilla Firefox Paste-Protection

Firefox zeigt beim Einfügen eine ähnliche Warnung:

```text
Scam Warning: Take care when pasting things you don't understand. This could allow attackers to steal your identity or take control of your computer.
```

**Lösung:**

1. Tippe `allow pasting` in die Konsole und drücke **Enter**
2. Alternativ: Gehe zu `about:config` und setze `devtools.selfxss.count` auf `5` oder höher

### Microsoft Edge Paste-Protection

Edge verhält sich wie Chrome:

**Lösung:**

1. Tippe `allow pasting` in die Konsole und drücke **Enter**

---

## Tipps & Tricks

### Verzögerung anpassen

- **Standard:** 1500ms zwischen Anfragen
- **Bei Fehlern:** Erhöhe auf 2500-3000ms
- **Einstellung:** Im Tool unter "Verzögerung zwischen Anfragen"

### Große Listen aufteilen

Bei sehr vielen Artikeln (50+) empfiehlt es sich, die Liste in kleinere Gruppen aufzuteilen und zwischen den Durchläufen eine Pause einzulegen.

### Artikelnummern finden

Die Artikelnummer findest du auf der Playmobil-Website:

- In der URL der Produktseite
- Im Produkttitel (z.B. "30238993 - Hotdog-Brötchen")
- In den Produktdetails

### Konsole übersichtlich halten

- **Vor dem Einfügen:** Konsole leeren mit **Strg + L**
- **Filter nutzen:** In Chrome/Firefox kannst du nach "Playmobil" filtern

---

## Fehlerbehebung

### "Leider konnte deine Bestellung nicht aufgegeben werden"

**Ursache:** Session abgelaufen oder Rate-Limiting
**Lösung:**

1. Seite neu laden
2. Ggf. neu einloggen
3. Verzögerung erhöhen (2500-3000ms)
4. Weniger Artikel pro Durchlauf

### Script wird nicht ausgeführt

**Ursache:** Paste-Protection aktiv
**Lösung:** Siehe [Paste-Protection deaktivieren](#paste-protection-deaktivieren)

### Artikel nicht gefunden

**Ursache:** Ungültige Artikelnummer
**Lösung:** Artikelnummer auf playmobil.com überprüfen

### Netzwerkfehler

**Ursache:** Verbindungsproblem oder Server überlastet
**Lösung:**

1. Internetverbindung prüfen
2. Später erneut versuchen
3. Verzögerung erhöhen

---

## Technische Details

### Verwendete API

```text
POST /on/demandware.store/Sites-DE-Site/de_DE/Cart-AddProduct
```

### Request-Parameter

| Parameter  | Beschreibung               |
|------------|----------------------------|
| `pid`      | Produkt-ID (Artikelnummer) |
| `quantity` | Menge                      |

### Request-Headers

```text
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data
```

### Erfolgreiche Response

```json
{
  "action": "Cart-AddProduct",
  "success": true,
  "cart": { ... }
}
```

### Fehler-Response

```json
{
  "action": "Cart-AddProduct",
  "success": false,
  "message": "Fehlermeldung..."
}
```

---

## Lizenz

Dieses Tool ist für den persönlichen Gebrauch bestimmt. Nutzung auf eigene Verantwortung.

---

## Changelog

### v1.0.0

- Initiale Version
- Artikellisten-Eingabe mit verschiedenen Formaten
- Konfigurierbarer Delay
- Farbige Konsolen-Ausgabe
- Script-Generator mit Kopier-Funktion
