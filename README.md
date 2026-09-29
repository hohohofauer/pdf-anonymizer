# PDF-Anonymizer

Ein lokal ausführbares Browser-Werkzeug, das Text aus PDF-Dateien extrahiert und ausgewählte Begriffe durch Platzhalter ersetzt. Mit einem Zuordnungsschlüssel lassen sich individuelle Platzhalter später wieder in Klartext umwandeln.

Die Anwendung besteht aus einer einzigen HTML-Datei. Eine Installation oder Internetverbindung ist nicht erforderlich. Die Datei ist lokal nutzbar.

## Funktionen

- Text aus PDF-Dateien extrahieren oder direkt einfügen.
- Text und Ersetzungen in einem gemeinsamen, bearbeitbaren Textfeld anzeigen.
- Markierte Textpassagen per Button als Suchbegriffe übernehmen.
- Individuelle Platzhalter wie `[[MANDANT]]` oder `[[001]]` verwenden.
- Alternativ alle Suchbegriffe durch einen einheitlichen Platzhalter ersetzen.
- Groß- und Kleinschreibung, flexible Leerzeichen und Wortgrenzen berücksichtigen.
- Trefferzahlen pro Suchbegriff anzeigen.
- Ergebnisse kopieren oder als `.txt` speichern.
- Individuelle Platzhalter mithilfe eines Schlüssels zurückumwandeln.

## Starten

1. HTML-Datei herunterladen und öffnen.
2. Im Reiter **Anonymisieren** eine PDF-Datei auswählen oder hineinziehen.

Die benötigte PDF.js-Bibliothek ist in der HTML-Datei eingebettet.

## Anonymisieren

### Text laden

Eine PDF-Datei auswählen oder Text direkt in das gemeinsame Textfeld einfügen. Der Text lässt sich dort bearbeiten.

### Suchbegriffe festlegen

Links einen Suchbegriff pro Zeile eintragen:

```text
Max Mustermann = MANDANT
Erika Musterfrau = ZEUGIN
max@example.com
Musterstraße 12
```

Mit `Begriff = NAME` entsteht ein benannter Platzhalter wie `[[MANDANT]]`. Ohne Namensangabe vergibt das Werkzeug nummerierte Platzhalter. Leere Zeilen und Kommentarzeilen, die mit `#` beginnen, werden ignoriert.

Alternativ eine Passage im Textfeld markieren und **Als Suchbegriff übernehmen** anklicken. Ein einzelnes Wort lässt sich per Doppelklick markieren. Alle passenden Vorkommen werden anschließend ersetzt.

Bereits erzeugte Platzhalter können nicht als Suchbegriffe übernommen werden. Änderungen an ihnen erfolgen über die Suchbegriffsliste. Wird ein Suchbegriff entfernt, erscheint der zugehörige Originaltext wieder.

### Suchoptionen

| Option | Wirkung |
| --- | --- |
| Groß-/Kleinschreibung ignorieren | Findet Begriffe unabhängig von ihrer Schreibweise. |
| Leerzeichen und Zeilenumbrüche flexibel behandeln | Erkennt mehrteilige Begriffe auch bei abweichenden Abständen oder Zeilenumbrüchen. |
| Nur ganze Wörter ersetzen | Verhindert Treffer innerhalb längerer Wörter. |

### Ergebnis und Schlüssel sichern

Den angezeigten Text prüfen und über **Kopieren** oder **Als .txt speichern** übernehmen.

Bei individuellen Platzhaltern erscheint zusätzlich ein Schlüssel mit den Zuordnungen zum Klartext. Diesen separat kopieren und geschützt aufbewahren. Er wird nicht automatisch gespeichert.

Ein einheitlicher Platzhalter, beispielsweise `XXX`, ermöglicht keine Rückumwandlung.

## Rückumwandeln

1. Zum Reiter **Rückumwandeln** wechseln.
2. Den gespeicherten Schlüssel einfügen oder aus der aktuellen Anonymisierung übernehmen.
3. Den Text mit den Platzhaltern einfügen.
4. Das Ergebnis kopieren oder als `.txt` speichern.

Das Werkzeug weist auf verbleibende Platzhalter ohne passende Zuordnung hin.

## Lokale Verarbeitung

Die Verarbeitung erfolgt lokal im Browser. Die Anwendung benötigt keinen Server.

Der Schlüssel enthält die ersetzten Klartextdaten. Er sollte getrennt vom weitergegebenen Text aufbewahrt werden. 

## Grenzen

- **Keine automatische Erkennung:** Ersetzt werden ausschließlich eingetragene Suchbegriffe. Das Ergebnis muss vor der Weitergabe geprüft werden.
- **Keine PDF-Schwärzung:** Die ursprüngliche PDF-Datei wird nicht verändert. Die Ausgabe ist reiner Text.
- **Keine OCR:** Gescannte Seiten benötigen bereits eine Textebene.
- **Keine Layout-Erhaltung:** Tabellen, Spalten und andere komplexe PDF-Strukturen können bei der Textextraktion abweichend erscheinen.
- **Keine exakte Formatwiederherstellung:** Die Rückumwandlung verwendet die im Schlüssel hinterlegten Begriffe. Ursprüngliche Großschreibung, Abstände und Zeilenumbrüche werden nicht zwingend rekonstruiert.
- **Keine automatische Speicherung:** Vor dem Schließen oder Neuladen der Seite müssen benötigte Texte und Schlüssel gesichert werden.
- Passwortgeschützte PDFs werden derzeit nicht unterstützt.

## Technische Grundlage

Die Anwendung verwendet HTML, CSS und JavaScript sowie eine eingebettete Version von [Mozilla PDF.js](https://github.com/mozilla/pdf.js).

## Lizenz

### Mozilla PDF.js

Die eingebettete PDF.js-Bibliothek steht unter der **Apache License, Version 2.0**.

- Projekt: [Mozilla PDF.js](https://github.com/mozilla/pdf.js)
- Lizenztext: [LICENSE-PDFJS.txt](LICENSE-PDFJS.txt)
- Die Copyright- und Lizenzhinweise innerhalb der eingebetteten Bibliothek bleiben erhalten.

Bei einer Weitergabe des Werkzeugs müssen der Apache-2.0-Lizenztext und die erforderlichen Hinweise zur Bibliothek mitgeliefert werden. Deshalb sollten die HTML-Datei und die zugehörigen Lizenzdateien gemeinsam weitergegeben werden, beispielsweise als ZIP-Archiv. Bei einer Weitergabe ausschließlich als einzelne HTML-Datei muss der vollständige Lizenztext auch darin enthalten sein.
