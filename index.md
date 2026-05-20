---
layout: default
title: Datenschutzerklaerung — MindBalance
---

# Datenschutzerklaerung — MindBalance

> **Stand:** 7. Mai 2026
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

**Hinweis zur Datenkategorie:** Mood-Eintraege, Burnout-Check-Ergebnisse (MBI), Wearable-Daten und damit korrelierte Score-Berechnungen koennen Rueckschluesse auf deinen Gesundheitszustand zulassen und werden daher als **besondere Kategorien personenbezogener Daten (Gesundheitsdaten) im Sinne von Art. 9 Abs. 1 DSGVO** eingestuft. Die Verarbeitung erfolgt ausschliesslich auf deinem Geraet und auf Grundlage deiner ausdruecklichen Einwilligung gemaess Art. 9 Abs. 2 lit. a DSGVO (siehe §3).

### 2.2 KI-Funktionen (nur mit deinem Consent)
Wenn du den KI-Coach aktivierst, werden folgende Daten verschluesselt an die Anthropic API (Claude) uebermittelt:
- **Coach-Chat:** Deine Chat-Nachrichten mit Lumi
- **Tages-Insight:** Dein Balance Score, Trend und Wochentag (keine Chat-Inhalte, keine Mood-Texte, keine Journaling-Eintraege) — einmal taeglich fuer eine personalisierte Tages-Nachricht

**Rechtsgrundlage:** Art. 6 Abs. 1 lit. a DSGVO (Einwilligung) sowie — soweit der Tages-Insight Rueckschluesse auf Gesundheitszustand zulaesst — Art. 9 Abs. 2 lit. a DSGVO (ausdrueckliche Einwilligung in besondere Kategorien). Die Einwilligung ist jederzeit fuer die Zukunft widerrufbar (siehe §4).

**Anthropic-Verarbeitung:** Die Daten werden ueber die offizielle Anthropic-API uebermittelt. Anthropic verwendet sie **nicht** zum Training der Modelle und speichert sie nicht laenger als fuer die jeweilige Antwort technisch erforderlich. Stand der Vertragslage (Anthropic Commercial Terms / Usage Policies, Stand der Veroeffentlichung dieser Datenschutzerklaerung). Sollte sich diese Vertragslage aendern, wird die Datenschutzerklaerung aktualisiert und gegebenenfalls eine erneute Zustimmung eingeholt (siehe §8).

**Datenuebertragung in die USA:** Anthropic ist ein US-amerikanisches Unternehmen. Die Datenuebermittlung erfolgt auf Basis der Standardvertragsklauseln der EU-Kommission (Art. 46 Abs. 2 lit. c DSGVO) und im Rahmen des EU-US Data Privacy Framework, soweit zwischen den Parteien anwendbar. Du kannst diese Verarbeitung jederzeit durch Widerruf des KI-Coach-Consents in `Profil → Datenschutz-Einstellungen` beenden.

### 2.3 Keine weiteren Datenerhebungen
- Keine Analytics (ausser du aktivierst sie)
- Keine Werbung
- Kein Tracking
- Keine Weitergabe an Dritte

## 3. Consent-Modell (2 aktive Typen)

Alle optional, alle default OFF:
1. **KI-Coach** — Chat-Nachrichten an Anthropic API (siehe §2.2)
2. **Wearable-Daten** — Gesundheitsdaten von Health Connect (siehe §2.1)

Beide Consent-Toggles erfuellen die Anforderungen einer **ausdruecklichen Einwilligung im Sinne von Art. 9 Abs. 2 lit. a DSGVO**: der Toggle-Text benennt die jeweilige Datenkategorie und den Zweck eindeutig, die Einwilligung wird durch eine eindeutige Handlung (Toggle-Aktivierung) erteilt, der Default-Status ist deaktiviert, und der Widerruf ist jederzeit ueber denselben Toggle moeglich.

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
- **Datenportabilitaet** (Art. 20): Auf Anfrage per E-Mail an `rooftop-entertainment@mail.de` erhaeltst du eine maschinenlesbare Datei (JSON-Format) mit allen lokal gespeicherten Daten (siehe §2.1) zum Download. Bearbeitungszeit in der Regel innerhalb von 14 Tagen, in jedem Fall innerhalb der gesetzlichen Frist von einem Monat (Art. 12 Abs. 3 DSGVO). Eine automatische In-App-Export-Funktion ist fuer eine spaetere Version geplant.
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

MindBalance ist fuer Personen **ab 16 Jahren** bestimmt. Die Festlegung auf 16 Jahre orientiert sich an Art. 8 Abs. 1 DSGVO in der deutschen Umsetzung (§ 22 Abs. 1 BDSG / nationale Festlegung). Da der DSGVO-Mindestrahmen 13 Jahre vorsieht und einzelne EU-Mitgliedstaaten zwischen 13 und 16 Jahren festlegen, waehlt MindBalance den strengsten Wert (16 Jahre) als sicheren Default fuer den gesamten EU-Raum.

Bei Personen unter 16 Jahren ist eine wirksame Einwilligung im Sinne von Art. 8 DSGVO ohne Zustimmung des Sorgeberechtigten nicht moeglich. Die App-Funktionen, die ausdrueckliche Einwilligung erfordern (KI-Coach, Wearable-Integration), sind fuer diese Altersgruppe nicht freigegeben. Im Onboarding wird das Mindestalter abgefragt; bei Nicht-Erreichung wird die Nutzung verweigert.

## 8. Aenderungen

Aenderungen an dieser Datenschutzerklaerung werden in der App angezeigt. Bei wesentlichen Aenderungen wird eine erneute Zustimmung eingeholt.

## 9. Kontakt

Sebastian Eggert
Rooftop Entertainment
E-Mail: rooftop-entertainment@mail.de

## 10. Versionierung und Stand

| Stand | Aenderung |
|---|---|
| 21. April 2026 | Erstfassung |
| 7. Mai 2026 | §2.1 Hinweis auf Gesundheitsdaten-Kategorie (Art. 9 DSGVO); §2.2 Anthropic-Verarbeitung praezisiert (Standardvertragsklauseln, EU-US DPF); §3 ausdrueckliche Einwilligung gem. Art. 9 Abs. 2 lit. a DSGVO; §4 Art. 20 Datenportabilitaet praezisiert (JSON-Format, 14-Tage-Bearbeitungs-Zielsetzung); §7 Mindestalter-Begruendung erweitert. |

**Vorgehensweise bei Aenderungen:** Aenderungen werden hier nachvollziehbar versioniert. Bei wesentlichen Aenderungen (neue Datenkategorien, neue Auftragsverarbeiter, geaenderte Rechtsgrundlagen) wird vor Inkrafttreten eine erneute Zustimmung in der App eingeholt (siehe §8). Redaktionelle Aenderungen ohne neue Verarbeitungs-Tatbestaende werden lediglich in der App angezeigt.
