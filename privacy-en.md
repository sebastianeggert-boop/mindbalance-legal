---
layout: default
title: Privacy Policy — MindBalance
---

# Privacy Policy — MindBalance

> **As of:** 7 May 2026
> **Data Controller:** Sebastian Eggert, Rooftop Entertainment

---

## 1. Overview

MindBalance is an app for burnout prevention. We take the protection of your personal data seriously. This privacy policy informs you about the processing of your data in accordance with Art. 13 GDPR.

## 2. What data is processed?

### 2.1 Locally on your device (no server)
- Mood check-in entries (mood state, timestamp, optional emotions)
- Balance Score calculations
- Burnout Check results (MBI scores)
- Intervention usage (which exercise, for how long)
- Journal entries (your text diary)
- Emotion tags (which feelings you assigned to a check-in)
- Pattern detections (recognised patterns, e.g. "lower score on Mondays")
- Wearable cache (heart rate, sleep, steps read from Health Connect — local intermediate storage)
- Burnout Weather Report cache (most recently displayed daily message)
- Chat messages with the AI Coach
- Consent settings
- Notification log and settings (quiet hours, micro-break preferences)
- Audit log (technical events for traceability, e.g. "consent granted/revoked" — contains no content, only metadata with timestamps)

**This data does NOT leave your device**, unless you activate the AI Coach (see 2.2).

**Note on data category:** Mood entries, Burnout Check results (MBI), wearable data, and the Score calculations derived from them may permit inferences about your health status. They are therefore classified as **special categories of personal data (health data) within the meaning of Art. 9(1) GDPR**. Processing takes place exclusively on your device and on the basis of your explicit consent under Art. 9(2)(a) GDPR (see §3).

### 2.2 AI features (only with your consent)

If you activate the AI Coach, the following data is transmitted, encrypted, to the Anthropic API (Claude):

- **Coach Chat:** Your chat messages with Lumi
- **Daily Insight:** Your Balance Score, trend, and day of the week (no chat content, no mood texts, no journal entries) — once daily for a personalised daily message

**Legal basis:** Art. 6(1)(a) GDPR (consent), and — to the extent the Daily Insight permits inferences about your health status — Art. 9(2)(a) GDPR (explicit consent for special categories). The consent can be withdrawn at any time for the future (see §4).

**Anthropic processing:** Data is transmitted via the official Anthropic API. Anthropic does **not** use it to train its models and does not retain it longer than technically required for the respective response. Status of the contractual basis: Anthropic Commercial Terms / Usage Policies as of the publication of this Privacy Policy. Should the contractual basis change, this Privacy Policy will be updated and, where applicable, renewed consent will be obtained (see §8).

**International transfer (USA):** Anthropic is a U.S.-based company. Data transmission is based on the EU Standard Contractual Clauses (Art. 46(2)(c) GDPR) and, where applicable between the parties, the EU-US Data Privacy Framework. You can stop this processing at any time by withdrawing AI Coach consent in `Profile → Privacy Settings`.

### 2.3 No further data collection

- No analytics (unless you activate them)
- No advertising
- No tracking
- No sharing with third parties

## 3. Consent model (2 active types)

All optional, all default OFF:

1. **AI Coach** — chat messages to Anthropic API (see §2.2)
2. **Wearable data** — health data from Health Connect (see §2.1)

Both consent toggles meet the requirements of an **explicit consent within the meaning of Art. 9(2)(a) GDPR**: the toggle text identifies the data category and purpose unambiguously, the consent is given by an unambiguous action (toggle activation), the default state is off, and withdrawal is possible at any time via the same toggle.

Each consent is individually revocable under `Profile → Privacy Settings`. Upon revocation, the data belonging to the respective consent is additionally removed (e.g. chat history when AI Coach consent is revoked).

### 3.1 Future consent types

The following consents are prepared in the data model but only become visible once the respective feature is active in a future app version:

- **Anonymous usage statistics** — currently not implemented
- **Cloud backup** — planned for a later phase
- **Journal analysis** — currently not implemented (journal entries remain purely local, without AI analysis)
- **Crash reports** — currently not implemented

The visibility logic is enforced in code via `ConsentType.isFeatureImplemented()`: toggles for non-implemented features are shown neither in the onboarding nor in the settings — "informed consent" within the meaning of Art. 7 GDPR cannot be granted for processing that does not take place at all.

## 4. Your rights (Art. 15-22 GDPR)

- **Right of access** (Art. 15): On request by email, you receive a list of your stored data. Since all data is stored locally on your device, you can view it yourself at any time (e.g. check-ins in History, chat history in the Coach).
- **Right to rectification** (Art. 16): You can correct inaccurate data yourself (e.g. delete check-ins and create new ones).
- **Right to erasure** (Art. 17): **Available directly in the app** via `Profile → Privacy Settings → "Delete all my data"`. Upon confirmation, all local data (see §2.1) is removed and the onboarding flow restarts. Details on the technical implementation in §4.1.
- **Right to restriction of processing** (Art. 18): Individually deactivable via consent toggles in `Profile → Privacy Settings`. Upon revocation, the data belonging to the respective consent is additionally deleted.
- **Right to data portability** (Art. 20): On request by email to `datenschutz@rooftopentertainment.de`, you receive a machine-readable file (JSON format) containing all locally stored data (see §2.1) for download. Processing time typically within 14 days, in any case within the statutory deadline of one month (Art. 12(3) GDPR). An automatic in-app export function is planned for a future version.
- **Right to withdraw consent** (Art. 7(3)): Consent can be withdrawn at any time (see Art. 18 above).

### 4.1 How "Delete all my data" works technically

Clicking the delete button triggers an atomic, crash-resistant operation:

1. All check-ins, Burnout Checks, chat messages, journal entries, emotion tags, wearable caches, weather report caches, and intervention sessions are removed from the local database.
2. All app settings (notification preferences, pattern cooldown, micro-break settings, onboarding status) are reset to factory defaults.
3. All consent settings are set to `Revoked`.
4. The audit log (technical events) is **pseudonymised**: timestamps and event types are retained for traceability; personal content is removed (the GDPR-compliant accountability obligation per Art. 5(2) remains fulfilled, without personal content).
5. A completion event `UserDataCleared` is logged.

If the app crashes during the operation (e.g. due to out-of-memory, reboot): on the next start, the app detects the interrupted operation and continues it (crash recovery via start marker). No half-deleted states remain on the device.

## 5. Data processors

| Service | Purpose | DPA |
|---------|---------|-----|
| Anthropic (Claude) | AI Coach | Yes, API Terms |

Further services (analytics, crash reports) are integrated only after activation by the user.

## 6. Data security

- All local data in encrypted Room database
- API communication via HTTPS/TLS
- No storage of chat content on servers
- No third-party access

## 7. Children and adolescents

MindBalance is intended for persons **aged 16 and over**. The threshold of 16 is based on Art. 8(1) GDPR as implemented in Germany (§ 22(1) BDSG / national specification). Since the GDPR baseline minimum is 13 years and individual EU member states have set values between 13 and 16, MindBalance applies the strictest value (16 years) as a safe default for the entire EU.

For persons under 16, valid consent within the meaning of Art. 8 GDPR is not possible without parental authorisation. App functions that require explicit consent (AI Coach, wearable integration) are therefore not made available to that age group. The minimum age is queried during onboarding; if not met, use is denied.

## 8. Changes

Changes to this privacy policy will be displayed in the app. For material changes, renewed consent will be obtained.

## 9. Contact

Sebastian Eggert
Rooftop Entertainment
Email: datenschutz@rooftopentertainment.de

## 10. Versioning and Status

| Status | Change |
|---|---|
| 6 May 2026 | Initial English version (raw translation of the German source as of 21 April 2026) |
| 7 May 2026 | §2.1 health-data category notice (Art. 9 GDPR) added; §2.2 Anthropic processing detailed (Standard Contractual Clauses, EU-US DPF); §3 explicit consent under Art. 9(2)(a) GDPR clearly named; §4 Art. 20 data portability detailed (JSON format, 14-day target turnaround); §7 minimum-age reasoning expanded. |

**Approach for changes:** Changes are versioned here for traceability. For material changes (new data categories, new processors, changed legal bases), renewed consent will be obtained in the app before they take effect (see §8). Editorial changes without new processing operations are merely displayed in the app.
