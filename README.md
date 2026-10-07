# Vorlesungsverzeichnis & Stundenplaner

Dieses Tool dient dazu die Vorlesungsverzeichnisse der HfMT Köln übersichtlicher anzuzeigen und Stundenpläne zusammenzustellen.
Alles steckt in einer einzelnen HTML-Datei, die aus dem XML-Export eines Vorlesungsverzeichnisses (QIS/HISinOne)
eine durchsuchbare Übersicht macht — mit Stundenplan, Überschneidungswarnung und
Kalenderexport. Alles läuft lokal im Browser, die index.hmtl Datei kann auch heruntergeladen werden und ohne Internetverbindung genutzt werden.

Gebaut für die HfMT Köln, funktioniert aber mit jedem Vorlesungsverzeichnis im
gleichen XML-Format.

> ⚠️ **Inoffizielles Hilfsmittel, ohne Gewähr.** Die Daten stammen aus der XML-Datei,
> die du selbst hochlädst, und sind ab dem Moment des Exports ein Schnappschuss.
> Räume, Zeiten und Angebote ändern sich im laufenden Semester. **Verbindlich ist
> immer das Vorlesungsverzeichnis im Portal** — prüfe wichtige Termine dort gegen,
> bevor du dich darauf verlässt. Für Prüfungs- und Modulfragen gilt das
> Modulhandbuch bzw. die Studienberatung.

---

## Benutzen

1. **[Seite öffnen](https://hfmtkarl.github.io/stundenplaner/)**
2. XML-Datei aus dem Campus-Portal herunterladen (die Anleitung dazu steht auf der Startseite)
3. Datei auf die Seite ziehen — fertig

Zum reinen Ausprobieren liegt ein Beispielverzeichnis bei (EMP / IGP), das sich auf der
Startseite mit einem Klick laden lässt — **ohne Login, aber auch ohne Aktualität**. Es ist
eine Momentaufnahme und wird nicht gepflegt; ab 60 Tagen weist die Seite selbst darauf hin.
Für die echte Planung gilt der eigene, frische Export. Der Knopf erscheint nur auf der
gehosteten Fassung: eine lokal geöffnete Kopie darf keine Nachbardateien lesen.

Deine Auswahl bleibt im Browser gespeichert, auf deinem Gerät. Es wird nichts hochgeladen.

### XML-Datei besorgen

Im Portal einloggen → `Veranstaltungen` → `Vorlesungsverzeichnis` → bis zum Studiengang
durchklicken → kleines **PDF-Symbol** neben der gewünschten Baumebene → `Ausgabeformat`
auf **XML** → `Druckvorlage verwenden und drucken` → auf der nächsten Seite
`Bericht herunterladen / öffnen` mit **Rechtsklick → „Link speichern unter…"**.

Das dauert bei großen Bäumen ein bis zwei Minuten. Und es geht nur eingeloggt.

## Funktionen

- **Katalog** mit Baumstruktur, einklappbaren Rubriken, Inhaltsverzeichnis und Volltextsuche
  (umlauttolerant: „Übung" = „ubung" = „Uebung")
- **Dreistufige Auswahl**: fest · vielleicht · ausgeblendet
- **Stundenplan** als Wochen- oder Tagesraster, mit Konflikterkennung
- **Standortwechsel-Warnung**, wenn zwischen zwei Terminen an verschiedenen Orten
  zu wenig Zeit liegt
- **Eigene Termine** (Hauptfach, Üben, Sport …) frei eintragbar, mit Farbe und Raum
- **Filter** nach Standort und Studiengang/Bereich — exportierst du weit oben im Baum,
  lassen sich die enthaltenen Studiengänge einzeln isolieren; dazu Ausblenden einzelner
  Kurse und ganzer Rubriken
- **Export**: Kalenderdatei (.ics), Auswahl als JSON sichern/laden, Drucken als PDF
- **Mehrere Verzeichnisse gleichzeitig** — z. B. zwei Studiengänge; jede Quelle wird
  eine eigene oberste Rubrik und lässt sich einzeln wieder entfernen
- **Zweisprachig** Deutsch/Englisch
- Läuft auf dem Handy

## Hosting

Die Datei ist in sich geschlossen — nur `index.html` hochladen, sonst nichts.

Mit GitHub Pages: Repository anlegen, Datei als `index.html` hochladen,
unter *Settings → Pages* als Quelle `main` / `root` wählen. Nach ein bis zwei Minuten
ist die Seite erreichbar.

Der Hinweis „erst herunterladen, dann planen" blendet sich auf `*.github.io`
(sowie Netlify, Vercel, Cloudflare Pages) automatisch aus — dort wird ja zuverlässig
gespeichert. Bei eigener Domain diese in `GEHOSTET_HOSTS` eintragen.

## Anpassen

Ganz oben im `<script>`-Block stehen alle Einstellungen:

| Variable | Bedeutung |
|---|---|
| `QIS_URL`, `QIS_NAME` | Link zum Campus-Portal in der Anleitung |
| `GEHOSTET_HOSTS` | eigene Domains, auf denen fest gehostet wird |
| `WECHSEL_MIN` | Minuten Puffer, ab wann ein Standortwechsel gewarnt wird |
| `KONTAKT_MAIL`, `KONTAKT_NAME` | Kontakt im „Fragen?"-Block (leer = kein Kontakt) |
| `BEISPIELE` | mitgelieferte Beispieldateien samt Exportdatum (leere Liste = kein Beispielbereich) |

Die Texte beider Sprachen liegen gesammelt im Objekt `TXT` — dort lässt sich alles
umformulieren oder eine weitere Sprache ergänzen.

## Datenschutz

Die hochgeladene XML wird ausschließlich im Browser verarbeitet. Auswahl, Notizen und
eigene Termine liegen in `localStorage`, die zuletzt geladene Datei in `IndexedDB` —
beides nur lokal auf dem Gerät. Es gibt keinen Server, keine Analyse, keine Cookies.

## Lizenz

[MIT](LICENSE) — benutzen, ändern und weitergeben ausdrücklich erwünscht, ohne Gewährleistung.

---

## English

A single HTML file that turns the XML export of a QIS/HISinOne course catalogue into a
searchable overview with a timetable planner, clash detection and calendar export.
No server, no installation, no data leaves your browser. The interface is available in
German and English (toggle in the top right).

**Unofficial tool, no guarantee.** The data comes from the XML file you upload yourself and
is a snapshot from the moment of export. Rooms, times and offerings change during the
semester — the course catalogue in the portal is always the authoritative source. Check
anything important there before relying on it.

Licensed under [MIT](LICENSE).
