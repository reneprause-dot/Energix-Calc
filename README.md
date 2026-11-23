# Energix Calc

PWA für Eigenheimbesitzer: Strom-, Gas-, Wasser- und Fixkosten erfassen, Abschläge berechnen, Verbrauch auswerten und Investitionen (Wärmepumpe, PV) durchrechnen.

**Version:** 2.17.1 (Build 37) – wird in der App unter „Mehr“ angezeigt.

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | Die komplette App (eine Datei, kein Build nötig) |
| `sw.js` | Service Worker (Offline-Betrieb, Cache `energix-v2.17.0-b36`) |

Beide Dateien müssen bei jedem Update gemeinsam hochgeladen werden.

## Installation (GitHub Pages)

1. `index.html` und `sw.js` in das GitHub-Pages-Repository hochladen (gleicher Ordner).
2. Seite im Safari auf dem iPhone öffnen.
3. Teilen → „Zum Home-Bildschirm“.
4. Nach einem Update die App einmal schließen und neu öffnen, damit der neue Service Worker aktiv wird.

## Funktionen

### Start & Zähler
- Profile für Strom, Gas, Wasser, Einspeisung und Fixkosten mit Abschlag, Grundpreis, Preisänderungen und Preiserhöhungs-Ankündigung.
- Zählerstände erfassen (manuell, per Foto/KI-Auslesung, per Diktat), Zählerwechsel, Differenzverbrauch zwischen Ständen.
- Abschlags-Prognose und Hochrechnung aus den Zählerständen.
- Ablese-Erinnerung und automatische Buchung fälliger Zahlungen.

### Verlauf
- Verlauf, Diagramme (Tag/Woche/Monat/Jahr), Kosten-Charts, Preisverlauf.
- Auswertung mit Durchschnittsvergleich, CO₂-Bilanz und Jahresbericht (druckbar).
- Gradtag-bezogener Verbrauch mit Wetterdaten.

### Haus
- Heizkosten-Prognose (Saison Oktober–April).
- Eigenheim-Vorlagen für Fixkosten, Wartung, Rechnungen, Nebenkosten, Steuermappe (Rechnungs-Upload mit KI-Auslesung und Hinweis zur steuerlichen Absetzbarkeit).
- **Stromverbraucher:** Geräte anlegen, kWh-Stand des Zwischensteckers eintragen, Hochrechnung auf Jahr, Kosten, CO₂ und Anteil am Gesamtverbrauch.
- **Wärmepumpe statt Gas:** Gaskosten heute vs. WP-Stromkosten, Förderung (BEG), Eigenanteil, Amortisation, 20-Jahres-Vorteil, CO₂-Ersparnis, Diagramm.
- **Photovoltaik:** Investition, Ertrag, Eigenverbrauch, Autarkie, Amortisation, 20-Jahres-Gewinn, Diagramm.
- Sparrechner (Standby, Raumtemperatur, Nachtabsenkung).
- Alle Annahmen sind unter „Annahmen anpassen“ editierbar.

### Mehr
- Einstellungen, Start-Tab, Kartenreihenfolge (▲/▼), Speicherung des Auf-/Zuklapp-Zustands.
- Backup: verschlüsselter Export/Import, optionaler Abgleich über GitHub.
- Kalender-Export (ICS) für Termine.

## Datenschutz

- Alle Daten liegen lokal auf dem Gerät (localStorage, IndexedDB für Dokumente).
- API-Key (Gemini), PIN und GitHub-Token bleiben nur auf dem Gerät bzw. im verschlüsselten Backup.
- Externe Aufrufe: Wetterdaten, Zeitabgleich, Gemini (nur bei aktiver KI-Funktion), GitHub (nur bei aktivem Sync).

## Hinweise zu den Rechnern

- Wärmepumpen-Förderung (Voreinstellung): BEG ab 21.07.2026 – 30 % Grundförderung + 16 % Klimabonus, max. 80 %, Höchstkosten 28.000 € (sinkend ab 02/2027). Aktuelle Werte bei KfW/BAFA prüfen.
- PV-Einspeisevergütung (Voreinstellung): 7,70 ct/kWh Teileinspeisung bis 10 kWp ab 08/2026.
- Alle Ergebnisse sind Modellrechnungen, keine Anlage-, Steuer- oder Energieberatung.

## Changelog (Auszug)

- **2.17.0** – Prognose reagiert ab dem ersten Zählerstand (gewichtet mit der Schätzung in den ersten 30 Tagen), Karte „Prognose je Zählerstand“
- **2.16.0** – Stromverbraucher: Geräte mit Zwischenstecker-Messung, Hochrechnung auf Jahresverbrauch und -kosten
- **2.15.0** – Selbsttest, einmalige Boni mit Datum, Warnung nach neuem Zählerstand, saisonale Gas-Hochrechnung (Gradtage), Änderungsprotokoll mit Rückgängig für Profile/Zähler/Zählerstände/Verlauf, Vertragsübersicht mit Kalender-Export
- **2.14.x** – Abschlag in der Übersicht, Abschlag-Korrektur, Start-Fehler behoben
- **2.10.0** – Wärmepumpen- und PV-Wirtschaftlichkeitsrechner
- **2.9.0** – Praxisfunktionen (u. a. Diktat, Wechsel-Assistent, Abrechnungs-Erklärung, Backup-Merge, Preisverlauf)
- **2.8.0** – Übersichts-Verbesserungen
- **2.7.1** – Kartenreihenfolge selbst sortierbar


### v2.17.1 (Build 37)
- Profile ohne verknüpften Zähler werden automatisch mit dem einzigen passenden Zähler verknüpft.
- Hinweis auf der Startkarte, wenn die Prognose nur geschätzt ist (kein Zähler, nur 1 Stand, alle Stände am selben Tag) – mit Verknüpfen-Button.
- Selbsttest meldet Zähler ohne Profil.
