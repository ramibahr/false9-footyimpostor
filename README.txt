FALSE NINE — DEPLOY FOLDER
===========================

This folder is ready to host. It contains:
  - index.html   (the game)
  - sw.js        (service worker, makes it work offline once installed)

STEP 1 — Get it live (free, ~2 minutes, no signup)
---------------------------------------------------
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. Netlify gives you a live https:// URL immediately.
   (You can claim/rename it later with a free Netlify account if you want
   a nicer URL, e.g. false9.netlify.app instead of a random name.)

Alternative: GitHub Pages
1. Create a new GitHub repo, upload index.html and sw.js to it.
2. Repo Settings → Pages → set source to the main branch.
3. GitHub gives you a URL like yourname.github.io/repo-name.

Once it's hosted, visiting the URL on a phone and tapping
"Add to Home Screen" installs it as a real full-screen app — this works
today, on both iPhone and Android, with no app store review needed.


STEP 2 — Google Play (optional, ~$25 one-time, a few hours of work)
---------------------------------------------------------------------
1. Go to https://www.pwabuilder.com
2. Enter your hosted URL from Step 1.
3. Let it analyze the site, then generate the Android package (it uses
   Google's own Trusted Web Activity tooling behind the scenes).
4. It will also generate a file called assetlinks.json — you need to
   host that at:
       https://yourdomain.com/.well-known/assetlinks.json
   This proves you own both the website and the app, so Android doesn't
   show browser address-bar UI in the installed app.
5. Create a Google Play Console developer account (one-time ~$25 fee):
   https://play.google.com/console
6. Upload the .aab file PWABuilder gave you, fill in the store listing
   (screenshots, short description, privacy policy URL — required even
   for simple apps), and submit for review.

Google's review for this kind of app is generally quick and low-friction
compared to Apple's.


STEP 3 — Apple App Store (optional, harder, higher risk)
------------------------------------------------------------
Apple is much stricter about apps that are "just a website in a wrapper."
If you want to attempt this later, the realistic path is:
  - Use Capacitor (not a raw webview) to bundle these files as local
    app assets, so nothing loads over the network at runtime.
  - Swap the vibration calls for Capacitor's native Haptics plugin.
  - Add a native splash screen via Capacitor's config.
  - You'll need a Mac with Xcode and an Apple Developer Program
    membership (~$99/year) to build and submit it.
Budget for at least one rejection-and-resubmit cycle even if you do
all of the above — this is normal, not a sign something's wrong.
