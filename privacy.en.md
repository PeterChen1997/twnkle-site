---
title: Privacy Policy
lang: en-US
---
# Twnkle Privacy Policy

Effective date: 2026-10-19

Twnkle (the "App") is a local-first reminder tool. Our principle is simple: **your data stays on your own devices and in your own iCloud, and we do not collect any of your personal information.** The only exceptions are the ones described below: "Anonymous Usage Stats" (see Section 1) sends anonymous activity records, which contain none of your content, to a statistics service we host ourselves, and you can turn it off at any time; the Android and Mac versions request a version manifest from our website when they check for updates (see Section 1); and unlocking Pro on Android requires you to email us yourself to request an activation code (see Section 4).

## 1. What Data We Collect

**We do not collect personal information.** The App has no account system and does not include any third-party analytics or advertising SDKs. Everything you enter in the App, such as reminder content, times, and voice transcription results, is stored only in the local database on your device and is not sent to our servers.

### Anonymous Usage Stats (on by default, can be turned off at any time)

To learn which features people use and where things tend to go wrong, the App sends **anonymous activity records** to an open-source statistics service (Umami) that we deploy ourselves, without going through any third-party analytics platform. Specifically:

- **What is sent**: the type of action (such as "added an item", "completed an item", "opened the paywall") and its enumerated properties (such as whether the reminder mode is "Alarm" or "Notification", and whether the source was "typing" or "voice"), the current screen, OS version, device model, language, screen size, App version, and a randomly generated anonymous device identifier (used only to group actions from the same device into one session).
- **What is not sent**: anything you enter, such as reminder titles, times, voice transcription text, or backup contents, and any information that could identify you, such as your name, account, phone number, precise location, or advertising identifier.
- **How to turn it off**: Settings → Data → Anonymous Usage Stats. Once it is off, sending stops immediately and any records not yet sent are deleted. Records that have already been sent cannot be recalled, but they contain no information that could identify you.
- **At the network level**: as with any network request, the statistics service receives the IP address the request comes from. Umami uses it (together with the system information above) to tell sessions apart, and may use it to infer your approximate country or region.
- The Mac version does not send Anonymous Usage Stats.

### Checking for Updates (Android and Mac versions)

The Android version is not distributed through an app store, and the Mac version is downloaded directly from our website, so both check for updates on their own:

- **Android version**: each time the App launches or returns to the foreground (at most once every 10 minutes), it requests the latest version manifest from `blog.peterchen97.cn/twnkle/android-latest.json`. When you tap "Update Now", the installer is downloaded from the same website.
- **Mac version**: 15 seconds after launch and every 6 hours after that, it requests the version manifest from `blog.peterchen97.cn/twnkle/mac-update.json`. When a new version is available, the update package is downloaded from the same website.

These requests do not carry your task content, account, or any device identifier. As with any network request, however, the website and its CDN receive your IP address and the time of the request, and may keep routine access logs. Updates for the iOS version are handled by the App Store, so it makes no such requests.

## 2. Where Data Is Stored

- **On your device**: All reminder data is stored in the App's sandbox on your device.
- **Your iCloud Drive (optional)**: If you are signed in to iCloud and have iCloud Drive turned on, the App backs up snapshots of your data to the App's own dedicated container in **your own iCloud account**, so you can restore them after switching devices or reinstalling. This data is stored by Apple under its [iCloud privacy policy](https://www.apple.com/legal/privacy/), and the developer cannot access it.
- **Backups on Android**: Backup files are written to a folder you choose yourself and stay in your own keeping. They do not pass through our servers.
- **Sync across Apple devices (iCloud / CloudKit)**: Between iPhone, iPad, and Mac signed in to the same iCloud account, the App uses Apple's CloudKit to sync your tasks (title, the original text you typed, time, repeat rule, reminder mode, and list) and the status of each reminder (completed, snoozed, overdue, and so on). This data is kept in the **CloudKit private database of your own iCloud account**, stored by Apple under its privacy policy, and the developer cannot access it. Sync turns on automatically when you are signed in to iCloud; there is no separate switch in the App, and the sync status is shown in Settings → Sync Across Devices. Sync stops if you sign out of iCloud. The Android version does not take part in sync.

## 3. How We Use Permissions

| Permission | Purpose | Notes |
|---|---|---|
| Notifications | Delivers local notifications when a "Notification" reminder is due | All reminders are local notifications scheduled on your device. For sync across devices, the App registers with Apple for remote notifications, used only to receive silent pushes from CloudKit (nothing is shown and nothing rings; they only tell the App to fetch the latest data from iCloud). We do not run a push server, and the push token is not sent to any of our servers |
| Alarms (AlarmKit) | Rings when an "Alarm" reminder is due, breaking through Silent mode and Focus | Carried out on your device by the iOS system alarm framework |
| Microphone, Speech Recognition | "Voice capture" turns what you say into text | Speech recognition is handled by Apple's speech recognition service (the Speech framework), which may send audio to Apple's servers to complete the transcription and is subject to the [Apple Privacy Policy](https://www.apple.com/legal/privacy/); on Android, the phone's built-in speech recognition service is used, subject to the privacy policy of that service's provider; the App does not save recordings |
| Photos | "My Photo" (Pro): pick one photo with the system photo picker to use as your home screen wallpaper; the App receives only the photo you pick, crops it, and keeps a copy on your device. On Android, when you tap "Save QR Code", the WeChat Pay QR code image is also saved to a Twnkle folder in your photo gallery | The system photo picker needs no Photos permission, and the App does not request one; the wallpaper stays on your device only, is not included in the App's iCloud backup snapshots or synced to your other devices, and is never uploaded; the App never reads or uploads your photo library (you may see a Photos purpose string in Settings because the system requires it to be declared) |
| Approximate Location (optional) | "Match the weather": switches the home screen wallpaper based on the weather in your city, and shows the weather at the due time next to tasks | Only approximate (city-level) location is requested; the coordinates are kept to two decimal places and stored on your device (if iCloud backup is on, they are also included in backup snapshots stored in your own iCloud), and are used to look up the weather from Apple Weather (WeatherKit); the App does not upload your location to our servers; you can turn it off in system Settings at any time, after which the wallpaper goes back to random |

Each permission is requested only when you first use the feature that needs it. Declining a permission does not affect your use of other features.

### Weather (optional)

When "Match the weather" is on, the App uses your approximate location to look up the local weather from Apple's WeatherKit service, in order to switch the home screen wallpaper and show the weather at the due time next to tasks. Weather data comes from [Apple Weather](https://weatherkit.apple.com/legal-attribution.html). Your location is used only on your device and is not uploaded to our servers.

### Invite Codes and "Invite a Friend" (hidden in the current version)

In earlier versions, "Invite a Friend" generated an invite code for you, and a friend who entered it received Pro for a period of time. This option is currently hidden, and Pro days already claimed remain valid. Here is how the related data is handled:

- Invite codes are **derived from a key randomly generated on your device**. That key is stored only in your device's Keychain and is **never uploaded**.
- Who claimed which code and how many days remain are recorded **only on your device**. The App has **no** server-side attribution or referral records of any kind.
- The QR code or link you share contains only the invite code itself, and does not include your name, account, or device information.

## 4. In-App Purchases

Twnkle Pro subscriptions and lifetime purchases are handled by the Apple App Store. Purchases, renewals, refunds, and payment information are all managed by Apple. The App only reads from the system whether you currently have an active entitlement, and **never has access to your payment information**. You can manage or cancel your subscription at any time in Settings → Apple Account → Subscriptions.

### Mac Membership Follows Your iPhone

The Mac version cannot make in-app purchases. So that the Mac version can follow the membership status of the iPhone signed in to the same iCloud account, the iPhone version writes your **Apple-signed purchase records** (issued by Apple, containing information such as the product purchased, purchase and expiration dates, and transaction identifiers) to the **CloudKit private database of your own iCloud account**. The Mac version retrieves them from there and verifies Apple's signature offline on your Mac. These records do not pass through our servers, and the developer cannot access them.

### Android Activation Codes

The Android version has no in-app purchases. To unlock Pro, you pay by scanning a WeChat Pay QR code (the payment is handled by WeChat) and then **email us yourself**, including the "device code" shown on the paywall and a screenshot of the payment. After confirming the payment, we issue an activation code for that device code; you paste it into the App, and the code is verified offline on your phone.

- **Device code**: an 8-character short code derived by one-way hashing the device identifier provided by Android (ANDROID_ID), used to tie the activation code to this phone. The App itself never sends it to any server; it appears only in the email you send.
- **What we receive**: your email address, the device code, and the payment screenshot, used only to confirm the payment and issue the activation code.

## 5. Children's Privacy

The App is not directed at children under 13 and does not knowingly collect personal information from any child (as described above, the App does not collect personal information from anyone).

## 6. Changes to This Policy

If this policy changes, we will announce it in the App's release notes and on this page. By continuing to use the App, you accept the updated policy.

## 7. Contact Us

If you have any questions about this policy, please contact: **peterchendone@gmail.com**
