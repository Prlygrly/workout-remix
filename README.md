# Workout Remix

Stitch several YouTube videos into one back-to-back workout with **no breaks and no mid-video interruptions**, then share it as a single link.

Built for doing workout videos together over a video call: one person builds a mix (e.g. a 10-min + 15-min + 30-min video = one 55-min workout), texts the link to the other, and both press **Start** at the same moment. Because the videos auto-advance with no interstitials, the two screens stay aligned.

## How to use it

**Build a workout** — open the page with no link parameters (just the plain URL). Paste YouTube links or video IDs, reorder them, and hit **Copy share link**. Optionally name and **Save** it for reuse.

**Do a workout** — open a share link. Tap **▶ Start Workout** once (this also unlocks sound on iPad/iPhone). Videos play one after another; a progress bar shows which video you're on and total time left.

## The ad story (important, and honest)

YouTube's **embedded** player generally serves no mid-roll ads to signed-out viewers — this is the same mechanism that makes workout videos on sites like PopSugar play cleanly. This app is just a well-behaved embed, so a viewer *without* YouTube Premium gets the same clean playback they'd get on those sites.

Caveats:
- **This is empirical, not a YouTube guarantee.** YouTube controls ad behavior in embeds and could change it; if that ever happens, sites like PopSugar break the same way. Use the **Preview** button to check any video before relying on it for a workout.
- Some video owners **disable embedding** — those can't be used. The builder detects this the moment you add such a video and warns you.
- A person *with* YouTube Premium never sees ads anywhere, so this changes nothing for them.

## Share link format

```
.../index.html?v=VIDEOID:SECONDS,VIDEOID:SECONDS,...&t=Optional%20Name
```

Each entry is a video ID and its duration in seconds (duration is captured when you add the video, so the player can show total time remaining right away). The `t` parameter is an optional workout name. Hand-editing this URL works too; if a duration is missing the player still plays the video and just shows less-precise timing.

## Hosting

Single static file — no build step, no server, no dependencies except YouTube's own IFrame API script. Host it anywhere that serves static files. It's set up for **GitHub Pages**:

1. Push this repo to GitHub.
2. Repo **Settings → Pages → Deploy from branch → `main` / root**.
3. The link becomes `https://<user>.github.io/<repo>/`.

Every push redeploys for free. (This project intentionally has nothing to do with Netlify.)

## Notes

- Saved workouts live in the browser's `localStorage`, so they're per-device — saving on the PC doesn't carry to the iPad. Sharing is done via links, not sync.
- iPad/iPhone play inline (not forced fullscreen) thanks to `playsinline`; tap the video's fullscreen control if you want it full-screen on the TV or tablet.
