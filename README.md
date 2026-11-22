# Springerle-Formen-Generator

Ein kleines Browser-Tool, das aus einem Bild oder einer Skizze eine **Springerle-Backform** entwirft. Das Ergebnis ist eine gespiegelte Tiefenkarte (PNG) oder eine druckfertige **STL-Datei** für den 3D-Druck, wahlweise mit einem von **sechs Rändern**.

Das Tool besteht aus einer einzigen Datei (`index.html`) und läuft komplett lokal im Browser. Es braucht keine Installation, keinen Server und keine Internetverbindung. Dein Bild wird nirgendwohin hochgeladen.

## Verwendung

1. `index.html` im Browser öffnen (Doppelklick genügt).
   Alternativ per **GitHub Pages** veröffentlichen: *Settings → Pages → Branch `main` → `/ (root)`*.
2. Ein eigenes Bild wählen oder den **Beispiel-Fuchs** laden.
3. Format, Tiefe, Schwelle, Tiefenstufen und Glättung einstellen.
4. Einen der drei Ränder wählen.
5. Ergebnis prüfen: links die **gespiegelte Form** (dunkel = tief), rechts eine **Vorschau des Gebäcks**.
6. Exportieren:
   - **Tiefenkarte (PNG)**, 25 Pixel pro mm, für CNC-Fräsen, Schnitzvorlagen oder Heightmap-Import
   - **STL Form (Negativ)** zum direkten Drucken
   - **STL Positiv (Gießvorlage)** zum Abformen in Silikon

## Die sechs Ränder

| Rand | Beschreibung |
|---|---|
| **A · Doppellinie** | zwei feine, umlaufende Linien (0,6 und 0,35 mm), angelehnt an historische Model |
| **B · Perlrand** | Kette runder Mulden (Ø 1,2 mm, Abstand 2 mm) mit größeren Eckperlen |
| **C · Zackenband** | Kerbschnitt-Band aus kleinen Dreiecken zwischen zwei feinen Linien |
| **D · Wellenband** | fließende Wellenlinie (Ranke) zwischen zwei feinen Rahmenlinien |
| **E · Rautenband** | Kette kleiner Rauten aus sich kreuzenden Zickzacklinien |
| **F · Bogenfries** | Reihe kleiner Bögen mit Punkt (Girlande) unter der äußeren Linie |

Der äußere Rand dient beim Backen zugleich als Orientierung für die Schnittlinie.

## Einstellungen

| Regler | Wirkung |
|---|---|
| Breite / Höhe | Größe der Form in mm |
| Max. Tiefe | Tiefe der tiefsten Stelle (2–8 mm), nach Quellen sind ca. 4–5 mm üblich |
| Schwelle | ab welcher Dunkelheit eine Linie oder Fläche in die Tiefe geht |
| Tiefenstufen | 3 bis 32 (32 = stufenlos) |
| Wandschräge | neigt alle Wände (Winkel zur Senkrechten, Standard 12°), damit sich der Teig löst. Dünne Linien werden dadurch V-förmig und flacher, breite Flächen behalten die volle Tiefe. 0 = aus |
| Glättung | rundet Kanten, damit sich der Teig löst. Klein halten für filigrane Motive |
| Motiv hell / Grund dunkel | kehrt die Helligkeit des Bildes um |
| Mesh-Auflösung | Feinheit der STL (6, 8 oder 10 px/mm) |
| Sockel | Restdicke unter der tiefsten Stelle (STL), Standard 1,2 mm. Gesamtdicke = Sockel + Tiefe. Dünner spart Druckmaterial |

## Was eine gute Springerle-Form ausmacht

Die Voreinstellungen des Tools beruhen auf diesen Kriterien:

- **Negativform, spiegelverkehrt:** Was im Holz vertieft ist, wird auf dem Gebäck erhaben. Schrift und Motiv müssen gespiegelt sein.
- **Tiefer als bei flachen Gebäckformen:** Das Relief muss deutlich ausgeprägt sein. Die tiefste Stelle liegt dort, wo das Motiv am vollsten ist.
- **Keine Hinterschnitte, glatte und runde Mulden:** Sonst bleibt der Teig hängen. Das Tool neigt deshalb alle Wände um einen einstellbaren Winkel.
- **Klare Silhouette und feine Details:** Historische Model sind filigran. Die Linien dürfen sehr fein sein (ab ca. 0,3 mm in diesem Tool).
- **Rand oder Rahmen:** Doppellinien und Ornamentbänder geben dem Motiv Halt.
- **Holz mit kurzen Fasern**, etwa Birnbaum, wenn die Form geschnitzt wird.
- **Typische Größe:** ca. 4–10 cm Kantenlänge.

## 3D-Druck

- STL **flach drucken, Relief nach oben**.
- **Material sparen:** Sockel dünn halten (Standard 1,2 mm), wenig Füllung (ca. 10–15 %) und 2–3 Wände genügen.
- Für sehr feine Linien ist ein **Harzdrucker** oder eine **0,2-mm-Düse** besser geeignet als eine 0,4-mm-Düse. Schichthöhe etwa 0,1–0,15 mm.
- **Lebensmittelsicherheit:** 3D-gedruckte Oberflächen sind porös, in feinen Details können sich Reste festsetzen. Harz ist meist nicht lebensmittelgeeignet.
  Sicherere Variante: das **Positiv** drucken, davon eine Form aus **lebensmittelechtem Silikon** gießen und diese verwenden.
- Form vor jedem Gebrauch mit Mehl oder Stärke bestäuben, von Hand lauwarm abwaschen, nicht in die Spülmaschine.
- Vor dem Backen einen **Probeabdruck in Knetmasse** machen.

## Grenzen

- Das Tool rechnet Helligkeit in Tiefe um. Es erkennt keine Motive und ergänzt keine Details. Strichzeichnungen mit dunklen Linien auf hellem Grund funktionieren am besten, Fotos nur eingeschränkt.
- Die Maße der Ränder und die Tiefenwerte sind Richtwerte und sollten mit einem Testabdruck überprüft werden.
- Der Beispiel-Fuchs ist eine einfache, selbst gezeichnete Grafik und dient nur als Demo.

## Technik

Reines HTML, CSS und JavaScript ohne Abhängigkeiten. Die Tiefenkarte entsteht mit der Canvas-API. Die STL wird als Binär-STL direkt im Browser erzeugt (geschlossenes Mesh mit Sockel). Läuft in aktuellen Versionen von Chrome, Firefox, Edge und Safari. Für große STL-Dateien (Mesh-Auflösung 10 px/mm) wird etwas Arbeitsspeicher benötigt.

## Lizenz

MIT, siehe [LICENSE](LICENSE).

---

## Hinweis zu Claude

Dieses Projekt, einschließlich des Codes und dieser README, wurde mit Unterstützung von **Claude** (KI-Assistent von Anthropic) erstellt. Der Inhalt ist KI-generiert und wurde nicht umfassend geprüft. Bitte prüfe Ergebnisse, insbesondere Maße, Tiefen und exportierte STL-Dateien, vor der Verwendung selbst. Für Lebensmittelsicherheit, Materialwahl und Druckergebnisse übernimmt das Projekt keine Gewähr, die Verantwortung liegt bei den Nutzern.
