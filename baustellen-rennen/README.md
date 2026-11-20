# Baustellen-Rennen

Ein 3D-Kartrennen im Low-Poly-Stil für den Browser. Die Besonderheit: Es gibt keine Zufalls-Items. Wer hinten liegt, sammelt Baupunkte (BP) und baut damit die Strecke um, mit Rampen und Abkürzungen für sich selbst oder Baustellen gegen die Fahrer davor.

Das ganze Spiel steckt in einer einzigen Datei: `index.html`.

## Starten

`index.html` doppelklicken (Chrome, Edge, Firefox oder Safari). Es braucht eine Internetverbindung, weil three.js 0.160.0 von einem CDN geladen wird (für Online-Spiele zusätzlich PeerJS 1.5.4). Sonst ist nichts zu installieren.

**Wenn «Das hat nicht geklappt» erscheint:** Dann gibt der Browser der Seite keine 3D-Grafik (WebGL). Meist hat die Grafikkarte vorher einmal ausgesetzt, und der Browser sperrt die 3D-Grafik dann bis zum Neustart. Den Browser wirklich neu starten hilft fast immer: In Chrome oben in die Adresszeile `chrome://restart` tippen und Enter drücken (Edge: `edge://restart`). Nur die Fenster zu schliessen reicht oft nicht, weil Chrome unter Windows unsichtbar weiterläuft. Sonst in den Einstellungen des Browsers unter «System» die Grafikbeschleunigung einschalten (Chrome und Edge: «Grafikbeschleunigung verwenden, wenn verfügbar»). Hilft auch das nicht, den Computer neu starten. Ob die 3D-Grafik wieder geht, zeigt get.webgl.org. Die Meldung im Spiel nennt diese Schritte. Hat der Browser die Grafikkarte für alle Seiten abgeschaltet (er meldet dann «GL_VENDOR = Disabled» oder «VENDOR = 0xffff»), sagt die Meldung das ausdrücklich: Dann liegt es nicht am Spiel. Seit dem 18.11.2026 versucht das Spiel zuerst einfachere Grafik-Einstellungen (ohne Kantenglättung, andere Grafikkarte). Setzt die Grafikkarte mitten im Spiel aus, stellt es selbst eine Grafik-Stufe tiefer und lädt neu. War die 3D-Grafik gesperrt, startet es beim nächsten Mal ebenfalls eine Stufe tiefer. Geht beim Einrichten der Grafik sonst etwas schief, versucht es das Spiel mit der Stufe «Niedrig» und zeigt den technischen Grund an.

- **Gegen Bots:** 1 Spieler und bis zu 11 Bots, Stufe leicht, mittel, schwer oder ultra (praktisch unschlagbar).
- **Lokal am selben Gerät:** 2 Spieler an einer Tastatur, mit Gamepads bis 4, dazu bis zu 11 Bots. Der Bildschirm wird geteilt.
- **Online:** bis zu 22 Menschen und dazu bis zu 11 Bots, ohne eigenen Server (siehe unten).

## Die 8 Autos

Es gibt acht Autos in vier Klassen. Jedes hat eine eigene Form, einen eigenen Motorklang und 14 Fähigkeiten mit einem Wert von 1 (schwach) bis 10 (stark). Jedes Auto hat mindestens einen Wert 10, einen zweiten von 8 bis 10 und mindestens zwei Werte von 1 bis 3, und jedes ist in mindestens einer Fähigkeit allein das beste. Die Punktsummen liegen zwischen 75 und 79, im Mittel bei 77. Alle Modelle sind eigene Entwürfe aus einfachen Flächen, ohne Marken, Logos oder Waffen.

| Fähigkeit | Sportwagen | Limousine | Panzerwagen | Transporter | Geländewagen | Pick-up | Rennwagen | Rallye-Auto |
|---|---|---|---|---|---|---|---|---|
| *Klasse* | Luxus | Luxus | Militär | Militär | Gelände | Gelände | Rennsport | Rennsport |
| Höchsttempo | **10** | 8 | 8 | 6 | 3 | 3 | 4 | 3 |
| Beschleunigung | 7 | 4 | 4 | 7 | 5 | **8** | 4 | 6 |
| Lenkung | 4 | 3 | 3 | 3 | 6 | 7 | **8** | 4 |
| Kurvenlage | 5 | 4 | 8 | 3 | 6 | 7 | **10** | 4 |
| Drift-Aufladung | 4 | 5 | 8 | 6 | 6 | 6 | 4 | **10** |
| Drift-Turbo | 4 | 4 | 8 | 5 | 6 | 7 | **10** | 4 |
| Windschatten | 8 | **10** | 3 | 4 | 3 | 4 | 7 | 3 |
| Rempeln | 4 | 7 | 8 | **10** | 5 | 5 | 3 | 3 |
| Gelände | 3 | 3 | 3 | 5 | **10** | 4 | 3 | 7 |
| Bande | 3 | 6 | 8 | 8 | 5 | 4 | 3 | 8 |
| Hindernisse | 3 | 6 | **10** | 5 | 8 | 4 | 2 | 8 |
| Rampen und Boost-Felder | 4 | 4 | 3 | 6 | 6 | 3 | 4 | **10** |
| Baukosten | 8 | 7 | 3 | 5 | 4 | **10** | 7 | 3 |
| BP-Aufladung | 8 | 6 | 2 | 5 | 4 | 7 | 8 | 3 |
| **Summe** | 75 | 77 | 79 | 78 | 77 | 79 | 77 | 76 |
| **Typ** | Raser | Windschatten-Jäger | Unaufhaltsam | Rammbock | Querfeldein | Baumeister | Kurvenkünstler | Drift-Springer |
| **Risiko (gemessen)** | mittel | mittel | tief | tief | hoch | hoch | mittel | mittel |

Fett: in dieser Fähigkeit allein das beste Auto. Was ein Wert genau bewirkt, steht unter «Jedes Auto mit 14 Fähigkeiten».

- **Sportwagen (Raser):** Auf der Geraden kaum zu schlagen, verliert aber neben der Strasse und an der Bande sehr viel.
- **Limousine (Windschatten-Jäger):** Holt im Windschatten auf, hat vorne allein aber nichts davon und lenkt träge.
- **Panzerwagen (Unaufhaltsam):** Kaum aufzuhalten, lenkt aber träge und kann kaum bauen.
- **Transporter (Rammbock):** Schiebt alle weg, ist in engen Kurven aber langsam.
- **Geländewagen (Querfeldein):** Fährt überall fast gleich schnell, ist auf langen Geraden aber langsam.
- **Pick-up (Baumeister):** Baut viel und billig, fährt aber langsamer.
- **Rennwagen (Kurvenkünstler):** In Kurven und beim Driften der beste, jede Berührung kostet ihn aber viel.
- **Rallye-Auto (Drift-Springer):** Driftet und springt am besten, ist auf Geraden aber langsam und kann kaum bauen.

**Lack:** 16 Farben, darunter matte («Olivgold matt», «Schwarz matt»), metallische («Silber metallic», «Nachtblau metallic», «Weinrot metallic») und ein Tarnmuster. Die Militärfahrzeuge tragen immer ein Tarnmuster im Ton der gewählten Farbe.

**Zufalls-Auto:** Vor jedem Rennen bekommt jeder Fahrer, auch jeder Bot, eines der 8 Autos zugelost. Vor dem Countdown zeigt eine kurze Auslosung das Auto mit Typ, Risiko, den drei stärksten und den zwei schwächsten Fähigkeiten. Niemand bekommt zweimal hintereinander dasselbe Auto. In den Renn-Einstellungen steht der Schalter «Zufalls-Auto: Ein / Aus». Ist er aus, wählt jeder sein Auto im Showroom selbst. Online legt der Host den Schalter für den ganzen Raum fest. Ist das Zufalls-Auto eingeschaltet, wählt man nur den Lack.

**Die Bots kennen ihr Auto:** Jeder Bot nutzt die Stärken seines Autos und meidet seine Risiken: Der Geländewagen schneidet Kurven über das Gelände ab, der Panzerwagen fährt durch Pylonen, Transporter und Panzerwagen rempeln, die Limousine sucht den Windschatten, der Pick-up baut öfter, das Rallye-Auto nimmt jedes Boost-Feld mit. Mehr unter «Jedes Auto mit 14 Fähigkeiten».

## Ton und Bild

- **Motor:** Jedes Auto hat einen eigenen, mehrschichtigen Motor, der auf Drehzahl, Gas und Gangwechsel reagiert, vom tiefen Diesel des Transporters bis zum kreischenden Rennwagen. Das Rallye-Auto pfeift mit dem Turbo.
- **Fahrgeräusche:** Reifenquietschen im Drift, Abrollen auf Asphalt und auf Kies, Fahrtwind, Landung, Rempler, Wandkontakt, Treffer.
- **Umgebung:** Hämmern und Bohren beim Bauen, Publikum beim Start, bei jeder Zieldurchfahrt und im Ziel, Hall auf Brücken.
- **Andere Autos** hört man aus der richtigen Richtung, leiser mit dem Abstand und mit veränderter Tonhöhe beim Vorbeifahren (wenn ein Spieler allein am Gerät fährt).
- **Musik:** eigene, im Code erzeugte Stücke fürs Menü und fürs Rennen. In der letzten Runde wird die Musik schneller und dichter. Dazu Signale für Countdown, Überholen, Baupunkte, letzte Runde und Ziel.
- **Regler:** In den Einstellungen gibt es getrennte Regler für Effekte und Musik und das Stummschalten (auch mit <kbd>M</kbd>). Alles entsteht mit Web Audio, es gibt keine Sound-Dateien.
- **Bild:** Himmel mit Haufen- und Schleierwolken und einer Sonne, die blendet, Dunst in der Ferne, weiche Schatten, Spiegelungen auf Lack und Glas. Lampen, Fenster, Rücklichter und Boost-Felder leuchten und strahlen (siehe «Grafik-Stufen»). Jede Strecke hat ihre Stimmung und Farbabstimmung: die Kiesgrube liegt im Abendlicht, der Bergpass im klaren Morgen. Am Streckenrand stehen Fichten mit gezackten Astschichten und Laubbäume mit Kronen aus Blätterbüscheln, die sich im Wind wiegen, dazu Gras, Blumen und Steine, Büsche, Felsen, Häuser, Laternen und Tafeln. Auf den Baustellen schwenken Baukräne mit Gittermast langsam ihren Ausleger mit der Last, Bagger mit Raupen graben im Takt, Bauarbeiter mit Helm und Warnweste schaufeln. Auf den Tribünen jubeln die Zuschauer. Über der Strecke kreisen Vögel, Seen haben Wellen und einen Schaumrand. Auf dem Start/Ziel-Bogen wehen Zielflaggen, hinter den Tribünen bunte Fahnen, in Paris und New York gehen Passanten auf den Gehsteigen. Nachts blenden die Scheinwerfer, der Fahrer dreht den Kopf in die Kurve. Stösse an Wänden, Bauwerken und anderen Autos hinterlassen Kratzer und Dellen in der Karosserie. In den Kurven liegen Reifenspuren.
- **Berühmte Orte:** In «Paris» fährt man am Abend durch den Triumphbogen, an der Glaspyramide vorbei, über Pflaster am Fluss, über eine Stein- und eine Eisenbrücke und unter dem beleuchteten Eisenturm hindurch, dann hinauf zur Mühle und zur weissen Kuppelkirche. Die Fenster und Laternen leuchten, die Scheinwerfer werfen Licht auf die Strasse. Im «Himalaya» beginnt das Rennen im Bergdorf unter Gebetsfahnen, führt auf Schotter und Schnee in Kehren zum Kloster, über eine Hängebrücke und einen gefrorenen See und steil hinunter, während Schnee fällt. In «Ägypten» startet das Rennen zur Mittagszeit an der Uferstrasse am Nil zwischen Palmen, Lehmhäusern und Marktständen, führt durch ein Tempeltor mit Reliefs, eine Allee mit liegenden Löwen und eine Säulenhalle, an Sphinx und Pyramiden vorbei hinauf auf das Plateau und über Sanddünen mit einem Sprung. In «New York» fährt man nachts auf nassen Strassen durch Häuserschluchten mit beleuchteten Fenstern, über einen Platz voller Leuchtreklamen, über eine Hängebrücke mit Lichterketten, an alten Lagerhäusern am Hafen entlang mit Blick auf die Skyline, über eine Stahlbrücke mit Gitterrost an der Statue mit der Fackel vorbei und durch den Park zurück. Am Strassenrand stehen Taxis, aus Rohren steigt Dampf. Alle Bauwerke sind eigene, vereinfachte Nachbauten aus Grundformen, die Reklamen zeigen nur Farben und Formen.
- **Beläge:** Asphalt, nasser Asphalt, Kopfsteinpflaster, Steinplatten, Schotter, Sand, Schnee, Eis, Holzbohlen und Stahlgitter fahren sich verschieden. Auf Eis dreht das Auto nur zögernd ein, auf nassem Asphalt hält es in Kurven weniger, im Sand, auf Schnee und Schotter ist es etwas langsamer, auf Pflaster, Bohlen und Gitter rüttelt die Federung. Die Bots bremsen vor glatten Stellen früher. Die Werte stehen kommentiert in `CONFIG.belag`.
- **Boost-Felder:** Auf jeder Strecke liegen fünf leuchtende Felder (in Paris vier) mit wandernden Pfeilen, meist am Ausgang einer Kurve. Wer darüber fährt, bekommt 1 s lang Schub. Auch die Bots steuern sie an. Anzahl, Dauer und Stärke stehen kommentiert in `CONFIG.boostfeld`; eine Strecke kann ihre Felder auch selbst festlegen (`boostfelder`).
- **Grafik-Einstellung:** «Niedrig», «Mittel», «Hoch» oder «Ultra». Beim ersten Start wählt das Spiel selbst, siehe «Grafik-Stufen».
- **Streckenwahl und Ergebnis:** Unter der Streckenwahl steht ein Steckbrief mit einer kleinen Karte (Höhenschatten, Abkürzungen, Boost-Felder, Sehenswürdigkeiten), Beschreibung, Länge, Belägen, Tageszeit und der Zahl der Abkürzungen und Boost-Felder; dahinter fährt die Strecke selbst in 3D vor. Nach dem Rennen stehen die drei Ersten mit ihren echten Autos und Lackfarben auf dem Siegerpodest.

## Grafik-Stufen

Beim ersten Start misst das Spiel kurz, wie schnell das Gerät ein Bild zeichnet, und wählt die Stufe selbst. Ein Hinweis unten im Bild sagt, welche es geworden ist. In den Einstellungen lässt sie sich jederzeit ändern. Mit `index.html?grafik=ultra` (oder `hoch`, `mittel`, `niedrig`) lässt sich eine Stufe auch erzwingen.

| Stufe | gedacht für | was dazukommt |
|---|---|---|
| Niedrig | Mittelklasse-Handy | keine Schatten, keine Nachbearbeitung, einfache Bäume, kein Gras |
| Mittel | normaler Laptop | Schatten, Nachbearbeitung mit Leuchten, Bäume mit Blätterkronen, Gras und Blumen, Steine, Seen mit Wellen, Zuschauer, Bauarbeiter, Passanten, Vögel, wehende Fahnen, Kräne mit Gittermast und Bagger, die sich bewegen, Dellen nach Stössen |
| Hoch | gute Grafikkarte | feinere Schatten, mehr Gras, Sonnenblendung, mehr Rauch und Staub |
| Ultra | sehr starke Grafikkarte | noch feinere Schatten, Umgebungsverdeckung (Ecken und Fugen dunkeln ab), am meisten Gras und Vögel, schärfere Oberflächen |

**Nachbearbeitung** (ab «Mittel», Teil `7c` im Code): Das Bild wird zuerst in hoher Helligkeits-Auflösung gezeichnet. Danach leuchten helle Stellen weich nach (Lampen, Fenster, Rücklichter, Boost-Felder), auf «Ultra» kommt die Umgebungsverdeckung dazu. Zum Schluss bekommt jeder Ort seine Farbabstimmung: Sättigung, Kontrast, ein leichter Farbstich und dunklere Bildecken (`BILDSTIL` im Code). Im Split-Screen bleiben die Bildecken hell.

**Leben in der Landschaft** (Teil `7d`): Gras, Blumen, Steine, Bäume, Zuschauer, Bauarbeiter, Passanten, Fahnen und Vögel sind «Instanzen»: viele tausend Stück, aber nur ein Zeichenaufruf pro Art. Wind, Jubeln, Schritte, flatternde Tücher und Flügelschlag rechnet die Grafikkarte. Die Zahlen pro Stufe stehen kommentiert in `CONFIG.grafik.leben`, die Dellen in `CONFIG.grafik.delle`.

**Budget pro Bild** mit 8 Fahrern (gemessen 6 s nach dem Start, Kamera hinter dem eigenen Auto, Höchstwert über alle sechs Strecken; Werte in `CONFIG.grafik.budget`):

| Stufe | Dreiecke | Zeichenaufrufe |
|---|---|---|
| Niedrig | 160’000 | 160 |
| Mittel | 460’000 | 370 |
| Hoch | 560’000 | 390 |
| Ultra | 570’000 | 370 |

«Ultra» ist nur auf Kiesgrube und Bergpass gemessen (in der Testumgebung lief die Messung der anderen Strecken in eine Zeitüberschreitung). New York ist die schwerste Strecke, dort liegt «Ultra» vermutlich etwas höher.

Gemessen ist das nur mit Software-Grafik in meiner Testumgebung (dort läuft jede Stufe mit etwa 10 Bildern pro Sekunde). Wie flüssig es auf echten Geräten läuft, konnte ich nicht messen.

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
| Abkürzung | 6 BP | öffnet einen kurzen Weg nur für dich (in der Kiesgrube, am Bergpass und in Paris spart er 0,5 bis 1,2 s pro Runde) |
| Pylonen | 3 BP | Slalom für alle Fahrer vor dir |
| Schlammloch | 3 BP | bremst auf der halben Fahrbahn |
| Absperrung | 4 BP | sperrt rund 60 % der Breite |
| Umleitung | 6 BP | sperrt an einer Abzweigung 20 s lang den kurzen Weg |

Baustellen gelten nur für Fahrer, die beim Bauen vor dir lagen. Für alle anderen sind sie durchsichtig. Sie bauen sich 2 s lang sichtbar auf, stehen nie näher als 3 s Fahrzeit vor einem Betroffenen und lassen immer eine Lücke. Ein Treffer bremst, hält aber nie an, danach ist man 3 s geschützt.

## Bestenliste

Jede Strecke hat eine Bestenliste mit der schnellsten Runde: eine Gesamtliste und eine Liste für jedes der 8 Autos. Im Hauptmenü unter «Bestenlisten» wechselt man mit ◀ ▶ die Strecke und die Liste.

- **Bleibt immer erhalten:** Keine neue Fassung des Spiels löscht oder versteckt Zeiten. Neue Auto-Werte und umgebaute Strecken schreiben in dieselbe Liste wie bisher, die Kennung einer Liste ist immer die Kennung der Strecke. Fassung 1.2 hatte am 18.11.2026 für kurze Zeit eigene, leere Listen (`kiesgrube-2` usw.). Seit dem Nachtrag am selben Abend stehen deren Zeiten wieder zusammen mit allen älteren in der Liste der Strecke: auf dem Gerät einmal zusammengelegt, in der gemeinsamen Liste mitgelesen (`BL_FRUEHER` in `93_bestenliste.js`). Geprüft mit `tools/erhaltentest.js` (Einträge aus allen Zeiten, 20 Prüfungen).

- **Was zählt:** die schnellste Runde, nicht die Gesamtzeit, weil die Rundenzahl einstellbar ist. Jede fertig gefahrene Runde zählt, auch wenn das Rennen danach abgebrochen wird. Alle Modi zählen: gegen Bots, Split-Screen und online. Simulationen und der Debug-Modus (`?debug=1`) zählen nicht.
- **Menschen:** Jeder steht mit seinem Namen da, und zwar nur einmal pro Liste mit seiner besten Zeit (Gross- und Kleinschreibung zählt nicht). In die gemeinsame Liste kommen neue Zeiten nur von Spielern, die mit Google angemeldet sind, immer unter ihrem eigenen Spielnamen und mit grünem Häkchen (siehe «Mit Google anmelden»). In der Liste eines Autos steht die beste Zeit mit diesem Auto.
- **Bots:** Pro Liste steht nur ein einziger Bot drin, der schnellste aller Zeiten: in der Gesamtliste der schnellste Bot auf dieser Strecke, in der Liste eines Autos der schnellste Bot mit diesem Auto. Er ist mit einem Symbol und «Bot» markiert und steht auf dem Platz, der zu seiner Zeit passt. Fährt ein Bot schneller, ersetzt er den alten.
- **Anzeige:** Die ersten drei Plätze sind in Gold, Silber und Bronze markiert, zu jedem Eintrag stehen Auto und Datum. In der Streckenwahl stehen der Rundenrekord und die ersten drei, im Rennen steht der Rekord unter der Rundenzeit. Bei einer neuen Bestzeit erscheint kurz «Neuer Rekord!», «Rekord mit dem Rennwagen!» oder «Platz 3 in der Bestenliste». Im Ergebnis steht, wer neu in der Liste ist, die neuen Einträge sind hervorgehoben.
- **Name:** Heisst man noch «Spieler», fragt das Spiel nach dem ersten Eintrag einmal nach dem Namen. Ändern geht wie bisher im Menü. Ein neuer Name gilt für neue Einträge, alte behalten ihren Namen.
- **Alle Spieler:** Ist eine Datenbank eingetragen (siehe «Gemeinsame Bestenliste einrichten»), zeigt die Bestenliste die Zeiten von allen Geräten. Jedes Gerät lädt nur die Zeiten seiner eigenen Spieler hoch: gegen Bots und im Split-Screen alle am Gerät, online jeder seine eigenen. Bot-Zeiten lädt das Gerät hoch, das das Rennen leitet (online der Host). Hochladen kann nur ein angemeldetes Gerät, und nur Name, Rundenzeit, Auto, Strecke, Bot-Stärke, Datum und die Konto-Nummer, sonst nichts. Im Split-Screen kommt nur Spieler 1 mit dem Konto in die gemeinsame Liste, die anderen bleiben in der Liste des Geräts.
- **Gleiche Regeln für alle Geräte:** Jedes Konto steht pro Liste einmal mit seiner besten Zeit, egal auf welchem Gerät sie gefahren wurde, auch wenn es seinen Namen geändert hat. Einträge aus der Zeit ohne Anmeldung (bis 18.11.2026) zählen wie früher nach Namen und stehen für immer ohne Häkchen da. Pro Liste steht ein Bot, der schnellste von allen Geräten.
- **Aktualisieren:** Die Liste wird beim Öffnen der Bestenliste und der Streckenwahl frisch geladen (höchstens einmal pro Minute), der Knopf «Aktualisieren» lädt sofort. Die Zeile über der Liste zeigt den Stand, zum Beispiel «Alle Spieler · Stand 14:05» oder «Keine Verbindung: nur dieses Gerät». Mit «Zeigen: Alle Spieler / Dieses Gerät» wechselt man zwischen der gemeinsamen Liste und der Liste des Geräts. Eigene neue Zeiten stehen sofort drin, auch bevor sie hochgeladen sind, und bleiben hervorgehoben. Den Rekord in der Streckenwahl und im Rennen nimmt das Spiel aus der gemeinsamen Liste, geladen vor dem Rennstart, nie während des Rennens.
- **Ohne Verbindung:** Das Spiel läuft wie gewohnt mit der Liste des Geräts. Zeiten, die noch nicht hochgeladen sind, merkt sich das Gerät und lädt sie beim nächsten Mal hoch, die Stand-Zeile zeigt, wie viele warten. Langsame, fehlende oder kaputte Antworten führen nie zu einem Fehler: Nach 6 s gilt «Keine Verbindung».
- **Bisherige Zeiten:** Nach dem ersten Anmelden lädt das Gerät die Zeiten, die vorher auf ihm gefahren wurden, einmal mit dem Kontonamen hoch.
- **Schutz:** Namen erscheinen immer als Text. Namen mit unerwünschten Wörtern (Liste in `CONFIG.bestenliste.verboten`) werden weder hochgeladen noch gezeigt. Runden unter der Mindestzeit einer Strecke (Streckenlänge geteilt durch das doppelte Höchsttempo, zum Beispiel 23,2 s in der Kiesgrube) zeigt das Spiel nicht, die Datenbank lehnt alles unter 20 s ab. Ganz verhindern lässt sich Schummeln ohne eigenen Server nicht (siehe «Bekannte Grenzen»), falsche Einträge kannst du in der Datenbank löschen.
- **Speichern:** Die Liste des Geräts liegt im Browser, getrennt von den Einstellungen. Online gefahrene Rennen tragen dort die Zeiten aller Mitspieler ein. In einem privaten Fenster gilt sie nur bis zum Neuladen. Unter «Einstellungen» löscht «Bestenliste löschen» eine Strecke oder alle, aber nur auf diesem Gerät, die gemeinsame Liste bleibt. Ohne eingetragene Datenbank verhält sich alles wie bisher: Jedes Gerät hat nur seine eigene Liste.

## Mit Google anmelden

Seit dem 18.11.2026 kommen neue Zeiten nur noch von angemeldeten Spielern in die gemeinsame Bestenliste, immer unter ihrem eigenen Spielnamen. Ohne Anmeldung spielt man ganz normal, die Liste des Geräts funktioniert wie bisher.

- **Knopf:** Unten im Hauptmenü steht «Mit Google anmelden» (gestaltet nach Googles Vorgaben, das farbige «G» ist im Code gezeichnet). Die Anmeldung läuft in einem kleinen Google-Fenster (Popup) über Firebase Authentication. Die Bibliothek kommt über CDN mit fester Version (Firebase 13.2.0). Lädt sie nicht oder fehlt das Netz, läuft das Spiel ohne Anmeldung weiter.
- **Angemeldet** zeigt das Menü «Angemeldet als Name» mit dem Google-Bild (nur auf diesem Gerät, nie in der Datenbank), «Name ändern» und «Abmelden». Die Anmeldung bleibt nach dem Neuladen erhalten. Der Spielname steht fest im Namensfeld bei «Dein Auto», online und für Spieler 1 im Split-Screen.
- **Spielname:** Beim ersten Anmelden wählt man einen Namen (Vorschlag: der Vorname aus dem Google-Konto), 2 bis 14 Zeichen, Buchstaben, Ziffern, Leerzeichen, Bindestrich, Unterstrich und Apostroph, ohne verbotene Wörter. Ein Name gehört genau einem Konto, wer zuerst kommt. Schon beim Tippen sagt das Spiel, ob er frei oder vergeben ist. Ändert man ihn, wird der alte Name frei. Gross- und Kleinschreibung zählt nicht («Lena» und «lena» sind derselbe Name).
- **Was hochgeladen wird:** Zeiten von Spieler 1 mit dem Kontonamen (im Split-Screen nur Spieler 1, online jeder seine eigenen). Bot-Zeiten lädt wie bisher nur das Gerät hoch, das das Rennen leitet, und nur, wenn es angemeldet ist. Zeiten, die man auf diesem Gerät vor dem ersten Anmelden gefahren ist (unter dem bisherigen Namen oder «Spieler»), liefert das Spiel nach dem ersten Anmelden einmal mit dem Kontonamen nach, mit dem Datum des Nachlieferns. Meldet man sich im Ergebnis an, kommt auch die Zeit aus diesem Rennen nach.
- **Häkchen:** In der Bestenliste tragen Einträge angemeldeter Spieler ein grünes Häkchen. Ein Konto steht einmal da, auch wenn es seinen Namen geändert hat. Die bisherigen Einträge (Liste `v1`, ohne Anmeldung) bleiben für immer sichtbar, ohne Häkchen. Ohne Anmeldung steht bei der gemeinsamen Liste und im Ergebnis ein kurzer Hinweis mit dem Knopf.
- **Datenschutz:** In der Datenbank stehen nur der Spielname, die Konto-Nummer (eine zufällige Kennung von Firebase) und die Zeiten, nie die E-Mail-Adresse oder das Bild. Diesen Satz zeigt das Spiel auch beim Knopf. Die E-Mail-Adressen der Konten sieht nur der Besitzer des Firebase-Projekts in der Konsole unter Authentication → Users.

**Wenn es nicht geht, sagt das Spiel es genau:**

| Fall | Meldung im Spiel |
|---|---|
| Spiel als Datei per Doppelklick geöffnet | «Anmelden geht nur auf der Webseite» (zum Beispiel auf popc-u.github.io), spielen geht trotzdem |
| Domain in Firebase nicht freigegeben | «Adresse nicht freigegeben»: nennt die Domain, die unter Authentication → Settings → Authorized domains fehlt |
| Popup blockiert | «Anmelde-Fenster blockiert»: Popups für die Seite erlauben, nochmals tippen |
| Popup geschlossen | kurze Meldung «Anmeldung abgebrochen» |
| Kein Netz | «Keine Verbindung»: Internet prüfen, nochmals versuchen |
| Browser in einer App (WhatsApp, Instagram, Facebook, TikTok …) | «Im richtigen Browser öffnen»: so geht es in Safari oder Chrome |
| Google-Anmeldung in Firebase ausgeschaltet | «Google-Anmeldung ausgeschaltet»: wo man sie einschaltet |
| Privates Fenster ohne Speicher, Cookies blockiert | eigene Meldung mit dem Grund |

### Was Johann tun muss

1. **Prüfen** (laut dir schon erledigt): In der [Firebase-Konsole](https://console.firebase.google.com) im Projekt «baustellen-rennen» unter **Authentication → Sign-in method** steht «Google» auf «Aktiviert». Unter **Authentication → Settings → Authorized domains** steht `popc-u.github.io`. Weitere Domains nur, wenn du das Spiel auch dort hochlädst (zum Beispiel `deinname.netlify.app`).
2. **Web-App:** erledigt. Die Kennungen (`apiKey`, `authDomain`, `projectId`, `appId`) stehen in `CONFIG.bestenliste.firebase`. Sie sind öffentlich, kein Passwort.
3. **Neue Regeln veröffentlichen, bevor du den Pull Request zusammenführst:** Realtime Database → Reiter **Regeln** → den ganzen Text löschen, den Text unten («Regeln zum Kopieren») einfügen → **Veröffentlichen**. Erst danach den Pull Request zusammenführen. In der Reihenfolge andersherum klappt die Namenswahl erst, wenn die Regeln da sind. Ab den neuen Regeln kann die alte Version des Spiels nichts mehr hochladen (ihre Zeiten bleiben auf dem Gerät).
4. **Freiwillig:** Unter Authentication → Sign-in method → Google kannst du den «Öffentlichen Namen des Projekts» setzen, zum Beispiel «Baustellen-Rennen». Diesen Namen zeigt das Google-Fenster beim Anmelden.

### Prüfliste für Handy und Laptop

Auf `https://popc-u.github.io/26-Websites-Games/baustellen-rennen/`, nachdem die Regeln veröffentlicht und der Pull Request zusammengeführt ist:

1. **Laptop:** Seite öffnen, unten im Menü «Mit Google anmelden». Im Google-Fenster ein Konto wählen. Das Spiel fragt nach dem Spielnamen und schlägt deinen Vornamen vor. Speichern: Das Menü zeigt «Angemeldet als …».
2. «Gegen Bots» öffnen: Das Namensfeld zeigt deinen Spielnamen und lässt sich nicht ändern. Eine Runde fahren. Unter «Bestenlisten» steht dein Name mit grünem Häkchen.
3. Seite neu laden: Du bist noch angemeldet.
4. **Handy** (Safari oder Chrome): Seite öffnen, mit einem anderen Google-Konto anmelden. Denselben Spielnamen wie auf dem Laptop eintippen: Das Spiel sagt «schon vergeben». Einen anderen Namen wählen, eine Runde fahren. Auf dem Laptop «Bestenlisten» → «Aktualisieren»: Beide Namen stehen mit Häkchen da.
5. Auf dem Handy «Abmelden», eine Runde fahren: Im Ergebnis steht der Hinweis mit dem Knopf, die Zeit kommt nicht in die gemeinsame Liste.
6. Den Link per WhatsApp an dich selbst schicken und dort öffnen: Beim Anmelden kommt «Im richtigen Browser öffnen».
7. In der Firebase-Konsole unter Realtime Database → Daten: `bestenliste` → `v2` → Strecke hat die neuen Einträge mit `u` (Konto-Nummer), dazu `namen` und `konten`. Nirgends steht eine E-Mail-Adresse.

## Gemeinsame Bestenliste einrichten

Damit alle Geräte dieselbe Liste sehen, braucht das Spiel eine kleine Online-Datenbank. Gewählt habe ich die **Firebase Realtime Database** von Google: Der Gratis-Tarif «Spark» braucht keine Kreditkarte und pausiert nicht, wenn eine Woche niemand spielt. Das Spiel erreicht die Datenbank direkt mit `fetch`, für die Anmeldung lädt es die Firebase-Bibliothek. Lesen geht von überall, auch per Doppelklick, anmelden nur auf freigegebenen Adressen wie GitHub Pages (siehe «Mit Google anmelden»). Regeln in der Datenbank legen fest, was erlaubt ist, und in der Firebase-Konsole kannst du Einträge löschen. Der Gratis-Tarif reicht weit (1 GB Speicher, 10 GB Download pro Monat, ein Eintrag hat rund 100 Byte). Nicht gewählt habe ich Supabase, weil Gratis-Projekte nach einer Woche ohne Nutzung pausieren, und einfache JSON-Speicher ohne Regeln, weil dort jeder alles löschen könnte.

Das machst du einmal, es dauert rund 10 Minuten:

1. **Konto:** https://console.firebase.google.com öffnen und mit einem Google-Konto anmelden.
2. **Projekt:** «Projekt erstellen» (englisch «Create a project») wählen, als Namen zum Beispiel `baustellen-rennen` eingeben und den Bedingungen zustimmen. Google Analytics brauchst du nicht, schalte es aus. Dann «Projekt erstellen» und warten, bis es fertig ist.
3. **Datenbank:** Links im Menü unter «Build» (oder «Erstellen») auf «Realtime Database» klicken, dann «Datenbank erstellen». Als Standort «Belgien (europe-west1)» wählen, dann «Im gesperrten Modus starten» und «Aktivieren». Wichtig: «Realtime Database», nicht «Firestore».
4. **Regeln:** Oben den Reiter «Regeln» öffnen, den ganzen Text dort löschen, den Text unten («Regeln zum Kopieren») einfügen und auf «Veröffentlichen» klicken.
5. **Adresse:** Im Reiter «Daten» steht oben die Adresse der Datenbank, zum Beispiel `https://baustellen-rennen-default-rtdb.europe-west1.firebasedatabase.app/`. Schick mir diese Adresse, dann trage ich sie ein. Sie ist nicht geheim: Sie steht später im Spiel, so wie die Zugangsdaten des Umweg-Servers, geschützt wird die Datenbank durch die Regeln. Selbst eintragen geht auch: `index.html` mit einem Texteditor öffnen, nach `server: ''` suchen und die Adresse zwischen die beiden Anführungszeichen schreiben, also `server: 'https://…firebasedatabase.app',`. Speichern und die Datei wie gewohnt hochladen.
6. **Prüfen:** Das Spiel öffnen und «Bestenlisten» wählen. Über der Liste steht nach einem Moment «Alle Spieler · Stand …». Steht dort «Keine Verbindung», stimmt die Adresse nicht oder die Regeln fehlen. Nach einer Runde mit Anmeldung erscheint in Firebase im Reiter «Daten» unter `bestenliste` → `v2` → Strecke ein neuer Eintrag. Dann auf einem zweiten Gerät (zum Beispiel dem Handy) eine Runde auf derselben Strecke fahren: Nach «Aktualisieren» müssen auf beiden Geräten beide Namen stehen.
7. **Einträge löschen:** Im Reiter «Daten» `bestenliste` → `v2` → die Strecke aufklappen (alte Einträge ohne Anmeldung stehen unter `v1`). Jeder Eintrag hat eine lange Kennung (zum Beispiel `-NxYz…`) und darin `n` (Name), `z` (Zeit in Sekunden), `a` (Auto), `b` (Bot ja oder nein), `s` (Bot-Stärke), `u` (Konto-Nummer) und `d` (Datum). Mit der Maus auf den Eintrag zeigen und auf das Löschen-Zeichen (✕ oder Papierkorb) klicken. Jede Verbesserung ist ein eigener Eintrag, ein Name kann also mehrmals vorkommen: Bei einem Schummler alle Einträge mit seiner Konto-Nummer löschen. Sperren kannst du sein Konto unter Authentication → Users («Konto deaktivieren»). In der Konsole darfst du löschen, die Regeln gelten nur für das Spiel. Auf dem Gerät, auf dem die Zeit gefahren wurde, bleibt sie in dessen eigener Liste, bis man sie dort unter «Einstellungen» löscht.

**Regeln zum Kopieren** (Stand 18.11.2026, mit Google-Anmeldung; erzeugt mit `tools/regeln.js`, geprüft mit 39 Fällen im Firebase-Emulator):

```json
{
  "rules": {
    ".read": false,
    ".write": false,
    "bestenliste": {
      "v1": {
        "$strecke": {
          ".read": true
        }
      },
      "v2": {
        "$strecke": {
          ".read": true,
          ".validate": "$strecke.matches(/^[a-z0-9-]{1,24}$/)",
          "$eintrag": {
            ".write": "auth != null && !data.exists() && newData.exists()",
            ".validate": "newData.hasChildren(['n', 'z', 'a', 'b', 'u', 'd']) && (newData.child('b').val() === true || (root.child('konten').child(auth.uid).child('n').val() === newData.child('n').val() && root.child('namen').child(root.child('konten').child(auth.uid).child('k').val()).child('u').val() === auth.uid))",
            "n": {
              ".validate": "newData.isString() && newData.val().length >= 1 && (newData.val().length <= 14 || (newData.val().length <= 20 && newData.parent().child('b').val() === true))"
            },
            "z": {
              ".validate": "newData.isNumber() && newData.val() >= 20 && newData.val() <= 600"
            },
            "a": {
              ".validate": "newData.isString() && newData.val().matches(/^(sport|limo|panzer|transporter|gelaende|pickup|renn|rallye)$/)"
            },
            "b": {
              ".validate": "newData.isBoolean()"
            },
            "s": {
              ".validate": "newData.isString() && newData.val().matches(/^(leicht|mittel|schwer|ultra)?$/)"
            },
            "u": {
              ".validate": "newData.val() === auth.uid"
            },
            "d": {
              ".validate": "newData.val() === now"
            },
            "$anderes": {
              ".validate": false
            }
          }
        }
      }
    },
    "namen": {
      "$k": {
        ".read": true,
        ".write": "auth != null && (!data.exists() || data.child('u').val() === auth.uid) && (newData.exists() || newData.parent().parent().child('konten').child(auth.uid).child('k').val() !== $k)",
        ".validate": "newData.hasChildren(['u', 'n']) && newData.child('n').val().toLowerCase() === $k && newData.parent().parent().child('konten').child(auth.uid).child('k').val() === $k",
        "u": {
          ".validate": "newData.val() === auth.uid"
        },
        "n": {
          ".validate": "newData.isString() && newData.val().length >= 2 && newData.val().length <= 14"
        },
        "$anderes": {
          ".validate": false
        }
      }
    },
    "konten": {
      "$uid": {
        ".read": "auth != null && auth.uid === $uid",
        ".write": "auth != null && auth.uid === $uid && newData.exists()",
        ".validate": "newData.hasChildren(['n', 'k']) && newData.child('k').val() === newData.child('n').val().toLowerCase() && newData.parent().parent().child('namen').child(newData.child('k').val()).child('u').val() === auth.uid && (!data.exists() || data.child('k').val() === newData.child('k').val() || !newData.parent().parent().child('namen').child(data.child('k').val()).exists())",
        "n": {
          ".validate": "newData.isString() && newData.val().length >= 2 && newData.val().length <= 14"
        },
        "k": {
          ".validate": "newData.isString()"
        },
        "$anderes": {
          ".validate": false
        }
      }
    }
  }
}
```

Was die Regeln erlauben: Die alte Liste `v1` kann jeder lesen, schreiben kann dort niemand mehr. In die neue Liste `v2` schreibt nur, wer angemeldet ist, und nur neue Einträge mit der eigenen Konto-Nummer (`u`): Menschen nur unter dem Namen, der ihrem Konto gehört, Bots mit Kennzeichen (`b` = true). Ändern und löschen kann niemand (ausser dir in der Konsole). Die Zeit muss zwischen 20 s und 600 s liegen, auf jeder Strecke gleich, darum braucht eine neue oder umgebaute Strecke keine neuen Regeln. Unter `namen` gehört jeder Name genau einem Konto, wer zuerst kommt, und nur dieses Konto kann ihn ändern oder freigeben. Unter `konten` steht der Spielname jedes Kontos, lesen und schreiben kann ihn nur das Konto selbst. Eine E-Mail-Adresse steht nirgends in der Datenbank.

## Online spielen

1. Der Host wählt «Online: Raum erstellen» und bekommt einen Code mit 5 Zeichen.
2. Mit «Link kopieren» schickt er den Einladungslink (`…/index.html?raum=CODE`) an die Mitspieler. Der Link funktioniert, sobald das Spiel im Internet liegt. Wer die Datei lokal öffnet, wählt «Online: Raum beitreten» und tippt den Code ein.
3. Alle wählen Name, Fahrzeug und Farbe und drücken «Bereit». Der Host stellt Strecke, Runden und Bots ein und startet. In einen Raum passen bis zu 22 Menschen (Host eingerechnet), dazu nimmt der Host bis zu 11 Bots.

Die Verbindung läuft direkt von Browser zu Browser (WebRTC), vermittelt über den öffentlichen PeerJS-Server. Lässt das Netz keine direkte Verbindung zu (das kann auch im selben WLAN passieren, wenn Router oder Firewall sie blockieren), läuft sie über einen Umweg-Server (TURN, siehe unten). Fällt ein Mitspieler aus, fährt ein Bot für ihn weiter. Verlässt der Host das Spiel, endet es für alle.

**Wichtig für den Host:** Lass die Lobby offen und im Vordergrund, bis alle da sind. Handys und Tablets frieren eine Seite im Hintergrund ein (andere App, Bildschirm aus), dann kann niemand beitreten. Kommst du zurück, meldet sich der Raum von selbst wieder an.

### Wenn der Beitritt nicht klappt

Der Gast versucht es bis zu dreimal von selbst (je 12 s). Danach sagt die Meldung, woran es liegt, und «Nochmals versuchen» startet einen neuen Anlauf.

| Meldung | Bedeutung | Was hilft |
|---|---|---|
| «Diesen Raum gibt es nicht (mehr)» | Code falsch, Raum geschlossen oder Gerät des Hosts eingeschlafen | Code prüfen. Der Host holt das Spiel nach vorne oder erstellt einen neuen Raum. |
| «… das Gerät des Hosts antwortet nicht» | Der Raum ist angemeldet, aber die Seite des Hosts ist im Hintergrund | Der Host lässt die Lobby sichtbar, der Gast versucht es nochmals. |
| «… kein Umweg-Server eingerichtet» | Das Netz lässt keine direkte Verbindung zu, und es ist kein TURN-Zugang eingetragen | Einen Umweg-Server einrichten (siehe unten). |
| «Auch der Umweg-Server war nicht erreichbar» | Zugang falsch oder gelöscht, Gratis-Kontingent aufgebraucht, oder das Netz blockiert ihn (VPN, Schul- oder Firmennetz) | Im Konto beim Anbieter nachsehen, ohne VPN versuchen. |
| «Auch über den Umweg-Server ging es nicht» | Sehr strenges Netz | Nochmals versuchen, sonst ein anderes Netz (z. B. Handy-Hotspot). |
| «Der Vermittlungs-Server antwortet nicht» oder «… ist gerade nicht erreichbar» | Kein Internet, oder der PeerJS-Server ist überlastet | Internetverbindung prüfen, später nochmals versuchen. |

Unter der Meldung steht klein eine Zeile «Diagnose: …» mit der Stufe, der Anzahl Versuche, den gefundenen Adressen und der Zahl der eingerichteten Umweg-Server. `host` sind Adressen im selben Netz, `srflx` öffentliche Adressen, `relay` Umleitungen über einen TURN-Server. Fehlt `relay` bei den eigenen Adressen, war kein Umweg-Server erreichbar. Diese Zeile hilft bei der Fehlersuche.

### Umweg-Server (TURN) einrichten

Der frühere Gratis-Umweg-Server von PeerJS ist abgeschaltet. Im Spiel ist darum ein eigener Gratis-Zugang bei Metered eingetragen (Plan «Free Trial», 500 MB pro Monat, das reicht für grob 150 Rennen mit 8 Autos oder 50 Rennen mit 33 Autos, je für einen Gast über den Umweg, siehe «Rundenzeit und grosse Felder»). Ist das Kontingent aufgebraucht, klappt das Online-Spiel bis zum nächsten Monat nur in Netzen, die direkte Verbindungen zulassen. Den Verbrauch zeigt das Dashboard von Metered. So richtest du einen eigenen Zugang ein:

1. Bei [Metered Open Relay](https://www.metered.ca/tools/openrelay/) ein Gratis-Konto anlegen, eine App erstellen und den Plan «Free Trial» wählen (500 MB pro Monat, ohne Kreditkarte).
2. Im Dashboard unter «TURN Server» einen Zugang anlegen («Add Credential»).
3. Benutzername und Passwort in `CONFIG.netz.iceServer` beim Eintrag mit `relay.metered.ca` ersetzen. Statt fester Daten kann das Spiel sie auch über `CONFIG.netz.turnAbruf` (API-Key von Metered) holen.

Die Zugangsdaten stehen damit lesbar in der Seite. Schlimmstenfalls brauchen Fremde das Gratis-Kontingent auf, mehr kann damit nicht passieren.

## Hochladen

- **itch.io:** Neues Projekt, «Kind of project: HTML», `index.html` hochladen und «This file will be played in the browser» ankreuzen. Grösse zum Beispiel 1280 × 720, Vollbild-Knopf einschalten.
- **GitHub Pages:** Im Repository unter Settings → Pages den Branch und den Ordner `/ (root)` wählen. Das Spiel liegt dann unter `https://<name>.github.io/26-Websites-Games/baustellen-rennen/`.
- **Netlify:** Den Ordner `baustellen-rennen` auf https://app.netlify.com/drop ziehen.

## Balancing: gemessene Werte

Diese Messung gilt für die Autos bis Version 1.1 (eine Stärke und eine Schwäche pro Auto). Seit Version 1.2 hat jedes Auto 14 Fähigkeiten, die Messung dazu steht unter «Jedes Auto mit 14 Fähigkeiten».

Stand 17.11.2026, seit Pylonen 3 BP kosten und Bots kaum noch Pylonen setzen. Pro Strecke 200 Rennen mit 8 gleich starken Bots und 100 Rennen mit einem «Schwer»-Bot gegen 7 «Mittel»-Bots, jedes Rennen lost die Autos neu zu. «Vorher» ist derselbe Code mit den alten Werten (Pylonen 2 BP, Bots bauen wie bis 17.11.2026), mit demselben Zufall.

| Zielwert | Kiesgrube vorher | Kiesgrube nachher | Bergpass vorher | Bergpass nachher |
|---|---|---|---|---|
| Führender nach Runde 1 gewinnt (Ziel 35–60 %) | 45 % | 47 % | 31 % | 50 % |
| Feld kommt innerhalb von 8 s ins Ziel | 100 % (Median 1,9 s) | 100 % (Median 2,0 s) | 100 % (Median 2,2 s) | 100 % (Median 3,1 s) |
| Stärkerer Bot gewinnt gegen 7 schwächere (Ziel ab 50 %) | 100 % | 96 % | 92 % | 96 % |
| Grösster Zeitverlust durch ein Hindernis (Ziel höchstens rund 2 s) | 1,18 s | 1,55 s | 1,85 s | 1,88 s |
| Längster Stillstand eines Bots (Ziel unter 3 s) | 0,1 s | 0,1 s | 0,2 s | 0,2 s |
| **Pylonen pro Rennen** | **13,8** | **0,2** | **15,9** | **0,2** |
| Bauwerke pro Rennen (Schlamm, Absperrung) | 21 (4,2, 1,6) | 15 (7,7, 3,9) | 27 (4,9, 2,3) | 18 (9,1, 5,1) |
| Treffer pro Rennen | 4,4 | 1,6 | 8,0 | 5,1 |

Die Bots setzen also 98 % weniger Pylonen. Mit den Punkten bauen sie stattdessen öfter Rampen, Schlammlöcher und Absperrungen, oder sie sparen: Jedes zweite Mal, wenn sie ein Schlammloch statt Pylonen bauen würden, heben sie die Punkte auf (`CONFIG.bots.schlammSparen`), sonst gäbe es doppelt so viele Schlammlöcher. Ein Mensch kann weiterhin so viele Pylonen setzen, wie er will.

**Siegquote pro Auto** (Ziel rund 8 % bis 17 %, ideal 12,5 %):

| Auto | Kiesgrube vorher | Kiesgrube nachher | Bergpass vorher | Bergpass nachher |
|---|---|---|---|---|
| Sportwagen | 10,5 % | 16,0 % | 15,5 % | 10,5 % |
| Limousine | 24,0 % | 23,5 % | 10,0 % | 18,0 % |
| Panzerwagen | 9,5 % | 14,5 % | 15,5 % | 8,5 % |
| Transporter | 11,5 % | 8,5 % | 10,0 % | 13,0 % |
| Geländewagen | 10,0 % | 11,0 % | 13,5 % | 15,0 % |
| Pick-up | 11,0 % | 10,5 % | 9,0 % | 7,0 % |
| Rennwagen | 17,5 % | 10,5 % | 18,0 % | 24,0 % |
| Rallye-Auto | 6,0 % | 5,5 % | 8,5 % | 4,0 % |

Bei 200 Rennen schwanken diese Werte um rund ±2,5 Prozentpunkte. Schon vorher lagen in der Kiesgrube die Limousine (24 %) und das Rallye-Auto (6 %) ausserhalb des Ziels. Nachher liegt am Bergpass der Rennwagen mit 24 % klar darüber und das Rallye-Auto mit 4 % darunter. Der Grund: Ohne Pylonen gibt es viel weniger Treffer, und davon profitiert der Rennwagen, der schnellste, aber empfindlichste Wagen. Ich habe die Autos nicht neu abgestimmt, weil sie sonst anders fahren würden als vorher. Das wäre ein eigener Auftrag. Am 14.11.2026 (400 Rennen pro Strecke, damals noch mit vielen Pylonen) lagen alle Autos zwischen 9,5 % und 15 %.

Damit die Autos trotz ihrer Eigenheiten gleich stark waren, waren Höchsttempo und Lenkung jedes Autos bis Version 1.1 zusätzlich um wenige Prozent fein abgestimmt. Seit Version 1.2 gibt es solche versteckten Faktoren nicht mehr. Die Limousine hat einen 2,5-fachen statt 4-fachen Windschatten, weil sie sonst zu oft führte und dann doch verlor. Am Bergpass gewann der starke Bot damals mit 45 % etwas seltener als das Ziel von 50 %. Seit dem 17.11.2026 ist «Schwer» viel stärker und gewinnt 97 bis 100 % (siehe «Schwer»-Bots). Mit den alten Pylonen-Werten (`bots.pylonen` 1, Pylonen 2 BP, `bots.schlammSparen` 0) gehen Rennen mit 8 «Mittel»-Bots genau gleich aus wie vor der Pylonen-Änderung (36 von 36 Vergleichsrennen mit gleichem Zufall). Fahrphysik und Fahren der Bots sind also unverändert, anders ist nur, was sie bauen.

Selbst nachmessen: `index.html?sim=200` öffnen (dauert einige Minuten). Seit Version 1.2 zeigt diese Seite auch Siege, mittleren Platz, Streuung und letzte Plätze pro Auto.

## «Schwer»-Bots

Ein «Schwer»-Bot fährt wie ein Profi: perfekte Linie ohne Zufallsfehler, späte Bremspunkte, Drift schon in sanfteren Kurven (mit Mini-Turbo), jedes Boost-Feld, sieht jedes Hindernis rechtzeitig und hat keine schlechten Tage. Er nutzt dieselbe Fahrphysik wie der Spieler und hat zusätzlich 3 % mehr Höchsttempo (`CONFIG.bots.stufen.schwer.tempo`, höchstens erlaubt sind 3 %). «Leicht» und «Mittel» sind unverändert. Seit Fassung 1.3 fährt er die Ideallinie, solange niemand in der Nähe ist, und sonst wie alle Bots seine eigene Spur (siehe «Bots auf verschiedenen Spuren»).

**Siege eines «Schwer»-Bots gegen 7 «Mittel»-Bots** (je 200 Rennen pro Strecke, Autos jedes Mal neu zugelost, mit Bauen):

| Stand | Kiesgrube | Bergpass | Paris | Himalaya | Ägypten | New York |
|---|---|---|---|---|---|---|
| bis 17.11.2026 (viele Pylonen) | 100 % | 95 % | 100 % | 99 % | 97 % | 100 % |
| seit 17.11.2026 (Pylonen 3 BP) | 98 % | 97 % | 100 % | 99 % | 99 % | 99 % |

**Vergleich mit einem Optimierer** (`tools/optimierer.js`): Er sucht pro Strecke mit 160 Versuchen die Fahr-Einstellungen (Kurventempo, Bremspunkte, Drift) mit der schnellsten fliegenden Runde, mit derselben Fahrphysik wie der Spieler und ohne Tempo-Vorteil. Gleiches Auto für alle Messungen.

| Strecke | Optimierer | «Schwer» im Spiel | Abstand | «Schwer» ohne Tempo-Vorteil | Abstand |
|---|---|---|---|---|---|
| Kiesgrube | 42,71 s | 42,02 s | −1,6 % | 43,07 s | +0,8 % |
| Bergpass | 41,35 s | 41,03 s | −0,8 % | 42,38 s | +2,5 % |
| Paris | 43,81 s | 43,10 s | −1,6 % | 44,18 s | +0,8 % |
| Himalaya | 44,14 s | 43,53 s | −1,4 % | 44,77 s | +1,4 % |
| Ägypten | 46,20 s | 45,51 s | −1,5 % | 46,72 s | +1,1 % |
| New York | 42,64 s | 41,55 s | −2,5 % | 42,93 s | +0,7 % |

Mit seinem Tempo-Vorteil ist der «Schwer»-Bot also auf jeder Strecke schneller als die beste Runde des Optimierers. Nur am Fahrkönnen gemessen (ohne Vorteil) liegt er 0,7 bis 2,5 % dahinter; am Bergpass etwas über dem Ziel von 2 %.

## «Ultra»-Bots

«Ultra» ist die Stufe über «Schwer», wählbar gegen Bots, im Split-Screen und online («Ultra · unschlagbar»). Ein «Ultra»-Bot fährt mit derselben Fahrphysik wie der Spieler, so gut es diese erlaubt: Kurventempo, Bremspunkte und Drift sind pro Strecke mit dem Optimierer gesucht (`tools/ultra.js`, mit vier verschiedenen Autos geprüft, damit sie für jedes Auto passen). Er macht keine Fehler, nimmt jedes Boost-Feld mit, sieht jedes Hindernis und hat 8 % mehr Höchsttempo (`CONFIG.bots.stufen.ultra.tempo`), am Himalaya und in Paris 12 % (`CONFIG.bots.stufen.ultra.strecken.himalaya.tempo` und `.paris.tempo`, siehe unten und «Neue Strecken»). Er holt nicht künstlich auf. Seine Baupunkte gibt er vor allem für sich selbst aus (Abkürzung, Rampe), Hindernisse baut er selten und Pylonen nie. Wie «Schwer» fährt er seit Fassung 1.3 allein die Ideallinie und im Verkehr seine eigene Spur.

**Schnellste Runde** (Sportwagen, beste fliegende Runde ohne andere Fahrer; der Optimierer hat hier 200 Versuche, darum weichen seine Zeiten leicht von der Tabelle bei «Schwer» ab):

| Strecke | Optimierer | «Ultra» im Spiel | Abstand | «Ultra» ohne Tempo-Vorteil | Abstand |
|---|---|---|---|---|---|
| Kiesgrube | 42,50 s | 39,87 s | −6,2 % | 42,50 s | 0,0 % |
| Bergpass | 41,17 s | 39,01 s | −5,3 % | 41,30 s | +0,3 % |
| Paris | 43,46 s | 41,04 s | −5,6 % | 43,81 s | +0,8 % |
| Himalaya (12 %) | 43,86 s | 40,85 s | −6,9 % | 44,34 s | +1,1 % |
| Ägypten | 46,07 s | 43,24 s | −6,1 % | 46,17 s | +0,2 % |
| New York | 42,36 s | 39,27 s | −7,3 % | 42,37 s | 0,0 % |

Ziel war: mindestens 4 % schneller als der Optimierer. Das ist auf allen Strecken erreicht.

**Siege eines «Ultra»-Bots gegen 7 «Schwer»-Bots** (je 200 Rennen pro Strecke, Autos jedes Mal neu zugelost, mit Bauen):

| Kiesgrube | Bergpass | Paris | Himalaya | Ägypten | New York |
|---|---|---|---|---|---|
| 99,5 % | 99,5 % | 99,5 % | 99,5 % (mit 8 %: 91 %) | 100 % | 100 % |

Dabei stand «Ultra» nie länger als 0,28 s still und musste nie zurückgesetzt werden. Pro Rennen baute er 0,26 bis 0,37 Mal etwas für sich selbst und 0,04 bis 0,24 Mal ein Hindernis für andere.

**Himalaya:** Mit 8 % Tempo-Vorteil gewann «Ultra» hier nur 91 % statt 99 % der Rennen. Die «Schwer»-Bots bauen jedes Hindernis vor alle Fahrer, die vor ihnen liegen, also immer auch vor den Führenden. In der letzten Runde stehen darum oft mehrere Hindernisse hintereinander vor «Ultra». Am Himalaya liegen zwei Bauplätze an heiklen Stellen: einer in der S-Kurve kurz nach der Schanze, wo «Ultra» mit seinem Tempo noch in der Luft ist, und einer in der holprigen Kehre vor dem Ziel, durch die er rutscht. Dort trifft er oft ein Schlammloch oder eine Absperrung. Ich habe sechs Arten ausprobiert, wie er dort vorsichtiger fahren kann (früher ausweichen, in der Mitte der Lücke bleiben, vor der Schanze bremsen, in der Luft ruhiger lenken, langsamer in Kurven, nicht driften). Jede kostete mehr Zeit, als sie sparte (71 bis 90 % Siege). Geholfen hat nur, vor einer Umleitung früh auf die Seite des Nebenwegs zu fahren. Mit mehr Tempo-Vorteil reicht es: Mit 10 % gewann er am Himalaya 97 %, mit 12 % 99 % der Rennen (je 100 Rennen). Am 17.11.2026 entschieden: «Ultra» bekommt 12 % nur am Himalaya, auf allen anderen Strecken bleiben es 8 %. Nachgemessen mit 200 Rennen gewinnt er dort 99,5 %.

## Rundenzeit und grosse Felder

Stand 17.11.2026 (Etappe 1 des Auftrags «faire Rundenzeit, grosse Lobbys, neue Strecken»).

### Rundenzeit ab der Ziellinie

Die Uhr jeder Runde läuft erst, wenn das Auto die Ziellinie zum ersten Mal überquert (genauer Zeitpunkt der Überfahrt, wie bei allen anderen Runden). Bis dahin zeigt das HUD «Runde 0:00.0». Renndistanz, Reihenfolge im Ziel und die Gesamtzeit ab dem Startsignal bleiben wie bisher. Das gilt überall gleich: gegen Bots, Split-Screen, online (der Host meldet die Überfahrt an alle Gäste), Bestenliste, Simulation und Werkzeuge.

**Fairness gemessen:** schnellste Runde nach Startplatz, je 200 Rennen mit 12 «Mittel»-Bots im gleichen Auto (Sportwagen), über alle sechs Strecken, mit Bauen. Die Zahl ist der Vorteil gegenüber dem Mittel aller Plätze (positiv = schneller). Ziel: kein Startplatz mehr als 0,1 s Vorteil.

| Startplatz | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | grösster Vorteil |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 Runde, vorher | +0,66 | +0,43 | +0,26 | +0,18 | +0,11 | +0,02 | −0,02 | −0,27 | −0,18 | −0,32 | −0,36 | −0,51 | **0,66 s** |
| 1 Runde, nachher | +0,06 | −0,01 | −0,05 | −0,05 | −0,10 | −0,09 | −0,03 | +0,06 | −0,00 | +0,02 | +0,06 | +0,13 | **0,13 s** |
| 3 Runden, vorher | −0,08 | −0,05 | −0,03 | −0,05 | −0,01 | −0,02 | −0,05 | −0,00 | +0,02 | +0,05 | +0,10 | +0,13 | **0,13 s** |
| 3 Runden, nachher | −0,02 | −0,05 | −0,03 | −0,06 | −0,06 | −0,02 | +0,02 | +0,02 | +0,04 | +0,07 | +0,04 | +0,05 | **0,07 s** |

Jeder Wert schwankt um rund ±0,03 s. Mit 3 Runden ist das Ziel erreicht. Mit 1 Runde ist der grosse Vorteil der vorderen Plätze (0,66 s) weg, übrig bleiben 0,13 s für den letzten Platz. Das kommt nicht mehr von der Uhr, sondern vom Rennen selbst: Ohne Bauen (gleiche Messung, `BAUEN=0`) ist die erste Reihe 0,30 s schneller, weil sie freie Fahrt hat. Mit Bauen holen die hinteren Plätze mit Rampen, Abkürzungen und Windschatten etwas mehr als das wieder auf. Bei nur einer Runde ist die schnellste Runde eben auch die einzige, mit allem Gedränge.

**Entscheidung Startaufstellung:** Wer vorne steht, hat weniger Anlauf und fährt langsamer über die Linie. Darum rückt ein kleines Feld auf der Startgeraden um ganze Reihen nach hinten, bis die vorderste Reihe höchstens 45 m Anlauf hat (`CONFIG.rennen.startAnlauf`) und die hinterste Reihe noch auf der geraden Strasse steht (Radius über 150 m). Mit 8 Autos stehen sie dann 44 bis 54 m vor der Linie statt 7 bis 32 m. Auf Ägypten und New York liegt die Linie kurz nach einer Kurve, dort bleibt das Feld vorne (Messung nur dieser beiden Strecken, 1 Runde: grösster Vorteil 0,07 s). Bei den Strecken-Umbauten (Etappen 4 und 5) bekommen alle Strecken eine lange Startgerade.

### Bis zu 11 Bots und 22 Menschen

- Gegen Bots und im Split-Screen wählt man bis zu 11 Bots (`CONFIG.rennen.maxBots`), online nimmt der Host bis zu 11 Bots dazu.
- Online treten bis zu 22 Menschen einer Lobby bei (`maxMenschen`). **Lesart:** Die Bots kommen dazu, im Rennen sind also höchstens 33 Autos (`maxFahrer`). Sind insgesamt höchstens 22 Autos gemeint, ist das nur `maxFahrer: 22`.
- **Startaufstellung:** in Dreierreihen, 4,6 m zwischen den Reihen, 3,4 m zwischen den Autos einer Reihe, jede Reihe leicht versetzt. 33 Plätze reichen von 7 m bis 55 m vor der Linie.
- **Jedes Auto bleibt unterscheidbar:** 16 Lacke. Sind mehr Autos als Lacke im Rennen, trägt jedes Namensschild eine Startnummer im Farbkreis des Lacks. Bots und Gäste bekommen immer den Lack, den bisher am wenigsten Autos haben. Das HUD zeigt «Platz 17/33».
- **Ergebnis mit 33 Zeilen und Lobby mit 22 Menschen:** Ab 13 Autos rückt die Ergebnisliste enger zusammen, auf dem Handy fallen die Spalten BP, Überholt, Bauwerke und Treffer weg (Platz, Name, Zeit, beste Runde bleiben). Die Lobby-Liste zeigt «Fahrer (22/22, bereit 21/21)», rückt ab 9 Spielern zusammen und lässt sich scrollen. Unter «Neu in der Liste» stehen nach dem Rennen höchstens 5 neue Bestenlisten-Zeiten, die eigenen zuerst, der Rest als «… und 17 weitere» (`CONFIG.bestenliste.neuZeilen`). Mit 22 Menschen war das sonst eine Liste von 44 Zeilen über dem Ergebnis.
- **Handy als Host:** Der Host rechnet alle Autos. Leitet ein Handy oder Tablet ein Rennen mit mehr als 12 Autos (`CONFIG.netz.handyHostMax`), zeigt die Lobby allen einen Hinweis.

### Leistung mit vielen Autos

**Grafik:** Nur die 8 Autos, die einer Kamera am nächsten sind («Niedrig»: 6), haben ein eigenes Modell (`CONFIG.grafik.feinMax`). Alle anderen zeichnet die Grafikkarte als Instanzen in einer noch einfacheren Fassung (1200 bis 2000 Dreiecke statt 1900 bis 3500), ein Zeichenaufruf pro Autotyp, und nur, wenn sie im Bild sind. Ein Auto wechselt erst, wenn es zwei Plätze weiter vorne oder hinten ist, damit es an der Grenze nicht flackert. Namensschilder zeigt jedes Bild höchstens für die 10 nächsten Autos (`CONFIG.grafik.schilder`). Mit bis zu 8 Autos («Niedrig»: 6) ändert sich nichts.

Dreiecke und Zeichenaufrufe pro Bild, gemessen 1,5 s nach dem Start mit der Kamera hinter dem letzten Auto, also mit dem ganzen Feld im Bild (der schwerste Moment eines Rennens):

| Stufe | Strecke | 8 Autos | 12 Autos | 33 Autos | Budget |
|---|---|---|---|---|---|
| Niedrig | Kiesgrube | 89 000 / 105 | 96 000 / 116 | 126 000 / 109 | 160 000 / 160 |
| Niedrig | Paris | 130 000 / 130 | 137 000 / 140 | 166 000 / 134 | 160 000 / 160 |
| Mittel | Kiesgrube | 396 000 / 367 | 401 000 / 375 | 433 000 / 380 | 460 000 / 370 |
| Mittel | Paris | 424 000 / 394 | 429 000 / 405 | 462 000 / 407 | 460 000 / 370 |
| Hoch | Kiesgrube | 473 000 / 371 | 479 000 / 379 | 510 000 / 382 | 560 000 / 390 |
| Hoch | Paris | 490 000 / 396 | 494 000 / 408 | 527 000 / 410 | 560 000 / 390 |

33 statt 8 Autos kosten ab «Mittel» rund 8 % mehr Dreiecke und höchstens 15 Zeichenaufrufe mehr, auf «Niedrig» (dort sind die Autos ein grosser Teil des Bildes) 28 bis 41 % mehr Dreiecke. Über dem Budget liegt mit 33 Autos nur Paris auf «Niedrig» (166 000, 4 % darüber) und knapp auf «Mittel» (462 000). Die Zeichenaufrufe liegen in Paris schon mit 8 Autos in diesem Moment über dem Budget, das 6 s nach dem Start gemessen ist. «Ultra» habe ich mit vielen Autos nicht gemessen (Zeitüberschreitung in der Testumgebung).

**Rechenzeit pro Schritt** (der Host rechnet alle Autos, 60 Schritte pro Sekunde, Kiesgrube, Paris und New York, Mittel aus 30 s Rennen mit «Mittel»- und «Schwer»-Bots): mit 8 Autos 0,2 bis 0,3 ms, mit 12 Autos 0,3 ms und mit 33 Autos 1,0 ms (99 % der Schritte unter 2,3 ms). Das sind mit 33 Autos rund 6 % der Rechenzeit einer Sekunde auf meinem Testrechner. Ein Handy rechnet grob drei- bis fünfmal langsamer, darum der Hinweis in der Lobby, wenn ein Handy ein grosses Rennen leitet.

### Netz

**Rennstart:** Beim Start baut jedes Gerät zuerst die Strecke auf. Bisher galt ein Gerät nach 6 Sekunden Funkstille als ausgefallen. Brauchte der Host für den Aufbau länger, meldeten alle Gäste «Die Verbindung zum Host ist abgebrochen», und ein langsamer Gast flog beim Host raus. Neu gilt beim Start eine Frist von 30 Sekunden, bis das erste Rennbild da ist (`CONFIG.netz.startTimeout`), danach wieder 6 Sekunden.

Der Host schickt jedem Gast 20-mal pro Sekunde den Zustand. Neu bekommt jeder Gast die 10 Autos, die seinem Auto am nächsten sind, jedes Mal, die übrigen jedes zweite Mal, und Werte, die sich selten ändern (BP, Rang, Runde), nur jedes fünfte Mal. Zahlen werden kürzer geschrieben. Fremde Autos zeichnet der Gast wie bisher 100 ms verzögert weich nach; fehlt ein Zustand, rechnet er höchstens 0,25 s weiter.

| Nutzdaten (KB/s, ohne WebRTC-Kopf) | vorher pro Gast | nachher pro Gast | vorher Host | nachher Host |
|---|---|---|---|---|
| 8 Autos, 7 Gäste | 12,0 | 8,6 | 84 | 60 |
| 33 Autos, 21 Gäste | 49,4 | **25,5** | 1038 | **536** |

Ziel erreicht: pro Gast höchstens 30 KB/s, beim Host zusammen höchstens 1 MB/s (Mittel über ein ganzes Rennen).

**Volltest mit 22 Menschen im Browser** (zwei Läufe): 22 Browserfenster auf einem Rechner (Host und 21 Gäste, dazu 11 Bots, Paris, 1 Runde) über einen lokalen Vermittlungsserver. Alle 22 traten der Lobby bei und waren 5 s nach «Rennen starten» im Rennen, alle 21 Gäste kamen ins Ergebnis, und alle 22 sahen dieselbe Ergebnisliste mit 33 Zeilen. In den ersten 15 Sekunden, wenn das ganze Feld dicht beisammen fährt und darum fast jedes Auto zu den 10 nächsten gehört, kamen pro Gast 29,9 und 30,6 KB/s an (also genau an der Grenze) und der Host schickte zusammen 627 und 643 KB/s. Verteilt sich das Feld, sinkt es auf die Werte der Tabelle.

**Umweg-Server (500 MB pro Monat):** Ein Rennen mit 3 Runden dauert mit Start und Ziel rund 2,5 Minuten. Mit 33 Autos sind das pro Gast rund 3,7 MB Nutzdaten, mit Verpackung und weil der Umweg-Server beide Richtungen zählt, grob 10 MB pro Gast, der den Umweg braucht (mit 8 Autos grob 3 MB). Die 500 MB reichen also für rund 50 «Gast-Rennen» über den Umweg: Brauchen 2 von 21 Gästen den Umweg, sind das rund 25 Rennen mit 22 Spielern im Monat, bei 5 Gästen rund 10. Wer im selben WLAN oder in einem offenen Netz spielt, braucht den Umweg meist nicht.

### Bauen mit vielen Autos

Mit vielen Autos wird im Pulk viel öfter überholt (am Bergpass 52-mal pro Rennen mit 8 Autos, 1317-mal mit 33), und jeder Fahrer verdiente doppelt so viele Baupunkte. Darum gibt es ab 9 Fahrern weniger pro Mal: Baupunkte × (8 ÷ Fahrer)^0,5, also × 0,82 mit 12 und × 0,49 mit 33 Fahrern (`CONFIG.bp.feldExponent`). Mit bis zu 8 Fahrern ändert sich nichts. Gleichzeitig stehen wie bisher höchstens 6 Hindernisse auf der Strecke.

Gemessen mit «Mittel»-Bots, je Strecke 100 Rennen (33 Fahrer: 40), Werte für Kiesgrube / Bergpass, pro Rennen:

| Fahrer | Baupunkte pro Fahrer | Bauwerke | davon Hindernisse | Treffer pro Auto | Überholmanöver | Feld in 8 s im Ziel |
|---|---|---|---|---|---|---|
| 8 | 7,0 / 8,6 | 14 / 18 | 11 / 14 | 0,16 / 0,59 | 38 / 52 | 100 / 100 % |
| 12, ohne Faktor | 9,6 / 10,8 | 30 / 32 | 24 / 24 | 0,38 / 1,43 | 102 / 143 | 100 / 100 % |
| 12, mit Faktor | 8,0 / 8,7 | 25 / 27 | 20 / 21 | 0,32 / 1,18 | 97 / 141 | 100 / 100 % |
| 33, ohne Faktor | 16,2 / 17,2 | 53 / 47 | 34 / 29 | 0,64 / 1,92 | 671 / 1317 | 100 / 100 % |
| 33, mit Faktor | 9,5 / 10,4 | 49 / 43 | 33 / 28 | 0,60 / 1,80 | 612 / 1218 | 100 / 98 % |

Mit dem Faktor verdient jeder Fahrer wieder fast so viele Baupunkte wie mit 8 Autos. Gebaut wird trotzdem kaum weniger, weil höchstens 6 Hindernisse gleichzeitig stehen und diese Grenze in grossen Feldern fast immer erreicht ist. Ein Hindernis im Pulk trifft mehr Autos: Am Bergpass fährt mit 33 Autos jedes rund 1,8-mal pro Rennen in eine Baustelle, mit 8 Autos 0,6-mal. Länger als 0,4 s steht dabei niemand still. Wer in grossen Feldern weniger Baustellen will, setzt `CONFIG.bp.feldExponent` höher (1 heisst: Baupunkte × 8 ÷ Fahrer).

## Ruhigere Fahrt

Stand 18.11.2026 (Etappe 3). Geändert ist nur, wie die Autos gezeichnet werden. Die Fahrphysik rechnet genau wie vorher: Gleiche Rennen mit gleicher Saat enden genau gleich, Höchsttempo, Beschleunigung, Lenkung und Drift sind unverändert.

### Ruckel-Mass

`tools/ruckeln.js` fährt auf jeder Strecke ein Rennen mit 8 «Mittel»-Bots (60 s, feste Saat) und lässt die Bildzeiten wie auf einem echten Gerät schwanken (12 bis 22 ms pro Bild). In jedem Bild schreibt es die dargestellte Lage jedes Autos auf: Höhe und Neigung des Aufbaus (Nicken, Rollen), Richtung und Ort. Ein **Ausreisser** ist eine Beschleunigung von Bild zu Bild über der Schwelle (auf 60 Bilder pro Sekunde umgerechnet: Höhe 1 cm, Nicken und Rollen 0,6°, Richtung 1,1°, Ort 2 cm). Jeder Ausreisser bekommt eine Ursache: Landung nach einem Sprung, Stoss (Wand, Rempler, Treffer), in der Luft, Randstein, sonst der Belag unter dem Auto. Dazu misst es die Kamera des eigenen Autos und spielt einen Online-Gast nach: Der Host schickt sein Bild 20-mal pro Sekunde wie im Spiel, jedes Paket kommt 40 bis 65 ms später an, und gemessen wird die Bahn der fremden Autos beim Gast.

Gemessen am 18.11.2026 mit `tools/ruckeln.js`, je Strecke 60 s Rennen mit 8 Autos (rund 8 Auto-Minuten), vorher = Stand vor Etappe 3, nachher = Etappe 3, gleiche Saat und gleiche Bildzeiten. Gezählt sind Ausreisser in der Lage der eigenen Autos (Höhe, Nicken, Rollen, Richtung, Ort), in der Bahn der fremden Autos beim Online-Gast (Höhe, Richtung, Ort) und bei der Kamera:

| Strecke | eigene Autos vorher | nachher | weniger | davon Asphalt | fremde Autos online vorher | nachher | weniger | Kamera |
|---|---|---|---|---|---|---|---|---|
| Kiesgrube | 2'247 | 140 | −94 % | 1'248 → 23 | 24'615 | 897 | −96 % | 91 → 0 |
| Bergpass | 4'427 | 1'041 | −76 % | 2'290 → 192 | 29'027 | 1'524 | −95 % | 82 → 0 |
| Paris | 7'761 | 362 | −95 % | 764 → 11 | 26'404 | 670 | −97 % | 95 → 0 |
| Himalaya | 9'166 | 833 | −91 % | 0 → 0 | 29'505 | 1'917 | −94 % | 43 → 4 |
| Ägypten | 2'467 | 527 | −79 % | 630 → 65 | 25'864 | 1'114 | −96 % | 30 → 1 |
| New York | 2'826 | 44 | −98 % | 0 → 0 | 24'703 | 484 | −98 % | 52 → 0 |
| **alle** | **28'894** | **2'947** | **−90 %** | **4'932 → 291** | **160'118** | **6'606** | **−96 %** | **393 → 5** |

Eigene Autos nach Ursache und Belag, alle Strecken zusammen:

| Ursache oder Belag | vorher | nachher | weniger |
|---|---|---|---|
| Pflaster | 10'115 | 105 | −99 % |
| Asphalt | 4'932 | 291 | −94 % |
| Schotter | 2'581 | 57 | −98 % |
| Randstein | 2'537 | 80 | −97 % |
| in der Luft | 1'993 | 880 | −56 % |
| Landung | 1'854 | 1'032 | −44 % |
| Schnee | 1'365 | 17 | −99 % |
| Stoss (Wand, Rempler, Treffer) | 883 | 262 | −70 % |
| nasse Strasse | 712 | 8 | −99 % |
| Sand | 631 | 39 | −94 % |
| Holz (Brücken) | 448 | 0 | −100 % |
| Gitter (Brücken) | 323 | 0 | −100 % |
| Fuss einer Schanze oder Rampe | 288 | 161 | −44 % |
| Platten | 132 | 0 | −100 % |
| Gelände neben der Strasse | 99 | 14 | −86 % |

Nach Grösse: Höhe 9'708 → 2'390 (−75 %), Nicken 7'794 → 211 (−97 %), Rollen 9'994 → 79 (−99 %). Höhe, Nicken und Rollen zusammen 27'496 → 2'680 (−90 %). Bei den fremden Autos kamen 145'705 der 160'118 Ausreisser vom Netz (Pakete, Verspätung), nachher 3'562 (−98 %).

- **Ziel «insgesamt mindestens 80 % weniger»:** erreicht (eigene Autos −90 %, fremde Autos −96 %, Kamera −99 %).
- **Ziel «auf Asphalt keine Ausreisser mehr»:** nicht ganz erreicht, 4'932 → 291 (−94 %). Die übrigen liegen knapp über der Schwelle und kommen von Knicken im Höhenprofil der Strasse, fast alle am Bergpass (steile Kehren bergauf) und in Ägypten. Die Federung verteilt einen Knick auf einige Bilder, aber höchstens um 6 cm, damit der Aufbau sichtbar auf den Rädern bleibt. Die Knicke selbst liegen in der Strecke. Sie zu glätten ändert die Fahrphysik und gehört darum zum Strecken-Umbau.
- **Was bleibt, ist gewollt:** 2'073 der 2'947 Ausreisser nachher sind Sprünge (in der Luft, Landung, Fuss einer Schanze). Dort gibt es weiter einen Stoss, nur weicher als vorher.

**Fahrgefühl unverändert:** `tools/gleichcheck.js` fährt auf allen 6 Strecken je 6 Rennen mit 8 «Mittel»-Bots in der alten und der neuen Fassung: alle 36 Ergebnisse sind genau gleich. Damit sind Höchsttempo, Beschleunigung, Lenkung, Drift und die schnellste Runde des Optimierers unverändert (0 % statt der erlaubten 1 %).

### Was das Holpern verursacht hat und was jetzt anders ist

Das Spiel rechnet 60 Schritte pro Sekunde, zeichnet aber so oft, wie das Gerät kann, meist mit ungleichmässigen Abständen. Zwischen zwei Schritten zeichnet es die Autos zwischen dem alten und dem neuen Stand. Mehrere Dinge sind dabei an diesem Takt vorbei gesprungen:

- **Fremde Autos online** (die grösste Ursache): Der Gast bekommt den Zustand jedes fremden Autos 20-mal pro Sekunde (ferne Autos 10-mal). Bisher fuhr er gerade von Paket zu Paket. An jedem Paket knickte die Bahn, und weil der Schritt danach den alten Stand überschrieb, sprang das Auto zwischen zwei Bildern zurück. Neu folgt der Ort einer Hermite-Kurve: Sie geht durch jeden empfangenen Zustand und hat dort dessen Tempo und Fahrtrichtung. Höhe und Blickrichtung laufen weich durch die Nachbarzustände. Fremde Autos rechnet der Gast nicht mehr selbst weiter (`Online.vorSchritt`, `hermite` in `10_config.js`).
- **Rütteln auf dem Belag:** Der Aufbau bekam in jedem Bild eine neue Zufallszahl. Bei schwankender Bildrate zitterte er darum ungleichmässig. Neu ist es eine weiche Schwingung, die mit dem Tempo schneller wird, gleich stark wie bisher (Randstein, Kies und Pflaster spürt man weiter).
- **Steigung und Rampen:** Die Neigung des Autos sprang an jeder Kante des Höhenprofils auf den neuen Wert. Neu folgt sie weich und mit begrenzter Beschleunigung.
- **Landung:** Nach jedem Sprung tauchte die Karosserie mit einem festen Stoss ein. Neu federt sie mit einem Teil der Fallgeschwindigkeit ein, kleine Hüpfer also kaum, hohe Sprünge deutlich.
- **Hüpfer beim Drift-Beginn und Schräglauf:** Beide folgten dem Rechenschritt und setzten hart ein. Neu hat der Hüpfer eine eigene Uhr, die genau mit der Zeit jedes Bildes läuft, und eine weiche Form (11 cm hoch, 0,28 s lang). Der sichtbare Schräglauf folgt dem Drift gedämpft (nur Optik, die Fahrtrichtung rechnet wie vorher).
- **Knicke im Höhenprofil** (Beginn einer Steigung, Kuppe, Brückenkante): Das Auto folgte dem Profil hart. Neu bleiben die Räder auf der Strasse, und der Aufbau federt weich nach: Er übernimmt das Höhen-Tempo jedes Rechenschritts, nur der Knick wird über einige Bilder verteilt (höchstens 6 cm Versatz).
- **Kamera:** Sie nahm die Fahrtrichtung und das Tempo des letzten Rechenschritts und sprang beim Driftbeginn zur Seite. Neu nimmt sie die Werte zwischen zwei Schritten und schwenkt beim Drift weich ein.

### Beweis

Bildfolge in Zeitlupe (48 Bilder, 50 ms pro Bild), links vorher, rechts nachher: Kiesgrube, 6 s nach dem Start, Sicht eines Online-Gasts mitten im Feld, gleiche Saat und gleiche ungleichmässige Bildzeiten (12 bis 22 ms). Vorher zucken die fremden Autos vor der Kamera bei jedem Paket vor und zurück, nachher fahren sie gleichmässig. Die Datei liegt im Projektordner unter `rundenzeit-lobby/e3-ruckeln-vorher-nachher.gif`, erzeugt mit `tools/ruckelbild.js`.

## Mehr Bilder pro Sekunde, keine Hänger

Stand 18.11.2026, Version 1.1 (Etappe 1 des Auftrags «Auto-Fähigkeiten, Bots, Leistung, Strecken»). Die Fahrphysik rechnet genau wie vorher: 36 von 36 Vergleichsrennen mit gleicher Saat enden gleich (`tools/gleichcheck.js`), das Ruckel-Mass der eigenen Autos ist unverändert (16,3 Ausreisser pro Auto-Minute vorher und nachher).

### Bildrate anzeigen und Leistungstest

- **Einstellungen → «Bildrate anzeigen»:** Oben rechts stehen die Bilder pro Sekunde, die tiefsten 1 %, die Hänger (Bilder über 50 ms) und wie lange das Spiel pro Bild selbst rechnet.
- **Einstellungen → «Leistungstest»:** Pro Grafik-Stufe 20 Sekunden feste Fahrt in New York mit 12 Autos (die ersten 3 Sekunden zählen nicht). Am Schluss eine Tabelle zum Kopieren. Geht auch mit `index.html?leistungstest=1`. Der letzte Test bleibt gespeichert («Letzter Leistungstest»).
- Die Kopie vom Stand vor dieser Etappe mit nur dem Leistungstest liegt im Projektordner unter `leistungstest/index-vorher.html`. So lässt sich auf dem eigenen Gerät vorher und nachher vergleichen.

### Was das Spiel jetzt anders macht

- **Autos gebündelt:** Räder, Sitze, Lenkrad und Fahrerkopf eines Autos sind je Material ein einziges Netz, das sich mit den Rädern und der Lenkung bewegt (Skinning). Pro Auto rund 14 statt 32 Zeichenaufrufe, das Bild ist gleich (Vergleichsbilder: 0,00 % abweichende Bildpunkte).
- **Schattenbild ohne Programmwechsel:** Teile mit Instanzen oder Skinning haben ihr eigenes Tiefen-Material, three.js muss pro Bild nicht mehr dutzendfach das Shader-Programm neu suchen.
- **Shader und Bilder vor dem Countdown:** Alle Shader-Programme, auch für Bauwerke, Hologramme und Lampen, die erst im Rennen auftauchen, werden vor dem ersten Bild übersetzt, alle Bilder (Lack, Schmutz, Schilder) vorher hochgeladen.
- **Schmutz:** Höchstens ein Auto pro Bild lädt seinen Schmutz neu hoch.
- **Siegerpodest:** Es entsteht in Schritten (Spiegelbild der Umgebung, dann je ein Podestplatz pro Bild), die Shader übersetzt der Browser im Hintergrund, dann wird es eingeblendet. Vorher geschah alles im Bild, in dem das Ergebnis aufging.
- **Ladeanzeige:** Vor dem Rennen zeigt ein Balken den Fortschritt. Die Welt der Strecke entsteht in 9 Schritten, dazwischen zeichnet der Browser die Anzeige. Der Countdown beginnt erst, wenn die Grafik bereit ist.
- **Shader-Programme bleiben erhalten:** Die alten Autos werden erst freigegeben, wenn die neuen vorbereitet sind. Sonst löschte three.js die Programme der Autos und übersetzte sie für das nächste Rennen neu.
- **Menü-Hintergrund:** Er zeigt die zuletzt gewählte Strecke. Startet man dort, ist die Welt schon gebaut.
- **Bildrate-Grenze (Einstellungen):** «Automatisch», 30, 60 oder «Aus». Automatisch: Auf Bildschirmen mit mehr als 75 Hz zeichnet das Spiel nur jedes zweite Bild, wenn es die volle Rate nicht schafft. Gleichmässig 72 Bilder wirken ruhiger als zwischen 90 und 144 springend.
- **Auflösung anpassen (Einstellungen, an):** Bremst die Grafikkarte (Bilder zu langsam, das Spiel selbst rechnet aber wenig), zeichnet das Spiel mit etwas weniger Bildpunkten, bis 70 % der Stufe (auf «Niedrig» bis 85 %). Reicht es wieder, wird es langsam wieder schärfer.
- **Vorschlag nach dem Rennen:** Lief ein Rennen dauerhaft unter 45 Bildern pro Sekunde (Handy und Tablet unter 28), schlägt das Ergebnis die nächsttiefere Grafik-Stufe vor, mit einem Knopf zum Wechseln.

### Messungen vorher und nachher

Alle Messungen in der Testumgebung mit Software-Grafik (SwiftShader). Zeichenaufrufe, Rechenzeit des Spiels und neue Shader sind damit gut vergleichbar, Bilder pro Sekunde nicht (die Software-Grafik ist viel langsamer als jede Grafikkarte).

| Messung | Szene | vorher | nachher | Ziel |
|---|---|---|---|---|
| Zeichenaufrufe pro Bild | New York, «Mittel», 8 Autos | 379 | 238 (−37 %) | −25 % ✓ |
| Zeichenaufrufe pro Bild | New York, «Mittel», 33 Autos | 384 | 247 (−36 %) | −25 % ✓ |
| Zeichenaufrufe pro Bild | Paris, «Niedrig», 8 Autos | 127 | 104 (−18 %) | −25 % ✗ |
| Rechenzeit JavaScript pro Bild, Mittel (95 %) | Paris, «Niedrig», 8 Autos | 2,46 ms (6,1) | 1,89 ms (3,7) | −30 %: −23 % (−39 %) ✗ |
| Rechenzeit JavaScript pro Bild, Mittel (95 %) | New York, «Mittel», 33 Autos | 6,51 ms (13,7) | 4,09 ms (7,5) | −40 %: −37 % (−45 %) ✗ |
| Grafik-Befehle pro Bild | New York, «Mittel», 33 Autos | 2520 | 2053 (−19 %) | |
| neue Shader-Programme nach dem Countdown | ganzes Rennen Kiesgrube, «Hoch», 8 Autos | 7 | 0 | 0 ✓ |
| neue Bilder (Texturen) nach dem Countdown | ebenso | 8 | 0 | |
| Speicherbereinigung über 10 ms | beide Szenen, je 200 Bilder | 0 (längste 8,9 ms) | 0 (längste 1,4 ms) | höchstens 1 pro Minute ✓ |
| Laden bis zum Countdown, Strecke läuft schon im Menü | 6 Strecken, «Hoch», 8 Autos | 28,0 s | 19,9 s (−29 %) | −30 % ✗ knapp |
| Laden bis zum Countdown, andere Strecke im Menü | 5 Strecken | 23,4 s | 21,4 s (−8 %) | −30 % ✗ |

Rechenzeit JavaScript: Fenster 480 × 270, ohne die Zeit in den Grafik-Befehlen (`tools/profil.js`, je 200 Bilder). Laden: Fenster 960 × 540 (`tools/ladezeit.js`, mit `GLEICH=1` läuft dieselbe Strecke schon im Menü). Hänger-Suche: `tools/haenger.js` fährt ein ganzes Rennen bis zum Podest und zählt pro Bild neue Shader-Programme, Texturen und Geometrien. Jedes neue Programm ist auf einem echten Gerät ein möglicher Hänger von 20 bis 300 ms. Auslöser vorher: Start, erster Rempler, erster Turbo, erstes Bauwerk (Hologramm, Kanten, Lampe). Programme pro Rennen: `tools/programme.js`.

**Online, gestörtes Netz** (`tools/ruckeln.js`, Kiesgrube, 60 s, 8 Autos; Ausreisser in der Bahn der fremden Autos beim Gast pro Auto-Minute):

| Netz | vorher | nachher | Verzögerung nachher |
|---|---|---|---|
| ungestört (40 bis 65 ms) | 133 | 156 | 137 ms (vorher fest 100 ms) |
| gestört (80 bis 160 ms, 3 % Verlust) | 4106 | 163 (−96 %) | 237 ms |
| Verhältnis gestört zu ungestört | 31-mal | 1,04-mal (Ziel höchstens 2-mal ✓) | |
| Rempeln zweier Menschen (eigenes Auto des Gasts, Saat 2): Sprünge, grösster | 27, 0,93 m | 4, 0,07 m | |

Was online geändert ist: Die Verzögerung der fremden Autos passt sich pro Auto an (so lang, dass 98 % der Pakete rechtzeitig da sind, plus anderthalb Paketabstände für ein verlorenes Paket, zwischen 60 und 400 ms) und ändert sich höchstens um 3 % Tempo, ohne Ruck. Pakete, die sich überholt haben, werden einsortiert statt weggeworfen. Rempelt ein fremdes Auto das eigene, schiebt es dieses pro Rechenschritt höchstens 8 cm weg, den Rest erledigt der Stoss. Die Meldung «Rempler» (Ton, Funken, Delle) kommt mit fremden Autos höchstens alle 0,3 s pro Paar.

**Vergleichsbilder** (`tools/ortbild.js`, gleiche Blickwinkel, Kiesgrube und New York, jede Grafik-Stufe, volle Auflösung): Im festen Blick weichen 0,5 bis 1,5 % der Bildpunkte ab (New York) und 0,5 bis 19 % in der Kiesgrube. Das kommt von dem, was sich bewegt: Zuschauer, Bäume im Wind, Autos am Start. Sichtbar ist kein Unterschied. Die Bilder liegen im Projektordner unter `leistung/` (`e1-vorher-…`, `e1-nachher-…`, `e1-diff-…`), dazu die Ladeanzeige, die Einstellungen und der Leistungstest. Die Messdaten stehen in `leistung/messungen-etappe1.tgz`.

### CONFIG-Werte dieser Etappe

| Wert | Bedeutung |
|---|---|
| `leistung.strecke`, `autos`, `dauer`, `aufwaermen` | Leistungstest: New York, 12 Autos, 20 s pro Stufe, die ersten 3 s zählen nicht |
| `leistung.haenger` | 50: ein Bild über 50 ms zählt als Hänger |
| `leistung.skalaMin`, `skalaSchritt`, `skalaRuhe` | Auflösung anpassen: bis 0,7 (auf «Niedrig» 0,85), Schritte von 0,1, danach 1,5 s Ruhe |
| `leistung.zuLangsam`, `reicht` | 1,25 und 1,08: ab wann die Auflösung sinkt und wieder steigt (Bildabstand mal Ziel) |
| `leistung.vorschlag`, `vorschlagHandy` | 45 und 28 Bilder pro Sekunde: darunter schlägt das Ergebnis eine tiefere Stufe vor |
| `netz.puffer`, `pufferMin`, `pufferMax` | Verzögerung der fremden Autos: Start 0,10 s, nie unter 0,06 s, nie über 0,40 s |
| `netz.pufferAnteil`, `pufferAbstand`, `pufferRand` | 0,98 der Pakete, 1,5 Abstände, 0,012 s Rand |
| `netz.pufferHoch`, `pufferRunter` | 0,03 und 0,01: so schnell darf die Verzögerung wachsen und schrumpfen (Sekunden pro Sekunde) |
| `fahren.fernKorr` | 0,08 m: so weit schiebt ein fremdes Auto das eigene pro Rechenschritt höchstens weg |

### Entscheidungen

- Gemessen wird in der Software-Grafik der Testumgebung. Dort sind Zeichenaufrufe, Rechenzeit, neue Shader und Speicherbereinigung verlässlich, Bilder pro Sekunde nicht. Für das echte Gerät gibt es den Leistungstest in den Einstellungen.
- Der Menü-Hintergrund zeigt die zuletzt gewählte Strecke statt einer zufälligen: Dann ist sie beim Start schon gebaut.
- Online startet das Rennen ohne Ladeanzeige wie bisher, weil alle Geräte gemeinsam auf die Uhr des Hosts warten.
- Die adaptive Auflösung ist eingeschaltet und lässt sich in den Einstellungen ausschalten. Die Vergleichsbilder sind mit voller Auflösung gemacht.

### Grenzen

- Ladezeit: −30 % ist knapp nicht erreicht (−29 %, wenn die Strecke schon im Menü läuft; −8 % sonst). In der Software-Grafik dauert das erste Bild 3 bis 5 Sekunden und überwiegt alles. Auf einem echten Gerät fällt das Bauen der Welt (0,3 bis 0,6 s) stärker ins Gewicht, und das läuft jetzt in Schritten mit Balken.
- Rechenzeit: −23 % statt −30 % auf «Niedrig» mit 8 Autos und −37 % statt −40 % mit 33 Autos (Mittelwert). Die langsamen Bilder (95 %) sind um 39 % und 45 % schneller.
- Zeichenaufrufe auf «Niedrig»: −18 % statt −25 %. Dort ist der Anteil der Autos kleiner.
- Hänger auf echten Geräten lassen sich hier nicht messen. Ersatz: Im ganzen Rennen entstehen keine neuen Shader-Programme und keine neuen Bilder mehr.
- Gebündelte Autos laden pro Bild eine kleine Tabelle mit 4 Knochen-Lagen hoch (wenige hundert Bytes pro Auto).

## Jedes Auto mit 14 Fähigkeiten

Stand 18.11.2026, Version 1.2 (Etappe 2 des Auftrags «Auto-Fähigkeiten, Bots, Leistung, Strecken»).

Jedes Auto hat jetzt 14 Fähigkeiten mit Werten von 1 bis 10 (Tabelle unter «Die 8 Autos»). Was ein Wert bewirkt, steht als kommentierte Tabelle in `CONFIG.faehigkeit`, die Werte der Autos stehen in `CONFIG.fahrzeuge`. Die Fahrphysik, die Bots und die Anzeige rechnen nur mit diesen Zahlen. Versteckte Zusatzfaktoren pro Auto gibt es keine (`CONFIG.feinabstimmung` ist leer).

### In der Auto-Wahl

Unter dem Showroom stehen 14 Balken von 1 bis 10 in fünf Gruppen: Fahren (Höchsttempo, Beschleunigung, Lenkung, Kurvenlage), Drift (Aufladung, Turbo), Robust (Rempeln, Bande, Hindernisse), Strecke (Gelände, Windschatten, Rampen und Boost-Felder) und Bauen (Baukosten, BP-Aufladung). Rot sind Werte von 1 bis 3, grün Werte von 8 bis 10. Daneben stehen Klasse, Typ, das gemessene Risiko und zwei Zeilen «Stark bei …» (alle Werte ab 8) und «Risiko bei …» (die Werte bis 3). Antippen, Zeigen mit der Maus oder Ansteuern mit der Tab-Taste erklärt eine Fähigkeit in einem Satz mit der echten Wirkung, zum Beispiel «Baukosten 3: Alle Bauwerke kosten 1,3-mal so viel.» Bei der Auslosung des Zufalls-Autos zeigt eine Karte die Kurzfassung: Typ, Risiko, die drei stärksten und die zwei schwächsten Werte.

Die Bilder liegen im Projektordner unter `leistung/`: `e2-sport-wahl.png` (Auto-Wahl am Computer), `e2-handy-wahl.png` (Auto-Wahl auf dem Handy mit der Erklärung zu «Gelände 10») und `e2-handy-los.png` (Karte bei der Auslosung), erzeugt mit `tools/faehigbild.js`.

### Was die Werte bewirken (`CONFIG.faehigkeit`)

Jede Zahl ist ein Faktor zur Einstellung weiter oben in `CONFIG` (1 = genau wie dort). Die Spalte «Startwert» ist die Spanne aus dem Auftrag.

| Fähigkeit | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | Startwert | wirkt auf |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Höchsttempo | 0,9925 | 0,9942 | 0,9958 | 0,9975 | 0,9992 | 1,0008 | 1,0025 | 1,0042 | 1,0058 | 1,0075 | −4 % bis +4 % | Höchsttempo |
| Beschleunigung | 0,9 | 0,922 | 0,944 | 0,967 | 0,989 | 1,011 | 1,033 | 1,056 | 1,078 | 1,1 | ×0,7 bis ×1,3 | Beschleunigung |
| Lenkung | 0,95 | 0,961 | 0,972 | 0,983 | 0,994 | 1,006 | 1,017 | 1,028 | 1,039 | 1,05 | ×0,85 bis ×1,15 | Drehrate und wie direkt die Lenkung reagiert |
| Kurvenlage | 1,2 | 1,144 | 1,089 | 1,033 | 0,978 | 0,922 | 0,867 | 0,811 | 0,756 | 0,7 | ×1,4 bis ×0,5 | Tempoverlust beim Lenken |
| Drift-Aufladung | 1,15 | 1,117 | 1,083 | 1,05 | 1,017 | 0,983 | 0,95 | 0,917 | 0,883 | 0,85 | ×1,5 bis ×0,6 | Zeit bis zum Mini-Turbo |
| Drift-Turbo | 0,85 | 0,889 | 0,928 | 0,967 | 1,006 | 1,044 | 1,083 | 1,122 | 1,161 | 1,2 | ×0,6 bis ×1,5 | Schub des Mini-Turbos (Stärke und Dauer je mit der Wurzel) |
| Windschatten | 0,3 | 0,45 | 0,6 | 0,8 | 1 | 1,2 | 1,45 | 1,75 | 2,1 | 2,5 | ×0,3 bis ×2,5 | Tempo-Gewinn im Windschatten |
| Rempeln | 0,6 | 0,7 | 0,8 | 0,9 | 1 | 1,25 | 1,5 | 1,9 | 2,4 | 3 | ×0,6 bis ×3 | Masse beim Rempeln |
| Gelände | 1,5 | 1,35 | 1,2 | 1,1 | 1 | 0,9 | 0,75 | 0,6 | 0,47 | 0,35 | ×1,5 bis ×0,35 | Tempoverlust neben der Strasse, im Schlamm, auf Kies, Sand, Schnee und Abkürzungen |
| Bande | 1,5 | 1,35 | 1,2 | 1,1 | 1 | 0,9 | 0,8 | 0,65 | 0,5 | 0,4 | ×1,5 bis ×0,4 | Tempoverlust an Wand und Bande |
| Hindernisse | 1,6 | 1,45 | 1,3 | 1,15 | 1 | 0,88 | 0,75 | 0,6 | 0,45 | 0,3 | ×1,6 bis ×0,3 | Bremsen durch Pylonen und Absperrungen |
| Rampen und Boost-Felder | 0,85 | 0,894 | 0,939 | 0,983 | 1,028 | 1,072 | 1,117 | 1,161 | 1,206 | 1,25 | ×0,7 bis ×1,5 | Schub-Dauer eigener Rampen und der Boost-Felder |
| Baukosten | 1,5 | 1,4 | 1,3 | 1,2 | 1,1 | 1 | 0,9 | 0,8 | 0,65 | 0,5 | ×1,5 bis ×0,6 | Preis aller Bauwerke |
| BP-Aufladung | 0,6 | 0,7 | 0,8 | 0,9 | 1 | 1,1 | 1,2 | 1,35 | 1,55 | 1,75 | ×0,6 bis ×1,5 | gesammelte Baupunkte |

Preise mit Baukosten: Grundpreis × Faktor, kaufmännisch gerundet (x,5 aufwärts), mindestens 1 BP. Beispiel Pick-up (Baukosten 10, Faktor 0,5): Rampe 2, Pylonen 2, Schlammloch 2, Absperrung 2, Abkürzung 3, Umleitung 3 BP.

### Gemessen: gleich stark?

Je 400 Rennen pro Strecke und Stufe: 8 Bots derselben Stufe, jedes Auto einmal, zufällige Startplätze, mit Bauen (`node tools/faehig.js 400`). «Ultra» mit 100 Rennen pro Strecke. Ziel über alle Strecken: jedes Auto 10 bis 15 % Siege und mittlerer Platz 4,0 bis 5,0. Streuung: Standardabweichung der Zielplätze.

| Auto | Siege «Mittel» | Platz «Mittel» | Siege «Schwer» | Platz «Schwer» | Siege «Ultra» | Platz «Ultra» | Streuung (Mittel und Schwer) | vorher Siege «Mittel» / «Schwer» |
|---|---|---|---|---|---|---|---|---|
| Sportwagen | 12,9 % | 4,44 | 13,4 % | 4,42 | 17,2 % | 4,26 | 2,28 | 13,5 % / 8,0 % |
| Limousine | 12,5 % | 4,14 | 11,8 % | 4,10 | 12,7 % | 4,01 | 2,21 | 21,7 % / 27,0 % |
| Panzerwagen | 12,3 % | 4,32 | 11,5 % | 4,21 | 9,0 % | 4,44 | 2,12 | 17,0 % / 14,3 % |
| Transporter | 12,0 % | 4,11 | 8,6 % | 4,08 | 8,0 % | 4,36 | 2,08 | 10,7 % / 10,7 % |
| Geländewagen | 14,2 % | 4,77 | 15,8 % | 4,71 | 12,3 % | 4,81 | 2,42 | 13,2 % / 16,0 % |
| Pick-up | 13,0 % | 4,99 | 9,8 % | 5,29 | 6,8 % | 5,24 | 2,42 | 11,5 % / 12,7 % |
| Rennwagen | 13,4 % | 4,38 | 11,3 % | 4,78 | 15,8 % | 4,45 | 2,27 | 8,8 % / 8,7 % |
| Rallye-Auto | 9,7 % | 4,86 | 17,8 % | 4,42 | 18,2 % | 4,43 | 2,30 | 3,7 % / 2,7 % |

«Vorher» ist der Stand vor dieser Etappe (alte Autos mit einer Stärke und einer Schwäche), 100 Rennen pro Strecke und Stufe, gleicher Zufall.

**Pro Strecke** (Siege, Mittel aus «Mittel» und «Schwer»; erlaubt sind 4 bis 25 %, jedes Auto soll auf mindestens einer Strecke unter den besten drei sein):

| Strecke | Sportwagen | Limousine | Panzerwagen | Transporter | Geländewagen | Pick-up | Rennwagen | Rallye-Auto |
|---|---|---|---|---|---|---|---|---|
| Kiesgrube | 9,9 % | 8,8 % | 19,1 % | 10,5 % | 3,6 % | 24,9 % | 14,3 % | 9,0 % |
| Bergpass | 13,0 % | 9,8 % | 12,9 % | 10,3 % | 12,3 % | 14,9 % | 18,4 % | 8,6 % |
| Paris | 14,1 % | 13,1 % | 12,8 % | 17,8 % | 5,6 % | 9,1 % | 14,3 % | 13,3 % |
| Himalaya | 3,9 % | 3,1 % | 6,9 % | 7,6 % | 41,9 % | 8,6 % | 7,6 % | 20,4 % |
| Ägypten | 15,5 % | 10,3 % | 9,8 % | 8,9 % | 24,1 % | 4,6 % | 8,9 % | 18,0 % |
| New York | 22,5 % | 28,0 % | 10,3 % | 7,0 % | 2,5 % | 6,1 % | 10,5 % | 13,1 % |
| unter den besten drei | 4-mal | 1-mal | 1-mal | 1-mal | 2-mal | 3-mal | 3-mal | 3-mal |

Über alle Strecken liegen 4 von 8 Autos in beiden Stufen zwischen 10 und 15 %. Daneben liegen: Transporter (8,6 % auf «Schwer»), Geländewagen (15,8 % auf «Schwer»), Pick-up (9,8 % auf «Schwer», mittlerer Platz 5,29), Rallye-Auto (9,7 % auf «Mittel», 17,8 % auf «Schwer»). Beim Rallye-Auto gehen die beiden Stufen in verschiedene Richtungen: Ein Punkt mehr hilft ihm auf «Mittel» und macht es auf «Schwer» noch stärker. Pro Strecke sind die Unterschiede gross: Der Geländewagen gewinnt am Himalaya 41,9 %, in der Kiesgrube und in New York unter 5 %. Das liegt an den Strecken selbst (Gelände, Abkürzungen, lange Geraden). Sie werden in Etappe 4 und 5 neu gebaut, danach gleiche ich in Etappe 6 noch einmal aus.

### Risiko

Das Risiko eines Autos ist die Streuung seiner Zielplätze: die Standardabweichung der Plätze in den Rennen oben, gemittelt über «Mittel» und «Schwer». Ein Auto, das jeden der 8 Plätze gleich oft erreicht, hat die Streuung 2,29. Risiko «tief» heisst Streuung unter 2,20, «hoch» ab 2,35, dazwischen «mittel». Diese gemessene Stufe steht in `FAHRZEUGE` (`risiko`) und erscheint in der Auto-Wahl und bei der Auslosung.

| Auto | Streuung | Risiko (gemessen) | Siege | Letzter Platz | Risiko im Auftrag geschätzt |
|---|---|---|---|---|---|
| Sportwagen | 2,28 | mittel | 13,1 % | 12,6 % | hoch |
| Limousine | 2,21 | mittel | 12,2 % | 10,4 % | mittel |
| Panzerwagen | 2,12 | tief | 11,9 % | 6,8 % | tief |
| Transporter | 2,08 | tief | 10,3 % | 6,0 % | mittel |
| Geländewagen | 2,42 | hoch | 15,0 % | 15,9 % | tief |
| Pick-up | 2,42 | hoch | 11,4 % | 23,0 % | mittel |
| Rennwagen | 2,27 | mittel | 12,3 % | 13,3 % | sehr hoch |
| Rallye-Auto | 2,30 | mittel | 13,7 % | 12,1 % | mittel |

Autos mit Risiko «hoch» streuen im Mittel 15 % mehr als die mit Risiko «tief» (Ziel: mindestens 20 %, nicht erreicht). In Rennen unter Bots entscheidet vor allem das Tempo auf der Ideallinie. Treffer, Wandkontakte und Gelände kommen selten vor, darum wirken die riskanten Werte weniger, als ihre Tabellen vermuten lassen. Menschen treffen Wände und Hindernisse öfter, für sie ist der Unterschied grösser. Mehr Streuung bräuchte noch grössere Tabellen bei Bande, Hindernissen und Gelände, das prüfe ich in Etappe 6 mit den neuen Strecken.

### Die Bots kennen ihr Auto

Jeder Bot liest die Werte seines Autos und fährt danach (`CONFIG.bots.auto`). Regeln für einzelne Autos gibt es keine, alles folgt aus den Fähigkeiten. Darum gilt es auch für jedes Auto, dessen Werte jemand ändert:

- **Gelände:** Ab 8 schneidet er Kurven innen neben der Strasse ab (bis 2,2 m), wo er dort nicht langsamer wird. Je höher der Wert, desto öfter baut er Abkürzungen, mit 1 bis 4 seltener als normal. (Geländewagen)
- **Hindernisse 9 und 10:** Fährt durch Pylonen, statt auszuweichen, und durch Absperrungen, wenn der Umweg mehr als 1,5 m zur Seite führen würde. (Panzerwagen)
- **Rempeln 8 bis 10:** Weicht beim Überholen leichteren Autos (unter 70 % seiner Masse) nur halb aus und schiebt sie zur Seite. (Panzerwagen, Transporter)
- **Bande 1 bis 4:** Hält beim Überholen mehr Abstand, bei Bande 3 rund einen halben Meter, damit er nicht an Gegner und Wand stösst. (Sportwagen, Pick-up, Rennwagen)
- **Windschatten 4 bis 10:** Sucht hinter anderen den Windschatten, je stärker, desto auch in leichten Kurven. (Limousine am meisten)
- **Drift:** Je besser Drift-Aufladung und Drift-Turbo zusammen, desto öfter und früher driftet er.
- **Rampen und Boost-Felder:** Mit dem Wert 10 nimmt er jedes Boost-Feld mit. Je höher der Wert, desto lieber baut er Rampen. (Rallye-Auto)
- **Baukosten und BP-Aufladung:** Mit günstigen Bauwerken und schneller Aufladung baut er öfter (bis 30 Prozentpunkte), mit teuren seltener (bis 15 Prozentpunkte). (Pick-up am meisten)

### «Schwer» und «Ultra» pro Auto

Mit zufälligen Autos wie bisher, je 100 Rennen pro Strecke (`node tools/faehig.js 100 stark,ultra`), mit Bauen. Die Zeile «gesamt» zählt alle 600 Rennen, die Spalten pro Auto nur die Rennen, in denen der stärkere Bot dieses Auto fuhr (je rund 75).

| | gesamt | Sportwagen | Limousine | Panzerwagen | Transporter | Geländewagen | Pick-up | Rennwagen | Rallye-Auto |
|---|---|---|---|---|---|---|---|---|---|
| «Schwer» gewinnt gegen 7 «Mittel» | 98,7 % | 96,7 % | 98,7 % | 100,0 % | 98,8 % | 100,0 % | 96,4 % | 98,5 % | 100,0 % |
| «Ultra» gewinnt gegen 7 «Schwer» | 99,3 % | 100,0 % | 98,3 % | 98,9 % | 100,0 % | 99,1 % | 98,3 % | 100,0 % | 100,0 % |

Pro Strecke gewinnt «Schwer» Kiesgrube 100,0 %, Bergpass 97,0 %, Paris 100,0 %, Himalaya 97,0 %, Ägypten 98,0 %, New York 100,0 % und «Ultra» Kiesgrube 100,0 %, Bergpass 100,0 %, Paris 98,0 %, Himalaya 99,0 %, Ägypten 99,0 %, New York 100,0 %.

**Schnellste Runde «Ultra» pro Auto** (allein, beste fliegende Runde, `node tools/ultraauto.js`): «im Spiel» mit 8 % Tempo-Vorteil (Himalaya 12 %), daneben derselbe Bot ohne Tempo-Vorteil. Ohne Tempo-Vorteil fährt er die Linie des Optimierers und liegt damit beim Sportwagen 0 bis 1 % hinter dessen Zeiten (siehe «Ultra»-Bots). Der Abstand ist also der Vorsprung auf den Optimierer.

| Auto | Kiesgrube | Bergpass | Paris | Himalaya | Ägypten | New York | kleinster Vorsprung |
|---|---|---|---|---|---|---|---|
| Sportwagen | 39,88 s (−6,1 %) | 39,09 s (−5,3 %) | 41,34 s (−5,3 %) | 40,52 s (−11,5 %) | 43,25 s (−7,0 %) | 39,28 s (−7,3 %) | 5,3 % |
| Limousine | 40,06 s (−6,2 %) | 39,40 s (−5,1 %) | 41,58 s (−5,4 %) | 40,97 s (−8,7 %) | 43,62 s (−6,1 %) | 39,51 s (−7,3 %) | 5,1 % |
| Panzerwagen | 39,57 s (−6,9 %) | 39,07 s (−5,3 %) | 41,39 s (−4,7 %) | 40,67 s (−8,3 %) | 42,89 s (−7,3 %) | 39,34 s (−7,0 %) | 4,7 % |
| Transporter | 40,02 s (−6,2 %) | 39,49 s (−4,6 %) | 41,36 s (−5,1 %) | 40,58 s (−9,9 %) | 43,31 s (−6,5 %) | 39,45 s (−7,3 %) | 4,6 % |
| Geländewagen | 40,00 s (−6,3 %) | 39,28 s (−5,0 %) | 41,21 s (−6,2 %) | 39,74 s (−8,2 %) | 43,02 s (−7,1 %) | 39,53 s (−7,3 %) | 5,0 % |
| Pick-up | 39,92 s (−6,4 %) | 39,57 s (−4,2 %) | 41,15 s (−5,7 %) | 40,60 s (−9,4 %) | 43,20 s (−7,1 %) | 39,57 s (−7,4 %) | 4,2 % |
| Rennwagen | 39,83 s (−6,4 %) | 38,69 s (−6,0 %) | 41,49 s (−4,9 %) | 40,75 s (−9,8 %) | 43,33 s (−7,1 %) | 39,38 s (−7,4 %) | 4,9 % |
| Rallye-Auto | 39,64 s (−6,3 %) | 39,40 s (−4,8 %) | 41,07 s (−5,4 %) | 40,09 s (−8,5 %) | 42,41 s (−7,3 %) | 39,36 s (−7,4 %) | 4,8 % |

**Himalaya mit 8 statt 12 %:** «Ultra» gewinnt dort dann 82,5 % gegen 7 «Schwer» (200 Rennen). Die 12 % braucht es also noch. Der Himalaya wird in Etappe 5 neu gebaut, danach prüfe ich es wieder.

### Online und Bestenliste

- Alle fahren mit denselben Werten, denn sie stehen im Spiel selbst. Damit niemand mit einer alten Fassung mitfährt, schickt jedes Gerät seine Fassung (`CONFIG.version`, jetzt 1.2) mit. Hat ein Gast eine ältere geladen, steht in der Lobby neben seinem Namen «andere Fassung: Seite neu laden», und der Host kann erst starten, wenn alle dieselbe Fassung haben. Ab Fassung 1.2 sieht auch der Gast selbst einen Hinweis, wenn seine Fassung nicht zu der des Hosts passt. Ein Host mit der alten Fassung 1.1 prüft das noch nicht.
- Bestenliste: Zuerst bekam jede Strecke eine neue, leere Liste (`kiesgrube-2` usw.), weil Zeiten mit den neuen Autos nicht mehr ganz mit den alten vergleichbar sind. Das wollte Johann nicht: Die Bestenliste bleibt immer erhalten (siehe «Bestenliste»). Seit dem Nachtrag vom 18.11.2026 stehen darum alle Zeiten wieder in der Liste der Strecke, auch die aus den paar Stunden mit eigenen Listen.

### CONFIG-Werte dieser Etappe

| Wert | Bedeutung |
|---|---|
| `CONFIG.faehigkeit.<fähigkeit>` | 10 Faktoren pro Fähigkeit für die Werte 1 bis 10 (Tabelle oben) |
| `CONFIG.fahrzeuge.<auto>` | die 14 Werte des Autos von 1 bis 10, in der Reihenfolge von `FAEHIGKEITEN` |
| `CONFIG.feinabstimmung` | leer: keine versteckten Faktoren pro Auto |
| `CONFIG.belag.<art>.gelaende` | `true` bei Schotter, Schnee, Kies und Sand: Dort wirkt die Fähigkeit «Gelände» auf den Tempoverlust |
| `CONFIG.wirkung.abkuerzungGelaende` | 0,12: Tempo auf Abkürzungen × (1 − 0,12 × (Gelände-Faktor − 1)), also −6 % bei Gelände 1 und +7,8 % bei Gelände 10 |
| `CONFIG.bots.auto` | wie die Bots ihr Auto nutzen: `durchTreffer` 0,5, `durchSchlenker` 1,5 m, `rempelMasse` 1,8, `rempelSeite` 1,4 m, `gedraenge` 1,2 m, `abschneiden` 2,2 m, `abschneidenKr` 0,04, `driftPlus` 0,25, `bauen` 0,6 |
| `CONFIG.version` | 1.2: Online müssen alle dieselbe Fassung haben |
| `BL_FRUEHER` (in `93_bestenliste.js`) | `['-2']`: frühere Listen-Kennungen aus Fassung 1.2, ihre Zeiten liest das Spiel für immer mit |

### Entscheidungen

- **Tabellen enger als im Auftrag:** Mit den Startwerten (Höchsttempo ±4 %) gewann der Rennwagen 66 % der Rennen und der Sportwagen 30 %, die anderen fast nie. Unter Bots entscheidet das Tempo auf der Linie, schon 1 % Höchsttempo ist ein grosser Vorteil. Darum wirken Höchsttempo (±0,75 %), Beschleunigung, Lenkung, Kurvenlage, Drift und Rampen schwächer als im Vorschlag. Windschatten, Rempeln, Gelände, Bande, Hindernisse, Baukosten und BP-Aufladung haben die Spannen aus dem Auftrag, an den starken Enden zum Teil etwas mehr. So sind die Risiken echt spürbar, und die Tempo-Werte kippen das Gleichgewicht nicht.
- **Werte der Autos:** Gesucht mit `tools/ausgleich.js`. Es verschiebt ganze Punkte zwischen den Tempo-Fähigkeiten und den übrigen, bis alle Autos ähnlich oft gewinnen. Die Schwerpunkte (die Werte 10 und der zweite hohe Wert) und die Risiken (Werte 1 bis 3) bleiben dabei fest. Gegenüber dem Vorschlag im Auftrag haben sich vor allem die Tempo-Werte verschoben. Die Summen liegen zwischen 75 und 79 (erlaubt 77 ± 2).
- **Zweite Schlussmessung:** In der ersten Messung mit 400 Rennen pro Strecke gewann der Sportwagen 17 %, Panzerwagen und Transporter kamen auf «Schwer» nur auf 8,8 und 8,5 %, das Rallye-Auto auf «Mittel» auf 7,8 %, und der Pick-up hatte den mittleren Platz 5,3. Darum habe ich fünf Autos um je einen Punkt verschoben: Sportwagen Beschleunigung 8 → 7 und Rempeln 3 → 4, Panzerwagen Beschleunigung 3 → 4 und Bande 9 → 8, Transporter Beschleunigung 6 → 7, Pick-up Beschleunigung 7 → 8 und BP-Aufladung 8 → 7, Rallye-Auto Beschleunigung 5 → 6. Die Tabellen oben zeigen die zweite Messung. Eine dritte Runde habe ich nicht gemacht, weil die Strecken in Etappe 4 und 5 ohnehin neu gebaut werden.
- **Rempeln:** Weicht ein schwerer Bot gar nicht aus, gewinnt der Transporter viel zu oft (mittlerer Platz 3,0). Darum weicht er leichteren Autos halb aus und schiebt sie dabei weg.
- **Baukosten:** Grundpreis × Faktor, kaufmännisch gerundet (x,5 aufwärts), mindestens 1 BP. Bei Baukosten 5 ist der Faktor 1,1: Rampe, Pylonen, Schlammloch und Absperrung kosten nach dem Runden gleich viel wie bisher, Abkürzung und Umleitung 1 BP mehr.
- **Drift-Turbo:** Der Faktor teilt sich mit der Wurzel auf Stärke und Dauer auf, damit ein starker Turbo nicht doppelt zählt.
- **Gelände:** wirkt neben der Strasse, im Schlamm, auf Schotter, Schnee, Kies, Sand und auf Abkürzungen, nicht auf festem Belag wie Asphalt, Pflaster, Platten, Holz, Gitter oder Eis.
- **Rampen und Boost-Felder:** wirkt auf die Dauer des Schubs eigener Rampen und der Boost-Felder der Strecke.
- **Risiko-Stufen:** feste Grenzen der Streuung (2,20 und 2,35) statt Rängen, damit «hoch» immer dasselbe heisst, auch wenn sich Werte ändern. «Sehr hoch» zeigt das Spiel nicht, die Messung kennt nur drei Stufen.

### Grenzen

- Gemessen ist das Gleichgewicht mit Bots. Menschen treffen Wände, Hindernisse und Gelände öfter, für sie zählen Bande, Hindernisse und Gelände mehr. Wer viel neben die Strasse gerät, ist mit dem Geländewagen oder dem Panzerwagen besser bedient, als die Tabelle oben zeigt.
- Ganze Punkte sind grob: Ein Punkt Höchsttempo ändert die Siegquote eines Autos um mehrere Prozentpunkte. Feiner geht es nur über die Tabellen, und die gelten für alle Autos.
- Bei 400 Rennen pro Strecke schwankt eine Siegquote von 12,5 % um rund ±1,7 Prozentpunkte, über alle 6 Strecken um rund ±0,7.
- Die Strecken werden in Etappe 4 und 5 neu gebaut. Danach messe ich das Gleichgewicht in Etappe 6 noch einmal und stimme die Werte, falls nötig, nach.

### Ziele dieser Etappe

| Ziel | Ergebnis | |
|---|---|---|
| 14 Fähigkeiten, Wirkung als kommentierte Tabellen in CONFIG | `CONFIG.faehigkeit`, keine versteckten Faktoren | erreicht |
| Jedes Auto: eine 10, ein zweiter Wert 8 bis 10, mindestens zwei Werte 1 bis 3 | alle 8 Autos | erreicht |
| Jedes Auto in mindestens einer Fähigkeit allein das beste | alle 8 Autos | erreicht |
| Punktsumme 77, nach dem Feintuning höchstens 2 daneben | 75 bis 79 | erreicht |
| Über alle Strecken 10 bis 15 % Siege («Mittel» und «Schwer») | 8,6 % bis 17,8 % | **nicht erreicht** |
| Mittlerer Zielplatz 4,0 bis 5,0 | 4,08 bis 5,29 | **nicht erreicht** |
| Pro Strecke 4 bis 25 % Siege | 2,5 % bis 41,9 % | **nicht erreicht** |
| Jedes Auto auf mindestens einer Strecke unter den besten drei | 4, 1, 1, 1, 2, 3, 3, 3 Strecken | erreicht |
| «Ultra» gemessen und berichtet | Tabelle oben | erreicht |
| `?sim=` zeigt Siege, mittleren Platz und Streuung pro Auto | Tabelle «pro Auto» auf der Sim-Seite | erreicht |
| Spiel zeigt das gemessene Risiko | Auto-Wahl und Auslosung | erreicht |
| Auto-Wahl: 14 Balken in Gruppen, Typ, Risiko, «Stark bei …», «Risiko bei …», Erklärung beim Antippen, Kurzfassung bei der Auslosung, auf dem Handy lesbar | Bilder im Projektordner | erreicht |
| Die Bots kennen ihr Auto | `CONFIG.bots.auto`, siehe oben | erreicht |
| Risiko «hoch» streut mindestens 20 % mehr als «tief» | 15 % mehr | **nicht erreicht** |
| «Schwer» gewinnt fast immer gegen 7 «Mittel» | 98,7 % (schwächstes Auto 96,4 %) | erreicht |
| «Ultra» gewinnt mindestens 99 % gegen 7 «Schwer» | 99,3 % (schwächstes Auto 98,3 %) | erreicht |
| «Ultra» mindestens 4 % schneller als der Optimierer | jedes Auto auf jeder Strecke, kleinster Vorsprung 4,2 % | erreicht |
| «Ultra» höchstens 8 % Tempo-Vorteil | 8 %, am Himalaya 12 % | **nicht erreicht** |
| Online alle mit denselben Werten, ältere Fassung bekommt einen Hinweis | Fassung 1.2 wird geprüft, Hinweis in der Lobby, Start gesperrt | erreicht |
| Bestenliste: alle alten Zeiten bleiben sichtbar (Nachtrag 18.11.2026, Johanns Wunsch) | alle Zeiten in der Liste der Strecke, `tools/erhaltentest.js` 20 von 20 | erreicht |

## Bots auf verschiedenen Spuren

Stand 18.11.2026, Version 1.3 (Etappe 3 des Auftrags «Auto-Fähigkeiten, Bots, Leistung, Strecken»). Geändert ist nur, wohin die Bots lenken. Die Fahrphysik, die Autos und die Strecken sind unverändert.

### Was die Bots jetzt anders machen

- **Lieblingsspur auf Geraden:** Jeder Bot wählt rechts, Mitte oder links und fährt dort mit etwas Abstand zum Rand. Im Mittel alle 25 Sekunden wählt er neu und zieht weich hinüber. Dabei meidet er volle Spuren: Er zählt die Autos von 15 m hinter bis 60 m vor sich in jedem Drittel der Strasse und wählt ein Drittel umso seltener, je mehr dort fahren.
- **Eigene Linie durch die Kurven:** Pro Rennen fährt jeder Bot etwas enger oder weiter als die Ideallinie und lenkt etwas früher oder später ein. Starke Bots bleiben näher an der Ideallinie: «Leicht» bis 1 m daneben und 6 m früher oder später, «Mittel» 0,7 m und 4 m, «Schwer» 0,35 m und 2 m, «Ultra» 0,15 m und 1 m.
- **Vor der Kurve:** Ab 55 m vor einer Kurve zieht der Bot von seiner Spur zu seiner Kurvenlinie, je näher die Kurve, desto mehr. 12 m nach der Kurve geht er zurück auf seine Spur.
- **Kein Gänsemarsch:** Ist ein Bot weniger als 15 m hinter einem anderen und weniger als 2,2 m seitlich daneben, fährt er seitlich versetzt dahinter, auch in Kurven. Fährt er trotzdem 2 Sekunden genau hinter einem anderen her (weniger als 1,2 m seitlich), wählt er ein anderes Drittel.
- **Windschatten:** Wer ihn sucht, fährt 1,4 m versetzt dahinter. Bis 2 m seitlich wirkt er noch.
- **Boost-Felder:** Jeder Bot entscheidet bei jeder Durchfahrt neu, ob er das Feld mitnimmt: seltener, je weiter es neben seiner Spur liegt, öfter, wenn er hinten liegt, und seltener, wenn knapp vor ihm schon jemand darauf zufährt. «Schwer», «Ultra» und Autos mit starkem Schub von Rampen und Boost-Feldern nehmen jedes Feld mit.
- **«Schwer» und «Ultra»:** Allein fahren sie die Ideallinie wie bisher. Sobald jemand bis 40 m vor oder 20 m hinter ihnen fährt, nehmen sie ihre Spur und gehen in 2 Sekunden ganz hinüber.
- **Abkürzungen und Umleitungen:** Eine Abkürzung darf nur fahren, wer sie gebaut hat, und eine Umleitung schickt alle auf den langen Weg. Auf den heutigen Strecken gibt es dort also nichts zu wählen. Gabelungen, an denen jeder Bot bei jeder Durchfahrt neu entscheidet, kommen mit den neuen Strecken (Etappe 4 und 5).

### Messungen vorher und nachher

11 Bots (3 «Leicht», 4 «Mittel», 3 «Schwer», 1 «Ultra»), Autos und Startplätze zugelost, mit Bauen, 3 Runden, 40 Rennen pro Strecke, vorher und nachher mit gleichem Zufall (`node tools/spuren.js 40`, mit `VORHER=` für den Stand vor der Etappe). Gezählt werden nur fahrende Bots (über 5 m/s). Gerade heisst: im Umkreis von 20 m nirgends enger als 250 m Radius, Kurve: enger als 60 m. Gänsemarsch heisst: Ein Bot fährt weniger als 15 m hinter einem anderen und weniger als 1 m seitlich daneben (Anteil der Zeit).

| Messung (alle 6 Strecken, 240 Rennen) | vorher | nachher | Ziel |
|---|---|---|---|
| Seitliche Streuung auf Geraden | 1,10 m | 3,09 m (2,8-mal) | mindestens doppelt ✓ |
| Rechts / Mitte / links auf Geraden | 0,8 / 19,6 / 79,5 % | 22,2 / 45,3 / 32,5 % | jedes Drittel mindestens 20 % ✓ |
| Seitliche Streuung in Kurven | 1,16 m | 1,38 m | |
| Rechts / Mitte / links in Kurven | 25,3 / 13,6 / 61,1 % | 24,7 / 16,7 / 58,6 % | |
| Gänsemarsch auf Geraden | 37,2 % | 17,2 % (−54 %) | −60 % ✗ |
| Gänsemarsch auf Geraden ab 12 s nach dem Start | 28,0 % | 9,7 % (−65 %) | |
| Gänsemarsch überall | 31,2 % | 19,5 % (−38 %) | |
| Boost-Felder: Durchfahrten mit Schub | 92,2 % | 88,0 % | |
| Eigene Abkürzung genommen (Fahrten pro Rennen) | 74,0 % (1,2) | 80,2 % (1,5) | |
| Berührungen zwischen Bots pro Rennen | 99,9 | 88,6 (−11 %) | höchstens +10 % ✓ |
| Zurücksetzen | 1 Mal in 240 Rennen | 2 Mal in 240 Rennen | höchstens +10 % ✗ |
| Stillstand pro Rennen (alle Bots zusammen) | 0,28 s | 0,41 s (+49 %) | höchstens +10 % ✗ |

**Pro Strecke auf Geraden** (Streuung, rechts / Mitte / links, Gänsemarsch):

| Strecke | vorher | nachher |
|---|---|---|
| Kiesgrube | 1,07 m · 0 / 12 / 88 % · 39,5 % | 3,01 m · 19 / 46 / 34 % · 22,9 % |
| Bergpass | 1,35 m · 3 / 24 / 73 % · 33,4 % | 3,24 m · 25 / 44 / 31 % · 14,7 % |
| Paris | 0,94 m · 0 / 12 / 88 % · 32,5 % | 2,86 m · 18 / 48 / 34 % · 16,2 % |
| Himalaya | 1,11 m · 0 / 18 / 82 % · 32,6 % | 3,26 m · 23 / 41 / 36 % · 14,4 % |
| Ägypten | 1,01 m · 0 / 17 / 83 % · 44,3 % | 3,06 m · 22 / 47 / 31 % · 19,1 % |
| New York | 1,03 m · 1 / 28 / 72 % · 40,8 % | 3,03 m · 22 / 47 / 31 % · 19,3 % |

**«Schwer» und «Ultra»** (wie in Etappe 2: `node tools/faehig.js 100 stark,ultra` und `node tools/ultraauto.js`):

| | vorher (Etappe 2) | nachher |
|---|---|---|
| «Schwer» gewinnt gegen 7 «Mittel» | 98,7 % (schwächstes Auto 96,4 %) | 98,2 % (schwächstes Auto 96,4 %) |
| «Ultra» gewinnt gegen 7 «Schwer» | 99,3 % (schwächstes Auto 98,3 %) | 99,5 % (schwächstes Auto 98,1 %) |
| Schnellste Runde «Ultra» allein, 8 Autos × 6 Strecken | | im Mittel gleich (−1,6 bis +1,9 %) |
| «Ultra» schneller als der Optimierer, kleinster Vorsprung | 4,2 % (Pick-up, Bergpass) | 4,8 % (Transporter, Bergpass) |

Pro Strecke gewinnt «Schwer» Kiesgrube 99 %, Bergpass 96 %, Paris 100 %, Himalaya 98 %, Ägypten 100 %, New York 96 % und «Ultra» Kiesgrube 99 %, Bergpass 100 %, Paris 100 %, Himalaya 99 %, Ägypten 99 %, New York 100 %.

**Bilder** (`tools/spurbild.js`, Kiesgrube, 11 Bots, fester Blick von oben, vorher und nachher gleich): im Projektordner unter `leistung/` `e3-vorher-start.png`, `e3-nachher-start.png` (30 m nach der Startlinie, 3,2 s nach dem Start), `e3-vorher-gerade.png`, `e3-nachher-gerade.png` (Gerade bei 560 m, rund 20 s nach dem Start) und alle vier zusammen in `e3-uebersicht.png`. Vorher fahren alle in einer Reihe links, nachher verteilen sie sich über die ganze Strasse. Die Messdaten stehen in `leistung/messungen-etappe3.tgz`.

### CONFIG-Werte dieser Etappe

| Wert | Bedeutung |
|---|---|
| `bots.spuren.anteil` | 0,6 bis 0,95: so weit liegt die Spur rechts oder links neben der Mitte (Anteil der halben Fahrbahn ohne Rand) |
| `bots.spuren.mitte` | 0,25: so weit streut die mittlere Spur um die Mitte |
| `bots.spuren.rand` | 1,4 m Abstand der Spur vom Fahrbahnrand |
| `bots.spuren.wechsel`, `tempo` | im Mittel alle 25 s eine neue Spur, hinüber mit 0,3 der halben Fahrbahn pro Sekunde |
| `bots.spuren.meiden` | 2: volle Spuren meiden, Gewicht eines Drittels = 1 ÷ (1 + 2 × Autos dort) |
| `bots.spuren.kurveAb`, `kurveVoll` | ab 1/400 (Radius 400 m) beginnt eine Kurve, ab 1/150 fährt der Bot ganz auf seiner Kurvenlinie |
| `bots.spuren.vorlauf`, `nachlauf` | 55 m vor der Kurve beginnt er hinüberzuziehen, 12 m danach geht er zurück |
| `bots.spuren.abstand` | 2,2 m seitlicher Versatz hinter einem Vordermann (unter 15 m) |
| `bots.spuren.folgen` | 2 s genau dahinter, dann wählt er ein anderes Drittel |
| `bots.spuren.windVersatz` | 1,4 m Versatz im Windschatten |
| `bots.spuren.profiWechsel` | 0,5: so schnell wechseln «Schwer» und «Ultra» zwischen Ideallinie (allein) und Spur (im Verkehr), Anteil pro Sekunde |
| `bots.spuren.boostWeg`, `boostHinten`, `boostVerkehr` | 0,35, 0,2, 0,25: weniger Lust auf ein Boost-Feld neben der eigenen Spur, mehr Lust weiter hinten, weniger, wenn schon jemand darauf zufährt |
| `bots.stufen.*.kurvenStreu` | 1,0 / 0,7 / 0,35 / 0,15 m: eigene Kurvenlinie neben der Ideallinie («Leicht», «Mittel», «Schwer», «Ultra») |
| `bots.stufen.*.einlenkStreu` | 6 / 4 / 2 / 1 m: so viel früher oder später lenkt der Bot ein |
| `version` | 1.3: Online müssen alle dieselbe Fassung haben |

### Entscheidungen

- **«Schwer» und «Ultra» allein auf der Ideallinie:** Mit einer Spur auf jeder Geraden fuhr «Ultra» allein bis 2,8 % langsamere Runden. Dann wäre er nicht mehr überall 4 % schneller als der Optimierer gewesen. Darum fahren die Profis allein die Ideallinie und nehmen ihre Spur nur, wenn jemand in der Nähe ist. Ihre schnellsten Runden sind damit im Mittel gleich wie vorher.
- **Volle Spuren meiden:** Mit der Regel für die Profis kam das rechte Drittel auf Geraden nur noch auf 17,8 %, weil die Ideallinie auf den heutigen Strecken auf Geraden fast immer links liegt (vorher 79,5 % aller Durchfahrten im linken Drittel). Statt die Bots einfach öfter nach rechts zu schicken, meiden sie jetzt volle Spuren. Das verlangt der Auftrag ohnehin für die Wege («volle Wege meiden»). Danach kam das rechte Drittel auf 22,2 %.
- **Versatz hinter dem Vordermann:** Verglichen habe ich mehrere Varianten (je 20 Rennen pro Strecke): 1,6, 2,2 und 2,7 m seitlicher Versatz, versetzt losfahrende Startreihen, schnellerer und seltenerer Spurwechsel. Mit 2,7 m gab es wieder mehr Gänsemarsch und mehr Berührungen, weil die Bots dann oft hinter dem Nächsten landen. Die anderen Varianten änderten wenig. Gewählt habe ich 2,2 m.
- **Stillstand:** Fünf Abhilfen habe ich ausprobiert (kein Versatz vor engen Kurven, nach der Kurve weicher zurück auf die Spur, keine eigene Kurvenlinie, früher auf die Kurvenlinie, nach einer Abkürzung zuerst die Ideallinie). Keine half deutlich, darum ist keine davon im Spiel. Woher der Stillstand kommt, steht unter «Grenzen».
- **Boost-Felder:** Vorher zog jeder Bot nur teilweise zum Feld hin, je nach seiner Lust darauf. Jetzt entscheidet er bei jeder Durchfahrt ja oder nein und zieht bei ja ganz hinüber. So nimmt nicht mehr jeder Bot jedes Feld halb mit, sondern mancher lässt es aus (88,0 statt 92,2 % der Durchfahrten mit Schub).
- **Fassung 1.3:** Die Bots fahren anders als in Fassung 1.2. Online müssen darum alle die Seite neu laden, damit alle mit derselben Fassung fahren (Hinweis in der Lobby wie bisher).

### Grenzen

- **Gänsemarsch:** −54 % auf Geraden statt −60 %. Fast der ganze Rest entsteht in den ersten Sekunden nach dem Start, solange das Feld in den drei Spalten der Startaufstellung fährt. Ab 12 s nach dem Start sind es −65 %. In Kurven fahren alle Bots nahe an der Ideallinie, dort bleibt mehr Gänsemarsch.
- **Stillstand:** 0,41 statt 0,28 s pro Rennen, alle 11 Bots zusammen. Die ganze Zunahme kommt von zwei Stellen: dem Ende der Abkürzung in Ägypten und dem Ende der zweiten Abkürzung am Himalaya. Wer dort seine eigene Abkürzung fährt, bleibt beim Zurückfahren auf die Strasse oft kurz am Rand hängen, schon vor dieser Etappe (Ägypten 5, Himalaya 27 Mal in 40 Rennen). Jetzt fahren die Bots dort öfter eine eigene Abkürzung (Ägypten 0,7 statt 0,1 Mal pro Rennen) und bleiben darum öfter hängen (27 und 58 Mal). Beide Strecken werden in Etappe 5 neu gebaut, dann prüfe ich die Einmündungen.
- **Zurücksetzen:** 2 statt 1 Mal in 240 Rennen. Das ist zu selten für eine sichere Aussage, zählt aber formal als nicht erreicht.
- **Wege:** Auf den heutigen Strecken gibt es keine Gabelungen, und eine Abkürzung darf nur fahren, wer sie gebaut hat. Die Ziele zu den Wegen (jeder Weg 30 bis 70 %, die Hälfte der Bots nimmt beide Wege, höchstens 65 % gleicher Weg wie der Vordermann) und die Minikarte mit Bots auf verschiedenen Wegen kommen mit den neuen Strecken in Etappe 4 und 5.
- In Kurven streuen die Bots nur wenig mehr als vorher (1,38 statt 1,16 m), weil sie dort ihrer Kurvenlinie nahe an der Ideallinie folgen. So ist es gewollt: Die Kurve schnell zu fahren ist wichtiger.

### Ziele dieser Etappe

| Ziel | Ergebnis | |
|---|---|---|
| Zuerst messen, wo die Bots heute fahren | Tabelle oben, vorher | erreicht |
| Lieblingsspur auf Geraden, eigene Linie durch die Kurven, starke Bots näher an der Ideallinie | siehe oben | erreicht |
| Spurwechsel zum Überholen, für Windschatten, Hindernisse und Boost-Felder | siehe oben | erreicht |
| Boost-Felder: bei jeder Durchfahrt neu entscheiden (Spur, Verkehr, Lage im Rennen) | siehe oben | erreicht |
| Auf Geraden mindestens doppelt so starke Streuung | 2,8-mal (3,09 statt 1,10 m) | erreicht |
| Jedes Drittel der Strasse mindestens 20 % | 22,2 / 45,3 / 32,5 % | erreicht |
| Gänsemarsch −60 % | −54 % auf Geraden (ab 12 s nach dem Start −65 %) | **nicht erreicht** |
| Berührungen höchstens +10 % | −11 % | erreicht |
| Zurücksetzen höchstens +10 % | 2 statt 1 Mal in 240 Rennen | **nicht erreicht** |
| Stillstand höchstens +10 % | +49 % (0,41 statt 0,28 s pro Rennen) | **nicht erreicht** |
| «Schwer» gewinnt fast immer gegen 7 «Mittel» | 98,2 % | erreicht |
| «Ultra» gewinnt mindestens 99 % gegen 7 «Schwer» | 99,5 % | erreicht |
| «Ultra» mindestens 4 % schneller als der Optimierer | kleinster Vorsprung 4,8 % | erreicht |
| Bilder vom Start und von einer Geraden, vorher und nachher | im Projektordner unter `leistung/` | erreicht |
| Wege an Gabelungen, Minikarte mit Bots auf verschiedenen Wegen | Kiesgrube, Bergpass und Paris seit Etappe 4 (siehe «Neue Strecken»), die anderen drei Strecken folgen in Etappe 5 | zum Teil erreicht |

## Neue Strecken: Kiesgrube, Bergpass und Paris

Stand 20.11.2026, Version 1.4 (Etappe 4 des Auftrags «Auto-Fähigkeiten, Bots, Leistung, Strecken»). Die Kiesgrube, der Bergpass und Paris sind neu gebaut, mit mehr Kurven, mehr Stellen zum Driften und Gabelungen mit zwei etwa gleich schnellen Wegen. Himalaya, Ägypten und New York folgen in Etappe 5. Die Fahrphysik und die Autos sind unverändert. Die Bestenliste behält auf allen Strecken ihre Kennung, die alten Zeiten bleiben also sichtbar (so am 18.11.2026 entschieden, siehe «Grenzen»).

### Gabelungen

- **Zwei Wege, beide immer offen:** An einer Gabelung teilt sich die Strasse in zwei Wege, die sich verschieden fahren und etwa gleich schnell sind. Anders als eine Abkürzung muss man nichts bauen, und anders als eine Umleitung schickt sie niemanden auf einen bestimmten Weg.
- **Früh zu sehen:** Ein blaues Schild über der Strasse 55 m vor der Gabelung zeigt beide Wege mit Pfeilen und Namen. Ab 150 m vor der Gabelung steht im Hinweisfeld, welcher Weg links und welcher rechts abgeht, in der Kiesgrube zum Beispiel «↖ Kieshalden · Gabelung in 120 m · Schanze ↗» (blau, damit man es nicht mit einer Warnung verwechselt; eine Baustellen-Warnung hat Vorrang). Auf der Minikarte und im Steckbrief ist der zweite Weg hell und so breit wie die Strasse eingezeichnet, die Wände am Weg sind grau statt orange.
- **Steckbrief:** zeigt neu die Zahl der Kurven und der Gabelungen.
- **Bots:** Jeder Bot entscheidet bei jeder Durchfahrt neu, nach seinem Auto (der Geländewagen eher auf losem Belag, kurvenstarke Autos eher auf dem engeren Weg, Autos mit starkem Schub eher dort, wo eine Schanze oder ein Boost-Feld liegt), nach seiner Vorliebe in diesem Rennen, nach dem Verkehr (volle Wege meidet er) und nach seiner Lage im Rennen (wer hinten liegt, wagt eher den wilderen Weg). Er nimmt gern den Weg, den er beim letzten Mal nicht genommen hat, und folgt nicht einfach dem Bot direkt vor ihm.
- **Auf jedem Weg höchstens ein Bauplatz:** Die Bauplätze liegen auf dem ersten Weg, der zweite ist frei. Wer ein Hindernis auf dem ersten Weg sieht, nimmt eher den zweiten.
- Platz, Abstände, Zurücksetzen und «Falsche Richtung» rechnen auf beiden Wegen richtig (im Browser über jeden Weg geprüft, siehe unten).

### Die drei Strecken

**Kiesgrube** (1393 → 1558 m):
- Neu nach der zweiten Kehre: eine enge Gasse zwischen den Kieshalden (11 bis 13 statt 15 m breit) mit drei Knicken.
- Neu: Gabelung «Schanze» oder «Kieshalden». Geradeaus über die Schanze und durch eine enge Kurve, oder links durch Sandkurven zwischen den Halden (10 m breit; im Sand ist man langsamer und das Heck schwimmt, dem Geländewagen macht das wenig aus).
- Neu: um den Baggersee vier lange Bögen zum Driften (22 m Radius) und oben ein schneller Knick über eine Kuppe.
- Neu: S-Kurven am Grubenrand, hinunter in die Grube (Senke), eine Schikane auf Schotter auf dem Grubengrund, wieder hinauf und durch eine Schikane in der Mulde.
- Abkürzung «Grubenweg» neu gelegt, in Schlangenlinien durch die Grube, und Umleitung «Werkhof» neu. Die Abkürzung «Notbrücke» über den See fällt weg, weil sie die ganze neue Seeschlaufe abgeschnitten hätte (15 → 14 Bauplätze).

**Bergpass** (1291 → 1381 m):
- Drei Serpentinen hinauf wie bisher, dazwischen neu eine Baustellen-Schikane auf Schotter (links, rechts, links).
- Neu: eine Kuppe auf der Passhöhe, dann die Gabelung «Passstrasse» (Schikane) oder «Alpweg» (Kiesweg im Bogen über die Alp, bisher eine Umleitung).
- Über die Schluchtbrücke wie bisher, danach neu zwei Kehren hinunter, die enge Felsgasse (11 bis 12 m breit) und die Felskehre, dann die Zielkurve mit der Schanze.
- Abkürzung «Steilhang» neu gelegt (von der Brücke den Hang hinunter, mit einer Kehre), neue Umleitung «Talweg» an der Start-Geraden.

**Paris** (1409 → 1560 m):
- Start durch den Triumphbogen wie bisher, neu mit der Umleitung «Kreisel».
- Neu: Gabelung «Boulevard» oder «Passage» (schmal, Pflaster, schräg durch die Häuser hinunter zum Fluss; bisher eine Abkürzung). Die Passage zweigt zuerst sanft ab, damit man sie auch mit vollem Tempo erwischt, und macht in der Mitte einen leichten Knick um ein Haus.
- Neu: eine Schlaufe am Quai auf Pflaster (links, Kehre rechts, links) statt der schnellen S-Kurven, dann über die Steinbrücke mit dem Buckel.
- Neu: Gabelung «Eisenturm» oder «Parkweg» (Kiesweg im Bogen durch den Park, bisher eine Umleitung). Vor dem Eisenturm neu eine Schlaufe auf den Sandwegen des Marsfelds.
- Neu: nach der Eisenbrücke enge Gassen hinauf zum Hügel (11,5 bis 13 m breit, Pflaster) mit Kehren am Weinberg und an der Treppe statt des geraden Anstiegs. Danach wie bisher die Kehre um die Mühle, die Kehre um den Obelisken und der Zielhang mit der Schanze. Die Abkürzung «Treppengasse» zweigt jetzt im Bogen ab und führt fast gerade hinter der Mühle durch.

Alles, was an einer Strecke hängt, ist neu eingerichtet: Bauplätze, Nebenwege, Boost-Felder (Paris legt seine vier Felder selbst fest, damit keines auf einem Weg einer Gabelung liegt), Startaufstellung (auch mit 33 Autos), Ideallinie, «Ultra»-Einstellungen und Optimierer-Zeiten. Draufsichten vorher und nachher: `e4-plan-<strecke>-vorher.png` und `-nachher.png` im Projektordner unter `leistung/` (rot: Kurven unter 25 m Radius, orange: unter 60 m, violett: Gabelung, grün: Abkürzung, blau: Umleitung).

### Messungen vorher und nachher

**Strecken** (`node tools/streckenmass.js`, vorher Fassung 1.3, nachher 1.4). Kurven: Stücke der Mittellinie mit weniger als 60 m Radius, mindestens 6 m lang. Drift-Kurven: wo «Ultra» allein mit dem Sportwagen einen Drift mit Mini-Turbo fährt, Mittel aus Runde 2 und 3, an jeder Gabelung auf dem ersten Weg (auf dem zweiten Weg: Kiesgrube 7, Bergpass 6, Paris 8). Vorher hing die Zahl davon ab, welchen Weg der Bot zufällig nahm.

| Strecke | Länge (Ziel: höchstens) | Kurven (Ziel: mindestens) | davon enger als 25 m | Drift-Kurven pro Runde (Ziel: mindestens) | Gabelungen | Abkürzungen / Umleitungen | Boost-Felder | Bauplätze | «Ultra» allein, schnellste Runde |
|---|---|---|---|---|---|---|---|---|---|
| Kiesgrube | 1393 → 1558 m (1601) ✓ | 17 → 27 (24) ✓ | 5 → 17 | 6 → 9 (9) ✓ | 0 → 1 | 2 / 1 → 1 / 1 | 5 → 5 | 15 → 14 | 39,9 → 44,3 s |
| Bergpass | 1291 → 1381 m (1484) ✓ | 9 → 14 (13) ✓ | 5 → 14 | 4 → 6 (6) ✓ | 0 → 1 | 1 / 1 → 1 / 1 | 5 → 5 | 15 → 14 | 38,9 → 40,9 s |
| Paris | 1409 → 1560 m (1620) ✓ | 12 → 17 (17) ✓ | 8 → 13 | 6 → 9 (9) ✓ | 0 → 2 | 2 / 1 → 1 / 1 | 5 → 4 | 15 → 14 | 41,5 → 46,4 s (12 %) |

Eine gute Runde dauert damit 41 bis 47 s («Ultra» mit Tempo-Vorteil) oder 43 bis 50 s (Optimierer ohne Tempo-Vorteil), also unter einer Minute.

**Gabelungen** (`SAATEN=99,98,97,96 node tools/gabeltest.js <strecke> 300 30`): Optimierer mit vier Suchen zu je 300 Versuchen pro Weg (pro Weg zählt die beste Runde; eine einzelne Suche streut um bis zu 0,3 s) (Sportwagen, ohne Tempo-Vorteil, alle Gabelungen auf denselben Weg), dazu 30 Rennen mit 11 Bots (3 «Leicht», 4 «Mittel», 3 «Schwer», 1 «Ultra», Autos gemischt, mit Bauen, 3 Runden). «Gleicher Weg wie der Bot davor» zählt nur Paare, die weniger als 1,5 s hintereinander an die Abzweigung kommen.

| Gabelung (erster / zweiter Weg) | Optimierer erster / zweiter Weg | Unterschied (Ziel: höchstens 0,2 s) | zweiter Weg (Ziel: 30 bis 70 %) | Bots, die beide Wege nehmen (Ziel: mindestens 50 %) | gleicher Weg wie der Bot davor (Ziel: höchstens 65 %) |
|---|---|---|---|---|---|
| Kiesgrube: «Schanze» / «Kieshalden» | 46,48 / 46,37 s | 0,11 s ✓ | 57,9 % ✓ | 76,1 % ✓ | 39,9 % ✓ |
| Bergpass: «Passstrasse» / «Alpweg» | 42,93 / 43,05 s | 0,12 s ✓ | 60,2 % ✓ | 77,6 % ✓ | 42,1 % ✓ |
| Paris: «Boulevard» / «Passage» | 49,31 / 49,15 s | 0,16 s ✓ | 58,6 % ✓ | 78,8 % ✓ | 42,1 % ✓ |
| Paris: «Eisenturm» / «Parkweg» | 49,31 / 49,16 s | 0,15 s ✓ | 58,9 % ✓ | 75,5 % ✓ | 43,6 % ✓ |

Nach Stufe nehmen den zweiten Weg: «Leicht» 52 %, «Mittel» 58 %, «Schwer» 63 %, «Ultra» 71 % (alle vier Gabelungen zusammen). Die starken Bots nehmen ihn öfter. Das passt dazu, dass Hindernisse nur auf dem ersten Weg stehen können und die starken Bots sie früher sehen.

**Bots auf Spuren** (`STRECKEN=kiesgrube,bergpass,paris node tools/spuren.js 40`, wie in Etappe 3: 11 Bots, Stufen gemischt, Autos und Startplätze zugelost, mit Bauen, 3 Runden, 40 Rennen pro Strecke, mit `VORHER=` für die alten Fassungen, gleicher Zufall). Die Ziele aus Teil 3 gelten gegenüber dem Stand vor Etappe 3 (Fassung 1.2).

| Messung (Kiesgrube, Bergpass, Paris; 120 Rennen) | Fassung 1.2 (vor Etappe 3) | 1.3 (alte Strecken) | 1.4 (neue Strecken) | Ziel (gegenüber 1.2) |
|---|---|---|---|---|
| Seitliche Streuung auf Geraden | 1,17 m | 3,07 m | 3,12 m (2,7-mal) | mindestens doppelt ✓ |
| Rechts / Mitte / links auf Geraden | 1,5 / 18,0 / 80,5 % | 22,0 / 45,7 / 32,3 % | 21,3 / 44,4 / 34,3 % | jedes Drittel mindestens 20 % ✓ |
| Gänsemarsch auf Geraden | 34,0 % | 16,5 % | 15,7 % (−54 %) | −60 % ✗ |
| Gänsemarsch auf Geraden ab 12 s nach dem Start | 23,7 % | 8,5 % | 5,0 % (−79 %) | |
| Gänsemarsch überall | 27,5 % | 18,1 % | 14,9 % (−46 %) | |
| Seitliche Streuung in Kurven | 1,11 m | 1,28 m | 1,19 m | |
| Boost-Felder: Durchfahrten mit Schub | 89,2 % | 86,0 % | 91,1 % | |
| Eigene Abkürzung genommen (Fahrten pro Rennen) | 98,0 % (1,7) | 99,1 % (1,8) | 100,0 % (1,8) | |
| Berührungen zwischen Bots pro Rennen | 89,3 | 79,1 | 71,0 (−20 %) | höchstens +10 % ✓ |
| Zurücksetzen | 1 Mal in 120 Rennen | 1 Mal in 120 Rennen | 0 Mal in 120 Rennen | höchstens +10 % ✓ |
| Stillstand pro Rennen (alle Bots zusammen) | 0,11 s | 0,11 s | 0,01 s | höchstens +10 % ✓ |

**Pro Strecke auf Geraden** (Streuung · rechts / Mitte / links · Gänsemarsch):

| Strecke, auf Geraden | 1.2 | 1.3 | 1.4 |
|---|---|---|---|
| Kiesgrube | 1,07 m · 0 / 12 / 88 % · 39,5 % | 3,01 m · 19 / 46 / 34 % · 22,9 % | 3,43 m · 26 / 40 / 34 % · 17,5 % |
| Bergpass | 1,35 m · 3 / 24 / 73 % · 33,4 % | 3,24 m · 25 / 44 / 31 % · 14,7 % | 2,99 m · 21 / 48 / 31 % · 14,9 % |
| Paris | 0,94 m · 0 / 12 / 88 % · 32,5 % | 2,86 m · 18 / 48 / 34 % · 16,2 % | 3,10 m · 19 / 43 / 38 % · 15,6 % |

Auf den neuen Strecken verteilen sich die Bots so wie in Etappe 3 auf den alten. Der Gänsemarsch auf Geraden bleibt bei −54 %, fast der ganze Rest entsteht kurz nach dem Start. Berührungen, Zurücksetzen und Stillstand sind seltener als in beiden alten Fassungen.

**«Ultra» allein** (`FEST=1 node tools/ultra.js <strecke> 200` und `SAATEN=4711,4712,4713 STRECKEN=<strecke> node tools/ultraauto.js`): schnellste Runde mit dem Sportwagen gegen den Optimierer und jedes Auto mit gegen ohne Tempo-Vorteil (8 %, in Paris 12 %). Pro Auto zählt seit dieser Etappe die schnellste Runde aus drei Rennen statt aus einem: «Ultra» will nicht in jeder Kurve driften (in Paris in 94 %), und wenn er zufällig auf einem langen kurvigen Stück nicht will, verliert er in einem einzelnen Rennen über 1 s. Mit nur einem Rennen wäre der Rennwagen in Paris nur 3,5 % schneller gewesen.

| Strecke | Optimierer | «Ultra» (Sportwagen) | schneller als der Optimierer (Ziel: mindestens 4 %) | jedes Auto mit statt ohne Tempo-Vorteil, kleinster Vorsprung (Ziel: mindestens 4 %) |
|---|---|---|---|---|
| Kiesgrube | 46,63 s | 44,43 s | 4,7 % ✓ | 4,4 % (Geländewagen) ✓ |
| Bergpass | 43,01 s | 40,85 s | 5,0 % ✓ | 5,1 % (Limousine, Panzerwagen, Rallye-Auto) ✓ |
| Paris | 49,28 s | 46,85 s | 4,9 % ✓ | 5,4 % (Rallye-Auto) ✓ |

**«Schwer» und «Ultra» im Rennen** (`node tools/faehig.js 100 stark,ultra`, wie in Etappe 2 und 3: zufällige Autos, mit Bauen, 100 Rennen pro Strecke; vorher Fassung 1.3 auf den alten Strecken):

| | Kiesgrube | Bergpass | Paris | alle drei |
|---|---|---|---|---|
| «Schwer» gewinnt gegen 7 «Mittel» (Ziel: fast immer) | 99 → 97 % | 96 → 100 % | 100 → 100 % | 98,3 → 99,0 % ✓ |
| «Ultra» gewinnt gegen 7 «Schwer» (Ziel: mindestens 99 %) | 99 → 99 % | 100 → 100 % | 100 → 100 % | 99,7 → 99,7 % ✓ |


**Gleich starke Bots mit verschiedenen Autos** (`STRECKEN=kiesgrube,bergpass,paris node tools/faehig.js 200`: 8 Bots derselben Stufe, jedes Auto einmal, zufällige Startplätze, mit Bauen, 200 Rennen pro Strecke und Stufe). Siege, Mittel aus «Mittel» und «Schwer»; erlaubt sind pro Strecke 4 bis 25 % (Ziel aus Teil 2). Vorher: Etappe 2 auf den alten Strecken (400 Rennen).

| Strecke | Sportwagen | Limousine | Panzerwagen | Transporter | Geländewagen | Pick-up | Rennwagen | Rallye-Auto |
|---|---|---|---|---|---|---|---|---|
| Kiesgrube vorher | 9,9 % | 8,8 % | 19,1 % | 10,5 % | 3,6 % | 24,9 % | 14,3 % | 9,0 % |
| Kiesgrube nachher | 8,5 % | 5,5 % | 17,0 % | 12,3 % | 9,3 % | **28,5 %** | 12,5 % | 6,5 % |
| Bergpass vorher | 13,0 % | 9,8 % | 12,9 % | 10,3 % | 12,3 % | 14,9 % | 18,4 % | 8,6 % |
| Bergpass nachher | 13,3 % | 6,8 % | 14,3 % | 8,0 % | 5,5 % | 21,5 % | 21,5 % | 9,3 % |
| Paris vorher | 14,1 % | 13,1 % | 12,8 % | 17,8 % | 5,6 % | 9,1 % | 14,3 % | 13,3 % |
| Paris nachher | 10,5 % | 5,3 % | 15,0 % | 10,5 % | 14,3 % | 17,5 % | 14,3 % | 12,8 % |

Alle Autos liegen im erlaubten Bereich ausser dem Pick-up in der Kiesgrube (28,5 %, vorher 24,9 %). Ohne Bauen gewinnt er dort 20 % (Bots, die nie bauen, 100 Rennen pro Stufe): Etwa die Hälfte seines Vorsprungs kommt also vom Bauen, das er am billigsten kann. Am anderen Ende liegt die Limousine, auf allen drei Strecken knapp über der Grenze (5,3 bis 6,8 %). Die Autos stimme ich wie im Auftrag vorgesehen in Etappe 6 ab, wenn alle sechs Strecken neu sind: Ein Auto jetzt für die Kiesgrube zu ändern, würde auch die drei Strecken verschieben, die in Etappe 5 noch umgebaut werden.

**33 Autos** (`node tools/gross.js gleich33 6 <strecke>`: 33 «Mittel»-Bots, 6 Rennen pro Strecke, vorher Fassung 1.3 auf den alten Strecken). Die Startaufstellung mit 33 Autos passt auf allen drei Strecken (Bilder unten).

| 33 «Mittel»-Bots, pro Rennen | Kiesgrube | Bergpass | Paris |
|---|---|---|---|
| Treffer pro Auto | 0,81 → 0,13 | 1,91 → 0,81 | 1,00 → 0,14 |
| Zurücksetzen | 0 → 0 | 0,33 → 0 | 0 → 0 |
| längster Stillstand eines Autos | 0,2 → 0,1 s | 0,4 → 0,2 s | 0,2 → 0,2 s |
| Abstand vom Ersten zum Letzten im Ziel (Median) | 4,5 → 7,2 s | 5,6 → 5,4 s | 8,5 → 9,2 s |

Im grossen Feld treffen die Bots viel seltener ein Hindernis, weil die Bauplätze jetzt auf Geraden und in weiten Bögen liegen. In der Kiesgrube und in Paris kommt das Feld weiter auseinander ins Ziel, weil die Strecken länger und kurviger sind.

**Leistung** (Software-Grafik der Testumgebung, vorher Fassung 1.3 auf den alten Strecken). Dreiecke und Zeichenaufrufe pro Bild (`tools/leistung.js`: 8 Fahrer, 5 s nach dem Start, Kamera hinter dem eigenen Auto, grösster Wert aus 10 Bildern, ein Lauf), dazu das Budget pro Grafik-Stufe aus `CONFIG.grafik.budget`:

| Strecke | Stufe | Dreiecke vorher → nachher | Zeichenaufrufe vorher → nachher | Budget (Dreiecke / Aufrufe) |
|---|---|---|---|---|
| Kiesgrube | «Niedrig» | 87'992 → 92'806 | 82 → 83 | 160'000 / 160 |
| Kiesgrube | «Mittel» | 280'422 → 404'151 | 138 → 219 | 460'000 / 370 |
| Kiesgrube | «Hoch» | 361'954 → 381'536 | 160 → 162 | 560'000 / 390 |
| Kiesgrube | «Ultra» | 477'339 → 491'035 | 161 → 143 | 570'000 / 370 |
| Bergpass | «Niedrig» | 77'928 → 81'024 | 77 → 85 | 160'000 / 160 |
| Bergpass | «Mittel» | 255'004 → 381'936 | 154 → 199 | 460'000 / 370 |
| Bergpass | «Hoch» | 331'270 → 336'896 | 156 → 157 | 560'000 / 390 |
| Bergpass | «Ultra» | 446'633 → 450'615 | 158 → 156 | 570'000 / 370 |
| Paris | «Niedrig» | 126'108 → 130'362 | 106 → 107 | 160'000 / 160 |
| Paris | «Mittel» | 303'671 → 316'605 | 143 → 146 | 460'000 / 370 |
| Paris | «Hoch» | 377'445 → 380'059 | 181 → 149 | 560'000 / 390 |
| Paris | «Ultra» | 471'614 → 477'452 | 187 → 185 | 570'000 / 370 |

Rechenzeit der Spiel-Logik pro Rechenschritt von 1/60 s (`tools/schrittzeit.js`: 30 s Rennen, Mittel und die langsamsten 1 % der Schritte, Median aus je 3 Läufen, vorher und nachher abwechselnd, während sonst nichts lief):

| Strecke | 8 Autos: Mittel (langsamste 1 %) vorher → nachher | 33 Autos: Mittel (langsamste 1 %) vorher → nachher |
|---|---|---|
| Kiesgrube | 0,38 (1,05) → 0,39 (1,15) ms | 1,32 (2,72) → 1,29 (2,78) ms |
| Bergpass | 0,26 (0,64) → 0,27 (0,64) ms | 1,32 (2,27) → 1,33 (2,94) ms |
| Paris | 0,27 (0,55) → 0,25 (0,70) ms | 1,38 (2,76) → 1,30 (2,31) ms |

Alle Werte liegen im Budget. Die neuen Strecken zeichnen meist 1 bis 6 % mehr Dreiecke, weil sie länger sind und mehr Kurven, Wände und Bauten haben; die Zeichenaufrufe ändern sich wenig. Auf «Mittel» streuen die Dreiecke in der Kiesgrube und am Bergpass von Lauf zu Lauf stark, je nachdem, wo die Autos 5 s nach dem Start gerade stehen und was die Kamera sieht. Diese Fälle habe ich darum dreimal gemessen, «Hoch» zum Vergleich auch: Kiesgrube auf «Mittel» vorher 280'000 bis 362'000, nachher 382'000 bis 415'000 Dreiecke (Median +12 %), Bergpass vorher 248'000 bis 255'000, nachher 261'000 bis 382'000 (Median +2 %). Auf «Hoch» streut es kaum (bis 2,3 %). Der höchste Wert, 415'000 Dreiecke in der Kiesgrube, liegt bei 90 % des Budgets von «Mittel» (460'000).

Die Spiel-Logik rechnet auf den neuen Strecken gleich schnell wie auf den alten: mit 8 Autos 0,25 bis 0,39 ms pro Rechenschritt, mit 33 Autos 1,3 ms. Die langsamsten 1 % streuen von Lauf zu Lauf um rund 0,3 ms.

**Im Browser** (Fassung 1.4, Software-Grafik der Testumgebung, Firebase und Google gesperrt):

- `tools/naehe.js`: auf allen drei Strecken 0 Fundstellen. Nichts steht auf der Fahrbahn oder dem Seitenstreifen, nichts schwebt darüber.
- `tools/gabelbrowser.js`: jede Strecke zweimal über 2 Runden mit 3 Bots, das eigene Auto fährt ein «Schwer»-Bot, einmal an allen Gabelungen auf dem ersten Weg, einmal auf dem zweiten. Geprüft: der Weg wurde wirklich gefahren, beide Runden zählen, kein Zurücksetzen, nie «Falsche Richtung», die gefahrene Strecke springt nie (Platz und Abstände stimmen), der Hinweis zur Gabelung steht im HUD. 46 von 46 Prüfungen gut.
- `tools/elfbots.js`: Bergpass und Paris mit 11 Bots bis zum Ergebnis, Rundenzeit ab der Ziellinie. 17 von 17 gut.
- `tools/erhaltentest.js`: Die alten Zeiten der Bestenliste bleiben sichtbar. 20 von 20 gut.
- `tools/browsertest.js`: ein Rennen gegen 7 Bots am Bergpass und in Paris bis zum Ergebnis, lokal am selben Gerät bis zum Ergebnis, online mit Host und Gast bis zum Ergebnis, mit Revanche und Abbruch, und das gestörte Netz (Host stumm, Netz blockiert, Neu-Anmeldung, Rennen mit drei Geräten): alles gut. In Paris und im geteilten Bild dauert ein Bildschirmfoto in der Software-Grafik der Testumgebung manchmal länger als die 30 s, die der Test bisher wartete (gemessen 34 s mit `tools/haengprobe.js`, mit und ohne die Korrektur der Auto-Vorschau gleich, in Paris auch mit Fassung 1.3). Der Test brach darum dort ab. Mit `FOTO_MS=120000` wartet er länger, dann laufen beide bis zum Ergebnis durch.
- `tools/haenger.js`: ein ganzes Rennen in Paris auf «Hoch» bis zum Podest. Nach dem Countdown entsteht kein neues Shader-Programm und keine neue Textur.
- In der Konsole stehen nur die bekannten Hinweise von three.js und der Software-Grafik und die gesperrten Adressen der Testumgebung.

**Bilder** im Projektordner unter `leistung/`: Draufsichten `e4-plan-<strecke>-vorher.png` und `-nachher.png`; jede Strecke vorher und nachher aus denselben zwei Blickwinkeln (`e4-<strecke>-vorher-1.png` bis `-nachher-2.png`, Grafik «Hoch»); jede Gabelung mit dem blauen Schild 75 bis 90 m davor (`e4-gabel-<strecke>-<gabel>-schild.png`), kurz davor mit Hinweis und Minikarte einmal auf jedem Weg (`-vor-weg1.png`, `-vor-weg2.png`) und auf dem zweiten Weg (`-auf-weg2.png`); die Minikarte in einem Rennen mit 11 Autos in dem Moment, in dem mitten auf beiden Wegen einer Gabelung mindestens zwei Autos fahren, einmal ganz und einmal vergrössert um die Gabelung (`e4-minikarte-<strecke>-<gabel>.png` und `-nah.png`, dazu der ganze Bildschirm `-ganz.png`); die Startaufstellung mit 33 Autos (`e4-start33-<strecke>.png`); der Steckbrief im Menü (`e4-menue-kiesgrube.png`, `e4-menue-paris.png`). Die Messdaten stehen in `leistung/messungen-etappe4.tgz`.

### CONFIG-Werte dieser Etappe

| Wert | Bedeutung |
|---|---|
| Strecke `wege: [{ art: 'gabelung', name, nameHaupt, anteil, … }]` | Gabelung: zweiter Weg mit Namen, `nameHaupt` ist der Name des ersten Wegs auf dem Schild, `anteil` (0,5) die Grundlust der Bots auf den zweiten Weg |
| `bots.gabel.auto` | 0,22: Auto (Geländewagen auf losem Belag, kurvenstarke Autos auf dem engeren Weg, Autos mit starkem Schub dort, wo Schanze oder Boost-Feld liegt) |
| `bots.gabel.lieb` | 0,18: eigene Vorliebe pro Gabelung und Rennen, zufällig bis so viel mehr oder weniger |
| `bots.gabel.verkehr` | 0,07 pro Auto, das bis 50 m vor ihm einen Weg fährt oder gewählt hat: so viel weniger Lust auf diesen Weg |
| `bots.gabel.hinten` | 0,12: wer hinten liegt, nimmt eher den wilderen Weg (loser Belag, Schanze) |
| `bots.gabel.wechsel` | 0,12: mehr Lust auf den Weg, den er beim letzten Mal nicht genommen hat |
| `bots.gabel.folgen` | 0,12: weniger Lust, dem Bot direkt vor ihm (unter 1,5 s) einfach zu folgen |
| `bots.gabel.sehen` | 0,35: mehr Lust auf den zweiten Weg, wenn er auf dem ersten ein Hindernis gesehen hat |
| `bots.gabelZwang` | nur für Messungen: alle Bots auf den ersten (0) oder zweiten Weg (1), oder pro Gabelung (`{ park: 1 }`) |
| `bots.stufen.ultra.strecken.kiesgrube`, `.bergpass`, `.paris` | neue Fahr-Einstellungen von «Ultra» für die neuen Strecken (`tools/ultra.js`, Paris mit einer Suche über alle 8 Autos); Kiesgrube und Bergpass mit 8 % Tempo-Vorteil, Paris mit 12 % (`tempo: 1.12`, wie am Himalaya, so am 19.11.2026 entschieden) |
| Strecke `boostfelder: [{ pos, d }]` | Boost-Felder fest an diesen Stellen statt automatisch verteilt (neu in der Kiesgrube und am Bergpass, Paris hatte das schon) |
| `version` | 1.4: Online müssen alle dieselbe Fassung haben |

### Entscheidungen

- **Entwurf übernommen:** Den angefangenen Umbau (Gabelungen im Code, `tools/streckenmass.js`, `tools/plan.js`, `tools/gabeltest.js` und die Kiesgrube) habe ich übernommen und fertig gebaut: Schild, Hinweis, Minikarte, Steckbrief und die Wahl der Bots sind neu, die Kiesgrube habe ich weitergebaut, bis sie die Ziele erreicht, und der zweite Bauplatz auf einem Weg ist weg. `tools/gabeltest.js` prüft jetzt jede Gabelung einzeln und fährt jede gefundene Einstellung auch auf dem anderen Weg (Gegenprobe gegen den Zufall der Suche).
- **«Die längeren zwei»:** verstanden als: Die zwei längsten Strecken aus der Tabelle im Auftrag bekommen zwei Gabelungen, also Ägypten (1478 m) und Paris (1409 m). Paris hat darum zwei, Kiesgrube und Bergpass je eine. Ägypten folgt in Etappe 5.
- **Aus Nebenwegen werden Gabelungen:** Die Passage in Paris (bisher eine Abkürzung), der Parkweg in Paris und der Alpweg am Bergpass (bisher Umleitungen) sind jetzt Gabelungen, weil sie schon als zweiter Weg da waren und zum Ort passen. Damit jede Strecke weiterhin eine Umleitung hat, gibt es neu den «Kreisel» in Paris und den «Talweg» am Bergpass, beide an der Start-Geraden. Die «Notbrücke» in der Kiesgrube fällt weg, weil sie die ganze neue Seeschlaufe abgeschnitten hätte.
- **Wege ausgleichen:** In der Kiesgrube war der Weg über die Kieshalden zuerst 0,3 s schneller. Jetzt ist er Sand statt Schotter, 10 statt 12 m breit und hat eine grössere S-Kurve. In Paris war der Weg unter dem Eisenturm zuerst 1,2 s schneller als der Parkweg. Die neue Schlaufe auf dem Marsfeld und der Sand dort gleichen das aus. Mit vier Suchen statt einer fand der Optimierer unter dem Eisenturm später eine noch schnellere Runde, der Parkweg war damit 0,25 s langsamer. Sein Bogen reicht jetzt 7 m weniger weit in den Park hinaus. Am Bergpass passten die Wege schon.
- **Bauplätze nur auf dem ersten Weg:** Der zweite Weg einer Gabelung hat keinen Bauplatz. So liegt nie mehr als ein Bauplatz auf einem Weg, und der zweite Weg ist der Ausweg, wenn auf dem ersten ein Hindernis steht.
- **Bestenliste:** Der Auftrag verlangt für jede umgebaute Strecke eine neue Liste. Das widerspricht der Regel vom 18.11.2026, dass alle Zeiten sichtbar bleiben. Am 18.11.2026 hat Johann entschieden: Die alten Zeiten bleiben sichtbar, jede Liste behält ihre Kennung.
- **«Ultra» in Paris:** `tools/ultra.js` sucht mit vier Autos. Mit den Einstellungen, die es fand, war «Ultra» in Paris mit dem Rallye-Auto, dem Pick-up und dem Transporter nur 3,5 bis 3,7 % schneller als ohne Tempo-Vorteil. 8 % ist die Grenze aus dem Auftrag (nur der Himalaya hatte 12 %, so entschieden am 17.11.2026). Ich habe darum 30 zufällige Einstellungen in der Nähe mit allen 8 Autos gemessen und die gewählt, mit der jedes Auto mindestens 4 % schneller ist als ohne Tempo-Vorteil und der Sportwagen mindestens 4 % schneller als der Optimierer. Trotzdem gewann «Ultra» in Paris mit 8 % nur 94 von 100 Rennen gegen sieben «Schwer», auch nachdem die Bauplätze verschoben waren und er kaum mehr ein Hindernis traf. Er verlor im dichten Feld in den engen Gassen, meist in der ersten Runde. Mit 10 % gewann er 99, mit 12 % alle 100 Rennen. Am 19.11.2026 hat Johann entschieden: Paris bekommt wie der Himalaya 12 %. Damit ist jedes Auto allein 4,4 bis 7,3 % schneller als ohne Tempo-Vorteil.
- **«Ultra» am Bergpass:** Die neue Suche fand Einstellungen, mit denen «Ultra» weniger driftet (5,5 statt 6 Drifts pro Runde). Die bisherigen Einstellungen passen auch auf die neue Strecke, darum bleiben sie.
- **Boost-Felder in Paris:** Die automatische Verteilung legte ein Feld auf einen Weg einer Gabelung und hätte diesen Weg schneller gemacht. Paris legt seine vier Felder darum selbst fest: vor der Steinbrücke, vor der Eisenbrücke, nach der Mühle und am Zielhang.
- **Nichts auf der Strasse:** Das neue Prüfwerkzeug `tools/naehe.js` fand Kieshaufen, die mit ihrem Rand auf den Seitenstreifen reichten, einen Hügel hinter dem Pass, der am Alpweg bis an den Rand stieg, und die Treppengasse in Paris, die gleich neben der Strasse schon 1 m höher lag. Kieshaufen neben der Strasse sind jetzt nur so gross, wie Platz ist, der Hügel steht 22 m weiter hinten, und die Gasse steigt flacher an. Nachdem der Parkweg in Paris flacher geworden war, standen zwei Beine des Eisenturms auf seinem Seitenstreifen. Der Turm ist unten jetzt etwas schmaler (die Beine stehen 18,5 statt 21 m von seiner Mitte entfernt). Das ändert nur das Bild, an keiner Messung etwas.
- **Zu spitze Kurven gerundet:** In der Kiesgrube waren drei Zickzack-Kurven (Gasse, Grubenrand, Mulde) mit 7 bis 9 m Radius so eng, dass die innere Wand einklappte und der Stand auf der Strecke beim Fahren sprang. Ich habe die Ecken abgeschnitten (jetzt mindestens 10 m Radius), so blieben die Drift-Stellen erhalten.
- **Platz auf den Wegen:** Der Stand eines Autos auf einem Weg wird auf die Hauptstrecke umgerechnet: weit weg von ihr anteilig zwischen Abzweigung und Einmündung, nahe an ihr so, wie er auf der Hauptstrecke gemessen wird, dazwischen fliessend. Vorher sprang der Stand an der Abzweigung und an der Einmündung um mehrere Meter, und damit kurz auch Platz und Abstände.
- **Wegweiser höher:** Die blaue Tafel hing auf breiten Strassen mit der Unterkante nur 3,8 m über der Fahrbahn, und der obere Balken schwebte gut einen halben Meter über den Pfosten. Jetzt liegt die Unterkante 5,2 m hoch (der untere Balken 4,9 m), und die Pfosten reichen bis über den oberen Balken.
- **Betonelemente an Baustellen:** Sie wurden immer in Stücken von zwei Abschnitten gezeichnet. Wo eine Baustelle direkt an einer Einmündung liegt (Paris, Ende der Passage), ragte darum das letzte Stück 2 m in den Weg hinein. Jetzt enden sie genau dort, wo der Weg beginnt.
- **Abkürzungen neu abgestimmt:** Eine eigene Abkürzung soll etwas Zeit sparen, aber nicht das Rennen entscheiden. Im ersten Entwurf sparte der gerade Steilhang am Bergpass 2,5 s pro Runde und der gerade Grubenweg in der Kiesgrube 1,9 s, so viel, dass «Ultra» und «Schwer» oft gegen Bots verloren, die eine Abkürzung bauten. Der Steilhang hat jetzt eine Kehre im Hang, der Grubenweg Schlangenlinien. Die Treppengasse in Paris dagegen war mit zwei spitzen Ecken 2,7 s langsamer als die Strasse (in Fassung 1.3 blieben Bots sogar darin hängen); sie führt jetzt fast gerade hinter der Mühle durch. Gewinn pro Runde, «Schwer» allein, Abkürzung in Runde 2 fertig gebaut, Mittel aus 8 Fahrten mit dem Sportwagen: Grubenweg 1,1 s (Fassung 1.3: 0,8 s), Steilhang 0,5 s (1.3: 2,9 s langsamer als die Strasse), Treppengasse 0,5 s (1.3: der Bot blieb darin hängen). Mit Pick-up und Rallye-Auto: Grubenweg 0,95 bis 1,19 s, Steilhang 0,52 bis 0,69 s, Treppengasse 0,50 bis 0,78 s.
- **Kein Kreis mehr nach einer Umleitung:** Am Bergpass verlor «Schwer» jedes sechste Rennen gegen «Mittel». Der Grund: Wer von einer Umleitung zurück auf die Strasse kam, war noch keine 70 m nach deren Einfahrt. Der Bot wollte die Umleitung, die ja noch galt, nochmals nehmen und fuhr einen Kreis zurück (bis 7 s). Die neuen Umleitungen (Werkhof, Talweg, Kreisel) überbrücken nur 62 bis 68 m, darum trat das erst jetzt auf. Jetzt lenkt kein Bot mehr in eine Einfahrt, die schon hinter ihm liegt; das galt bisher nur für «Ultra». Das betrifft alle Strecken.
- **Passage sanfter:** Die Passage zweigte mit 54° vom Boulevard ab. Jeder neunte Bot, der sie nehmen wollte, kam mit seinem Tempo nicht mehr hinein und prallte an die Ecke zwischen den beiden Wegen (in 30 Rennen 37 von 338 bei «Schwer», 7 von 53 bei «Ultra»). Jetzt biegt sie zuerst mit 27° ab und erst danach stärker. Danach war sie aber 0,27 s schneller als der Boulevard (beste von vier Suchen des Optimierers pro Weg, Ziel höchstens 0,2 s). Schmaler machen (8,5, 8 oder 7,5 statt 9 m) half kaum. Jetzt macht sie in der Mitte einen leichten Knick um ein Haus. In 30 Rennen verpassen sie seither 2 von 347 «Schwer» und 1 von 341 «Mittel», die sie nehmen wollen, und kein «Ultra».
- **Bauplätze aus engen Kehren genommen:** Nach dem Umbau gewann «Ultra» am Bergpass nur 96 % und in Paris 92 %, «Schwer» in der Kiesgrube 95 %. Der Grund: Neun der neuen Bauplätze lagen mitten in engen Kehren oder direkt am Ausgang einer Kurve. Ein Hindernis dort konnte auch der beste Bot nicht umfahren (Prüfung mit einem Bot allein, das Hindernis steht fertig vor ihm: am Bergpass H9 in 24 von 24 Fahrten getroffen; «Ultra» fuhr dort im Mittel fast 5 Hindernisse pro Rennen an). Jetzt liegen diese Bauplätze auf Geraden oder in weiten Bögen (Kiesgrube H4, H5, H9; Bergpass H7, H8, H9; Paris H7, H8, H9), und man kann jedem Hindernis an jedem Bauplatz ausweichen (0 Treffer in 24 Fahrten pro Bauplatz, nur am Bergpass H2 einmal bei Pylonen). Die Boost-Felder der Kiesgrube und des Bergpasses stehen jetzt fest an ihren bisherigen Stellen: Sonst hätte die Strecke sie wegen der verschobenen Bauplätze neu verteilt, in der Kiesgrube auch weg vom ersten Weg der Gabelung, und die beiden Wege wären nicht mehr gleich schnell gewesen. Seither gewinnt «Ultra» am Bergpass 100 statt 96 von 100 Rennen und in der Kiesgrube 99, «Schwer» in der Kiesgrube 97 statt 95 (Paris siehe nächster Punkt).
- **Treppengasse im Bogen:** Die neue Treppengasse zweigte rechtwinklig ab. Fast jeder dritte Bot, der sie gebaut hatte, kam mit vollem Tempo nicht hinein und fuhr an ihr vorbei (in 30 Rennen 18 von 59). Jetzt zweigt sie 11 m früher im Bogen ab, seither nehmen sie alle (in 30 Rennen 55 von 55, nach dem Ausgleich der Höhen im nächsten Punkt 58 von 58). Sie spart je nach Auto 0,5 bis 0,8 s pro Runde, weniger als der Grubenweg und etwa gleich viel wie der Steilhang.
- **Abkürzungen ohne Stufe an den Enden:** Wo eine Abkürzung neben der Strasse beginnt oder endet, liegt sie auf deren Seitenstreifen und muss dort gleich hoch sein wie die Strasse. Der Steilhang lag beim Einbiegen bis 1,4 m darüber, die Autos schwebten dort kurz über der Strasse (so war es schon in Fassung 1.3). Der Grubenweg lag am Anfang bis 0,4 m darunter, die Treppengasse 0,4 m darüber. Jetzt fällt der Steilhang gleichmässig mit etwa 6 % statt am Ende mit 9 %, und alle drei liegen an den Enden höchstens 0,3 m neben der Strasse, in ihrer Mitte höchstens 0,15 m. Danach habe ich den Gewinn der Abkürzungen (oben) und die Einfahrten neu gemessen: In 30 Rennen nehmen 58 von 58 Bots die Treppengasse, 38 von 38 den Steilhang und 48 von 49 den Grubenweg (ein «Leicht» kam mit 28 m/s nicht hinein).
- **Abkürzungen richtig gezählt:** `tools/spuren.js` zählte eine eigene Abkürzung nur als genommen, wenn der Bot 18 m nach der Abzweigung schon auf ihr war. Der neue Steilhang verlässt die Strasse erst nach 29 m, darum stand er dort mit 0 %. Jetzt zählt, ob der Bot bis 60 m nach der Abzweigung (höchstens die halbe Länge) auf ihr ist. Alle Werte vorher und nachher in dieser Etappe sind so gemessen.
- **Auto-Vorschau blieb manchmal leer:** Beim Testen meldete three.js einmal einen Fehler. Wird das Auto gewechselt oder ein Rennen gestartet, während die Vorschau im Menü ihre Shader noch übersetzt, bricht `compileAsync` von three.js ab, und die Vorschau bleibt unsichtbar, bis man sie wieder öffnet. Das gab es seit Etappe 1. Jetzt fragt das Spiel selbst nach, ob die Shader fertig sind, und überspringt Materialien, die schon freigegeben sind.
- **Fassung 1.4:** Die Strecken sind anders als in Fassung 1.3. Online müssen darum alle die Seite neu laden, damit alle mit derselben Fassung fahren (Hinweis in der Lobby wie bisher).


### Grenzen

- **Alte Zeiten in der Bestenliste:** Die alten Zeiten stammen von den kürzeren Strecken. Eine schnelle Runde dauert jetzt 2 bis 5 s länger, ein Rennen über 3 Runden also 6 bis 15 s. Neue Zeiten landen darum vorerst hinter den alten. So ist es am 18.11.2026 entschieden: Alle Zeiten bleiben sichtbar, jede Liste behält ihre Kennung.
- **Pick-up in der Kiesgrube:** 28,5 % Siege unter gleich starken Bots, erlaubt sind höchstens 25 %. Die Limousine liegt auf allen drei Strecken knapp über 4 %. Das stimme ich in Etappe 6 ab, wenn alle Strecken neu sind.
- **Gänsemarsch:** −54 % auf Geraden statt −60 %, wie schon in Etappe 3 auf den alten Strecken. Fast der ganze Rest entsteht kurz nach dem Start, solange das Feld in den drei Spalten der Startaufstellung fährt (ab 12 s nach dem Start −79 %).
- **Paris auf den zweiten Wegen:** Wer an beiden Gabelungen den zweiten Weg nimmt, fährt pro Runde 8 Drift-Kurven statt 9. Das Ziel von 9 gilt für den ersten Weg.
- **Passage:** In 30 Rennen verpassen 2 von 347 «Schwer» und 1 von 341 «Mittel» die Einfahrt, die sie nehmen wollten, kein «Ultra». Wer sie verpasst, fährt auf dem Boulevard weiter und verliert nichts.
- **Bauplatz H2 am Bergpass:** Pylonen dort traf der Prüf-Bot in 1 von 24 Fahrten, an allen anderen Bauplätzen nie.
- **Optimierer:** Eine einzelne Suche streut um bis zu 0,3 s. Darum sind die Gabelungen mit vier Suchen gemessen, und jede gefundene Einstellung fährt auch den anderen Weg. Je nachdem, welche Einstellungen die Suchen finden, verschiebt sich der Unterschied trotzdem um rund 0,1 s: Der Weg unter dem Eisenturm lag in Paris je nach Fassung des Parkwegs bei 49,20 oder 49,31 s.
- **«Ultra» in Paris mit 12 %:** mehr als die 8 % aus dem Auftrag, wie am Himalaya (Entscheidung vom 19.11.2026, siehe oben).
- **Himalaya, Ägypten und New York** sind noch nicht umgebaut. Ihre Abkürzungen sparen bisher keine Zeit: Am Himalaya und in Ägypten kosten sie rund 4 s, weil die Bots an der Ausfahrt hängen bleiben (siehe Etappe 3), in New York 0,1 s. Am Himalaya liegen die Enden der Abkürzungen zudem bis 1,9 m über oder unter der Strasse. Das nehme ich mir in Etappe 5 mit dem Umbau vor.
- **Minikarte bei einer Gabelung:** Auf der Minikarte im Spiel liegen die beiden Wege einer Gabelung nahe beieinander, weil sie auch auf der Strecke höchstens 23 bis 37 m auseinanderliegen. Wer welchen Weg fährt, sieht man auf der kleinen Karte erst mitten in der Gabelung. Darum gibt es das Bild der Minikarte auch vergrössert.
- **Bildschirmfotos in der Testumgebung:** In Paris und im geteilten Bild dauert ein Bildschirmfoto in der Software-Grafik bis 34 s (in Paris auch mit Fassung 1.3), und einzelne Bilder im Rennen brauchen dort mehrere Sekunden, ohne dass ein neuer Shader oder eine neue Textur dazukommt (`tools/haenger.js`). Ob Paris auf echten Geräten flüssig läuft, zeigt nur der Leistungstest im Spiel auf dem Gerät selbst.


### Ziele dieser Etappe

| Ziel | Ergebnis | |
|---|---|---|
| Kiesgrube: mindestens 24 Kurven, 9 Drift-Kurven pro Runde, höchstens 1601 m | 27 Kurven, 9 Drift-Kurven, 1558 m | erreicht |
| Bergpass: mindestens 13 Kurven, 6 Drift-Kurven, höchstens 1484 m | 14 Kurven, 6 Drift-Kurven, 1381 m | erreicht |
| Paris: mindestens 17 Kurven, 9 Drift-Kurven, höchstens 1620 m | 17 Kurven, 9 Drift-Kurven (auf den zweiten Wegen 8), 1560 m | erreicht |
| Mehr Kurven, gut gemischt; eine gute Runde unter einer Minute | Haarnadeln, S-Kurven, Schikanen, Bögen zum Driften, Knicke; 41 bis 50 s | erreicht |
| Jede Strecke mindestens eine Gabelung, die längeren zwei | Kiesgrube 1, Bergpass 1, Paris 2 (Ägypten folgt in Etappe 5) | erreicht |
| Beide Wege einer Gabelung höchstens 0,2 s auseinander (Optimierer) | 0,11 / 0,12 / 0,16 / 0,15 s | erreicht |
| Gabelung früh zu sehen (Schilder, Pfeile, Minikarte) | Schild 55 m vorher, Hinweis ab 150 m, Minikarte und Steckbrief | erreicht |
| Platz, Abstände, Zurücksetzen und «Falsche Richtung» auf beiden Wegen | im Browser über jeden Weg geprüft, 46 von 46 | erreicht |
| Auf jedem Weg höchstens ein Bauplatz | zweiter Weg ohne Bauplatz | erreicht |
| Mindestens drei neue Elemente pro Strecke, passend zum Ort | siehe «Die drei Strecken» | erreicht |
| Nichts auf der Strasse oder in der Luft (Prüfwerkzeug) | 0 Fundstellen auf allen drei Strecken (`tools/naehe.js`), Abkürzungen an den Enden höchstens 0,3 m neben der Strasse | erreicht |
| Leistungsziele aus Teil 1 auch auf den neuen Strecken | Dreiecke und Zeichenaufrufe auf allen Stufen im Budget, Rechenzeit der Spiel-Logik wie vorher | erreicht |
| Vorschau, Minikarte und Steckbrief nachgeführt | Steckbrief neu mit Kurven und Gabelungen | erreicht |
| Bauplätze, Nebenwege, Boost-Felder, Startaufstellung (auch 33), Ideallinie, Spuren, «Ultra», Optimierer neu eingerichtet | siehe oben | erreicht |
| Teil 2: «Schwer» gewinnt fast immer gegen 7 «Mittel» | 99,0 % (97 / 100 / 100 %) | erreicht |
| Teil 2: «Ultra» gewinnt mindestens 99 % gegen 7 «Schwer» | 99,7 % (99 / 100 / 100 %) | erreicht |
| Teil 2: «Ultra» mindestens 4 % schneller als der Optimierer, mit jedem Auto | 4,7 / 5,0 / 4,9 %, jedes Auto mindestens 4,4 % | erreicht |
| Teil 2: pro Strecke jedes Auto 4 bis 25 % Siege | Pick-up in der Kiesgrube 28,5 % | **nicht erreicht** (Etappe 6) |
| Teil 3: Streuung auf Geraden mindestens doppelt, jedes Drittel mindestens 20 % | 2,7-mal; 21,3 / 44,4 / 34,3 % | erreicht |
| Teil 3: Gänsemarsch −60 % | −54 % (ab 12 s nach dem Start −79 %) | **nicht erreicht** |
| Teil 3: jeder Weg einer Gabelung 30 bis 70 % | zweiter Weg 57,9 bis 60,2 % | erreicht |
| Teil 3: mindestens die Hälfte der Bots nimmt beide Wege | 75,5 bis 78,8 % | erreicht |
| Teil 3: höchstens 65 % derselbe Weg wie der Bot davor | 39,9 bis 43,6 % | erreicht |
| Teil 3: Berührungen, Zurücksetzen und Stillstand höchstens +10 % | −20 %, 0 statt 1 Mal, 0,01 statt 0,11 s | erreicht |
| Bestenliste: neue Liste für jede umgebaute Strecke | alte Zeiten bleiben sichtbar, Entscheidung vom 18.11.2026 | geändert |
| Bilder: jede Strecke vorher und nachher, jede Gabelung, Minikarte mit Bots auf verschiedenen Wegen | Draufsichten, je zwei Blickwinkel vorher und nachher, jede Gabelung mit Schild und Hinweis und auf beiden Wegen (16 Bilder), Minikarte mit Bots auf beiden Wegen einer Gabelung auf jeder Strecke (ganz und vergrössert), Start mit 33 Autos, Steckbrief | erreicht |
| Im Browser: jede umgebaute Strecke über jeden Weg jeder Gabelung | jeder Weg jeder Gabelung über 2 Runden, 46 von 46 Prüfungen gut (`tools/gabelbrowser.js`, dreimal gelaufen) | erreicht |

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
| `bau.preise` | 3, 6, 3, 3, 4, 6 | Rampe, Abkürzung, Pylonen, Schlamm, Absperrung, Umleitung (Pylonen bis 17.11.2026: 2 BP) |
| `bau.minVorlauf`, `bau.schutzZeit` | 3 s, 3 s | Vorwarnzeit und Schutz nach einem Treffer |
| `bau.maxProSpieler`, `bau.maxGesamt`, `bau.wartezeit` | 2, 6, 4 s | Grenzen für Hindernisse |
| `bp.feldExponent` | 0,5 | ab 9 Fahrern gibt es pro Mal weniger Baupunkte: × (8 ÷ Fahrer)^0,5, also × 0,82 mit 12 und × 0,49 mit 33 Fahrern (0 = wie mit 8) |
| `bau.maxSchlenker` | 4 m | Sperren stehen so, dass die Ideallinie höchstens so weit im gesperrten Teil liegt |
| `rennen.maxBots`, `maxMenschen`, `maxFahrer` | 11, 22, 33 | Bots pro Rennen, Menschen pro Online-Raum (Host eingerechnet), Autos pro Rennen |
| `rennen.startAnlauf` | 45 m | ein kleines Feld rückt nach hinten, bis die vorderste Reihe höchstens so viel Anlauf bis zur Ziellinie hat |
| `rennen.startBreite`, `startReihe`, `startSeite3`, `startVersatz` | 3, 4,6 m, 3,4 m, 0,9 m | Autos pro Startreihe, Abstand der Reihen, Abstand in der Reihe, Versatz innerhalb der Reihe |
| `netz.nahAnzahl`, `fernTeiler`, `refTeiler` | 10, 2, 5 | die 10 nächsten Autos bekommt jeder Gast 20-mal pro Sekunde, die übrigen jedes 2. Mal, Platz, BP und Runde jedes 5. Mal |
| `netz.handyHostMax` | 12 | leitet ein Handy oder Tablet ein Rennen mit mehr Autos, zeigt die Lobby einen Hinweis |
| `netz.startTimeout` | 30 s | beim Rennstart darf es so lange still bleiben, bis das erste Rennbild da ist (langsame Geräte bauen dann die Strecke auf), danach gilt `netz.ausfallTimeout` (6 s) |
| `windschatten.bonus` | 0,02 | 2 % mehr Höchsttempo im Windschatten |
| `bots.stufen` | Mut 0,76 / 0,83 / 1,04 / 1,18 bis 1,30 | Fahrkönnen der Bots leicht, mittel, schwer, ultra («Ultra» je Strecke eigene Werte) |
| `bots.stufen.schwer` | `profi`, `bremsen` 34, `driftAb` 0,5, `tempo` 1,03 | Profi ohne Fehler, spätere Bremspunkte, früher Drift, 3 % Tempo-Vorteil (höchstens erlaubt) |
| `bots.stufen.ultra` | `tempo` 1,08 (Himalaya und Paris 1,12), `strecken`, `hindernisse` 0,15, `pylonen` 0, `umsichtig` | 8 % Tempo-Vorteil, am Himalaya und in Paris 12 %, Fahr-Einstellungen pro Strecke vom Optimierer, baut nur selten Hindernisse und nie Pylonen, weicht vorausschauend aus |
| `bots.spuren` | Spur 0,6 bis 0,95 der halben Fahrbahn, neue Spur alle 25 s, `meiden` 2, `abstand` 2,2 m | Lieblingsspur auf Geraden, volle Spuren meiden, kein Gänsemarsch (siehe «Bots auf verschiedenen Spuren») |
| `bots.gabel` | `auto` 0,22, `lieb` 0,18, `verkehr` 0,07, `hinten` 0,12, `wechsel` 0,12, `folgen` 0,12, `sehen` 0,35 | Wahl der Bots an einer Gabelung: nach Auto, eigener Vorliebe, Verkehr und Lage im Rennen, mit Abwechslung, ohne dem Vordermann einfach zu folgen, weg von einem gesehenen Hindernis (siehe «Neue Strecken») |
| `bots.pylonen` | 0,4 | so oft wie früher setzen Bots Pylonen (1 = wie bis 17.11.2026, 0 = nie) |
| `bots.schlammSparen` | 0,5 | so oft sparen Bots ihre Punkte, statt ein Schlammloch zu bauen (0 = nie, wie bis 17.11.2026) |
| `grafik.auto` | 3,5 / 8 / 16 ms | so schnell muss ein Bild auf «Hoch» sein für «Ultra», «Hoch», «Mittel» |
| `grafik.leben` | Gras 6000 / 14000 / 26000 | Gras, Blumen, Steine und Vögel pro Grafik-Stufe |
| `grafik.leben.passanten` | 50 / 90 / 140 | Fussgänger in Paris und New York ab «Mittel» |
| `grafik.lod` | 30 / 45 / 70 m | ab dieser Entfernung zeigen Autos ihre einfache Fassung («Mittel», «Hoch», «Ultra») |
| `grafik.feinMax` | 6 / 8 / 8 / 8 | so viele Autos (die nächsten) haben ein eigenes Modell («Niedrig», «Mittel», «Hoch», «Ultra»), alle übrigen sind Instanzen |
| `grafik.schilder` | 10 | höchstens so viele Namensschilder pro Bild |
| `grafik.delle` | ab 3 m/s, höchstens 0,13 m | Dellen nach Stössen |
| `bestenliste` | `proName` 1, `zeigen` 10, `speichern` 50, `minRunde` 8 s | Zeiten pro Name und Liste, sichtbare und gespeicherte Plätze, kürzeste gültige Runde |
| `bestenliste.neuZeilen` | 5 | so viele «Neu in der Liste»-Zeilen zeigt das Ergebnis nach dem Rennen (eigene zuerst), mehr werden zu «… und 17 weitere» |
| `bestenliste.firebase` | Kennungen der Web-App «baustellen-rennen» | öffentliche Kennungen für «Mit Google anmelden», leer heisst: kein Knopf |
| `bestenliste.pfad`, `pfadAlt` | `bestenliste/v2`, `bestenliste/v1` | Ordner der gemeinsamen Liste mit Anmeldung und der alten Liste, die nur noch gelesen wird (leer = nicht mehr zeigen) |
| `bestenliste.server` | Firebase-Datenbank «baustellen-rennen» (Belgien) | Adresse der gemeinsamen Datenbank, leer heisst: jedes Gerät hat nur seine eigene Liste |
| `bestenliste.zeitlimit`, `frisch`, `nochmals` | 6 s, 60 s, 15 s | Wartezeit auf die Datenbank, so lange gilt eine geladene Liste, neuer Versuch nach einem Fehler |
| `bestenliste.mindestTempo`, `verboten` | 2, 10 Wörter | Mindestzeit = Streckenlänge ÷ (2 × Höchsttempo), unerwünschte Wörter in Namen |

## Entscheidungen, die ich getroffen habe

- Höchstens 33 Autos pro Rennen: online bis zu 22 Menschen und dazu bis zu 11 Bots (bis 17.11.2026 höchstens 8). Sind insgesamt höchstens 22 Autos gemeint, ist das nur `CONFIG.rennen.maxFahrer: 22`.
- Die Rundenzeit läuft ab der ersten Fahrt über die Ziellinie. Die Gesamtzeit und die Reihenfolge im Ziel zählen weiter ab dem Startsignal, damit die Reihenfolge im Ziel zur Gesamtzeit passt.
- Baupunkte gibt es nur für neu gewonnene Plätze. Wer einen eben verlorenen Platz zurückholt, bekommt dafür wenig. Sonst füttert das Hin und Her im Pulk laufend neue Baustellen.
- Wer dicht an der Spitze klebt, sammelt weniger. Wer weit zurückliegt, sammelt voll. So hilft das Bauen vor allem denen, die wirklich hinten liegen.
- In den ersten 8 s nach dem Start und für Plätze, die man mit Rampe oder Abkürzung gekauft hat, gibt es keine Punkte.
- Absperrung und Schlammloch stehen auf der Seite, auf der ein aufmerksamer Fahrer nur einen kleinen Schlenker braucht. Ausweichen kostet rund 0,1 s, ein Treffer 0,3 bis 0,7 s.
- Die Umleitung ist eine schräge Leitwand, die auf den langen Weg lenkt. Niemand wird angehalten.
- Wer an die Spitze überholt, bekommt die Punkte noch, kann sie aber erst wieder ausgeben, wenn er nicht mehr führt.
- Bestenliste: Gewertet wird die schnellste Runde, weil die Rundenzahl einstellbar ist. Die Zeiten stehen im selben Format wie im übrigen Spiel (0:41.23). Ein Name, den es in der Liste schon gibt, gilt als dieselbe Person, es bleibt die bessere Zeit.
- Nach dem Namen fragt das Spiel nur im Modus «Gegen Bots». Im Split-Screen und online gibt jeder seinen Namen ohnehin vor dem Rennen ein.
- Gemeinsame Bestenliste: Die Datenbank ist ein Protokoll. Jede Verbesserung ist ein neuer Eintrag, nichts wird überschrieben. So reicht die Regel «nur hinzufügen», und das Spiel sucht beim Laden pro Name die beste Zeit und pro Liste den schnellsten Bot heraus.
- Den Standardnamen «Spieler» lädt das Spiel nicht hoch, sonst stünden alle, die keinen Namen eingegeben haben, als eine Person in der Liste.
- Die Mindestzeit ist bewusst grosszügig (die besten Bots brauchen rund 40 % länger), damit keine echte Runde abgelehnt wird, auch nicht mit Abkürzung, Rampe und Windschatten. Unsinn wie eine 5-Sekunden-Runde lehnt die Datenbank ab, eine erfundene Zeit knapp über der Grenze nicht.
- Bei Online-Rennen vor dieser Version hat jedes Gerät die Zeiten aller Mitspieler gespeichert, ohne sich zu merken, wer an welchem Gerät sass. Davon lädt ein Gerät beim ersten Hochladen nur die Zeiten mit dem eigenen Namen hoch, Bot-Zeiten aus solchen Rennen gar nicht.
- Beim Öffnen lädt das Spiel die Liste höchstens einmal pro Minute neu, damit Blättern nicht jedes Mal lädt. «Aktualisieren» lädt sofort.
- «Ultra» hat 8 % Tempo-Vorteil (die Grenze aus dem Auftrag), nur am Himalaya 12 % (entschieden am 17.11.2026, weil er dort mit 8 % nur 91 % der Rennen gegen «Schwer» gewann) und in Paris 12 % (entschieden am 19.11.2026, weil er auf der neuen Strecke mit 8 % nur 94 % gewann). Den Rest holt er nur mit Fahrkönnen: Die Einstellungen pro Strecke stammen aus derselben Suche wie beim Optimierer, nur mit Tempo-Vorteil und mit vier Autos geprüft.
- «Ultra» baut fast nur für sich selbst (Abkürzung, Rampe). Hindernisse für andere baut er in rund jedem siebten Fall, in dem ein anderer Bot eines bauen würde, Pylonen nie.
- Pylonen: Bots setzen sie noch in 40 % der Fälle wie früher (`CONFIG.bots.pylonen` 0,4). Mit dem höheren Preis von 3 BP kommt das zusammen auf rund 0,2 Pylonen pro Rennen statt 14 bis 16. Menschen bauen wie bisher.
- Ohne weitere Regel hätten die Bots die gesparten Punkte fast ganz in Schlammlöcher gesteckt (doppelt so viele wie vorher). Darum heben sie in der Hälfte dieser Fälle ihre Punkte auf (`CONFIG.bots.schlammSparen`).
- In der Bestenliste steht pro Liste nur der schnellste Bot. Das ist jetzt meistens ein «Ultra»-Bot («Bot · Ultra»), so ist es gewollt.
- **Anmelden (18.11.2026):** im Popup-Fenster statt mit Weiterleitung, weil die Weiterleitung auf `popc-u.github.io` mit der Firebase-Adresse als Anmeldeseite in vielen Browsern nicht mehr klappt. Ein Name gehört dem Konto, das ihn zuerst wählt. Die alte Liste bleibt lesbar und sichtbar (ohne Häkchen), für immer: Auch eine umgebaute Strecke behält ihre Liste. Bot-Zeiten kommen nur noch von angemeldeten Geräten, die das Rennen leiten. Für alle Strecken gilt in der Datenbank dieselbe Mindestzeit von 20 s, das Spiel selbst prüft weiter die genaue Mindestzeit jeder Strecke.

## Bekannte Grenzen

- **Stand des Grafik-Auftrags (17.11.2026):** Fertig sind die «Schwer»-Bots, die Grafik-Grundlage (Nachbearbeitung, Himmel mit Wolken, Sonnenblendung, Stufe «Ultra» mit automatischer Wahl), leuchtende und blendende Lichter, Dellen nach Stössen, der Fahrerkopf und eine einfache Fassung der Autos für die Ferne, der Tacho mit Nadel und die Minikarte mit Höhenschatten, Gras, Blumen, Steine, Bäume im Wind, Vögel, Seen mit Wellen und Schaumrand, jubelnde Zuschauer, Bauarbeiter, Passanten in Paris und New York, wehende Fahnen, Baukräne mit Gittermast und grabende Bagger, der Steckbrief in der Streckenwahl und das Siegerpodest. Noch offen sind: feinere Karosserien (Rundungen, Fugen, Lufteinlässe), Ort für Ort feinere Sehenswürdigkeiten, fahrender Verkehr im Hintergrund, Regen, Vorschaubilder der Strecken als gerenderte Bilder, und das neue Aussehen von Garage, Lobby, Ladebild und Handy-Ansicht.
- Die Autos bestehen aus einfachen Flächen. Sie sind klar unterscheidbar und haben Felgen, leuchtende Lichter, getönte Scheiben, Spoiler, Spiegel und Auspuff, sehen aber nicht fotorealistisch aus.
- Ton lässt sich in der Test-Umgebung nicht anhören. Geprüft ist, dass alle Klänge ohne Fehler laufen, abgehört hat sie noch niemand.

- Der Online-Modus ist mit zwei Browsern gegen einen lokalen Vermittlungsserver getestet (Lobby, Rennen, Ergebnis, Revanche, Bot-Übernahme), ebenso die Fehlerfälle beim Beitritt (falscher Code, Host antwortet nicht, Netz blockiert, Vermittler nicht erreichbar). Über den öffentlichen PeerJS-Server im echten Internet konnte ich ihn in meiner Testumgebung nicht ausprobieren. Ein erster Versuch mit zwei Geräten scheiterte am 13.11.2026 beim Beitritt. Die Ursache ist noch offen, die Diagnose-Zeile unter der Fehlermeldung soll sie zeigen. Zwischen Geräten in verschiedenen Netzen braucht es manchmal einen TURN-Server, und die mitgelieferten von PeerJS sind nicht immer erreichbar.
- **Grosse Lobbys:** 22 Menschen sind mit 22 Browserfenstern auf einem Rechner gegen einen lokalen Vermittlungsserver getestet, nicht mit 22 echten Geräten in verschiedenen Netzen. Der Host rechnet alle Autos und schickt allen Gästen die Daten. Mit 33 Autos sollte darum ein Laptop oder Computer der Host sein, kein Handy. Auf Ägypten und New York steht das Feld noch wie bisher vorne, weil die Ziellinie dort kurz nach einer Kurve liegt (wird mit den Strecken-Umbauten behoben).
- **Ruhigere Fahrt:** Auf Asphalt bleiben wenige Ausreisser an Knicken im Höhenprofil der Strasse, vor allem am Bergpass und in Ägypten (291 statt 4'932 in je 60 s mit 8 Autos auf allen Strecken). Sie verschwinden erst, wenn das Höhenprofil beim Strecken-Umbau weicher wird.
- Die Bildrate ist nur mit Software-Grafik geprüft. Ruckelt es auf einem Gerät, hilft die Grafikstufe «Niedrig».
- Die Touch-Steuerung ist eingebaut, aber nicht getestet.
- Einen Grand-Prix-Modus gibt es nicht.
- Bots bauen selten Umleitungen und Abkürzungen, weil die Punkte knapp sind.
- three.js 0.160.0 schreibt eine harmlose Warnung in die Browser-Konsole.
- **Umleitung kurz nach der Abzweigung:** Seit Fassung 1.4 für alle Stufen behoben (bis dahin nur für «Ultra»): Kein Bot lenkt mehr in eine Einfahrt, die schon hinter ihm liegt (siehe «Neue Strecken», «Kein Kreis mehr nach einer Umleitung»).
- **Mit Google anmelden:** Die Anmeldung ist gegen die Firebase-Emulatoren getestet (Regeln, Namenswahl, Hochladen, Abmelden, alle Fehlermeldungen), das echte Google-Fenster konnte ich in meiner Testumgebung nicht öffnen. Der echte Test ist die Prüfliste unter «Mit Google anmelden». Wer angemeldet ist und sich auskennt, kann weiterhin eine erfundene Zeit über 20 s schicken, aber nur unter seinem eigenen Konto: Solche Einträge findest du über die Konto-Nummer und kannst das Konto sperren.
- **Gemeinsame Bestenliste:** Solange keine Datenbank eingetragen ist, hat jedes Gerät nur seine eigene Liste (wie bisher). Die Anbindung an Firebase ist nur gegen einen nachgebauten Ersatz-Server mit denselben Regeln getestet, weil die Test-Umgebung das Internet nicht erreicht. Der echte Test sind zwei Geräte (siehe «Gemeinsame Bestenliste einrichten», Schritt 6). Schummeln lässt sich ohne eigenen Server nicht ganz verhindern: Wer sich auskennt, kann eine erfundene Zeit über der Mindestzeit schicken. Solche Einträge löschst du in der Firebase-Konsole. Gleicher Name heisst gleiche Person, auch auf verschiedenen Geräten: Zwei Leute mit demselben Namen teilen sich einen Platz. Die Liste kann jeder lesen, der die Adresse kennt, darum besser Spitznamen statt voller Namen. Wer die Website-Daten im Browser löscht, löscht die Liste des Geräts und noch nicht hochgeladene Zeiten, die gemeinsame Liste bleibt.

## Für Bastler

- `index.html?debug=1` zeigt Messwerte und Bauplätze.
- `index.html?sim=200` lässt 200 Bot-Rennen laufen und zeigt die Auswertung.
