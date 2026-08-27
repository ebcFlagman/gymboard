# GymBoard

**Die digitale Lösung für die Durchführung von Geräteturn-Wettkämpfen — von der Anmeldung bis zur Rangliste.**

> Dieses Dokument beschreibt GymBoard aus Sicht von Vereinen, Verbänden und Wettkampf-Organisatoren (nicht aus technischer Sicht). Es dient als Grundlage für die Kundenakquise sowie als Referenz für neue Feature- und Bug-Tickets. 

## Das Problem

Geräteturn-Wettkämpfe werden heute vielerorts noch mit Excel-Listen, Papier-Notenblättern und manuellen Rangierungen organisiert. Das ist fehleranfällig, aufwändig und bietet weder Zuschauer:innen noch Vereinen Einblick in aktuelle Resultate. Bei Wettkämpfen mit mehreren hundert Turner:innen, verschiedenen Kategorien und parallel laufenden Abteilungen wird das schnell unübersichtlich.

## Die Lösung

GymBoard ist eine Webanwendung, mit der Organisationskomitees einen Geräteturn-Wettkampf komplett digital abwickeln: Teilnehmende importieren, Noten erfassen, Ranglisten automatisch berechnen und live veröffentlichen — öffentlich einsehbar, ganz ohne Login für Zuschauer:innen. Das System unterstützt die Wettkampfmodi (STV und SOTV) inklusive der jeweiligen Kategorien- und Geräte-Logik.

## Für wen ist GymBoard gedacht?

- **Turnvereine und Verbände**, die eigene Wettkämpfe organisieren (regional oder kantonal)
- **Organisationskomitees (OK)**, die für einen einzelnen Anlass eine einfache, zuverlässige Lösung suchen
- **Erfasser:innen**, die Noten tabletgestützt während des Wettkampfs eintragen
- **Zuschauer:innen und Vereine**, die Live-Ranglisten verfolgen möchten

## Funktionen im Überblick

### Wettkampf-Organisation
- Wettkämpfe mit Datum, Ort und Organisator anlegen — wer einen Wettkampf erstellt, wird automatisch dessen Administrator
- Beliebig viele Wettkämpfe parallel verwalten; ein Kontext-Umschalter in der Kopfzeile erlaubt den schnellen Wechsel zwischen den eigenen Wettkämpfen
- Unterstützung der Wettkampfmodi **STV** und **SOTV** mit automatischer Prüfung, welche Kategorien im jeweiligen Modus zulässig sind

### Teilnehmerverwaltung
- Import von Turner:innen und Geräte-Startreihenfolge direkt aus Excel (XLSX) — kein manuelles Nacherfassen nötig
- Verwaltung von Turner:innen, Vereinen und Teams inkl. Zuordnung zu Kategorien und Geschlecht
- Turner:innen können bei mehreren parallel laufenden Abteilungen sauber der richtigen Abteilung zugeordnet bzw. umgeteilt werden

### Noteneingabe
- Eingabemaske zur Erfassung der Noten pro Turner:in und Gerät (Boden, Ringe, Sprung, Barren, Reck, Balken)
- Eingabevalidierung verhindert fehlerhafte oder unplausible Notenwerte
- Zugriff für Editor:innen (nur Noteneingabe) und Administrator:innen getrennt geregelt

### Ranglisten & Live-Übertragung
- Automatische Berechnung von Einzel- und Teamranglisten nach den geltenden Wettkampfregeln
- Öffentliche Ranglisten pro Kategorie, ohne Login einsehbar
- **Live-Aktualisierung während des laufenden Wettkampfs**: Sobald eine Note erfasst oder die Rangliste freigegeben wird, aktualisiert sich die Ansicht der Zuschauer:innen automatisch — ohne manuelles Neuladen
- Organisatoren steuern selbst, wann die vollständige Rangliste veröffentlicht wird (Letzte Note wird zurückbehalten)

### Export & Auswertung
- Export der Ranglisten als Excel-Datei
- Export von Notenblättern als PDF sowie Wertungsrichterblättern als Excel — pro Abteilung mit sprechenden, sortierten Bezeichnungen statt technischer Kürzel

### Benutzer- und Rechteverwaltung
- Rollenmodell pro Wettkampf: **Administrator** (volle Kontrolle) und **Editor** (nur Noteneingabe)
- Wettkampf-Administrator:innen können weiteren Personen direkt per E-Mail-Einladung Zugriff geben — auch wenn diese noch kein Konto haben; das Konto wird dabei automatisch erstellt
- Öffentliche Selbstregistrierung ist bewusst deaktiviert: Zugänge entstehen ausschliesslich über Einladung, was unkontrollierten Zugriff verhindert

## Sicherheit

- Anmeldung über einen modernen, industriestandardisierten Login (OIDC) statt eigener Passwortverwaltung
- Zweistufiges Rechtemodell: globale Super-Admin-Rolle für den Betreiber sowie granulare, wettkampfspezifische Rollen für Organisationskomitees
- Schutzmechanismen gegen Fehlbedienung, z. B. kann sich niemand selbst zum Admin machen und der letzte verbleibende Admin eines Wettkampfs kann nicht entfernt werden

## Typischer Ablauf eines Wettkampftages

1. Organisator legt den Wettkampf an und importiert die Teilnehmerliste aus Excel
2. Weitere OK-Mitglieder werden per E-Mail eingeladen und erhalten Editor- oder Admin-Zugriff
3. Der Organisator druckt die Notenblätter für die Wertungsrichter:innen
4. Am Wettkampftag erfassen die dafür vorgesehenen Editor:innen die Noten
5. Zuschauer:innen und Vereine verfolgen die Rangliste live auf ihrem Smartphone — ganz ohne Login
6. Nach Wettkampfende werden Rangliste für die Siegerehrung exportiert und/oder freigeschalten

## Zielplattform

GymBoard läuft im Browser als Web-Applikation.
