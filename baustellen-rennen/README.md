# Baustellen-Rennen

Ein 3D-Kartrennen im Low-Poly-Stil für den Browser. Die Besonderheit: Es gibt keine Zufalls-Items. Wer hinten liegt, sammelt Baupunkte (BP) und baut damit die Strecke um, mit Rampen und Abkürzungen für sich selbst oder Baustellen gegen die Fahrer davor.

Das ganze Spiel steckt in einer einzigen Datei: `index.html`.

## Starten

`index.html` doppelklicken (Chrome, Edge, Firefox oder Safari). Es braucht eine Internetverbindung, weil three.js 0.160.0 von einem CDN geladen wird (für Online-Spiele zusätzlich PeerJS 1.5.4). Sonst ist nichts zu installieren.

- **Gegen Bots:** 1 Spieler und bis zu 7 Bots, Stufe leicht, mittel oder schwer.
- **Lokal am selben Gerät:** 2 Spieler an einer Tastatur, mit Gamepads bis 4, dazu Bots. Der Bildschirm wird geteilt.
- **Online:** bis 8 Fahrer, ohne eigenen Server (siehe unten).

## Die 8 Autos

Es gibt acht Autos in vier Klassen. Jedes hat eine eigene Form, einen eigenen Motorklang, genau eine klare Stärke und eine klare Schwäche. Alle Modelle sind eigene Entwürfe aus einfachen Flächen, ohne Marken, Logos oder Waffen.

| Klasse | Auto | Stärke | Schwäche |
|---|---|---|---|
| Luxus | Sportwagen | Höchstes Tempo auf der Geraden | Verliert auf Kies und im Schlamm viel Tempo |
| Luxus | Limousine | Starker Windschatten, holt hinter anderen auf | Träge Lenkung |
| Militär | Panzerwagen (acht Räder) | Treffer an Baustellen bremsen kaum | Langsame Beschleunigung |
| Militär | Transporter (sechs Räder) | Schiebt andere beim Rempeln weg | Langsam in engen Kurven |
| Gelände | Geländewagen | Kaum Tempoverlust neben der Strecke und auf Abkürzungen | Tieferes Höchsttempo |
| Gelände | Pick-up | Bauwerke kosten 1 Baupunkt weniger | Etwas langsamer als alle anderen |
| Rennsport | Rennwagen | Beste Kurvenlage, stärkerer Drift-Schub | Treffer bremsen ihn stärker |
| Rennsport | Rallye-Auto | Drift lädt schneller, Rampen geben mehr Schub | Tieferes Höchsttempo |

**Lack:** 16 Farben, darunter matte («Olivgold matt», «Schwarz matt»), metallische («Silber metallic», «Nachtblau metallic», «Weinrot metallic») und ein Tarnmuster. Die Militärfahrzeuge tragen immer ein Tarnmuster im Ton der gewählten Farbe.

**Zufalls-Auto:** Vor jedem Rennen bekommt jeder Fahrer, auch jeder Bot, eines der 8 Autos zugelost. Vor dem Countdown zeigt eine kurze Auslosung das Auto mit Stärke und Schwäche. Niemand bekommt zweimal hintereinander dasselbe Auto. In den Renn-Einstellungen steht der Schalter «Zufalls-Auto: Ein / Aus». Ist er aus, wählt jeder sein Auto im Showroom selbst. Online legt der Host den Schalter für den ganzen Raum fest. Ist das Zufalls-Auto eingeschaltet, wählt man nur den Lack.

**Die Bots kennen ihr Auto:** Der Geländewagen baut eher Abkürzungen, das Rallye-Auto eher Rampen, der Pick-up baut öfter, die Limousine sucht den Windschatten.

## Ton und Bild

- **Motor:** Jedes Auto hat einen eigenen, mehrschichtigen Motor, der auf Drehzahl, Gas und Gangwechsel reagiert, vom tiefen Diesel des Transporters bis zum kreischenden Rennwagen. Das Rallye-Auto pfeift mit dem Turbo.
- **Fahrgeräusche:** Reifenquietschen im Drift, Abrollen auf Asphalt und auf Kies, Fahrtwind, Landung, Rempler, Wandkontakt, Treffer.
- **Umgebung:** Hämmern und Bohren beim Bauen, Publikum beim Start, bei jeder Zieldurchfahrt und im Ziel, Hall auf Brücken.
- **Andere Autos** hört man aus der richtigen Richtung, leiser mit dem Abstand und mit veränderter Tonhöhe beim Vorbeifahren (wenn ein Spieler allein am Gerät fährt).
- **Musik:** eigene, im Code erzeugte Stücke fürs Menü und fürs Rennen. In der letzten Runde wird die Musik schneller und dichter. Dazu Signale für Countdown, Überholen, Baupunkte, letzte Runde und Ziel.
- **Regler:** In den Einstellungen gibt es getrennte Regler für Effekte und Musik und das Stummschalten (auch mit <kbd>M</kbd>). Alles entsteht mit Web Audio, es gibt keine Sound-Dateien.
- **Bild:** Himmel mit Wolken und Sonne, Dunst, weiche Schatten, Spiegelungen auf Lack und Glas. Jede Strecke hat ihre Stimmung: die Kiesgrube liegt im Abendlicht, der Bergpass im klaren Morgen. Am Streckenrand stehen Tannen, Laubbäume, Büsche, Felsen, Häuser, Laternen, Tafeln, Kräne, Bagger und eine Tribüne mit Zuschauern. In den Kurven liegen Reifenspuren.
- **Grafik-Einstellung:** «Hoch», «Mittel» oder «Niedrig». «Niedrig» verzichtet auf Schatten und Spiegelungen und zeigt weniger Dekoration.

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

Die Verbindung läuft direkt von Browser zu Browser (WebRTC), vermittelt über den öffentlichen PeerJS-Server. Fällt ein Mitspieler aus, fährt ein Bot für ihn weiter. Verlässt der Host das Spiel, endet es für alle.

**Wichtig für den Host:** Lass die Lobby offen und im Vordergrund, bis alle da sind. Handys und Tablets frieren eine Seite im Hintergrund ein (andere App, Bildschirm aus), dann kann niemand beitreten. Kommst du zurück, meldet sich der Raum von selbst wieder an.

### Wenn der Beitritt nicht klappt

Der Gast versucht es bis zu dreimal von selbst (je 12 s). Danach sagt die Meldung, woran es liegt, und «Nochmals versuchen» startet einen neuen Anlauf.

| Meldung | Bedeutung | Was hilft |
|---|---|---|
| «Diesen Raum gibt es nicht (mehr)» | Code falsch, Raum geschlossen oder Gerät des Hosts eingeschlafen | Code prüfen. Der Host holt das Spiel nach vorne oder erstellt einen neuen Raum. |
| «… das Gerät des Hosts antwortet nicht» | Der Raum ist angemeldet, aber die Seite des Hosts ist im Hintergrund | Der Host lässt die Lobby sichtbar, der Gast versucht es nochmals. |
| «… die direkte Verbindung … kam nicht zustande» | Das Netz lässt keine direkte Verbindung zu (Gäste-WLAN, VPN, manche Mobilfunk-, Schul- und Firmennetze) | Beide Geräte ins selbe WLAN ohne VPN. Sonst einen eigenen TURN-Server in `CONFIG.netz.iceServer` eintragen. |
| «Der Vermittlungs-Server antwortet nicht» oder «… ist gerade nicht erreichbar» | Kein Internet, oder der PeerJS-Server ist überlastet | Internetverbindung prüfen, später nochmals versuchen. |

Unter der Meldung steht klein eine Zeile «Diagnose: …» mit der Stufe, der Anzahl Versuche und den gefundenen Adressen. `host` sind Adressen im selben Netz, `srflx` öffentliche Adressen, `relay` Umleitungen über einen TURN-Server. Diese Zeile hilft bei der Fehlersuche.

## Hochladen

- **itch.io:** Neues Projekt, «Kind of project: HTML», `index.html` hochladen und «This file will be played in the browser» ankreuzen. Grösse zum Beispiel 1280 × 720, Vollbild-Knopf einschalten.
- **GitHub Pages:** Im Repository unter Settings → Pages den Branch und den Ordner `/ (root)` wählen. Das Spiel liegt dann unter `https://<name>.github.io/26-Websites-Games/baustellen-rennen/`.
- **Netlify:** Den Ordner `baustellen-rennen` auf https://app.netlify.com/drop ziehen.

## Balancing: gemessene Werte

Stand 14.11.2026 mit den 8 Autos, pro Strecke 400 Rennen mit 8 gleich starken Bots und 200 Rennen mit einem starken gegen 7 mittlere Bots. Jedes Rennen lost die Autos neu zu.

| Zielwert | Kiesgrube | Bergpass |
|---|---|---|
| Führender nach Runde 1 gewinnt (Ziel 35–60 %) | 47,8 % | 38,0 % |
| Feld kommt innerhalb von 8 s ins Ziel | 100 % (Median 2,0 s) | 100 % (Median 2,5 s) |
| Stärkerer Bot gewinnt gegen 7 schwächere (Ziel ab 50 %) | 66,5 % | 45,0 % (knapp darunter) |
| Grösster Zeitverlust durch ein Hindernis (Ziel höchstens rund 2 s) | 1,52 s | 1,82 s |
| Längster Stillstand eines Bots (Ziel unter 3 s) | 0,1 s | 0,2 s |
| Bauwerke und Treffer pro Rennen | 22, 4 | 26, 8 |

**Siegquote pro Auto** (Ziel rund 8 % bis 17 %, ideal 12,5 %):

| Auto | Kiesgrube | Bergpass |
|---|---|---|
| Sportwagen | 12,0 % | 10,8 % |
| Limousine | 14,8 % | 10,8 % |
| Panzerwagen | 13,3 % | 14,0 % |
| Transporter | 12,3 % | 14,5 % |
| Geländewagen | 12,8 % | 13,0 % |
| Pick-up | 11,3 % | 12,5 % |
| Rennwagen | 13,0 % | 15,0 % |
| Rallye-Auto | 10,8 % | 9,5 % |

Damit die Autos trotz ihrer Eigenheiten gleich stark sind, sind Höchsttempo und Lenkung jedes Autos zusätzlich um wenige Prozent fein abgestimmt (`CONFIG.fahrzeuge`). Die Limousine hat einen 2,5-fachen statt 4-fachen Windschatten, weil sie sonst zu oft führte und dann doch verlor. Am Bergpass gewinnt der starke Bot mit 45 % etwas seltener als das Ziel von 50 %, weil das zugeloste Auto dort mehr ausmacht.

Selbst nachmessen: `index.html?sim=200` öffnen (dauert einige Minuten). Die Siegquote pro Auto zeigt diese Seite noch nicht an, sie stammt aus meiner Mess-Reihe.

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

- **Stand der grossen Überarbeitung (14.11.2026):** Autos, Zufalls-Auto, Showroom, Ton, Himmel, Licht und das neue Aussehen der Menüs sind eingebaut. Noch nicht gebaut sind Tunnels und zusätzliche Brücken, ein eigenes Abrollgeräusch für Schlamm und ein neues Aussehen der Anzeigen im Rennen (dort sind nur Schrift und Farben angepasst).
- Die Autos bestehen aus einfachen Flächen. Sie sind klar unterscheidbar und haben Felgen, leuchtende Lichter, getönte Scheiben, Spoiler, Spiegel und Auspuff, sehen aber nicht fotorealistisch aus.
- Ton lässt sich in der Test-Umgebung nicht anhören. Geprüft ist, dass alle Klänge ohne Fehler laufen, abgehört hat sie noch niemand.

- Der Online-Modus ist mit zwei Browsern gegen einen lokalen Vermittlungsserver getestet (Lobby, Rennen, Ergebnis, Revanche, Bot-Übernahme), ebenso die Fehlerfälle beim Beitritt (falscher Code, Host antwortet nicht, Netz blockiert, Vermittler nicht erreichbar). Über den öffentlichen PeerJS-Server im echten Internet konnte ich ihn in meiner Testumgebung nicht ausprobieren. Ein erster Versuch mit zwei Geräten scheiterte am 13.11.2026 beim Beitritt. Die Ursache ist noch offen, die Diagnose-Zeile unter der Fehlermeldung soll sie zeigen. Zwischen Geräten in verschiedenen Netzen braucht es manchmal einen TURN-Server, und die mitgelieferten von PeerJS sind nicht immer erreichbar.
- Die Bildrate ist nur mit Software-Grafik geprüft. Ruckelt es auf einem Gerät, hilft die Grafikstufe «Niedrig».
- Die Touch-Steuerung ist eingebaut, aber nicht getestet.
- Einen Grand-Prix-Modus gibt es nicht.
- Auf dem «Bergpass» gewinnt der starke Bot mit 52 % nur knapp über dem Zielwert.
- Bots bauen selten Umleitungen und Abkürzungen, weil die Punkte knapp sind.
- three.js 0.160.0 schreibt eine harmlose Warnung in die Browser-Konsole.

## Für Bastler

- `index.html?debug=1` zeigt Messwerte und Bauplätze.
- `index.html?sim=200` lässt 200 Bot-Rennen laufen und zeigt die Auswertung.
