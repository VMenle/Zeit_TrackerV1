Zeit Tracker — README
Kurzbeschreibung
Ein einfacher, lokal laufender Zeit‑Tracker (PWA‑freundlich). Startet und stoppt Sessions, speichert Einträge im LocalStorage, bietet CSV‑Export und optionalen Service Worker für Offline‑Caching.

Installation

Repository klonen oder neues Repo erstellen.
Dateien ins Repo-Root legen:
index.html (oder Zeit_Tracker.html)
manifest.json
service-worker.js
Ordner icons erstellen und die beiden PNGs dort ablegen:
icons/icon-192.png (192×192)
icons/icon-512.png (512×512)
(Optional) Falls du die Icons eingebettet hast, reicht index.html allein.
GitHub Pages (schnellstart)

Repo → Settings → Pages → Branch: main, Folder: / (root) → Save.
Warte 1–2 Minuten. Deine App ist dann erreichbar unter https://.github.io// (wenn index.html vorhanden) oder https://.github.io//Zeit_Tracker.html.
Bedienung

Start: Beginnt eine neue Session und deaktiviert den Start‑Button.
Stopp: Beendet die offene Session, berechnet Dauer und aktiviert Start wieder.
Export CSV: Lädt eine CSV-Datei mit allen Sessions herunter.
Technische Details

Speicherung: localStorage unter dem Schlüssel zt_sessions als JSON-Array von Objekten { start: ISOString, end: ISOString | null }.
Offline: service-worker.js cached index/HTML, manifest und Icons; einfache Cache-Fallback-Strategie (cache-first).
PWA: manifest.json verweist auf die beiden Icons; bei Verwendung als index.html kann die Seite als PWA installiert werden.
Dateiübersicht

index.html — Hauptanwendung (UI, Logik, eingebettetes Icon optional).
manifest.json — Web App Manifest (Name, Icons, start_url).
service-worker.js — Einfacher Service Worker für Caching.
icons/icon-192.png — App‑Icon (192×192).
icons/icon-512.png — App‑Icon (512×512).
Sicherheit & Datenschutz

Alle Daten bleiben lokal im Browser (localStorage). Keine Server‑Uploads oder Account‑Verknüpfungen.
Anpassungen (schnell)

Startseite: index.html umbenennen, wenn du root‑Zugriff auf GitHub Pages möchtest.
Icon‑Pfade: manifest.json → icons[].src ggf. anpassen (relativ vs. absolut).
Sprache / Format: In index.html die toLocaleString()/toLocaleTimeString() Aufrufe anpassen für andere Lokalisierungen.
Fehlerbehebung

PWA‑Installation erscheint nicht: Stelle sicher, dass index.html über HTTPS (GitHub Pages) geladen wird und manifest.json + Icons erreichbar sind.
Service Worker lädt nicht neu: Nach Änderungen Cache‑Version im service-worker.js (CACHE_NAME) erhöhen und neu deployen.
