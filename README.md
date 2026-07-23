# OpenShop Admin

🇭🇰 OpenShop platform **admin** app/dashboard — manage merchants, drivers, orders, billing. Internal use by opensystem staff only.

> **Brand:** OpenShop → opensystem
> **App type:** Internal admin
> **Platform:** Android (Kotlin + Jetpack Compose) — future companion to web admin
> **Backend:** Firebase + custom Cloud Functions
> **Auth:** Restricted to @opensystem.hk emails + 2FA

## 🎯 Purpose

Platform operations:
- 🏪 **Merchant management** — onboarding, KYC review, status changes, tier upgrades
- 🛵 **Driver / fleet management** — assign to OpenVan routes, monitor fleet
- 📦 **Order monitoring** — real-time view across all merchants, intervene on stuck orders
- 💰 **Billing & commissions** — generate payouts, view commission ledger, handle disputes
- 📊 **Analytics** — DAU, GMV, take-rate, fulfillment rate
- 🛠 **Platform config** — payment gateway toggle, commission slabs, promotional codes

## 🛡️ Security

- 🔒 App distribution limited to internal Firebase testers
- 🔐 All admin actions logged with operator ID + timestamp
- 🚫 No public exposure — no Play Store listing
- 📧 SSO with corporate email

## 🏗️ Stack

| Layer | Tech |
|---|---|
| Language | Kotlin 1.9+ |
| UI | Jetpack Compose (data-heavy layouts + charts) |
| Charts | Vico / MPAndroidChart |
| Auth | Firebase Auth + custom claims (admin role) |
| DB | Firebase Firestore (admin-scoped via Security Rules) |
| Push | FCM (admin alerts — stuck orders, KYC review needed, etc.) |

## 🚀 Building

```bash
studio . &
./gradlew :app:assembleDebug
# APK → app-debug.apk → Firebase App Distribution (internal track)
```

## 🔗 Related Repos

- `gary3159/openshop-customer`
- `gary3159/openshop-pos`
- `gary3159/opensystem` — umbrella
