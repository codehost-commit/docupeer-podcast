# DocuPeer Podcast

A private, browser-based podcast room for up to **4 people**. No installs, no accounts, no server to run. You host a room, share a code, and everyone joins with camera and mic. The layout switches automatically to whoever is speaking, and the host can record the whole thing as a single video for the DocuPeer website.

## What's in this folder

| File | What it is |
|------|------------|
| `index.html` | The entire app (HTML + CSS + JavaScript in one file). |
| `peerjs.min.js` | The PeerJS library (v1.5.4), bundled locally so there's no CDN dependency. |
| `DocuPeer.png` | The logo, used in the app and as the browser-tab icon. |
| `README.md` | This file. |

Keep all four files together in the same folder.

## Put it online (GitHub Pages)

1. Create a new repository on GitHub (it can be private or public).
2. Upload the **contents** of this folder — `index.html`, `peerjs.min.js`, and `DocuPeer.png` — to the repository root.
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**, pick your `main` branch and the `/ (root)` folder, then **Save**.
5. Wait about a minute. GitHub gives you a URL like `https://yourname.github.io/your-repo/`.
6. Open that URL — you'll see the DocuPeer Podcast lobby. Share the link with your co-hosts.

That's it. Because the page is fully self-contained, dropping the folder into any static host (GitHub Pages, Netlify, etc.) just works.

> **HTTPS is required** for camera/microphone access. GitHub Pages is always HTTPS, so you're covered. (Opening `index.html` directly from your hard drive as a `file://` link will *not* let the camera work — use the Pages URL.)

## How to use it

**Host a session.** Enter your name and click *Host a new session*. You'll get a session code like `DP-4KX9-M2`. Click **Copy** and send it to your guests.

**Join a session.** Enter your name, type the code your host sent, and click *Join*.

**Everyone can:**
- Turn their **mic** on/off
- Turn their **camera** on/off
- **Rename** themselves (click your own name on your tile)
- **Share their screen** (screen share automatically takes the main stage; everyone else moves to the gallery on the right until sharing stops)

**The host can additionally:**
- **Rename anyone** (click any person's name on their tile)
- **Record** the session (the round Record button — only the host sees it)

**In Settings (gear button):**
- **Auto-feature the speaker** (everyone) — on by default. Turn it off to keep everyone in the equal gallery and never auto-switch.
- **Tap a person to feature them** (host only) — turn this on, then tap anyone's video to make them the big view *for everyone*; tap again (or use **Release** in Settings) to go back. This overrides the automatic switching while it's set.
- **Speaking sensitivity** — how easily your voice registers. Slide toward *More* if your timer keeps pausing while you talk, toward *Less* if background noise triggers it. It now defaults to a higher, more forgiving setting so timers stay steady through natural pauses.

**The automatic layout:**
- One person talking → they fill the main stage, everyone else in a gallery on the right
- One person clearly louder than the others → that person takes the main stage
- Several people talking at once with nobody dominating → everyone shares an equal gallery
- Nobody talking → everyone in the equal gallery

**Speaking timers** on the left track how long each person has actually spoken. If two people talk at the same time, both of their timers count up.

## Recording

Only the host records, and the recording happens **in the host's browser**. It captures the composed view — the automatic layout switching, the timers, everyone's video and mixed audio — exactly as it looked.

- Press **Record** to start, press it again (**Stop**) to finish.
- When you stop, the video **downloads automatically** to the host's computer.
- The file is named like `docupeer-podcast-20260820-1430.mp4`.
- Recording auto-stops at **60 minutes** or if it reaches the size cap, whichever comes first.
- At about **450 kbps video + 96 kbps audio**, a full hour comes out around **240 MB** — under your 250 MB target.

That downloaded file is the one you upload to the DocuPeer website.

> **File format:** Chrome, Edge, and Safari (recent versions) save a real **`.mp4`**. If a browser can't record MP4, DocuPeer falls back to `.webm` (it still plays everywhere and can be converted to MP4 if a specific tool requires it). For a guaranteed MP4, have the host use an up-to-date Chrome or Edge.

## Good to know / limits

- **Best in Chrome, Edge, or Safari** on a computer with a decent connection.
- Built for **4 people** — it's a full peer-to-peer mesh, which is ideal for a small podcast.
- It uses free public **STUN** servers to help browsers connect. On most home and office networks that's all that's needed. On unusually strict corporate or locked-down networks, one person occasionally can't connect peer-to-peer — switching networks (or a phone hotspot) fixes it. Adding a paid TURN server would remove that edge case if you ever need it.
- Everyone sees the **same automatic layout** — that's the point, so the recording looks like a produced podcast.
- Nothing is uploaded anywhere. Audio and video go directly between participants, and the recording lives only on the host's computer until they choose to share it.
