---
layout: default
title: Datenschutzerklaerung — MindBalance
---

# Datenschutzerklaerung — MindBalance

> **Stand:** 21. April 2026
> **Verantwortlicher:** Sebastian Eggert, Rooftop Entertainment

---

## 1. Ueberblick

MindBalance ist eine App zur Burnout-Praevention. Wir nehmen den Schutz deiner persoenlichen Daten ernst. Diese Datenschutzerklaerung informiert dich gemaess Art. 13 DSGVO ueber die Verarbeitung deiner Daten.

## 2. Welche Daten werden verarbeitet?

### 2.1 Lokal auf deinem Geraet (kein Server)
- Mood Check-In Eintraege (Stimmung, Zeitstempel, optionale Emotionen)
- Balance Score Berechnungen
- Burnout-Check Ergebnisse (MBI-Scores)
- Interventions-Nutzung (welche Uebung, wie lange)
- Journaling-Eintraege (dein Text-Tagebuch)
- Emotion-Tags (welche Gefuehle du zu einem Check-In zugeordnet hast)
- Pattern-Detektionen (erkannte Muster, z.B. "Montags niedriger Score")
- Wearable-Cache (von Health Connect gelesene Herzfrequenz, Schlaf, Schritte — lokaler Zwischenspeicher)
- Burnout-Wetterbericht-Cache (zuletzt angezeigte Tages-Nachricht)
- Chat-Nachrichten mit dem KI-Coach
- Consent-Einstellungen
- Benachrichtigungs-Log und Einstellungen (Ruhezeiten, Micro-Break-Praeferenzen)
- Audit-Log (technische Ereignisse fuer Nachvollziehbarkeit, z.B. "Consent erteilt/widerrufen" — enthaelt keine Inhalte, nur Metadaten mit Zeitstempel)

**Diese Daten verlassen dein Geraet NICHT**, ausser du aktivierst den KI-Coach (siehe 2.2).

### 2.2 KI-Funktionen (nur mit deinem Consent)
Wenn du den KI-Coach aktivierst, werden folgende Daten verschluesselt an die Anthropic API (Claude) gesendet:
- **Coach-Chat:** Deine Chat-Nachrichten mit Lumi
- **Tages-Insight:** Dein Balance Score, Trend und Wochentag (keine persoenlichen Inhalte) — einmal taeglich fuer eine personalisierte Tages-Nachricht

Anthropic speichert diese Daten NICHT und verwendet sie NICHT fuer Training. Rechtsgrundlage: Art. 6 Abs. 1 lit. a DSGVO (Einwilligung).

### 2.3 Keine weiteren Datenerhebungen
- Keine Analytics (ausser du aktivierst sie)
- Keine Werbung
- Kein Tracking
- Keine Weitergabe an Dritte

## 3. Consent-Modell (2 aktive Typen)

Alle optional, alle default OFF:
1. **KI-Coach** — Chat-Nachrichten an Anthropic API
2. **Wearable-Daten** — Gesundheitsdaten von Health Connect

Jeder Consent ist einzeln widerrufbar unter `Profil → Datenschutz-Einstellungen`. Beim Widerruf werden die zum jeweiligen Consent gehoerenden Daten zusaetzlich entfernt (z.B. Chat-Historie beim Widerruf des KI-Coach-Consents).

### 3.1 Zukuenftige Consent-Typen

Folgende Consents sind im Datenmodell vorbereitet, werden aber erst sichtbar, wenn das jeweilige Feature in einer kuenftigen App-Version aktiv wird:

- **Anonyme Nutzungsstatistiken** — derzeit nicht implementiert
- **Cloud-Backup** — geplant fuer eine spaetere Phase
- **Journaling-Analyse** — derzeit nicht implementiert (Journaling-Eintraege bleiben rein lokal, ohne KI-Analyse)
- **Absturzberichte** — derzeit nicht implementiert

Die Sichtbarkeits-Logik ist im Code durch `ConsentType.isFeatureImplemented()` abgesichert: Toggles fuer nicht-implementierte Features werden weder im Onboarding noch in den Einstellungen angezeigt — eine "informierte Einwilligung" im Sinne von Art. 7 DSGVO kann nicht fuer eine Verarbeitung erteilt werden, die gar nicht stattfindet.

## 4. Deine Rechte (Art. 15-22 DSGVO)

- **Auskunft** (Art. 15): Auf Anfrage per E-Mail erhaeltst du eine Aufstellung deiner gespeicherten Daten. Da alle Daten lokal auf deinem Geraet liegen, kannst du sie jederzeit selbst einsehen (z.B. Check-Ins im Verlauf, Chat-Historie im Coach).
- **Berichtigung** (Art. 16): Falsche Daten kannst du selbst korrigieren (z.B. Check-Ins loeschen und neu anlegen).
- **Loeschung** (Art. 17): **Direkt in der App moeglich** ueber `Profil → Datenschutz-Einstellungen → "Alle meine Daten loeschen"`. Nach Bestaetigung werden samtliche lokalen Daten (siehe §2.1) entfernt, der Onboarding-Flow startet neu. Details zur technischen Umsetzung siehe §4.1.
- **Einschraenkung** (Art. 18): Ueber Consent-Toggles in `Profil → Datenschutz-Einstellungen` einzeln deaktivierbar. Beim Widerruf werden die zum jeweiligen Consent gehoerenden Daten zusaetzlich geloescht.
- **Datenportabilitaet** (Art. 20): Auf Anfrage per E-Mail. Eine automatische In-App-Exportfunktion ist in Vorbereitung.
- **Widerruf** (Art. 7 Abs. 3): Consent jederzeit widerrufbar (siehe Art. 18 oben).

### 4.1 Wie "Alle meine Daten loeschen" technisch funktioniert

Der Klick auf den Loesch-Button loest einen atomaren, crash-resistenten Vorgang aus:

1. Alle Check-Ins, Burnout-Checks, Chat-Nachrichten, Journaling-Eintraege, Emotion-Tags, Wearable-Caches, Wetterbericht-Caches und Interventions-Sessions werden aus der lokalen Datenbank entfernt.
2. Alle App-Einstellungen (Notification-Praeferenzen, Pattern-Cooldown, Micro-Break-Einstellungen, Onboarding-Status) werden auf Werks-Default zurueckgesetzt.
3. Alle Consent-Einstellungen werden auf `Widerrufen` gesetzt.
4. Der Audit-Log (technische Ereignisse) wird **pseudonymisiert**: Zeitstempel und Event-Typen bleiben fuer Nachvollziehbarkeit erhalten, personenbezogene Inhalte werden entfernt (DSGVO-konforme Rechenschaftspflicht nach Art. 5 Abs. 2 bleibt erfuellt, ohne personenbezogenen Inhalt).
5. Ein Abschluss-Event `UserDataCleared` wird protokolliert.

Falls die App waehrend des Vorgangs abstuerzt (z.B. durch Out-of-Memory, Reboot): beim naechsten Start erkennt die App den unterbrochenen Vorgang und setzt ihn fort (Crash-Recovery via Start-Marker). Keine halb-geloeschten Zustaende bleiben auf dem Geraet zurueck.

## 5. Auftragsverarbeiter

| Dienst | Zweck | AVV |
|--------|-------|-----|
| Anthropic (Claude) | KI-Coach | Ja, API Terms |

Weitere Dienste (Analytics, Crash Reports) werden erst nach Aktivierung durch den Nutzer eingebunden.

## 6. Datensicherheit

- Alle lokalen Daten in verschluesselter Room-Datenbank
- API-Kommunikation ueber HTTPS/TLS
- Keine Speicherung von Chat-Inhalten auf Servern
- Kein Zugriff durch Dritte

## 7. Kinder und Jugendliche

MindBalance ist fuer Personen ab 16 Jahren bestimmt.

## 8. Aenderungen

Aenderungen an dieser Datenschutzerklaerung werden in der App angezeigt. Bei wesentlichen Aenderungen wird eine erneute Zustimmung eingeholt.

## 9. Kontakt

Sebastian Eggert
Rooftop Entertainment
E-Mail: datenschutz@rooftopentertainment.de
