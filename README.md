# Between Us

A private board for two people: live status (working, sleeping, in a meeting…), mood check-ins every four hours on a 24-hour dial, tasks for each other, pinned notes with read receipts, and chat with reactions.

It is a plain web app. Host these files anywhere static (GitHub Pages, Netlify, Firebase Hosting), open the address, and follow the setup screen. Your partner only needs the invite link: no account, no install.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole app |
| `sw.js` | Offline support and notification taps |
| `manifest.webmanifest`, `icon-*.png` | Lets phones add it to the home screen as an app |
| `firestore.rules` | Security rules to paste into Firebase |

## One-time setup (about 10 minutes)

1. Host the files (see below) and open the address.
2. Tap **Set up a new board**. The screen walks you through creating a free Firebase project:
   Firestore database, the security rules from `firestore.rules`, Anonymous sign-in, and copying the web config.
3. Paste the config and tap **Create our board**. You get an invite link.
4. Send the link to your partner. They open it, type their name, and tap **Join**.

## Hosting on GitHub Pages

1. Create a public repository and upload these files to it (Add file → Upload files).
2. Settings → Pages → Source: *Deploy from a branch* → `main` / root → Save.
3. After a minute the app is live at `https://<your-username>.github.io/<repo-name>/`.

## Privacy

- Everything you type is encrypted on your phones (AES-GCM) before it is saved. The key exists only inside the invite link, after the `#`, which browsers never send to any server. Firebase stores unreadable text.
- Anyone who has the invite link can open the board. Share it only with your partner.
- Optional push alerts go through the free ntfy service and only say who did something ("Talha sent a message"), never what.

## Limits

- Phone notifications while the app is fully closed need the optional ntfy push (Updates → Push alerts when the app is closed).
- Free Firebase limits (50,000 reads and 20,000 writes a day) are far above what two people use.
- On iPhone, a home-screen app keeps its own storage. Open it once, tap the paste box, and paste the invite link.
