# Tenpal-Signatur in 3 Schritten

1. Datei `signatur_<dein-name>.html` per Doppelklick im Browser öffnen.
2. Cmd+A, Cmd+C.
3. Gmail → Zahnrad → „Alle Einstellungen aufrufen“ → „Signatur“ → „Neu erstellen“ → ins Feld klicken → Cmd+V → unten „Änderungen speichern“.

Fertig. Testmail an dich selbst schicken.

Optional: In den Signaturstandards die neue Signatur für „Neue E-Mails“ und „Antworten“ auswählen und den Haken bei „Zeile ‚--‘ entfernen“ setzen.

---

Für Kasimir: neue Signatur bauen mit

```bash
python3 "outputs/signatur/tool/make_signature.py" --slug leo --name "Leo Elbert" --title "Sales" --phone "+49 …" --linkedin … --calendly … --photo ~/Downloads/leo.jpg --out ~/Downloads/signatur-leo --repo "outputs/signatur/pages-repo"
```

Foto ändern = neuer Slug (Gmail cacht Bilder pro URL).
