# Baustellen-Rennen

Ein 3D-Kartrennen im Low-Poly-Stil für den Browser. Die Besonderheit: Es gibt keine Zufalls-Items. Wer hinten liegt, sammelt Baupunkte (BP) und baut damit die Strecke um, mit Rampen und Abkürzungen für sich selbst oder Baustellen gegen die Fahrer davor.

Das ganze Spiel steckt in einer einzigen Datei: `index.html`.

## Starten

`index.html` doppelklicken (Chrome, Edge, Firefox oder Safari). Es braucht eine Internetverbindung, weil three.js 0.160.0 von einem CDN geladen wird (für Online-Spiele zusätzlich PeerJS 1.5.4). Sonst ist nichts zu installieren.

- **Gegen Bots:** 1 Spieler und bis zu 7 Bots, Stufe leicht, mittel oder schwer.
- **Lokal am selben Gerät:** 2 Spieler an einer Tastatur, mit Gamepads bis 4, dazu Bots. Der Bildschirm wird geteilt.
- **Online:** bis 8 Fahrer, ohne eigenen Server (siehe unten).

## Steuerung

| Aktion | Tastatur links | Tastatur rechts | Gamepad |
|---|---|---|---|
| Lenken | A, D | ←, → | linker Stick |
| Gas | W | ↑ | A oder RT |
| Bremsen, rückwärts | S | ↓ | B oder LT |
| Driften | Leertaste | Shift rechts oder Enter | X oder RB |
| Bauwerk wählen | Q oder 1–6 | , | Steuerkreuz ← → |
| Bauplatz wechseln | F | - | Steuerkreuz ↑ |
| Bauen | E | . | Y |
| Zurück auf die Strecke | R | Rücktaste | Select |
| Pause | Esc oder P | | Start |

Wer allein fährt, kann beide Tastatur-Hälften benutzen. Zahlentasten: einmal drücken wählt das Bauwerk, nochmals drücken baut es. `M` schaltet den Ton aus.

**Drift:** Taste in der Kurve halten. Nach 1 s sprühen blaue, nach 2 s orange Funken, beim Loslassen gibt es einen Mini-Turbo. **Windschatten:** rund 1,5 s dicht hinter einem Fahrzeug bleiben.

## Bauen

Baupunkte gibt es nur fürs Aufholen: +3 pro überholtem Fahrer und +1 pro 15 m, die man auf den Vordermann gutmacht. Der Führende verdient nichts und kann nicht bauen, seine gesparten Punkte behält er. Mehr als 20 BP kann man nicht haben.

| Bauwerk | Preis | Wirkung |
|---|---|---|
| Sprungrampe | 3 BP | Sprung und 1,5 s Schub, nur für dich |
| Abkürzung | 6 BP | öffnet einen kurzen Weg nur für dich, spart rund 2 s |
| Pylonen | 2 BP | Slalom für alle Fahrer vor dir |
| Schlammloch | 3 BP | bremst auf der halben Fahrbahn |
| Absperrung | 4 BP | sperrt rund 60 % der Breite |
| Umleitung | 6 BP | sperrt an einer Gabelung 20 s lang den kurzen Weg |

Baustellen gelten nur für Fahrer, die beim Bauen vor dir lagen. Für alle anderen sind sie durchsichtig. Sie bauen sich 2 s lang sichtbar auf, stehen nie näher als 3 s Fahrzeit vor einem Betroffenen und lassen immer eine Lücke. Ein Treffer bremst, hält aber nie an, danach ist man 3 s geschützt.

## Online spielen

1. Der Host wählt «Online: Raum erstellen» und bekommt einen Code mit 5 Zeichen.
2. Mit «Link kopieren» schickt er den Einladungslink (`…/index.html?raum=CODE`) an die Mitspieler. Der Link funktioniert, sobald das Spiel im Internet liegt. Wer die Datei lokal öffnet, wählt «Online: Raum beitreten» und tippt den Code ein.
3. Alle wählen Name, Fahrzeug und Farbe und drücken «Bereit». Der Host stellt Strecke, Runden und Bots ein und startet.

Die Verbindung läuft direkt von Browser zu Browser (WebRTC), vermittelt über den öffentlichen PeerJS-Server. In strengen Netzen (Schule, Firma) kann das scheitern, dann erscheint eine Meldung mit dem Hinweis auf Bots und lokales Spiel. Fällt ein Mitspieler aus, fährt ein Bot für ihn weiter. Verlässt der Host das Spiel, endet es für alle.

## Hochladen

- **itch.io:** Neues Projekt, «Kind of project: HTML», `index.html` hochladen und «This file will be played in the browser» ankreuzen. Grösse zum Beispiel 1280 × 720, Vollbild-Knopf einschalten.
- **GitHub Pages:** Im Repository unter Settings → Pages den Branch und den Ordner `/ (root)` wählen. Das Spiel liegt dann unter `https://<name>.github.io/26-Websites-Games/baustellen-rennen/`.
- **Netlify:** Den Ordner `baustellen-rennen` auf https://app.netlify.com/drop ziehen.

## Balancing: gemessene Werte

Stand 13.11.2026, pro Strecke 200 Rennen mit 8 gleich starken Bots und 100 Rennen mit einem starken gegen 7 mittlere Bots.

| Zielwert | Kiesgrube | Bergpass |
|---|---|---|
| Führender nach Runde 1 gewinnt (Ziel 35–60 %) | 51 % | 40 % |
| Feld kommt innerhalb von 8 s ins Ziel | 100 % (Median 1,9 s) | 100 % (Median 2,4 s) |
| Stärkerer Bot gewinnt gegen 7 schwächere (Ziel ab 50 %) | 73 % | 52 % |
| Grösster Zeitverlust durch ein Hindernis (Ziel höchstens rund 2 s) | 1,58 s | 1,43 s |
| Längster Stillstand eines Bots (Ziel unter 3 s) | 0,0 s | 0,1 s |
| Rundenzeit im Schnitt | 45,2 s | 44,6 s |
| Überholmanöver, Bauwerke, Treffer pro Rennen | 31, 20, 3 | 62, 26, 7 |

Selbst nachmessen: `index.html?sim=200` öffnen (dauert einige Minuten).

## Wichtigste CONFIG-Werte

Alle Werte stehen kommentiert ganz oben im Code im Objekt `CONFIG`.

| Wert | Einstellung | Bedeutung |
|---|---|---|
| `bp.ueberholen`, `bp.meterProBP` | 3, 15 | Lohn fürs Überholen und fürs Aufholen |
| `bp.letzterFaktor` | 1,5 | der Letzte sammelt so viel schneller |
| `bp.naheFaktor`, `bp.vollerRueckstand` | 0,25, 110 m | direkt hinter dem Führenden gibt es nur einen Viertel, ab 110 m Rückstand den vollen Lohn |
| `bp.rangVerfall` | 15 s | Lohn nur für neu gewonnene Plätze, ein verlorener Platz zählt erst nach 15 s wieder voll |
| `bp.startPause` | 8 s | keine Punkte im Startgedränge |
| `bp.erkauftZeit`, `bp.geschenktZeit` | 4 s, 6 s | keine Punkte für Plätze durch die eigene Rampe oder Abkürzung und für Fahrer, die gerade in eine Baustelle gefahren sind |
| `bau.preise` | 3, 6, 2, 3, 4, 6 | Rampe, Abkürzung, Pylonen, Schlamm, Absperrung, Umleitung |
| `bau.minVorlauf`, `bau.schutzZeit` | 3 s, 3 s | Vorwarnzeit und Schutz nach einem Treffer |
| `bau.maxProSpieler`, `bau.maxGesamt`, `bau.wartezeit` | 2, 6, 4 s | Grenzen für Hindernisse |
| `bau.maxSchlenker` | 4 m | Sperren stehen so, dass die Ideallinie höchstens so weit im gesperrten Teil liegt |
| `windschatten.bonus` | 0,02 | 2 % mehr Höchsttempo im Windschatten |
| `bots.stufen` | Mut 0,76 / 0,83 / 0,96 | Fahrkönnen der Bots leicht, mittel, schwer |

## Entscheidungen, die ich getroffen habe

- Höchstens 8 Fahrer pro Rennen.
- Baupunkte gibt es nur für neu gewonnene Plätze. Wer einen eben verlorenen Platz zurückholt, bekommt dafür wenig. Sonst füttert das Hin und Her im Pulk laufend neue Baustellen.
- Wer dicht an der Spitze klebt, sammelt weniger. Wer weit zurückliegt, sammelt voll. So hilft das Bauen vor allem denen, die wirklich hinten liegen.
- In den ersten 8 s nach dem Start und für Plätze, die man mit Rampe oder Abkürzung gekauft hat, gibt es keine Punkte.
- Absperrung und Schlammloch stehen auf der Seite, auf der ein aufmerksamer Fahrer nur einen kleinen Schlenker braucht. Ausweichen kostet rund 0,1 s, ein Treffer 0,3 bis 0,7 s.
- Die Umleitung ist eine schräge Leitwand, die auf den langen Weg lenkt. Niemand wird angehalten.
- Wer an die Spitze überholt, bekommt die Punkte noch, kann sie aber erst wieder ausgeben, wenn er nicht mehr führt.

## Bekannte Grenzen

- Der Online-Modus ist mit zwei Browsern gegen einen lokalen Vermittlungsserver getestet (Lobby, Rennen, Ergebnis, Revanche, Bot-Übernahme). Über den öffentlichen PeerJS-Server im echten Internet konnte ich ihn in meiner Testumgebung nicht ausprobieren.
- Die Bildrate ist nur mit Software-Grafik geprüft. Ruckelt es auf einem Gerät, hilft die Grafikstufe «Niedrig».
- Die Touch-Steuerung ist eingebaut, aber nicht getestet.
- Einen Grand-Prix-Modus gibt es nicht.
- Auf dem «Bergpass» gewinnt der starke Bot mit 52 % nur knapp über dem Zielwert.
- Bots bauen selten Umleitungen und Abkürzungen, weil die Punkte knapp sind.
- three.js 0.160.0 schreibt eine harmlose Warnung in die Browser-Konsole.

## Für Bastler

- `index.html?debug=1` zeigt Messwerte und Bauplätze.
- `index.html?sim=200` lässt 200 Bot-Rennen laufen und zeigt die Auswertung.
