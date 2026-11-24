# Harmony Lab · Offline practice guide

Harmony Lab runs on your computer and generates sound in your browser. Use it to compare intervals, build chords, identify what you hear, check an instrument’s pitch, and practice keeping time.

## Open the lab

1. Start with the separately supplied **`Harmony_Lab_Offline.zip`** practice package. On Windows, right-click the ZIP and choose **Extract All**. On macOS, double-click the ZIP to extract it.
2. Open **`Harmony-Lab.html`** from the extracted folder in desktop Chrome or Edge. You can disconnect from the internet before opening it. The single HTML file contains the application, styles, and audio code.
3. In **Intervals**, click **Compare A → B**. You should hear two pairs of notes and see the corresponding piano keys light up. Adjust the volume at the top of the lab.

## Try a first practice session

| Tab | What to do | What to listen or look for |
| --- | --- | --- |
| **Intervals** | Set the root to C, interval A to **Minor third**, and B to **Major third**. Choose **One at a time**, click **Compare A → B**, then repeat with **Together**. | Both start on C. The upper note moves from E♭ to E. Listen for that one-semitone change. |
| **Triads** | Choose C and **Major**. Click **Play chord**, then **Play one note at a time**. Switch to **Minor** and repeat. | C–E–G becomes C–E♭–G. Try picking out the middle note when all three sound together. |
| **Progressions** | In C major, choose **ii – V – I** and click **Play progression**. Change the last chord to **vi** and play again. | Dm–G–C resolves to the tonic. Dm–G–Am gives the same opening a different ending. |
| **Ear training** | Click **New interval**. Listen to both notes and choose the interval you heard. Use **Replay** to hear the same pair again. | Each answer updates your session score. After a miss, replay the pair with the correct interval name in mind. |
| **Pitch meter** | Click **Start microphone**, allow access, and play one sustained note on an instrument. Click **Stop microphone** when finished. | The meter shows the nearest note, frequency, and tuning offset. A4 is 440 Hz. Negative cents mean flat, positive cents mean sharp. |
| **Rhythm** | Start at **60 BPM**. Click **Start round**, listen through four count-in clicks, then press **Space** or tap the pad on each of the next eight clicks. | Each tap shows how early or late it landed. The round summary shows beats tapped, misses, extra taps, and mean timing error. |

## If something feels off

- **The page opens but you hear silence.** Click a playback button, check the lab’s volume, then check the browser tab’s mute setting and the system output device.
- **The pitch meter stays blank.** Check microphone permission in both the browser and the operating system. Play a single steady note near the selected microphone. The meter releases the microphone when you stop it or leave the exercise.
- **Every tap lands late by a similar amount.** Repeat the round with wired headphones or built-in speakers. The app runs locally, but your audio device can still add playback delay.
- **Your score reset.** The ear-training tally lasts for the current page session. Reloading the file starts a fresh session.

## Optional · Embed in a Tauri + Vite + React app

The practice package includes a React panel and editable source. From the extracted package:

1. Copy `Harmony-Lab.html` into your Vite frontend’s `public/` directory and `HarmonyLabPanel.tsx` into `src/`.
2. Import the named `HarmonyLabPanel` component into your practice screen and render `<HarmonyLabPanel />` while that screen is active. Unmount it on navigation to release microphone access.
3. Start the host project with `npm run tauri dev`. Check playback and microphone permission inside the desktop window. The WebView’s permissions can differ from your browser’s.
4. If your host blocks inline scripts, copy the contents of the package’s `dist/` into `public/harmony/` and set the panel’s iframe source to `import.meta.env.BASE_URL + "harmony/index.html"`.

To edit the standalone edition, change the source in the extracted package’s `dist/` folder, then run `node build.cjs` from the package root to regenerate `Harmony-Lab.html`.
