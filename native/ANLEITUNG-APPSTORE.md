# GBU App → App Store & Google Play

Deine bestehende Web-App wurde mit **Capacitor** in ein natives iOS- und Android-Projekt verpackt. Alles läuft weiterhin offline, jsPDF und Icons sind jetzt lokal gebündelt (keine CDN-Abhängigkeit mehr). PDF-Export und Teilen laufen in der App über die nativen iOS/Android-Funktionen (Share-Sheet mit „In Dateien sichern", WhatsApp, Mail etc.).

**App-ID:** `com.ropesconnectingpeople.gbu` · **Name:** GBU Baumsicherheit

---

## Schritt 0: Was du brauchst

| Was | Kosten | Dauer |
|---|---|---|
| Apple Developer Program → [developer.apple.com/programs/enroll](https://developer.apple.com/programs/enroll/) | 99 €/Jahr | Freigabe 1–2 Tage |
| Google Play Console → [play.google.com/console/signup](https://play.google.com/console/signup) | 25 $ einmalig | Identitätsprüfung bis zu einigen Tagen |
| Xcode (Mac App Store) | kostenlos | großer Download |
| Android Studio → [developer.android.com/studio](https://developer.android.com/studio) | kostenlos | |
| Node.js ≥ 18 → [nodejs.org](https://nodejs.org) | kostenlos | |

**Tipp Apple:** Als Einzelperson anmelden geht sofort mit Apple-ID. Als Firma brauchst du eine D-U-N-S-Nummer (kostenlos, dauert aber 1–2 Wochen). Im Store steht dann statt deines Namens der Firmenname.

**Wichtig für beide Stores:** Du brauchst eine **Datenschutzerklärungs-URL**. Da die App komplett offline arbeitet und keine Daten sammelt, ist die sehr kurz — leg sie einfach auf ropesconnectingpeople.com ab (z. B. `/gbu/datenschutz`).

---

## Schritt 1: Projekt auf dem Mac einrichten

```bash
cd gbu-native
npm install
npx cap sync
```

`npx cap sync` kopiert die Web-App in beide native Projekte und installiert die iOS-Pods (dafür einmalig: `sudo gem install cocoapods` oder `brew install cocoapods`).

---

## Schritt 2: iOS – Build & Upload

```bash
npx cap open ios
```

Xcode öffnet sich. Dann:

1. Links das Projekt **App** anklicken → Tab **Signing & Capabilities** → bei *Team* deinen Apple-Developer-Account auswählen (nach der Anmeldung unter Xcode → Settings → Accounts hinzufügen). Häkchen bei „Automatically manage signing".
2. **Testen:** Oben dein iPhone als Ziel auswählen (per Kabel verbinden) → ▶︎ drücken. Die App läuft jetzt nativ auf deinem Gerät — alles einmal durchklicken: Formular, Fotos, PDF, Teilen, Speichern.
3. **Archivieren:** Zielgerät auf „Any iOS Device (arm64)" stellen → Menü **Product → Archive** → im Organizer **Distribute App → App Store Connect → Upload**.
4. Auf [appstoreconnect.apple.com](https://appstoreconnect.apple.com) → **Meine Apps → + → Neue App**: Name „GBU Baumsicherheit", Bundle-ID `com.ropesconnectingpeople.gbu`, Sprache Deutsch.
5. Ausfüllen: Beschreibung, Keywords (Baumpflege, SVLFG, Gefährdungsbeurteilung, Arbeitssicherheit …), Support-URL, Datenschutz-URL, Screenshots (siehe unten), Altersfreigabe 4+, Preis: Kostenlos. Bei „App-Datenschutz": **Es werden keine Daten erfasst** — stimmt bei euch wirklich, großer Pluspunkt.
6. Build auswählen → **Zur Prüfung einreichen**. Review dauert meist 1–2 Tage.

**Screenshots:** Pflicht sind 6,7"- (z. B. iPhone 15 Pro Max) und 6,5"-Formate. Einfach im Xcode-Simulator die App öffnen und mit ⌘S Screenshots machen.

---

## Schritt 3: Android – Build & Upload

```bash
npx cap open android
```

Android Studio öffnet sich. Dann:

1. **Testen:** Eigenes Handy per USB verbinden (USB-Debugging aktivieren) oder Emulator starten → ▶︎.
2. **Signieren & bauen:** Menü **Build → Generate Signed App Bundle / APK → Android App Bundle** → „Create new…" für den Keystore.
   ⚠️ **Keystore-Datei und Passwort sicher aufbewahren (Backup!)** — ohne sie kannst du nie wieder Updates veröffentlichen.
3. In der [Play Console](https://play.google.com/console): **App erstellen** → Name, Sprache Deutsch, App (kostenlos).
4. Alle Pflicht-Erklärungen durchklicken (Datenschutz-URL, Inhaltsfreigabe, Zielgruppe „18+/Fachpublikum", Datensicherheit: **keine Datenerfassung**).
5. **Produktion → Neues Release** → das `.aab` hochladen → einreichen.

**Hinweis:** Neue Google-Konten müssen vor dem Produktions-Release einen geschlossenen Test mit min. 12 Testern über 14 Tage durchführen (Stand 2026 — steht direkt in der Play Console). Dafür eignen sich Kollegen aus der Baumpflege-Szene perfekt — gleich doppelt genutzt als Feedback-Runde.

---

## Schritt 4: Updates veröffentlichen

Wenn du die Web-App änderst (`www/index.html`):

```bash
npx cap sync
```

Dann in Xcode/Android Studio Versionsnummer hochzählen und neu archivieren/bauen und hochladen. Fertig.

---

## Was technisch geändert wurde

- **Capacitor 6** Projekt mit iOS- und Android-Plattform, Plugins: Filesystem + Share
- **jsPDF & Tabler Icons lokal gebündelt** (`www/vendor/`) — App braucht nie Internet
- **PDF-Export/Teilen nativ:** In der App wird das PDF über das native Share-Sheet gespeichert/geteilt (statt Browser-Download, der in Apps nicht funktioniert). Im Web bleibt alles wie vorher — dieselbe Datei funktioniert weiter als PWA auf GitHub Pages.
- **Service Worker** wird in der nativen App deaktiviert (dort unnötig)
- **Safe-Area-Insets** für Notch/Home-Indicator
- **Info.plist:** Kamera-/Fotozugriff-Begründungen (für Fotoanhänge), Verschlüsselungs-Erklärung für den Export-Compliance-Dialog
- **Icons & Splashscreens** für alle Größen generiert (aus deinem 512er-Icon — für maximale Schärfe später gern ein 1024×1024-Original in `assets/icon.png` legen und `npm run assets` ausführen)

## Empfehlung: Repo-Struktur

Leg dieses Projekt als eigenes Repo an (z. B. `ropesconnectingpeople/gbu-app-native`) oder als Ordner `native/` im bestehenden GBU-Repo. `node_modules/` ist nicht enthalten — nach dem Klonen einfach `npm install`.
