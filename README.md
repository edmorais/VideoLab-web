# Videolab — web edition

Videolab is an educational simulator of digital video. You see, and change, the
technical properties of a moving picture while it plays:

1. **Resolution** — resample to 2160 … 36 lines, nearest-neighbour or bilinear scaling.
2. **Frame rate** — 60 … 2 fps sample-and-hold, with 360°, 180° or 45° shutter (motion blur).
3. **Aspect ratio** — 4:3, 16:9, 1.85, 2.39 pictures on 4:3 or 16:9 monitors; box, crop or stretch; anamorphic squeeze and unsqueeze.
4. **Interlaced scanning** — progressive, woven fields, single field, bob; 50 Hz or 60 Hz; thicker scan lines.
5. **Chroma sampling** — Y′CbCr 4:4:4, 4:2:2, 4:2:0, 4:1:1; luma and chroma on/off; exaggerated chroma blocks.
6. **Colour depth** — 8 … 1 bits per channel, ordered dithering, gradient chart.

Sources: the built-in test card, the webcam, or any video or image file (open it or drop it on the deck).
Every lab has a tutorial in English and Portuguese.

See it in action at <https://edmorais.github.io/VideoLab-web/>

The original Videolab was written in Processing by Eduardo Morais (2013–2021):
<https://github.com/edmorais/VideoLab>

This web version was remade using Claude Opus 5.5. 

## Run it

The page loads its language files with `fetch`, so serve the folder over HTTP:

```sh
cd videolab-web
python3 -m http.server 8000
# open http://localhost:8000
```

The webcam works on `https://` addresses and on `localhost`. Browsers block it on plain `http://`
addresses and inside most embedded frames. The test signal and local files work everywhere.

## Files

```
index.html     the whole app: markup, styles and script
i18n/en.json   English interface tips, messages, figure labels and tutorials
i18n/pt.json   Portuguese (pt-PT) version of the same
```

Each language file has four parts:

- `ui.tips` — tooltips and accessible names for the controls.
- `msg` — on-screen messages (camera errors, file errors, snapshots).
- `fig` — words used inside the tutorial diagrams.
- `help.<topic>.pages[]` — tutorial pages. Each page has `title`, `body` (HTML),
  an optional `figure` (a diagram name from `FIG` in `index.html`) and optional `targets`
  (values of `data-help` attributes to highlight while the page is open).

To add a language, copy `en.json` to `xx.json`, translate it, and extend the language key
in `index.html` (`#k-lang`), which now toggles between `en` and `pt`.

The hardware labels on the panel stay in English in both languages, as in the original
Videolab, so that students learn the bilingual vocabulary of video equipment.

## Keyboard

| Key | Action |
| --- | --- |
| Space | still / play |
| ↑ ↓ | playback speed (1/16× … 2×) |
| 1–6, 0 | choose a lab, or switch labs off |
| Z, Shift+Z | zoom in, zoom out (click the screen to aim, drag to pan, double-click for ×4) |
| M | 4:3 or 16:9 monitor |
| O | on-screen text |
| Shift+S | save the picture as PNG |
| H, ?, F1 | tutorial (← → turn pages) |
| L | language |
| Esc | close the tutorial, or leave the lab |

A lab can also be opened from the address: `index.html#sampling` (`res`, `fps`, `aspect`,
`interlace`, `sampling`, `depth`).

## Notes on the simulation

- Processing runs on a working copy of the picture up to 960 pixels wide.
  The Resolution lab works from the full source frame.
- On the test signal, the Frame rate and Interlace labs render the scene at the exact
  instant of each frame, field or shutter sample. Camera and file sources can only offer
  the frame the browser has, so their shutter blur is built from successive display frames.
- Chroma conversion uses BT.601 weights; chroma blocks are averaged, as an encoder's filter would.
- Most screens show 8 bits per channel, so colour depths above 8 bits cannot be simulated.
