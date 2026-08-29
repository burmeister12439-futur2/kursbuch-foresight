# HANDBUCH — Projektadapter Kursbuch Foresight

Dieses Handbuch beschreibt ausschließlich den **Projektadapter** für das
Kursbuch Foresight: wo publiziert wird, über welchen Weg, mit welchen
Freigabe-Gates und welchen Prüfregeln. Es verändert die Publikation selbst
nicht. Dieses Handbuch konkretisiert die projektübergreifenden Prinzipien für das Kursbuch Foresight. Bei einem Widerspruch gelten die projektübergreifenden Prinzipien; der Projektadapter ist entsprechend zu korrigieren.

Leitprinzip: **robust · einfach · überprüfbar · anpassungsfähig**

## Projektstart (verbindlich)

Vor jedem Arbeitsschritt am Kursbuch gilt ein Doppel-Read, in dieser Reihenfolge:

1. zuerst `HANDBUCH.md` lesen
2. danach `ENTWICKLUNGSAGENDA.md` lesen

Ein Auftrag wie „weiter mit Kursbuch" darf erst **nach** diesem Doppel-Read in einen nächsten Arbeitsschritt übersetzt werden.

**Vorrangregel:** freigegebener Stand / `HANDBUCH.md` steht vor Entwicklungsabsicht / `ENTWICKLUNGSAGENDA.md`. Bei einem Widerspruch gilt der freigegebene Stand.

## Live-Adresse

Die veröffentlichte Fassung liegt unter:

**https://foresight.klaus-burmeister.de/**

## Publikationsverzeichnis und Struktur

`docs/` ist das **GitHub-Pages-Publikationsverzeichnis**. Nur was in `docs/`
liegt, wird veröffentlicht.

- `docs/index.html` — Einstieg/Weiterleitung
- `docs/Kursbuch/Start/` — Startseite des Rundgangs
- `docs/Kursbuch/Karte01/` bis `docs/Kursbuch/Karte06/` — die sechs Karten
- `docs/Kursbuch/Meta/` — begleitende Meta-Seiten
- `docs/CNAME` — muss **exakt** `foresight.klaus-burmeister.de` enthalten (eine Zeile, kein weiterer Eintrag)

## Produktionsweg

```
Arbeitsbranch → geprüfter Remote-SHA → main → GitHub Pages aus docs/ → Custom Domain → Live-Prüfung
```

Konkret:

1. Auf einem **Arbeitsbranch** entwickeln, nie direkt auf `main`.
2. Den Branch pushen; verbindlich ist der **geprüfte Remote-SHA**.
3. Erst nach Freigabe nach **`main`** übernehmen.
4. **GitHub Pages** veröffentlicht aus **`docs/`** auf `main`.
5. Die **Custom Domain** `foresight.klaus-burmeister.de` (über `docs/CNAME`) zeigt auf die Pages-Seite.
6. Abschließend **Live-Prüfung** an der echten Adresse.

## Abgrenzung — was hier NICHT gilt

- **kein Cyberduck**
- **kein STRATO-Webspace-Upload** — STRATO dient hier **ausschließlich** dem DNS/CNAME der Subdomain
- **kein Cloudflare-Worker**
- **kein Preflight-Script nur um des Scripts willen** — ein Prüfschritt braucht einen echten Zweck, sonst entfällt er

## Freigabe-Gates

Vier Gates, in dieser Reihenfolge:

- **CONTENT GREEN** — Inhalt und Redaktion freigegeben: Texte, Quellen und Kartenaussagen sind sachlich geprüft und abgenommen.
- **BUILD GREEN** — technischer Build freigegeben: Struktur steht, alle internen Links lösen auf, keine Konsolen-/JS-Fehler.
- **DEPLOY GREEN** — Veröffentlichung korrekt: der geprüfte Stand liegt auf `main`, Pages baut aus `docs/`, die Custom Domain steht.
- **READER GREEN** — reale Leserprüfung: die ausgelieferte Seite ist an der Live-Adresse geöffnet und funktioniert für eine echte Leserin.

## Prüfregeln

- **Interaktive Karten** werden nicht allein per Selbsttest/headless abgenommen. Geprüft wird **exakt dieselbe ausgelieferte Datei** unabhängig im **realen Browser**.
- **Nach jeder Codeänderung erlischt die technische Freigabe (BUILD GREEN) des vorherigen Builds.** Ein neuer Build wird neu geprüft.

## Pflege dieses Handbuchs

Dieses Handbuch wird **nur** aktualisiert, wenn sich **dauerhaft** etwas an
Architektur, Rollen, Prüfweg oder Deployment ändert — nicht für einzelne
Inhalts- oder Buildschritte.

## Git/GitHub-Arbeitsregel

Bei Git-/GitHub-Arbeiten gilt:

- Claude-Sandbox, lokaler Mac, GitHub-Remote und ChatGPT-Connector sind getrennte Zustände und dürfen nicht miteinander gleichgesetzt werden.
- Vor jeder Änderung wird zuerst der tatsächliche Ausgangsstand festgestellt.
- Danach wird genau ein Arbeitsweg gewählt und bis zum Ende verfolgt.
- Leitregel: **ein Ziel · ein Branch · ein SHA · ein nächster Schritt**.
- Keine Parallelpfade und keine Werkzeugwechsel innerhalb eines laufenden Schritts.
- Terminalblöcke enthalten ausschließlich ausführbare Befehle, keinen Begleittext.
- Ein lokal vorhandener Commit gilt nicht als remote vorhanden.
- „Erledigt“ darf erst gemeldet werden, wenn der relevante Remote-Stand geprüft wurde.
