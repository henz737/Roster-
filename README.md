# Malawi Airlines Roster Builder: iOS prototype

This folder wraps the crew roster planner as a native iOS app using Capacitor.
The whole app lives in `www/index.html`; Capacitor puts it inside an iPhone app shell.

## What you need
- A Mac with Xcode (free from the Mac App Store)
- Node.js 20 or newer (nodejs.org)
- An Apple Developer Program membership (99 USD a year) to share through TestFlight.
  A free Apple ID is enough to run it on your own iPhone, but the install expires after 7 days.

## 1. Build the iOS project
Open Terminal in this folder and run:

    npm install
    npx cap add ios
    npx cap open ios

Xcode opens the project.

## 2. Set it up in Xcode
1. Click the **App** project, then the **Signing & Capabilities** tab.
2. Choose your **Team** (sign in with your Apple ID if asked).
3. Change the **Bundle Identifier** to something unique, e.g. `com.yourname.marosterbuilder`
   (and update `appId` in `capacitor.config.json` to match).
4. Open **App > Assets > AppIcon** and drag in `resources/icon-1024.png`.

## 3. Run it
- **Simulator:** pick an iPhone at the top of Xcode and press Run.
- **Your iPhone:** plug it in, select it, press Run. On the phone, trust the developer under
  Settings > General > VPN & Device Management. Turn on Developer Mode if prompted.

## 4. Share it with testers (TestFlight)
1. In App Store Connect (appstoreconnect.apple.com), create a new app with the same Bundle Identifier.
2. In Xcode choose **Any iOS Device**, then **Product > Archive**.
3. In the Organizer window click **Distribute App > App Store Connect > Upload**.
4. After processing (usually 10 to 30 minutes), open the **TestFlight** tab in App Store Connect.
   - Internal testers (up to 100 people on your team): available straight away, no review.
   - External testers (up to 10,000 by email or public link): needs a short beta review first.
5. Testers install the TestFlight app and accept the invite.

## Updating the app
Replace `www/index.html` with the new version, then run:

    npx cap copy ios

and press Run (or Archive again for TestFlight).

## Notes
- Data (crew, flights, rules) is saved on the device and stays there between launches.
- The app runs fully offline. Everything, including fonts, is inside the app, and nothing is loaded from the internet.
- For a full App Store release, Apple often rejects apps that are only a web page in a wrapper
  (guideline 4.2). For a public launch you would add native features such as notifications,
  login and a shared server so the whole crew sees the same roster.
