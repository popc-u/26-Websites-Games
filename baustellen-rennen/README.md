# Baustellen-Rennen

Ein 3D-Kartrennen im Low-Poly-Stil für den Browser. Die Besonderheit: Es gibt keine Zufalls-Items. Wer hinten liegt, sammelt Baupunkte (BP) und baut damit die Strecke um, mit Rampen und Abkürzungen für sich selbst oder Baustellen gegen die Fahrer davor.

Das ganze Spiel steckt in einer einzigen Datei: `index.html`.

## Starten

`index.html` doppelklicken (Chrome, Edge, Firefox oder Safari). Es braucht eine Internetverbindung, weil three.js 0.160.0 von einem CDN geladen wird (für Online-Spiele zusätzlich PeerJS 1.5.4). Sonst ist nichts zu installieren.

- **Gegen Bots:** 1 Spieler und bis zu 7 Bots, Stufe leicht, mittel, schwer oder ultra (praktisch unschlagbar).
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
- **Menschen:** Jeder steht mit dem Namen da, den er für sich eingegeben hat, und zwar nur einmal pro Liste mit seiner besten Zeit (Gross- und Kleinschreibung zählt nicht). In der Liste eines Autos steht die beste Zeit mit diesem Auto.
- **Bots:** Pro Liste steht nur ein einziger Bot drin, der schnellste aller Zeiten: in der Gesamtliste der schnellste Bot auf dieser Strecke, in der Liste eines Autos der schnellste Bot mit diesem Auto. Er ist mit einem Symbol und «Bot» markiert und steht auf dem Platz, der zu seiner Zeit passt. Fährt ein Bot schneller, ersetzt er den alten.
- **Anzeige:** Die ersten drei Plätze sind in Gold, Silber und Bronze markiert, zu jedem Eintrag stehen Auto und Datum. In der Streckenwahl stehen der Rundenrekord und die ersten drei, im Rennen steht der Rekord unter der Rundenzeit. Bei einer neuen Bestzeit erscheint kurz «Neuer Rekord!», «Rekord mit dem Rennwagen!» oder «Platz 3 in der Bestenliste». Im Ergebnis steht, wer neu in der Liste ist, die neuen Einträge sind hervorgehoben.
- **Name:** Heisst man noch «Spieler», fragt das Spiel nach dem ersten Eintrag einmal nach dem Namen. Ändern geht wie bisher im Menü. Ein neuer Name gilt für neue Einträge, alte behalten ihren Namen.
- **Alle Spieler:** Ist eine Datenbank eingetragen (siehe «Gemeinsame Bestenliste einrichten»), zeigt die Bestenliste die Zeiten von allen Geräten. Jedes Gerät lädt nur die Zeiten seiner eigenen Spieler hoch: gegen Bots und im Split-Screen alle am Gerät, online jeder seine eigenen. Bot-Zeiten lädt das Gerät hoch, das das Rennen leitet (online der Host). Hochgeladen werden nur Name, Rundenzeit, Auto, Strecke, Bot-Stärke und Datum, sonst nichts. Den Namen «Spieler» lädt das Spiel nicht hoch, es fragt zuerst nach dem richtigen Namen.
- **Gleiche Regeln für alle Geräte:** Jeder Name steht pro Liste einmal mit seiner besten Zeit, egal auf welchem Gerät sie gefahren wurde (gleicher Name heisst gleiche Person). Pro Liste steht ein Bot, der schnellste von allen Geräten.
- **Aktualisieren:** Die Liste wird beim Öffnen der Bestenliste und der Streckenwahl frisch geladen (höchstens einmal pro Minute), der Knopf «Aktualisieren» lädt sofort. Die Zeile über der Liste zeigt den Stand, zum Beispiel «Alle Spieler · Stand 14:05» oder «Keine Verbindung: nur dieses Gerät». Mit «Zeigen: Alle Spieler / Dieses Gerät» wechselt man zwischen der gemeinsamen Liste und der Liste des Geräts. Eigene neue Zeiten stehen sofort drin, auch bevor sie hochgeladen sind, und bleiben hervorgehoben. Den Rekord in der Streckenwahl und im Rennen nimmt das Spiel aus der gemeinsamen Liste, geladen vor dem Rennstart, nie während des Rennens.
- **Ohne Verbindung:** Das Spiel läuft wie gewohnt mit der Liste des Geräts. Zeiten, die noch nicht hochgeladen sind, merkt sich das Gerät und lädt sie beim nächsten Mal hoch, die Stand-Zeile zeigt, wie viele warten. Langsame, fehlende oder kaputte Antworten führen nie zu einem Fehler: Nach 6 s gilt «Keine Verbindung».
- **Bisherige Zeiten:** Beim ersten Start mit eingetragener Datenbank lädt jedes Gerät seine bisherigen eigenen Zeiten einmal hoch.
- **Schutz:** Namen erscheinen immer als Text. Namen mit unerwünschten Wörtern (Liste in `CONFIG.bestenliste.verboten`) werden weder hochgeladen noch gezeigt. Runden unter der Mindestzeit einer Strecke (Streckenlänge geteilt durch das doppelte Höchsttempo, zum Beispiel 23,2 s in der Kiesgrube) lehnt die Datenbank ab und das Spiel zeigt sie nicht. Ganz verhindern lässt sich Schummeln ohne eigenen Server nicht (siehe «Bekannte Grenzen»), falsche Einträge kannst du in der Datenbank löschen.
- **Speichern:** Die Liste des Geräts liegt im Browser, getrennt von den Einstellungen. Online gefahrene Rennen tragen dort die Zeiten aller Mitspieler ein. In einem privaten Fenster gilt sie nur bis zum Neuladen. Unter «Einstellungen» löscht «Bestenliste löschen» eine Strecke oder alle, aber nur auf diesem Gerät, die gemeinsame Liste bleibt. Ohne eingetragene Datenbank verhält sich alles wie bisher: Jedes Gerät hat nur seine eigene Liste.

## Gemeinsame Bestenliste einrichten

Damit alle Geräte dieselbe Liste sehen, braucht das Spiel eine kleine Online-Datenbank. Gewählt habe ich die **Firebase Realtime Database** von Google: Der Gratis-Tarif «Spark» braucht keine Kreditkarte und pausiert nicht, wenn eine Woche niemand spielt. Das Spiel erreicht die Datenbank direkt mit `fetch`, ohne zusätzliche Bibliothek, von GitHub Pages, itch.io, Netlify und per Doppelklick. Regeln in der Datenbank legen fest, was erlaubt ist, und in der Firebase-Konsole kannst du Einträge löschen. Der Gratis-Tarif reicht weit (1 GB Speicher, 10 GB Download pro Monat, ein Eintrag hat rund 100 Byte). Nicht gewählt habe ich Supabase, weil Gratis-Projekte nach einer Woche ohne Nutzung pausieren, und einfache JSON-Speicher ohne Regeln, weil dort jeder alles löschen könnte.

Das machst du einmal, es dauert rund 10 Minuten:

1. **Konto:** https://console.firebase.google.com öffnen und mit einem Google-Konto anmelden.
2. **Projekt:** «Projekt erstellen» (englisch «Create a project») wählen, als Namen zum Beispiel `baustellen-rennen` eingeben und den Bedingungen zustimmen. Google Analytics brauchst du nicht, schalte es aus. Dann «Projekt erstellen» und warten, bis es fertig ist.
3. **Datenbank:** Links im Menü unter «Build» (oder «Erstellen») auf «Realtime Database» klicken, dann «Datenbank erstellen». Als Standort «Belgien (europe-west1)» wählen, dann «Im gesperrten Modus starten» und «Aktivieren». Wichtig: «Realtime Database», nicht «Firestore».
4. **Regeln:** Oben den Reiter «Regeln» öffnen, den ganzen Text dort löschen, den Text unten («Regeln zum Kopieren») einfügen und auf «Veröffentlichen» klicken.
5. **Adresse:** Im Reiter «Daten» steht oben die Adresse der Datenbank, zum Beispiel `https://baustellen-rennen-default-rtdb.europe-west1.firebasedatabase.app/`. Schick mir diese Adresse, dann trage ich sie ein. Sie ist nicht geheim: Sie steht später im Spiel, so wie die Zugangsdaten des Umweg-Servers, geschützt wird die Datenbank durch die Regeln. Selbst eintragen geht auch: `index.html` mit einem Texteditor öffnen, nach `server: ''` suchen und die Adresse zwischen die beiden Anführungszeichen schreiben, also `server: 'https://…firebasedatabase.app',`. Speichern und die Datei wie gewohnt hochladen.
6. **Prüfen:** Das Spiel öffnen und «Bestenlisten» wählen. Über der Liste steht nach einem Moment «Alle Spieler · Stand …». Steht dort «Keine Verbindung», stimmt die Adresse nicht oder die Regeln fehlen. Nach einer gefahrenen Runde erscheint in Firebase im Reiter «Daten» unter `bestenliste` → `v1` → Strecke ein neuer Eintrag. Dann auf einem zweiten Gerät (zum Beispiel dem Handy) eine Runde auf derselben Strecke fahren: Nach «Aktualisieren» müssen auf beiden Geräten beide Namen stehen.
7. **Einträge löschen:** Im Reiter «Daten» `bestenliste` → `v1` → die Strecke aufklappen. Jeder Eintrag hat eine lange Kennung (zum Beispiel `-NxYz…`) und darin `n` (Name), `z` (Zeit in Sekunden), `a` (Auto), `b` (Bot ja oder nein), `s` (Bot-Stärke) und `d` (Datum). Mit der Maus auf den Eintrag zeigen und auf das Löschen-Zeichen (✕ oder Papierkorb) klicken. Jede Verbesserung ist ein eigener Eintrag, ein Name kann also mehrmals vorkommen: Bei einem Schummler alle seine Einträge löschen. In der Konsole darfst du löschen, die Regeln gelten nur für das Spiel. Auf dem Gerät, auf dem die Zeit gefahren wurde, bleibt sie in dessen eigener Liste, bis man sie dort unter «Einstellungen» löscht.

**Regeln zum Kopieren** (die Mindestzeit jeder Strecke rechnet das Spiel selbst aus):

```json
{
  "rules": {
    ".read": false,
    ".write": false,
    "bestenliste": {
      "v1": {
        "$strecke": {
          ".read": true,
          "$eintrag": {
            ".write": "!data.exists() && newData.exists()",
            ".validate": "newData.hasChildren(['n', 'z', 'a', 'b', 'd'])",
            "n": {
              ".validate": "newData.isString() && newData.val().length >= 1 && (newData.val().length <= 14 || (newData.val().length <= 20 && newData.parent().child('b').val() === true))"
            },
            "z": {
              ".validate": "newData.isNumber() && newData.val() <= 600 && (($strecke === 'kiesgrube' && newData.val() >= 23.2) || ($strecke === 'bergpass' && newData.val() >= 21.5) || ($strecke === 'paris' && newData.val() >= 23.4) || ($strecke === 'himalaya' && newData.val() >= 22.8) || ($strecke === 'aegypten' && newData.val() >= 24.6) || ($strecke === 'newyork' && newData.val() >= 22.7))"
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
            "d": {
              ".validate": "newData.val() === now"
            },
            "$anderes": {
              ".validate": false
            }
          }
        }
      }
    }
  }
}
```

Was die Regeln erlauben: Lesen darf jeder, schreiben nur neue Einträge, ändern und löschen niemand (ausser dir in der Konsole). Ein Eintrag braucht genau diese Felder: Name mit 1 bis 14 Zeichen (Bots bis 20), Zeit als Zahl zwischen der Mindestzeit der Strecke und 600 s, eines der 8 Autos, Bot ja oder nein, die Bot-Stärke und das Datum vom Server. Alles andere lehnt die Datenbank ab. Kommt eine neue Strecke dazu, braucht es neue Regeln, die liefere ich dann mit.

## Online spielen

1. Der Host wählt «Online: Raum erstellen» und bekommt einen Code mit 5 Zeichen.
2. Mit «Link kopieren» schickt er den Einladungslink (`…/index.html?raum=CODE`) an die Mitspieler. Der Link funktioniert, sobald das Spiel im Internet liegt. Wer die Datei lokal öffnet, wählt «Online: Raum beitreten» und tippt den Code ein.
3. Alle wählen Name, Fahrzeug und Farbe und drücken «Bereit». Der Host stellt Strecke, Runden und Bots ein und startet.

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

Der frühere Gratis-Umweg-Server von PeerJS ist abgeschaltet. Im Spiel ist darum ein eigener Gratis-Zugang bei Metered eingetragen (Plan «Free Trial», 500 MB pro Monat, das reicht für grob 50 bis 100 Rennen mit einem Gast über den Umweg). Ist das Kontingent aufgebraucht, klappt das Online-Spiel bis zum nächsten Monat nur in Netzen, die direkte Verbindungen zulassen. Den Verbrauch zeigt das Dashboard von Metered. So richtest du einen eigenen Zugang ein:

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
| `bau.maxSchlenker` | 4 m | Sperren stehen so, dass die Ideallinie höchstens so weit im gesperrten Teil liegt |
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
| `grafik.delle` | ab 3 m/s, höchstens 0,13 m | Dellen nach Stössen |
| `bestenliste` | `proName` 1, `zeigen` 10, `speichern` 50, `minRunde` 8 s | Zeiten pro Name und Liste, sichtbare und gespeicherte Plätze, kürzeste gültige Runde |
| `bestenliste.server` | Firebase-Datenbank «baustellen-rennen» (Belgien) | Adresse der gemeinsamen Datenbank, leer heisst: jedes Gerät hat nur seine eigene Liste |
| `bestenliste.zeitlimit`, `frisch`, `nochmals` | 6 s, 60 s, 15 s | Wartezeit auf die Datenbank, so lange gilt eine geladene Liste, neuer Versuch nach einem Fehler |
| `bestenliste.mindestTempo`, `verboten` | 2, 10 Wörter | Mindestzeit = Streckenlänge ÷ (2 × Höchsttempo), unerwünschte Wörter in Namen |

## Entscheidungen, die ich getroffen habe

- Höchstens 8 Fahrer pro Rennen.
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

## Bekannte Grenzen

- **Stand des Grafik-Auftrags (17.11.2026):** Fertig sind die «Schwer»-Bots, die Grafik-Grundlage (Nachbearbeitung, Himmel mit Wolken, Sonnenblendung, Stufe «Ultra» mit automatischer Wahl), leuchtende und blendende Lichter, Dellen nach Stössen, der Fahrerkopf und eine einfache Fassung der Autos für die Ferne, der Tacho mit Nadel und die Minikarte mit Höhenschatten, Gras, Blumen, Steine, Bäume im Wind, Vögel, Seen mit Wellen und Schaumrand, jubelnde Zuschauer, Bauarbeiter, Passanten in Paris und New York, wehende Fahnen, Baukräne mit Gittermast und grabende Bagger, der Steckbrief in der Streckenwahl und das Siegerpodest. Noch offen sind: feinere Karosserien (Rundungen, Fugen, Lufteinlässe), Ort für Ort feinere Sehenswürdigkeiten, fahrender Verkehr im Hintergrund, Regen, Vorschaubilder der Strecken als gerenderte Bilder, und das neue Aussehen von Garage, Lobby, Ladebild und Handy-Ansicht.
- Die Autos bestehen aus einfachen Flächen. Sie sind klar unterscheidbar und haben Felgen, leuchtende Lichter, getönte Scheiben, Spoiler, Spiegel und Auspuff, sehen aber nicht fotorealistisch aus.
- Ton lässt sich in der Test-Umgebung nicht anhören. Geprüft ist, dass alle Klänge ohne Fehler laufen, abgehört hat sie noch niemand.

- Der Online-Modus ist mit zwei Browsern gegen einen lokalen Vermittlungsserver getestet (Lobby, Rennen, Ergebnis, Revanche, Bot-Übernahme), ebenso die Fehlerfälle beim Beitritt (falscher Code, Host antwortet nicht, Netz blockiert, Vermittler nicht erreichbar). Über den öffentlichen PeerJS-Server im echten Internet konnte ich ihn in meiner Testumgebung nicht ausprobieren. Ein erster Versuch mit zwei Geräten scheiterte am 13.11.2026 beim Beitritt. Die Ursache ist noch offen, die Diagnose-Zeile unter der Fehlermeldung soll sie zeigen. Zwischen Geräten in verschiedenen Netzen braucht es manchmal einen TURN-Server, und die mitgelieferten von PeerJS sind nicht immer erreichbar.
- Die Bildrate ist nur mit Software-Grafik geprüft. Ruckelt es auf einem Gerät, hilft die Grafikstufe «Niedrig».
- Die Touch-Steuerung ist eingebaut, aber nicht getestet.
- Einen Grand-Prix-Modus gibt es nicht.
- Bots bauen selten Umleitungen und Abkürzungen, weil die Punkte knapp sind.
- three.js 0.160.0 schreibt eine harmlose Warnung in die Browser-Konsole.
- **Umleitung kurz nach der Abzweigung:** Wird eine Umleitung gebaut, wenn ein Bot gerade an ihrer Abzweigung vorbei ist, lenkt er bei «Leicht», «Mittel» und «Schwer» trotzdem noch in den Nebenweg und fährt in die Wand. Das kostet einige Sekunden und kommt selten vor. Bei «Ultra» ist es behoben, bei den anderen Stufen nicht, damit sie genau gleich fahren wie vorher.
- **Gemeinsame Bestenliste:** Solange keine Datenbank eingetragen ist, hat jedes Gerät nur seine eigene Liste (wie bisher). Die Anbindung an Firebase ist nur gegen einen nachgebauten Ersatz-Server mit denselben Regeln getestet, weil die Test-Umgebung das Internet nicht erreicht. Der echte Test sind zwei Geräte (siehe «Gemeinsame Bestenliste einrichten», Schritt 6). Schummeln lässt sich ohne eigenen Server nicht ganz verhindern: Wer sich auskennt, kann eine erfundene Zeit über der Mindestzeit schicken. Solche Einträge löschst du in der Firebase-Konsole. Gleicher Name heisst gleiche Person, auch auf verschiedenen Geräten: Zwei Leute mit demselben Namen teilen sich einen Platz. Die Liste kann jeder lesen, der die Adresse kennt, darum besser Spitznamen statt voller Namen. Wer die Website-Daten im Browser löscht, löscht die Liste des Geräts und noch nicht hochgeladene Zeiten, die gemeinsame Liste bleibt.

## Für Bastler

- `index.html?debug=1` zeigt Messwerte und Bauplätze.
- `index.html?sim=200` lässt 200 Bot-Rennen laufen und zeigt die Auswertung.
