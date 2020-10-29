# Pandoc Vorlage für Projektdokumentation

[Pandoc](https://pandoc.org) ist ein Programm mit dessen Hilfe man Dateien von einem Format in ein anderes überführen kann. dem man Markdowndateien (und andere Formate) in viele verschiedene Formate überführen kann.
Hier findest du die Vorlage zur generierung einer PDF oder eines Latex-Files für B-Prüfungen an der WBH. Es integriert die Vorlage für B-Prüfungen in den Arbeitsablauf für Pandoc.

## Vorraussetzuungen
Zur Nutzung dieses Templates werden folgende Tools vorrausgesetzt

- Pandoc
- Pandoc-Citeproc
- Texlive
- pdflatex

**! WICHTIG !** Um einen reibungslosen Ablauf zu gewährleisten ist es notwendig immer die neusten Versionen zu verwenden. Auf Debian, Ubuntu und von dort abgeleiteten Distributionen sind die Texlive und Pandoc versionen stark veraltet und funktionieren daher nicht mit diesem Template.

## Installation

Zur installation kannst du das entweder das Git Repository mithilfe von `git clone ssh://gogs@git.calyrium.org:2244/WBH/pandoc-b_pruefung.git` clonen oder die Datei `b-pruefung.tex` herunterladen. Danach kopierst du die Datei in das Verzeichnis `pandoc/data/templates`.

```
Linux:
sudo cp b-pruefung.tex /usr/share/pandoc/data/templates/wbh.tex

Mac:

Windows:

```


## Verwendung

Um alle Felder der Vorlage aus zu füllen musst du die folgenden Zeilen an den Anfang deines Dokumentes einfügen und ausfüllen.

```yaml
---
title: Projektkommunikations- und Dokumentationsplan
project: Chaos
version: 1.0
date: 23.10.2020
lang: de-DE
numbersections: false
toc: false
changelog:
  - version: 0.1
    date: 16.10.2020
    author: Sebastian Preisner
    note: Entwurf
  - version: 0.9
    date: 21.10.2020
    author: Sebastian Preisner
    note: Finalisierung
  - version: 1.0
    date: 23.10.2020
    author: Aud Peters
    note: Rechtschreibkorrektur
...
```

Nun kannst du mit hilfe von `pandoc -s -t cc-template.tex -o output.pdf input.md` dein Markdown file in ein PDF mit der gegeben Vorlage umwandeln.

### Variablen

Im Folgenden sind die einzelnen Variablen und Schalter erläutert. Alle Optionalen Variablen werden nicht benötigt und können somit leer bleiben oder ganz weg gelassen werden.

|   Variable    |                     Beschreibung                      | Optional |    default    |
|:------------- |:----------------------------------------------------- |:-------- |:------------- |
| title         | Titel des Dokuments                           | nein     |               |
| project        | Arbeitstitel des Projektes       | ja       |               |
| version       | Aktuelle Version des Dokuments (wird nicht aus dem changelog übernommen)            | ja     |               |
| date          | Datum der Veröffentlichung                            | ja       | today         |
| lang          | Sprache des Dokumentes "Ländercode"                   | ja       | de            |
| tp | Titelseite erzeugen | ja | |
| logo          | Der Pfad zum Logo         | ja       | Pfad zum Bild |
| toc           | Hinzufügen des Inhaltsverzeichnises                   | ja       | true / false  |
| lot           | Verzeichnis der Tabellen                              | ja       | true / false  |
| lof           | Liste der Figuren/Abbildungen                         | ja       | true / false  |
| changelog     | Array der Änderungshistorie   | ja | |


Zum Changelog:

|   Variable    |                     Beschreibung                      | Optional |    default    |
|:------------- |:----------------------------------------------------- |:-------- |:------------- |
| version | Bearbeitungsversion des Dokuments | nein | |
| date | Datum der Änderung | nein | |
| author | Bearbeiter des Dokuments | nein | |
| note | Hinweis auf Art der Änderung | nein | |
