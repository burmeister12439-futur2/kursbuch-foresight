# Kursbuch Foresight · Entwicklungsagenda

**Zielpfad im Repository:** `ENTWICKLUNGSAGENDA.md`  
**Entwicklungsphase:** **Kursbuch Foresight · Entwicklungsphase 2 – Atlas & Design**  
**Status:** verbindliche Entwicklungsagenda · aktiviert 29.08.2026

> **Ausgangspunkt:** `RGI-20260827-B` · **FREIGEGEBEN**
>
> Dieser Stand wird nicht still verändert.
>
> Dieses Dokument beschreibt ausschließlich die Entwicklung **nach** dem freigegebenen Rundgang.

---

## 1. Zweck dieser Agenda

Die Entwicklungsagenda ist die verbindliche Brücke zwischen dem freigegebenen Rundgang und der nächsten Entwicklungsphase des Kursbuchs.

Sie beantwortet fünf Fragen:

1. Was steht und wird nicht erneut geöffnet?
2. Welche Entwicklungsfelder sind noch offen?
3. Welches unsichtbare Fundament braucht der offene Atlas?
4. Was ist das Ziel der Entwicklungsphase 2?
5. Wie arbeiten Klaus, HAL und Claude dabei zusammen?

Sie ersetzt keine Build-Dokumentation und kein technisches Abnahmeprotokoll.

Der freigegebene Stand bleibt im `HANDBUCH.md` dokumentiert.  
Diese Agenda beschreibt ausschließlich die Weiterentwicklung **nach** diesem Stand.

---

## 2. Was steht

Der integrierte Rundgang `RGI-20260827-B` ist der stabile Referenzstand.

Er umfasst:

- Startseite
- Karte 01 · Zeit
- Karte 02 · Begriffe
- Karte 03 · Landschaft
- Karte 04 · Praxis & Güte
- Karte 05 · Ich / Wir
- Karte 06 · Zukunft
- die zu Karte 06 gehörenden Vertiefungsseiten

Der Rundgang ist inhaltlich, technisch und im realen Firefox-Test abgenommen.

### Verbindliche Regel

Der freigegebene Rundgang wird **nicht still verändert**.

Neue gestalterische, inhaltliche oder technische Entwicklungen erfolgen:

- außerhalb des freigegebenen Referenzstands,
- mit eigener Entwicklungskennung,
- zunächst prototypisch,
- erst nach Auswahl und Abnahme als neuer Produktionsstand.

Es gibt **kein automatisches `RGI-C`**.

---

## 3. Entwicklungsphase 2 – Atlas & Design

### Ziel

Die nächste Phase trägt den Arbeitstitel:

# **Kursbuch Foresight · Entwicklungsphase 2 – Atlas & Design**

Ihr Ziel ist nicht, den vorhandenen Rundgang weiter zu polieren.

Ihr Ziel ist, aus dem heute guten integrierten Rundgang den **eigentlichen offenen Atlas eines Feldes** zu entwickeln.

### Sichtbare Produktstufe

Dafür gehören drei Entwicklungslinien zwingend zusammen:

1. **Themenportfolios**
2. **Wissensbasis**
3. **Designsystem / visuelle Identität**

Diese drei Linien bilden gemeinsam die nächste sichtbare Produktstufe.

### Unsichtbares Fundament

Darunter liegt eine vierte, infrastrukturelle Ebene:

4. **Datenmodell / Verknüpfungsarchitektur**

Sie ist kein zusätzliches Feature, sondern die Voraussetzung dafür, dass Themenportfolios, Wissensbasis und Design später belastbar miteinander verbunden werden können.

Zielbild:

**Thema ↔ Karte ↔ Akteur ↔ Begriff ↔ Quelle ↔ offene Frage**

Diese Beziehungskette ist nicht nur eine UX-Idee. Sie muss als adressierbares Modell verstanden werden.

---

## 4. Datenmodell / Verknüpfungsarchitektur

### Warum dieser Strang vorgezogen wird

Heute sind die Karten weitgehend eigenständige HTML-Dateien mit lokal eingebetteten Daten.

Beispiele:

- Akteure in Karte 03
- Begriffsknoten in Karte 02
- Zeitereignisse in Karte 01
- Quellenreferenzen und Statuslogiken in mehreren Karten

Für einen offenen Atlas reicht diese lokale Datenhaltung auf Dauer nicht aus.

Themenportfolios, Wissensbasis und Quernavigation setzen voraus, dass Entitäten wiedererkennbar und verknüpfbar sind.

### Erstes Ergebnis von Strang A

Der erste konkrete Output ist genau **ein read-only Inventardokument**:

`P2-DATA-01_Inventar-Entitaeten-IDs-Querverweise.md`

Es wird ausschließlich aus den freigegebenen `RGI-20260827-B`-Dateien gelesen und dokumentiert je Karte:

- welche Entitäten tatsächlich vorkommen,
- welche ID-Schemata real verwendet werden oder fehlen,
- welche Querverweise bereits existieren,
- welche Informationen derzeit nur lokal eingebettet sind.

Dieses Inventar verändert keine Daten, vergibt keine neuen IDs und führt keine Migration durch.

**Erst Inventar, dann Schema.**

### Erste Aufgabe: Inventar statt Neuerfindung

Bevor neue IDs definiert werden, wird geprüft:

- Welche stabilen IDs existieren bereits tatsächlich?
- Welche davon sind nur kartenspezifisch?
- Welche Beziehungen sind bereits vorhanden?
- Welche Entitäten brauchen künftig eine übergreifende Identität?

Beispielhafte Entitätstypen:

- Akteur
- Begriff
- Zeitereignis
- Praxisform
- Gütekriterium
- Szenario
- Thema
- Quelle
- Zeitschriftenquelle
- offene Frage

### Grundschema

Für jede relevante Entität ist mindestens zu klären:

`Entität → stabile ID → Eigenschaften → Beziehungen → Quelle → Status`

### Wichtige Vorsichtsregel

Bestehende IDs werden nicht aus Erinnerung übernommen.

Beispiel: Für die Akteure von Karte 03 ist zunächst zu prüfen, welche IDs im freigegebenen Datensatz tatsächlich verwendet werden. Neue globale IDs werden erst danach entschieden.

### Technische Richtung – noch keine Festlegung

Als leichter Mittelweg zwischen handgepflegten Einzeldateien und einem CMS soll geprüft werden:

**gemeinsame strukturierte Datenquellen + statischer Build**

Beispielhafte Struktur, ausdrücklich nur als Prüfmodell:

- `data/akteure.json`
- `data/begriffe.json`
- `data/zeit.json`
- `data/quellen.json`
- `data/themen.json`

Ziel:

Eine Information wird an einer Stelle gepflegt und kann an mehreren Stellen ausgespielt werden.

### Noch nicht entschieden

- JSON, YAML oder anderes Format
- Build-Werkzeug
- statischer Generator
- CMS
- React oder anderes Framework

Die Technologie folgt dem Daten- und Nutzungsmodell, nicht umgekehrt.

---

## 5. Themenportfolios

### Funktion

Die Themenportfolios bilden die **horizontale Zugangslogik** des Kursbuchs.

Der Rundgang ist linear und dramaturgisch:

`Start → Zeit → Begriffe → Landschaft → Praxis & Güte → Ich / Wir → Zukunft`

Die Themenportfolios verlaufen quer dazu.

Sie beantworten nicht die Frage:

> Was kommt als Nächstes?

sondern:

> Was finde ich im Kursbuch zu einem bestimmten Thema?

### Zielbild

Ein Themenportfolio soll Inhalte aus mehreren Karten intelligent zusammenführen, zum Beispiel:

- historische Spuren aus Karte 01
- relevante Begriffe aus Karte 02
- Akteure aus Karte 03
- Praxisformen und Gütekriterien aus Karte 04
- Selbst- und Community-Perspektiven aus Karte 05
- Zukunftsfragen und offene Kontroversen aus Karte 06
- Quellen und weiterführende Dokumente aus der Wissensbasis

### Leitregel

Ein Themenportfolio ist **keine zusätzliche Text-Unterseite** und keine „Karte 07“.

Es ist eine zweite, thematische Navigations- und Erkenntnisebene des Atlas.

### Aufnahmeheuristik

Ein Thema wird nur dann zum Portfolio, wenn es:

- tatsächlich quer durch mehrere Karten trägt,
- dort bereits verankerten Inhalt besitzt,
- mehr ist als ein Stichwort,
- einen eigenständigen Erkenntniswert erzeugt.

Arbeitsheuristik:

**Ein Portfolio sollte in der Regel mindestens drei Karten substanziell verbinden.**

Das ist zunächst ein Filter, kein Dogma.

### Kuratierung

Wenige, starke Portfolios haben Vorrang vor Portfolio-Inflation.

Die Zusammenstellung eines Portfolios ist eine redaktionelle Synthese und wird entsprechend kenntlich gemacht.

### Noch zu klären

- Welche ersten 5–8 Themen sind wirklich tragfähig?
- Nach welchen Kriterien wird ein Thema aufgenommen?
- Wie stark werden Portfolios redaktionell kuratiert?
- Welche Inhalte werden automatisch aus Daten übernommen?
- Welche Verbindungen werden bewusst redaktionell gesetzt?
- Wie werden Quellen und offene Fragen sichtbar gemacht?
- Wie bleibt ein Portfolio aktuell?

---

## 6. Wissensbasis

### Funktion

Die Wissensbasis macht die bereits entwickelte Quellen- und Evidenzarchitektur für Nutzer sichtbar und nutzbar.

Sie soll nicht nur Quellen auflisten, sondern nachvollziehbar machen:

- worauf Aussagen beruhen,
- was Primärquelle ist,
- was Register- oder Sekundärbeleg ist,
- was Kursbuch-Synthese ist,
- wo Evidenz fehlt,
- welche Charts, Modelle, Dokumente und Datensätze zum Thema gehören.

### Ziel

Die Wissensbasis soll ein eigenständiger Mehrwert des Kursbuchs werden:

**nicht nur Orientierung über Foresight, sondern transparente Orientierung über das Wissen, auf dem diese Orientierung beruht.**

### Verbindung zu den Themenportfolios

Die Themenportfolios greifen auf die Wissensbasis zu.

Damit entsteht ein vernetzter Atlas:

**Thema ↔ Karte ↔ Akteur ↔ Begriff ↔ Quelle ↔ offene Frage**

### Interne und öffentliche Evidenzlogik trennen

Die interne Provenienz- und Prüfstruktur muss vollständig bleiben.

Die öffentliche Darstellung muss dagegen verständlich, souverän und publizistisch sinnvoll sein.

Deshalb ist ausdrücklich zu entscheiden:

- Welche internen Statuskennzeichnungen werden öffentlich sichtbar?
- Wie werden offene Evidenzlagen formuliert?
- Wird ein fehlender Beleg als „Lücke“, „offene Forschungsfrage“ oder „Einladung zur Klärung“ gerahmt?
- Welche Kennzeichnungen bleiben ausschließlich intern?

Leitgedanke:

**Transparenz über Wissensgrenzen kann ein Markenzeichen des Kursbuchs sein, darf aber nicht als ungefilterter Werkstattstatus veröffentlicht werden.**

---

## 7. Designsystem / visuelle Identität

### Ausgangslage

Der freigegebene Rundgang ist:

- funktional,
- konsistent,
- technisch stabil,
- deutlich verbessert,

aber gestalterisch noch nicht unverwechselbar genug.

Die aktuelle Formensprache trägt noch sichtbare Merkmale eines generischen modernen Web-Interfaces:

- viele Karten
- viele Pills und Chips
- starke Rundungen
- weiche Schatten
- relativ konventionelle Container
- systemische Standardtypografie
- zu wenig eigenständige redaktionelle Dramaturgie

### Zielrichtung

Die neue visuelle Sprache soll sich an folgender Richtung orientieren:

# **Swiss Editorial + Atlas + moderner Bauhaus-Geist**

Nicht Bauhaus als Dekoration, sondern als Prinzip:

**Form folgt Funktion.**

### Leitprinzipien

- starkes, sichtbares Raster
- typografische Hierarchie als zentrales Gestaltungsmittel
- mehr Weißraum und klare Flächen
- deutlich weniger Rundungen
- keine weichen Schatten als Standard
- reduzierte Farbpalette
- Farbe nur mit semantischer Funktion
- asymmetrische, aber präzise Layouts
- Editorial- statt SaaS-Charakter
- Datenvisualisierung statt Card-Sammlung
- Einheit ohne Gleichförmigkeit
- Interaktion nur dort, wo sie Erkenntnis erzeugt

### Interaktionssprache

Reduktion darf Bedienbarkeit nicht unsichtbar machen.

Das Designsystem definiert deshalb ausdrücklich eine konsistente Interaktionssprache für:

- Links
- Buttons
- Auswahl
- aktive Zustände
- Hover
- Fokus
- geöffnet / geschlossen
- deaktivierte Zustände
- Tastaturbedienung

Grundregel:

**Bedienbar muss als bedienbar erkennbar sein – auch ohne Pills, Schatten und starke Rundungen.**

Interaktion wird nicht über Dekoration signalisiert, sondern über wenige, wiedererkennbare funktionale Cues, zum Beispiel:

- Unterstreichung
- definierte Signalfarbe
- Pfeil / Richtungszeichen
- Fokusrahmen
- eindeutiger Zustandswechsel

Die endgültige Sprache wird im Designprototyp festgelegt und real getestet.

### Farbrichtung

Grundpalette:

- warmes Papierweiß / Off-White
- fast schwarzes Ink
- Teal als durchgängiges Kursbuch-Signal

Teal ist die durchgängige **Identitäts- und Orientierungssignalfarbe** des Kursbuchs.

Coral, Violett und Gelb werden nur dort verwendet, wo sie eine **inhaltlich definierte semantische Bedeutung** tragen.

### Typografie

Ziel:

- charaktervolle Grotesk für Headlines und starke Aussagen
- präziser Lesetext
- optionale Mono-Schrift für Metadaten, Jahre, Quellen, IDs und Daten
- größere typografische Kontraste
- weniger UI-Textästhetik, mehr publizistische Wirkung

### Pilotprinzip

Nicht alle Seiten gleichzeitig redesignen.

Zuerst drei Prototypen:

1. **Start** – Editorial / Cover / Orientierung
2. **Karte 02** – Begriffskonstellation / konzeptionelle Interaktion
3. **Karte 03** – Datenatlas / Filter / Landschaft

Diese drei Seiten decken die wichtigsten Gestaltungstypen ab.

### Wichtige Abhängigkeit

Die Prototypen dürfen nicht so gebaut werden, als gäbe es später keine Quervernetzung.

Sie müssen das Zielmodell bereits kennen und Platz für mögliche Atlas-Beziehungen vorsehen, zum Beispiel:

- „Teil von 3 Themenportfolios“
- „Dazu 5 Quellen“
- „Historische Spuren“
- „Verwandte Begriffe“
- „Offene Frage“

Diese Verbindungen müssen in der Explorationsphase noch nicht produktiv funktionieren.

### Prüfmaßstab

Nicht:

> Sieht es moderner aus?

Sondern:

> Könnte diese Seite mit ausgeschaltetem Logo nur das Kursbuch Foresight sein?

---

## 8. Weitere Entwicklungsfelder

### A · Rundgang
**Status:** geschlossen / freigegeben

Der aktuelle RGI-B-Stand bleibt Referenz und wird nicht erneut geöffnet.

### B · Datenmodell / Verknüpfungsarchitektur
**Status:** zentrale strukturelle Voraussetzung

Bestehende Entitäten, IDs und Beziehungen inventarisieren und ein belastbares Zielmodell definieren.

### C · Themenportfolios
**Status:** konzeptionell offen

Sie bilden die fehlende horizontale Atlaslogik.

### D · Wissensbasis / Quellen
**Status:** teilweise vorhanden

Die interne Evidenz- und Quellenlogik ist weit entwickelt, aber für Nutzer noch nicht als eigenständiger Wissensraum erschlossen.

### E · Designsystem / visuelle Identität
**Status:** zentrale sichtbare Baustelle

Ziel ist eine eigenständige digitale Publikationssprache statt eines guten Standard-Webinterfaces.

### F · Karte 05 / Karte 06 – Evidenz & Beteiligung
**Status:** teilweise offen

Offen bleiben insbesondere:

- belastbare Community-Werte
- mögliche eigene Erhebung
- Entscheidung über echte Beteiligungsfunktion
- Umgang mit Einreichung, Moderation, Veröffentlichung und Rückkopplung

### G · Accessibility / Multi-Browser / Produktions-QA
**Status:** offen

Vor einer öffentlichen Produktionsfassung sind u. a. zu prüfen:

- Tastaturbedienung
- Fokusführung
- Kontraste
- Screenreader
- Reduced Motion
- Safari
- Chrome
- Firefox
- reale mobile Geräte
- Performance

### H · Publikationsarchitektur
**Status:** offen

Dazu gehören später:

- stabile öffentliche URLs
- Metadaten
- Social Sharing / OpenGraph
- Canonical URLs
- Pflege- und Updateprozess
- ggf. CMS oder andere Redaktionslösung
- Verantwortlichkeiten für dauerhaften Betrieb

### I · KI-Kooperationsmodell
**Status:** jetzt verbindlich definieren

Siehe nächster Abschnitt.

---

## 9. Kooperationsmodell Klaus · HAL · Claude

### Klaus

Verantwortet:

- Richtung
- Anspruch
- Inhalt
- Auswahl
- reale Nutzungserfahrung
- finale Entscheidungen

Klaus muss nicht in technische Mikrologik hineingezogen werden, wenn sie für seine Entscheidung nicht relevant ist.

### HAL

Verantwortet:

- Architektur
- kritisches Sparring / Red Team
- Priorisierung
- Recherche- und Evidenzprüfung
- Art Direction gemeinsam mit Klaus
- unabhängige Abnahme konkreter Builds
- Schutz vor Scope-Ausweitung und Überarbeitung

HAL implementiert nicht operativ und gibt keine selbst erzeugte Umsetzung als unabhängig geprüft frei.

### Claude

Verantwortet:

- operative Umsetzung
- Frontend
- Datenintegration
- technische Selbsttests
- Git-Arbeit
- Umsetzung klar freigegebener Spezifikationen

Claude hat zusätzlich eine wichtige konstruktive Funktion:

**Probleme aus der Nähe der Implementierung früh sichtbar machen.**

Dabei gilt:

Claude darf Probleme, Abhängigkeiten und Risiken melden, aber **nicht automatisch lösen**, wenn sie außerhalb des vereinbarten Scopes liegen.

Befund → Rückmeldung → Entscheidung.

Nicht:

Befund → eigenmächtige Erweiterung.

### Ziel der Zusammenarbeit

HAL entwickelt und prüft Architektur und Kriterien.  
Claude prüft diese auch aus der Perspektive der operativen Umsetzbarkeit.  
Klaus entscheidet über Richtung und Freigabe.

Kritik zwischen HAL und Claude ist ausdrücklich erwünscht, solange daraus keine ungefragte Folgearbeit entsteht.

---

## 10. Zwei Arbeitsmodi

### Explorationsmodus

Zweck: Möglichkeiten sichtbar machen.

Erlaubt:

- Varianten
- visuelle Experimente
- alternative Layouts
- schnelle Prototypen
- Verwerfen von Ansätzen
- kreative Abweichungen

Nicht erforderlich:

- Build-Freeze
- SHA-Dokumentation jeder Variante
- formale Einzelabnahme jeder Variante

### Produktionsmodus

Beginnt erst nach einer bewussten Auswahl.

Dann gelten:

- klare Spezifikation
- klarer Scope
- eindeutiger Build
- Selbsttest durch Claude
- unabhängige Prüfung durch HAL
- realer Nutzungstest
- eine gebündelte Korrekturrunde
- Freeze

### Grundregel

**Nicht gleichzeitig gestalten, redigieren, implementieren, testen und freigeben.**

Erst verstehen und entscheiden, dann bauen.

---

## 11. Namensraum der Entwicklungsphase 2

Prototypen und Explorationen liegen klar außerhalb der eingefrorenen RGI-Linie.

Sie verwenden **keine `RGI-C`-Kennung**.

Arbeitskonvention:

- `P2-EXP-...` für explorative Design-/UX-Prototypen
- `P2-DATA-...` für Datenmodell- und Verknüpfungsprototypen
- spätere Produktionskennungen werden erst nach Auswahl definiert

Ziel:

Die Freeze-Grenze muss in Git, Dateinamen und Kommunikation sichtbar bleiben.

---

## 12. Arbeitsrhythmus

Für neue Entwicklungen gilt möglichst:

**Briefing → Story/Architektur → Daten-/Informationsmodell → Redaktionsfassung → UX-/Design-Spezifikation → Prototyp/Build → Selbsttest → unabhängige Prüfung → realer Nutzertest → gebündelte Korrektur → Freeze**

Keine endlosen Mikroschleifen.

Inhalte werden in größeren zusammenhängenden Blöcken bearbeitet.

Design wird zunächst prototypisch erkundet.

Technische Detailabnahme erfolgt erst auf Build-Ebene.

---

## 13. Anti-Kaputtoptimierungs-Regel

Nach einem freigegebenen Stand wird nur geändert, wenn mindestens eines der folgenden Kriterien erfüllt ist:

1. etwas funktioniert nicht,
2. etwas signalisiert Interaktion, ist aber nicht bedienbar,
3. etwas ist bedienbar, signalisiert seine Bedienbarkeit aber nicht ausreichend,
4. Begriffe oder Navigation sind widersprüchlich,
5. ein klarer Darstellungsfehler stört die Nutzung,
6. eine ausdrücklich beschlossene neue Entwicklungsphase beginnt.

Nicht ausreichend als Änderungsgrund:

- „könnte noch etwas schöner sein“
- spontane Wortpolitur
- neue Idee ohne Priorisierung
- zusätzlicher Effekt
- neue Funktion ohne Produktentscheidung

---

## 14. Dauerhaftes Projektgedächtnis

Für das Kursbuch gelten künftig zwei zentrale Dateien:

### `HANDBUCH.md`

Dokumentiert:

- freigegebene Stände
- Builds
- Abnahmen
- technische und epistemische Regeln

### `ENTWICKLUNGSAGENDA.md`

Dokumentiert:

- Entwicklungsrichtung nach dem Freeze
- offene Baustellen
- Prioritäten
- Datenmodell / Verknüpfungsarchitektur
- Designrichtung
- Kooperationsmodell
- nächste Entwicklungsphase

### Verbindlicher Startpunkt für neue KI-Arbeit

Vor jeder neuen Arbeit am Kursbuch sind mindestens zu lesen:

1. `HANDBUCH.md`
2. `ENTWICKLUNGSAGENDA.md`

Bei Widerspruch gilt:

**freigegebener Stand / HANDBUCH vor Entwicklungsabsicht / Agenda.**

---

## 15. Start von Entwicklungsphase 2

**Operativer Kern der Agenda:** Für den tatsächlichen Start sind vor allem §10 (Arbeitsmodi), §13 (Anti-Kaputtoptimierung) und dieser §15 maßgeblich. Die übrigen Abschnitte dienen als verbindliches Nachschlagewerk.

Die Phase beginnt **zweigleisig, aber leicht versetzt**.

Strang A führt um eine kurze Kopflänge: Zuerst entstehen das read-only Inventar und eine grobe Beziehungsskizze. Strang B startet unmittelbar danach und nutzt diese erste Orientierung bereits für die Designannahmen.

Damit bleibt die Phase parallel, ohne dass die Gestaltung ungesicherte Datenannahmen verfestigt.

### Strang A · Datenmodell / Verknüpfungsarchitektur

Zunächst nur:

- read-only `P2-DATA-01_Inventar-Entitaeten-IDs-Querverweise.md`
- grobe Beziehungsskizze auf Basis dieses Inventars
- Beziehungen zwischen Entitäten
- Zielmodell für Themen, Karten, Akteure, Begriffe, Quellen und offene Fragen
- Prüfung einer gemeinsamen strukturierten Datenschicht
- keine Migration und kein Großumbau

Ziel:

Verstehen, welche Verknüpfungen der Atlas künftig tragen muss.

### Strang B · Art Direction / Designprototypen

Nur:

- Start
- Karte 02
- Karte 03

Ziel:

Drei deutlich unterschiedliche Seitentypen in **einer unverwechselbaren visuellen Sprache**.

Die Prototypen kennen das Zielmodell aus Strang A und berücksichtigen mögliche Quernavigation, ohne sie bereits produktiv umzusetzen.

### Synchronisationspunkt · Tor 1

Nach dem ersten begrenzten Durchlauf von Strang A und B wird gemeinsam geprüft:

- trägt das Datenmodell die gewünschten Portfolios?
- trägt das Design die geplanten Querverbindungen?
- entstehen Doppelstrukturen?
- welche technische Architektur ist tatsächlich notwendig?

Der Synchronisationspunkt endet mit einer **bewussten Go/No-Go-Entscheidung auf genau eine technische Richtung** für die nächste Phase:

1. handgepflegte HTML-Struktur beibehalten,
2. gemeinsame strukturierte Datendateien plus statischer Build,
3. Framework-/Generator-Architektur.

Keine dieser Richtungen ist vorab gesetzt.

**Ohne diese Entscheidung kein Übergang in die nächste Produktionsstufe.**

---

## 16. Danach: Themenportfolios und Wissensbasis

### Paket C · Themenportfolios

- Kriterien finalisieren
- erste 5–8 mögliche Themen prüfen
- nur tragfähige Querschnittsthemen auswählen
- Beispielstruktur eines Portfolios
- Daten-/Quellenbezug definieren

### Paket D · Wissensbasis

- sichtbare Nutzerarchitektur
- Verbindung Themenportfolio ↔ Karten ↔ Quellen
- interne und öffentliche Evidenzlogik unterscheiden
- Statuslogik für Quellen, Synthese und offene Forschungsfragen

---

## 17. Leitentscheidung

Der nächste Entwicklungsschritt ist **keine weitere Optimierung des bestehenden Rundgangs**.

Er ist der Übergang:

> vom integrierten Rundgang  
> zum **offenen Atlas eines Feldes**

Die Entwicklungsphase 2 verbindet deshalb bewusst:

**Themenportfolios + Wissensbasis + Designsystem**

getragen von einem gemeinsamen:

**Datenmodell / Verknüpfungsschema**

Diese Ebenen bilden gemeinsam die nächste Produktstufe des Kursbuchs.
