# DocuPeer Podcast

A private, browser-based podcast room. No installs, no sign-ups, no server to run. You start a room, share the **link**, and everyone joins with camera and mic. The layout follows whoever's speaking, and the host can record the whole thing as one video for the DocuPeer website.

## What's in this folder

| File | What it is |
|------|------------|
| `index.html` | The entire app (HTML + CSS + JavaScript in one file). |
| `peerjs.min.js` | The PeerJS library (v1.5.4), bundled locally so there's no CDN dependency. |
| `DocuPeer.png` | The logo, used in the app and as the browser-tab icon. |
| `README.md` | This file. |

Keep all four files together in the same folder.

## Put it online (GitHub Pages)

1. Create a new repository on GitHub (public or private).
2. Upload the **contents** of this folder — `index.html`, `peerjs.min.js`, and `DocuPeer.png` — to the repository root.
3. In the repo: **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**, pick your `main` branch and the `/ (root)` folder, then **Save**.
5. Wait about a minute for the URL, e.g. `https://yourname.github.io/your-repo/`.

Because the page is fully self-contained, dropping the folder into any static host just works. **HTTPS is required** for camera/mic — GitHub Pages is always HTTPS, so you're covered. (Opening the file directly from disk as `file://` won't allow the camera; use the Pages URL.)

## Persistent room links (like a meeting link)

When you start a room, the address bar becomes something like `…/your-repo/#m=dp4kx9m2`. **That link is the room.** Share it with your co-hosts however you like. Anyone who opens it lands in that room, and if anyone **refreshes the page or closes and reopens the link, they drop straight back into the same room** — nothing is lost. Your name is remembered, so re-joining is one tap.

You can also share just the short **room code** (shown top-left, e.g. `DP-4KX9-M2`); a guest can paste either the code or the full link on the start screen.

> The person who *starts* the room is its host. **If the host refreshes or briefly drops, everyone else stays connected and keeps talking** — the guests are linked directly to each other, not routed through the host — and the host automatically slips back in on reload. New people can join whenever the host is present; while the host is momentarily away, the existing group carries on and the host rejoins within a few seconds.

## How to use it

**Start a room.** Enter your name, click *Start a new room*. Share the link (top-left **Copy link**) or the room code with your guests.

**Join a room.** Open the link someone shared and click *Join room*, or enter your name, paste the code/link on the start screen, and click *Join*.

**Everyone can:**
- Turn their **mic** on/off
- Turn their **camera** on/off
- **Rename** themselves (tap your own name on your tile)
- **Share their screen** (a screen share automatically takes the main stage; everyone else moves to the gallery until sharing stops)

**The host can additionally:**
- **Mute anyone** or **turn anyone's camera off** — the small buttons on the top-right of each person's video. (They can turn their own mic/camera back on themselves — like most meeting apps, the host can switch off but not force-on.)
- **Rename anyone** (tap any person's name)
- **Record** the session (the Record button — only the host has it)
- Control the room's **layout and speaking sensitivity** in Settings (below)

**How many people?** There's no fixed limit — invite as many as you need. It's a direct peer-to-peer mesh, so it's happiest with a small podcast-sized group (roughly up to 6–8 on good connections); larger groups put more load on each person's browser.

**In Settings (gear button) — host only.** These apply to the whole room so everyone sees the same thing:
- **Auto-feature the speaker** — on by default. Makes whoever's talking the big view. The switch is eased and rate-limited, so it stays calm instead of jumpy — a person has to hold the floor for a moment before taking the spotlight. Turn it off to keep everyone in an equal gallery.
- **Tap a person to feature them** — turn on, then tap anyone's video to make them the big view *for everyone*; tap again (or **Release** in Settings) to go back.
- **Speaking sensitivity** — one setting for everyone's mics. Slide toward *More* if the speaking timers pause mid-sentence, toward *Less* if background noise sets them off.

Guests don't see these controls — only the host runs the layout and sensitivity.

**Speaking timers** on the left (a strip across the top on phones) show how long each person has actually spoken. The **host's device is the single source of truth** — it tallies everyone's time and everyone else's screen mirrors the host's numbers exactly, so there's no drift or disagreement between people. If two people talk at once, both count up. (The host's tallies survive a host refresh.)

## Recording

Only the host records, and it happens **in the host's browser**. It captures the composed view — the layout switching, the timers, everyone's video and mixed audio — exactly as it looked.

- Press **Record** to start, press again (**Stop**) to finish.
- On stop, the video **downloads automatically** to the host's computer, named like `docupeer-podcast-20260820-1430.mp4`.
- Auto-stops at **60 minutes** or a size cap, whichever comes first.
- At ~450 kbps video + 96 kbps audio, a full hour is around **240 MB** — under 250 MB.

That downloaded file is what you upload to the DocuPeer website.

> **Format:** recent Chrome, Edge, and Safari save a real **`.mp4`**. If a browser can't record MP4, it falls back to `.webm` (plays everywhere, convertible to MP4). For a guaranteed MP4, have the host use an up-to-date Chrome or Edge.

## Works on phones

The whole thing is built to work on a phone — one of your hosts can join from mobile. On a narrow screen the speaking times become a strip along the top, the speaker fills the screen with a swipeable filmstrip of everyone else beneath, and all controls stay labeled and reachable.

## Good to know

- **Best in Chrome, Edge, or Safari** with a decent connection.
- It uses free public **STUN** servers so browsers can find each other. That's enough on most home and mobile networks. On unusually locked-down corporate networks one person can occasionally fail to connect peer-to-peer — switching networks (or a phone hotspot) fixes it; a paid TURN server would remove that edge case entirely if you ever need it.
- Nothing is uploaded anywhere. Audio and video go directly between participants, and the recording stays on the host's computer until they choose to share it.
