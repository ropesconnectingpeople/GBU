# Baumsicherheitsbeurteilung – PWA

## Installation als App (für Nutzer)

### iPhone / iPad (Safari)
1. URL im Safari öffnen
2. Teilen-Button antippen (Rechteck mit Pfeil)
3. „Zum Home-Bildschirm" wählen
4. „Hinzufügen" tippen → App erscheint auf dem Homescreen

### Android (Chrome)
1. URL in Chrome öffnen
2. Drei-Punkte-Menü → „App installieren" oder „Zum Startbildschirm"
3. Bestätigen → App erscheint auf dem Homescreen

### Desktop (Chrome / Edge)
1. URL öffnen
2. Adressleiste rechts: Install-Symbol (⊕) klicken
3. „Installieren" → App öffnet sich als eigenständiges Fenster

---

## Kostenlos online stellen (einmalig, 5 Minuten)

### Option A: Netlify Drop (empfohlen, kein Account nötig)
1. Gehe zu: https://app.netlify.com/drop
2. Den gesamten Ordner `bsa-pwa` per Drag & Drop auf die Seite ziehen
3. Netlify gibt euch sofort eine URL → fertig!

### Option B: GitHub Pages
1. Kostenlosen Account auf github.com erstellen
2. Neues Repository anlegen (z.B. „baumsicherheit")
3. Alle Dateien hochladen
4. Settings → Pages → Branch: main → Save
5. URL: https://EUER-NAME.github.io/baumsicherheit

---

## Dateistruktur
```
bsa-pwa/
├── index.html       ← Die App
├── manifest.json    ← PWA-Konfiguration
├── sw.js            ← Offline-Unterstützung
├── favicon.ico
└── icons/
    ├── icon-16.png
    ├── icon-32.png
    ├── icon-180.png  ← Apple Touch Icon
    ├── icon-192.png  ← Android
    └── icon-512.png  ← Splash Screen
```
