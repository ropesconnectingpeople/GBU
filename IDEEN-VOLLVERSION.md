# Ideen-Backlog für die Vollversion (Store-App)

Die freie Web-App bleibt feature-eingefroren (nur Bugfixes). Diese Liste ist
der Speicher für die Weiterentwicklung Richtung TestFlight/Store.

## Fortlaufende GBUs über mehrere Tage (Mehrtages-Einsatz)
Anwendungsfall: mehrtägiger Einsatz am selben Ort (z.B. Parkanlage).
Die Gefährdungsbeurteilung muss je Einsatztag geprüft/dokumentiert werden,
die meisten Angaben bleiben aber gleich.

Idee: „Folgetag"-Funktion im Archiv
- übernimmt Einsatzort, Koordinaten, Team, Arbeiten, Ausrüstung, Gefahren-Checks
- setzt neues Datum, leere Unterschrift (muss täglich frisch erfolgen)
- Verkettung der Einträge (Tag 2 von 5), PDF-Hinweis „Fortführung vom TT.MM."
- Archiv gruppiert zusammengehörige Tage

## Notfallkontakt je Person (Idee: Michael Ort, Sauerland Baumpflege, Juni 2026)
Anwendungsfall: Unfall auf der Baustelle – wer ruft wen an? Bei eigenen Leuten
hat das Büro die Daten, bei wechselnden Subunternehmern hat sie niemand.

Umsetzung so klein wie möglich, kein eigenes Modul:
- Schritt Personal: je Person optional „+ Notfallkontakt" (Name / Telefon),
  standardmäßig eingeklappt, Formular sieht ohne Nutzung exakt gleich aus
- zählt NICHT zur Vollständigkeitsprüfung
- Team-Speicher merkt sich die Angabe pro Person (einmal tippen)
- PDF: klein unter dem Namen im Personal-Block, nur wenn ausgefüllt
- kein Sync, keine separate Kontaktliste, kein Telefonbuchzugriff
- Datenschutz: Daten Dritter, bleiben lokal, ein Satz in der Datenschutzerklärung
- Release-Notes: Michael als Ideengeber nennen

## Weitere gemerkte Themen
- Formular-Definition vom Code trennen (Länderpakete als Daten)
- Österreich-Paket (ASchG/Evaluierung, DOK-VO-Pflichtfelder, AUVA-Bezug)
  – siehe Länder-Roadmap-Recherche
- Pro über In-App-Kauf statt "App gekauft = Pro"
- Cloud-Backup/Sync als mögliches Abo-Feature (Anlass: verlorene GBU trotz
  WhatsApp-Versand)
- Crew-Signaturen (alle unterschreiben, nicht nur Verantwortlicher) – Pflicht
  für einen späteren US-Markt, auch in DACH sinnvoll
