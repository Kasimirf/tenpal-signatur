# Tenpal-E-Mail-Signatur: Anleitung

Die Signatur ist eine dunkelgrüne Box mit rundem Foto links, Name und Icons in der Mitte und dem Tenpal-Logo rechts. Sie funktioniert in Gmail (Browser), Apple Mail und Outlook. In Outlook wird die Box eckig, das ist normal.

## Teil A: Für Kollegen

### 1. Das brauchst du

Schick Kasimir diese fünf Dinge:

- **Foto**: Porträt in guter Auflösung (mindestens 800 × 800 px, JPG oder PNG). Gesicht mittig, gern das Profi-Headshot.
- **Name**, wie er in der Signatur stehen soll.
- **Titel**, z. B. „Sales“ oder „Customer Success“.
- **Handynummer** im Format +49 176 1234567. Sie wird für den Anruf-Button und WhatsApp verwendet.
- **LinkedIn-Link** und **Calendly-Link** (30-Minuten-Termin).

Du bekommst zurück: `signatur_<dein-name>.html` und `signatur_<dein-name>_preview.html`.

### 2. In Gmail einbauen

1. `signatur_<dein-name>.html` per Doppelklick im Browser öffnen.
2. Cmd+A, dann Cmd+C. Du kopierst die gerenderte Box, nicht den Quelltext.
3. Gmail → Zahnrad oben rechts → „Alle Einstellungen aufrufen“.
4. Reiter „Allgemein“ → nach unten scrollen zu „Signatur“ → „Neu erstellen“ → Namen vergeben.
5. Ins Textfeld klicken, Cmd+V.
6. Unter „Signaturstandards“ die neue Signatur für „Neue E-Mails“ und „Bei Antworten/Weiterleitungen“ auswählen.
7. Haken setzen bei „Signatur vor zitiertem Text einfügen und die Zeile ‚--‘ davor entfernen“.
8. Ganz unten „Änderungen speichern“.
9. Testmail an dich selbst schicken.

Wenn eine alte Signatur existiert: vorher ins Feld klicken, Cmd+A, Backspace, dann erst einfügen.

### 3. In Apple Mail einbauen

1. `signatur_<dein-name>_preview.html` im Browser öffnen (diese Version hat die Bilder eingebettet).
2. Cmd+A, Cmd+C.
3. Mail → Einstellungen → Signaturen → „+“ → Cmd+V.
4. Haken bei „Immer die Standardschrift verwenden“ entfernen.

### 4. Handy

Die Gmail-App hat eine eigene Text-Signatur, die HTML-Version greift dort nicht. Für das Handy reicht eine Text-Signatur mit Name, Titel und Calendly-Link.

## Teil B: Für Kasimir (Signatur erzeugen)

Alles liegt in `Claude Code/outputs/signatur/`:

- `tool/make_signature.py`: erzeugt Foto-Kreis und beide HTML-Dateien.
- `tool/icon_*.png`, `tool/logo_white.png`: gemeinsame Bilder, liegen schon auf GitHub Pages.
- `pages-repo/`: lokaler Clone von `Kasimirf/tenpal-signatur`. GitHub Pages liefert alles darin unter `https://kasimirf.github.io/tenpal-signatur/` aus.

Ein Aufruf pro Kollege:

```bash
python3 "outputs/signatur/tool/make_signature.py" --slug leo --name "Leo Muster" --title "Sales" --phone "+49 176 1234567" --linkedin https://www.linkedin.com/in/leo-muster --calendly https://calendly.com/leo-muster/30min --photo ~/Downloads/leo.jpg --out ~/Downloads/signatur-leo --repo "outputs/signatur/pages-repo"
```

Das Skript schneidet das Foto rund zu, schreibt beide HTML-Dateien nach `--out` und pusht das Foto ins Repo. Nach etwa einer Minute ist das Bild live. Dann die beiden HTML-Dateien an den Kollegen schicken.

Oder einfach an Claude: „Signatur für Leo: Sales, +49 176 …, LinkedIn …, Calendly …, Foto liegt in Downloads.“

### Foto nachträglich ändern

Gmail cacht Bilder über einen eigenen Proxy. Ein neues Foto unter gleichem Dateinamen bleibt in Gmail alt. Deshalb immer einen neuen Slug nehmen (z. B. `leo-v2`), das Skript neu laufen lassen und die Signatur in Gmail neu einfügen.

### Design-Werte

- Hintergrund Forest #1D3D14, Titel und Icons Mint #EBFFEE, Name Weiß.
- Breite 470 px, Außenspalten je 130 px, Foto 88 px, Logo 104 px.
- Schrift Inter mit Fallback Helvetica/Arial. Inter wird in Mailclients nur angezeigt, wenn sie installiert ist.
