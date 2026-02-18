# Privacy Policy

**Salva — Keeping Little Hands Safe**

**Effective Date:** February 18, 2026
**Last Updated:** February 18, 2026
**App Version:** 3.0 (Build 14)
**Developer:** Anthony Mallah
**Contact:** [tantoun1808@gmail.com](mailto:tantoun1808@gmail.com)

---

## 1. Introduction

Salva ("we," "our," or "us") is a parental screen-lock application for Android that protects your child's screen from accidental touches. This Privacy Policy explains what information we collect, how we use it, how we store and protect it, and your rights regarding your data.

Salva is designed for **parents and caregivers** — not for children directly. Children interact with the protected device screen; parents control all settings, rules, and monitoring.

By installing or using Salva, you agree to the practices described in this Privacy Policy.

---

## 2. Information We Collect

### 2.1 Data Stored On-Device Only (Never Uploaded)

The following data is stored exclusively on your device and is **never transmitted** to any server:

| Data | Description |
|------|-------------|
| **Screen content text** | Screen Sentinel scans on-screen text via the Accessibility Service for keyword matching. All processing is 100% on-device. Raw screen text is never sent to any server. |
| **Activity reports** | Protection history, blocked taps, session timelines, and daily summaries. |
| **Settings & preferences** | All configuration data (modes, thresholds, toggles) stored in local encrypted storage backed by Android Keystore. |
| **Ghost Mode knock pattern** | Your unlock pattern is stored in local encrypted storage and never transmitted. |
| **App whitelist** | Your list of whitelisted applications. |
| **Device identity tokens** | A device UUID and device-bound refresh token stored in encrypted shared preferences (Keystore-bound). |

### 2.2 Data Stored in the Cloud

If you create or join a household, the following data is synced to our cloud backend (hosted on Supabase):

| Data | Details | Purpose | Retention |
|------|---------|---------|-----------|
| **Content alerts** | Category label, app package name, short snippet (max 100 characters), timestamp, device ID | Allow parents to review alerts from child devices | Auto-purged after **7 days** |
| **Device heartbeat** | Protection mode, foreground app package, screen time (minutes), bypass attempt count, alert count, battery level, online status | Power the Family Dashboard for real-time monitoring | Overwritten every **15 seconds** (only latest state stored) |
| **Smart Rules** | Rule type, time window, target app packages, priority, days of week | Sync protection rules from parent to child devices | Stored until deleted by parent |
| **Screen Time Rewards** | Task name, description, emoji, bonus minutes, completion status | Sync reward tasks between parent and child devices | Stored until deleted by parent |
| **Household membership** | Device fingerprint (SHA-256 hash), device name, device role, household ID, device model, manufacturer | Device identity and household slot tracking | Stored until device is removed from household |
| **Account information** | Google account email (if signed in), display name, household role | Authentication and household management | Stored until account deletion |
| **Device metadata** | OS version, app version, integrity tier, truncated IP address, coarse region (e.g., "US-CA") | Technical support, debugging, anti-abuse geo-spread detection | Truncated IP: **30-day** rolling purge; coarse region: **90-day** rolling purge |
| **Pairing tokens** | One-time token, household ID, token type (QR/code), timestamps | Device pairing | Hard-deleted **7 days** after expiry |
| **Subscription records** | Purchase token, product ID, plan tier, subscription status, start and expiry timestamps | Entitlement verification | Tied to account lifecycle |

### 2.3 Data We Do NOT Collect

- **No advertising or ad tracking IDs**
- **No precise location data** — IP addresses are truncated at the gateway; only a coarse region (e.g., "US-CA") is derived and retained for a limited time
- **No contacts, call logs, or messages**
- **No photos, videos, or microphone recordings** — the camera permission is used exclusively for QR code scanning during household pairing and is declared as optional
- **No browsing history**
- **No third-party analytics** — we do not use Firebase Analytics, Mixpanel, or any third-party analytics SDKs
- **No personal content from screen scans** — Screen Sentinel processes text entirely on-device; only a category label, app name, and a maximum 100-character snippet are stored as an alert (auto-deleted after 7 days)

---

## 3. How We Use Your Information

We use the information we collect to:

- **Provide core functionality** — screen protection, touch blocking, mode switching, and scheduled protection
- **Enable household management** — let parents monitor and manage child devices remotely through the Family Dashboard
- **Deliver content alerts** — notify parents of potentially concerning on-screen content detected by Screen Sentinel
- **Sync rules and rewards** — keep Smart Rules and Screen Time Rewards consistent across household devices
- **Verify subscriptions** — confirm your subscription status and entitlements through Google Play Billing
- **Prevent abuse** — detect and mitigate fraudulent device pairing, geo-spread anomalies, and stolen entitlements
- **Provide technical support** — use device metadata for debugging and troubleshooting

We do **not** use your data for advertising, profiling, or sale to third parties.

---

## 4. Permissions We Request

| Permission | Why We Need It |
|------------|---------------|
| **Draw over other apps** (SYSTEM_ALERT_WINDOW) | Display the floating shield bubble and blocking overlay on top of all apps |
| **Accessibility Service** | Core touch-blocking, hardware key interception, app-switch detection, and Screen Sentinel on-screen text reading |
| **Foreground Service** | Run the overlay service persistently so protection remains active |
| **Notifications** | Send content alerts, screen time warnings, and remote control confirmations to parents |
| **Query installed apps** | Detect the foreground app for auto-protect, Smart Rules, app whitelist, and Screen Sentinel |
| **Run at startup** | Auto-start Salva after device reboot to maintain continuous protection |
| **Vibration** | Haptic feedback when switching modes or interacting with the shield |
| **Camera** (optional) | QR code scanning for household device pairing only |
| **Internet** | Sync household data with our cloud backend |
| **Exact alarms** | Schedule precise protection mode transitions for Scheduled Protection |
| **In-app purchases** | Process subscriptions through Google Play Billing |

All permissions are used solely for their stated purpose. The Accessibility Service is used exclusively for screen protection, touch interception, and content monitoring — never for collecting personal information.

---

## 5. Children's Privacy

Salva is a **tool for parents**, not a child-directed app. We take children's privacy seriously:

- **Child devices do not require a Google account.** They are paired to a household via QR code or 6-digit pairing code with the physical presence of a parent.
- **No IP address is stored** for child devices (`lastIp` and `lastRegion` are set to NULL).
- **Only a pseudonymous device fingerprint** (SHA-256 hash of device identifiers) is collected from child devices — no personal data.
- **Geo-spread detection** for child devices relies on the parent device's region at pairing time, not the child device's location.
- **Content alerts** from child devices include only a category label, app name, and short snippet (max 100 characters), and are automatically purged after 7 days.
- **Screen Sentinel** processes all screen text locally on the child device. No raw screen content leaves the device.
- **Children see no popups, notifications, or interruptions** from Salva's monitoring features — all alerts go exclusively to the parent.

We comply with the Children's Online Privacy Protection Act (COPPA) by collecting no personal information from children beyond a pseudonymous device fingerprint used for device management.

---

## 6. Third-Party Services

| Service | Purpose | Data Shared |
|---------|---------|-------------|
| **Supabase** (hosted PostgreSQL + Edge Functions) | Cloud backend for household sync, device management, alerts, rules, heartbeat, and entitlement verification | See Section 2.2 above |
| **Google Play Billing** | Subscription management and payment processing | Purchase tokens, plan tier, subscription status |
| **Google Play Integrity API** | Device integrity verification for anti-fraud and anti-tamper protection | Device integrity verdicts |
| **MaxMind GeoIP2** (at API gateway only) | Coarse region derivation from IP address for anti-abuse geo-spread detection | IP is truncated at the gateway; only a coarse region string is stored |

We do **not** use:
- Advertising networks (no AdMob, no ads of any kind)
- Third-party analytics services (no Firebase Analytics, no Mixpanel)
- Social media tracking pixels
- Any data broker services

---

## 7. Data Security

We implement the following security measures to protect your data:

- **On-device encryption** — Sensitive local data (settings, patterns, tokens) is stored in Android's EncryptedSharedPreferences backed by the hardware-level Android Keystore
- **Transport encryption** — All communication between the app and our cloud backend uses HTTPS/TLS
- **Pseudonymous identifiers** — Device fingerprints are SHA-256 hashed before storage
- **IP truncation** — Full IP addresses are never stored; only a truncated form is retained temporarily at the gateway level
- **Token-based authentication** — Device-bound refresh tokens with Keystore binding for entitlement verification
- **Row-level security** — Supabase enforces row-level security policies so users can only access their own household data
- **Integrity verification** — Google Play Integrity API checks ensure the app is running on genuine, untampered devices
- **Anti-abuse monitoring** — Automated detection of suspicious pairing patterns, geo-spread anomalies, and device farming

---

## 8. Data Retention & Deletion

### Automated Retention Schedules

| Data | Retention Period |
|------|-----------------|
| Content alerts | 7 days (auto-purged) |
| Device heartbeat | Overwritten every 15 seconds (only latest state) |
| Truncated IP addresses | 30-day rolling purge |
| Coarse region data | 90-day rolling purge |
| Pairing tokens | Hard-deleted 7 days after expiry |
| Device removal logs | Hard-deleted after 1 year |
| Abuse flags | 180 days or resolution + 90 days (whichever is shorter); details then redacted |
| Stale devices | Auto-marked inactive after 90 days of inactivity |

### User-Initiated Deletion

You can delete your data at any time through the following methods:

- **Clear individual alerts** — Manually remove specific content alerts from the parent dashboard
- **Remove a device from household** — All cloud data for that device (heartbeat, alerts, rewards) is permanently deleted
- **Delete household** — Settings → Account → Manage Household → "Delete Household" removes all household data from the cloud with cascading deletion of all associated records
- **Delete My Data** — Settings → Account → "Delete My Data" removes all account and household data from our cloud servers. This also nullifies all IP/region fields, anonymizes abuse flag details, and removes device removal log entries. Local data remains on-device until the app is uninstalled.
- **Uninstall the app** — Removes all local data (settings, reports, patterns) from your device. Cloud data persists until you use one of the deletion options above or until automated retention schedules expire.

---

## 9. Subscriptions & Payments

- All payments are processed exclusively through **Google Play Billing**. We never collect or store your credit card number, bank account details, or other financial information directly.
- Salva offers a **free tier** with core protection features — no ads, no hidden charges.
- Premium plans include a **7-day free trial**. Only one trial is allowed per Google account. If you do not cancel before the trial ends, your subscription will automatically convert to a paid plan. If you cancel during the trial, your account reverts to the free tier with no charge.
- You can manage or cancel your subscription at any time through the Google Play Store.

---

## 10. Your Rights

Depending on your jurisdiction, you may have the following rights regarding your personal data:

- **Right of access** — Request a copy of the data we hold about you
- **Right to rectification** — Request correction of inaccurate data
- **Right to erasure** — Request deletion of your data (available in-app via "Delete My Data")
- **Right to data portability** — Request your data in a portable format
- **Right to restrict processing** — Request that we limit how we use your data
- **Right to object** — Object to specific data processing activities
- **Right to withdraw consent** — Withdraw consent at any time by disabling permissions, removing devices, or deleting your account

To exercise any of these rights, contact us at [tantoun1808@gmail.com](mailto:tantoun1808@gmail.com). We will respond within 30 days.

**For EU/EEA residents (GDPR):** Our legal bases for processing data include: (a) performance of a contract (providing the service you subscribed to), (b) legitimate interests (security, anti-fraud), and (c) consent (optional features like Screen Sentinel alerts).

---

## 11. International Data Transfers

Our cloud backend is hosted on Supabase infrastructure. If you are located outside the region where our servers are hosted, your data may be transferred internationally. We ensure appropriate safeguards are in place for any such transfers in compliance with applicable data protection laws.

---

## 12. Changes to This Privacy Policy

We may update this Privacy Policy from time to time. When we make material changes, we will:

- Update the "Last Updated" date at the top of this policy
- Notify users through an in-app notification or update notes

We encourage you to review this Privacy Policy periodically. Your continued use of Salva after changes are posted constitutes your acceptance of the revised policy.

---

## 13. Contact Us

If you have any questions, concerns, or requests regarding this Privacy Policy or our data practices, please contact us:

**Email:** [tantoun1808@gmail.com](mailto:tantoun1808@gmail.com)
**Developer:** Anthony Mallah
**App:** Salva for Android

---

*This privacy policy applies to the Salva Android application (package: com.salva.app) distributed through the Google Play Store.*
