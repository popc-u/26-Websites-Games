# Baustellen-Rennen

Ein 3D-Kartrennen im Low-Poly-Stil für den Browser. Die Besonderheit: Es gibt keine Zufalls-Items. Wer hinten liegt, sammelt Baupunkte (BP) und baut damit die Strecke um, mit Rampen und Abkürzungen für sich selbst oder Baustellen gegen die Fahrer davor.

Das ganze Spiel steckt in einer einzigen Datei: `index.html`.

## Starten

`index.html` doppelklicken (Chrome, Edge, Firefox oder Safari). Es braucht eine Internetverbindung, weil three.js 0.160.0 von einem CDN geladen wird (für Online-Spiele zusätzlich PeerJS 1.5.4). Sonst ist nichts zu installieren.

- **Gegen Bots:** 1 Spieler und bis zu 11 Bots, Stufe leicht, mittel, schwer oder ultra (praktisch unschlagbar).
- **Lokal am selben Gerät:** 2 Spieler an einer Tastatur, mit Gamepads bis 4, dazu bis zu 11 Bots. Der Bildschirm wird geteilt.
- **Online:** bis zu 22 Menschen und dazu bis zu 11 Bots, ohne eigenen Server (siehe unten).

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
- **Bild:** Himmel mit Haufen- und Schleierwolken und einer Sonne, die blendet, Dunst in der Ferne, weiche Schatten, Spiegelungen auf Lack und Glas. Lampen, Fenster, Rücklichter und Boost-Felder leuchten und strahlen (siehe «Grafik-Stufen»). Jede Strecke hat ihre Stimmung und Farbabstimmung: die Kiesgrube liegt im Abendlicht, der Bergpass im klaren Morgen. Am Streckenrand stehen Fichten mit gezackten Astschichten und Laubbäume mit Kronen aus Blätterbüscheln, die sich im Wind wiegen, dazu Gras, Blumen und Steine, Büsche, Felsen, Häuser, Laternen und Tafeln. Auf den Baustellen schwenken Baukräne mit Gittermast langsam ihren Ausleger mit der Last, Bagger mit Raupen graben im Takt, Bauarbeiter mit Helm und Warnweste schaufeln. Auf den Tribünen jubeln die Zuschauer. Über der Strecke kreisen Vögel, Seen haben Wellen und einen Schaumrand. Auf dem Start/Ziel-Bogen wehen Zielflaggen, hinter den Tribünen bunte Fahnen, in Paris und New York gehen Passanten auf den Gehsteigen. Nachts blenden die Scheinwerfer, der Fahrer dreht den Kopf in die Kurve. Stösse an Wänden, Bauwerken und anderen Autos hinterlassen Kratzer und Dellen in der Karosserie. In den Kurven liegen Reifenspuren.
- **Berühmte Orte:** In «Paris» fährt man am Abend durch den Triumphbogen, an der Glaspyramide vorbei, über Pflaster am Fluss, über eine Stein- und eine Eisenbrücke und unter dem beleuchteten Eisenturm hindurch, dann hinauf zur Mühle und zur weissen Kuppelkirche. Die Fenster und Laternen leuchten, die Scheinwerfer werfen Licht auf die Strasse. Im «Himalaya» beginnt das Rennen im Bergdorf unter Gebetsfahnen, führt auf Schotter und Schnee in Kehren zum Kloster, über eine Hängebrücke und einen gefrorenen See und steil hinunter, während Schnee fällt. In «Ägypten» startet das Rennen zur Mittagszeit an der Uferstrasse am Nil zwischen Palmen, Lehmhäusern und Marktständen, führt durch ein Tempeltor mit Reliefs, eine Allee mit liegenden Löwen und eine Säulenhalle, an Sphinx und Pyramiden vorbei hinauf auf das Plateau und über Sanddünen mit einem Sprung. In «New York» fährt man nachts auf nassen Strassen durch Häuserschluchten mit beleuchteten Fenstern, über einen Platz voller Leuchtreklamen, über eine Hängebrücke mit Lichterketten, an alten Lagerhäusern am Hafen entlang mit Blick auf die Skyline, über eine Stahlbrücke mit Gitterrost an der Statue mit der Fackel vorbei und durch den Park zurück. Am Strassenrand stehen Taxis, aus Rohren steigt Dampf. Alle Bauwerke sind eigene, vereinfachte Nachbauten aus Grundformen, die Reklamen zeigen nur Farben und Formen.
- **Beläge:** Asphalt, nasser Asphalt, Kopfsteinpflaster, Steinplatten, Schotter, Sand, Schnee, Eis, Holzbohlen und Stahlgitter fahren sich verschieden. Auf Eis dreht das Auto nur zögernd ein, auf nassem Asphalt hält es in Kurven weniger, im Sand, auf Schnee und Schotter ist es etwas langsamer, auf Pflaster, Bohlen und Gitter rüttelt die Federung. Die Bots bremsen vor glatten Stellen früher. Die Werte stehen kommentiert in `CONFIG.belag`.
- **Boost-Felder:** Auf jeder Strecke liegen fünf leuchtende Felder mit wandernden Pfeilen, meist am Ausgang einer Kurve. Wer darüber fährt, bekommt 1 s lang Schub. Auch die Bots steuern sie an. Anzahl, Dauer und Stärke stehen kommentiert in `CONFIG.boostfeld`; eine Strecke kann ihre Felder auch selbst festlegen (`boostfelder`).
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
| Abkürzung | 6 BP | öffnet einen kurzen Weg nur für dich, spart rund 2 s |
| Pylonen | 3 BP | Slalom für alle Fahrer vor dir |
| Schlammloch | 3 BP | bremst auf der halben Fahrbahn |
| Absperrung | 4 BP | sperrt rund 60 % der Breite |
| Umleitung | 6 BP | sperrt an einer Gabelung 20 s lang den kurzen Weg |

Baustellen gelten nur für Fahrer, die beim Bauen vor dir lagen. Für alle anderen sind sie durchsichtig. Sie bauen sich 2 s lang sichtbar auf, stehen nie näher als 3 s Fahrzeit vor einem Betroffenen und lassen immer eine Lücke. Ein Treffer bremst, hält aber nie an, danach ist man 3 s geschützt.

## Bestenliste

Jede Strecke hat eine Bestenliste mit der schnellsten Runde: eine Gesamtliste und eine Liste für jedes der 8 Autos. Im Hauptmenü unter «Bestenlisten» wechselt man mit ◀ ▶ die Strecke und die Liste.

- **Was zählt:** die schnellste Runde, nicht die Gesamtzeit, weil die Rundenzahl einstellbar ist. Jede fertig gefahrene Runde zählt, auch wenn das Rennen danach abgebrochen wird. Alle Modi zählen: gegen Bots, Split-Screen und online. Simulationen und der Debug-Modus (`?debug=1`) zählen nicht.
- **Menschen:** Jeder steht mit seinem Namen da, und zwar nur einmal pro Liste mit seiner besten Zeit (Gross- und Kleinschreibung zählt nicht). In die gemeinsame Liste kommen neue Zeiten nur von Spielern, die mit Google angemeldet sind, immer unter ihrem eigenen Spielnamen und mit grünem Häkchen (siehe «Mit Google anmelden»). In der Liste eines Autos steht die beste Zeit mit diesem Auto.
- **Bots:** Pro Liste steht nur ein einziger Bot drin, der schnellste aller Zeiten: in der Gesamtliste der schnellste Bot auf dieser Strecke, in der Liste eines Autos der schnellste Bot mit diesem Auto. Er ist mit einem Symbol und «Bot» markiert und steht auf dem Platz, der zu seiner Zeit passt. Fährt ein Bot schneller, ersetzt er den alten.
- **Anzeige:** Die ersten drei Plätze sind in Gold, Silber und Bronze markiert, zu jedem Eintrag stehen Auto und Datum. In der Streckenwahl stehen der Rundenrekord und die ersten drei, im Rennen steht der Rekord unter der Rundenzeit. Bei einer neuen Bestzeit erscheint kurz «Neuer Rekord!», «Rekord mit dem Rennwagen!» oder «Platz 3 in der Bestenliste». Im Ergebnis steht, wer neu in der Liste ist, die neuen Einträge sind hervorgehoben.
- **Name:** Heisst man noch «Spieler», fragt das Spiel nach dem ersten Eintrag einmal nach dem Namen. Ändern geht wie bisher im Menü. Ein neuer Name gilt für neue Einträge, alte behalten ihren Namen.
- **Alle Spieler:** Ist eine Datenbank eingetragen (siehe «Gemeinsame Bestenliste einrichten»), zeigt die Bestenliste die Zeiten von allen Geräten. Jedes Gerät lädt nur die Zeiten seiner eigenen Spieler hoch: gegen Bots und im Split-Screen alle am Gerät, online jeder seine eigenen. Bot-Zeiten lädt das Gerät hoch, das das Rennen leitet (online der Host). Hochladen kann nur ein angemeldetes Gerät, und nur Name, Rundenzeit, Auto, Strecke, Bot-Stärke, Datum und die Konto-Nummer, sonst nichts. Im Split-Screen kommt nur Spieler 1 mit dem Konto in die gemeinsame Liste, die anderen bleiben in der Liste des Geräts.
- **Gleiche Regeln für alle Geräte:** Jedes Konto steht pro Liste einmal mit seiner besten Zeit, egal auf welchem Gerät sie gefahren wurde, auch wenn es seinen Namen geändert hat. Einträge aus der Zeit ohne Anmeldung (bis 18.11.2026) zählen wie früher nach Namen und stehen ohne Häkchen da, bis ihre Strecke umgebaut ist. Pro Liste steht ein Bot, der schnellste von allen Geräten.
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
- **Häkchen:** In der Bestenliste tragen Einträge angemeldeter Spieler ein grünes Häkchen. Ein Konto steht einmal da, auch wenn es seinen Namen geändert hat. Die bisherigen Einträge (Liste `v1`, ohne Anmeldung) bleiben sichtbar, ohne Häkchen, bis ihre Strecke umgebaut ist. Ohne Anmeldung steht bei der gemeinsamen Liste und im Ergebnis ein kurzer Hinweis mit dem Knopf.
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

Damit die Autos trotz ihrer Eigenheiten gleich stark sind, sind Höchsttempo und Lenkung jedes Autos zusätzlich um wenige Prozent fein abgestimmt (`CONFIG.fahrzeuge`). Die Limousine hat einen 2,5-fachen statt 4-fachen Windschatten, weil sie sonst zu oft führte und dann doch verlor. Am Bergpass gewann der starke Bot damals mit 45 % etwas seltener als das Ziel von 50 %. Seit dem 17.11.2026 ist «Schwer» viel stärker und gewinnt 97 bis 100 % (siehe «Schwer»-Bots). Mit den alten Pylonen-Werten (`bots.pylonen` 1, Pylonen 2 BP, `bots.schlammSparen` 0) gehen Rennen mit 8 «Mittel»-Bots genau gleich aus wie vor der Pylonen-Änderung (36 von 36 Vergleichsrennen mit gleichem Zufall). Fahrphysik und Fahren der Bots sind also unverändert, anders ist nur, was sie bauen.

Selbst nachmessen: `index.html?sim=200` öffnen (dauert einige Minuten). Die Siegquote pro Auto zeigt diese Seite noch nicht an, sie stammt aus meiner Mess-Reihe.

## «Schwer»-Bots

Ein «Schwer»-Bot fährt wie ein Profi: perfekte Linie ohne Zufallsfehler, späte Bremspunkte, Drift schon in sanfteren Kurven (mit Mini-Turbo), jedes Boost-Feld, sieht jedes Hindernis rechtzeitig und hat keine schlechten Tage. Er nutzt dieselbe Fahrphysik wie der Spieler und hat zusätzlich 3 % mehr Höchsttempo (`CONFIG.bots.stufen.schwer.tempo`, höchstens erlaubt sind 3 %). «Leicht» und «Mittel» sind unverändert.

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

«Ultra» ist die Stufe über «Schwer», wählbar gegen Bots, im Split-Screen und online («Ultra · unschlagbar»). Ein «Ultra»-Bot fährt mit derselben Fahrphysik wie der Spieler, so gut es diese erlaubt: Kurventempo, Bremspunkte und Drift sind pro Strecke mit dem Optimierer gesucht (`tools/ultra.js`, mit vier verschiedenen Autos geprüft, damit sie für jedes Auto passen). Er macht keine Fehler, nimmt jedes Boost-Feld mit, sieht jedes Hindernis und hat 8 % mehr Höchsttempo (`CONFIG.bots.stufen.ultra.tempo`), am Himalaya 12 % (`CONFIG.bots.stufen.ultra.strecken.himalaya.tempo`, siehe unten). Er holt nicht künstlich auf. Seine Baupunkte gibt er vor allem für sich selbst aus (Abkürzung, Rampe), Hindernisse baut er selten und Pylonen nie.

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

**Volltest mit 22 Menschen im Browser:** 22 Browserfenster auf einem Rechner (Host und 21 Gäste, dazu 11 Bots, Paris, 1 Runde) über einen lokalen Vermittlungsserver. Alle 22 traten der Lobby bei und waren 5 s nach «Rennen starten» im Rennen, alle 21 Gäste kamen ins Ergebnis, und alle 22 sahen dieselbe Ergebnisliste mit 33 Zeilen. In den ersten 15 Sekunden, wenn das ganze Feld dicht beisammen fährt und darum fast jedes Auto zu den 10 nächsten gehört, kamen pro Gast 30,6 KB/s an (knapp über dem Ziel) und der Host schickte zusammen 643 KB/s. Verteilt sich das Feld, sinkt es auf die Werte der Tabelle.

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
| `bots.stufen.ultra` | `tempo` 1,08 (Himalaya 1,12), `strecken`, `hindernisse` 0,15, `pylonen` 0, `umsichtig` | 8 % Tempo-Vorteil, am Himalaya 12 %, Fahr-Einstellungen pro Strecke vom Optimierer, baut nur selten Hindernisse und nie Pylonen, weicht vorausschauend aus |
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
- «Ultra» hat 8 % Tempo-Vorteil (die Grenze aus dem Auftrag), nur am Himalaya 12 % (entschieden am 17.11.2026, weil er dort mit 8 % nur 91 % der Rennen gegen «Schwer» gewann). Den Rest holt er nur mit Fahrkönnen: Die Einstellungen pro Strecke stammen aus derselben Suche wie beim Optimierer, nur mit Tempo-Vorteil und mit vier Autos geprüft.
- «Ultra» baut fast nur für sich selbst (Abkürzung, Rampe). Hindernisse für andere baut er in rund jedem siebten Fall, in dem ein anderer Bot eines bauen würde, Pylonen nie.
- Pylonen: Bots setzen sie noch in 40 % der Fälle wie früher (`CONFIG.bots.pylonen` 0,4). Mit dem höheren Preis von 3 BP kommt das zusammen auf rund 0,2 Pylonen pro Rennen statt 14 bis 16. Menschen bauen wie bisher.
- Ohne weitere Regel hätten die Bots die gesparten Punkte fast ganz in Schlammlöcher gesteckt (doppelt so viele wie vorher). Darum heben sie in der Hälfte dieser Fälle ihre Punkte auf (`CONFIG.bots.schlammSparen`).
- In der Bestenliste steht pro Liste nur der schnellste Bot. Das ist jetzt meistens ein «Ultra»-Bot («Bot · Ultra»), so ist es gewollt.
- **Anmelden (18.11.2026):** im Popup-Fenster statt mit Weiterleitung, weil die Weiterleitung auf `popc-u.github.io` mit der Firebase-Adresse als Anmeldeseite in vielen Browsern nicht mehr klappt. Ein Name gehört dem Konto, das ihn zuerst wählt. Die alte Liste bleibt lesbar und sichtbar (ohne Häkchen), bis ihre Strecke umgebaut ist, dann beginnt dort eine neue Liste. Bot-Zeiten kommen nur noch von angemeldeten Geräten, die das Rennen leiten. Für alle Strecken gilt in der Datenbank dieselbe Mindestzeit von 20 s, das Spiel selbst prüft weiter die genaue Mindestzeit jeder Strecke.

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
- **Umleitung kurz nach der Abzweigung:** Wird eine Umleitung gebaut, wenn ein Bot gerade an ihrer Abzweigung vorbei ist, lenkt er bei «Leicht», «Mittel» und «Schwer» trotzdem noch in den Nebenweg und fährt in die Wand. Das kostet einige Sekunden und kommt selten vor. Bei «Ultra» ist es behoben, bei den anderen Stufen nicht, damit sie genau gleich fahren wie vorher.
- **Mit Google anmelden:** Die Anmeldung ist gegen die Firebase-Emulatoren getestet (Regeln, Namenswahl, Hochladen, Abmelden, alle Fehlermeldungen), das echte Google-Fenster konnte ich in meiner Testumgebung nicht öffnen. Der echte Test ist die Prüfliste unter «Mit Google anmelden». Wer angemeldet ist und sich auskennt, kann weiterhin eine erfundene Zeit über 20 s schicken, aber nur unter seinem eigenen Konto: Solche Einträge findest du über die Konto-Nummer und kannst das Konto sperren.
- **Gemeinsame Bestenliste:** Solange keine Datenbank eingetragen ist, hat jedes Gerät nur seine eigene Liste (wie bisher). Die Anbindung an Firebase ist nur gegen einen nachgebauten Ersatz-Server mit denselben Regeln getestet, weil die Test-Umgebung das Internet nicht erreicht. Der echte Test sind zwei Geräte (siehe «Gemeinsame Bestenliste einrichten», Schritt 6). Schummeln lässt sich ohne eigenen Server nicht ganz verhindern: Wer sich auskennt, kann eine erfundene Zeit über der Mindestzeit schicken. Solche Einträge löschst du in der Firebase-Konsole. Gleicher Name heisst gleiche Person, auch auf verschiedenen Geräten: Zwei Leute mit demselben Namen teilen sich einen Platz. Die Liste kann jeder lesen, der die Adresse kennt, darum besser Spitznamen statt voller Namen. Wer die Website-Daten im Browser löscht, löscht die Liste des Geräts und noch nicht hochgeladene Zeiten, die gemeinsame Liste bleibt.

## Für Bastler

- `index.html?debug=1` zeigt Messwerte und Bauplätze.
- `index.html?sim=200` lässt 200 Bot-Rennen laufen und zeigt die Auswertung.
