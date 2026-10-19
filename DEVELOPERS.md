# Videolab: notes for developers

This file is for people who change or extend Videolab. For instructions on how to use the app, read [README.md](README.md).

## Files

```
index.html     the whole app: markup, styles and script
i18n/en.json   English interface tips, messages, figure labels and tutorials
i18n/pt.json   Portuguese (pt-PT) version of the same
docs/          images for the README
```

The page loads its language files with `fetch`. Serve the folder over HTTP:

```sh
cd videolab-web
python3 -m http.server 8000
# open http://localhost:8000
```

## Language files

Each language file has four parts:

- `ui.tips`: tooltips and accessible names for the controls.
- `msg`: on-screen messages (camera errors, file errors, snapshots).
- `fig`: words used inside the tutorial diagrams.
- `help.<topic>.pages[]`: tutorial pages. Each page has `title`, `body` (HTML), an optional `figure` (a diagram name from `FIG` in `index.html`) and optional `targets` (values of `data-help` attributes to highlight while the page is open).

To add a language, copy `en.json` to `xx.json` and translate it. Then extend the language key in `index.html` (`#k-lang`). At the moment, this key toggles between `en` and `pt`.

The labels on the panel keys stay in English in both languages, as in the original Videolab. Students learn the vocabulary that real video equipment uses.

## Notes on the simulation

- Processing runs on a working copy of the picture up to 960 pixels wide. The Resolution lab works from the full source frame.
- On the test signal, the Frame rate and Interlace labs render the scene at the exact instant of each frame, field or shutter sample. Camera and file sources can only give the frame that the browser has. For these sources, shutter blur is built from successive display frames.
- In the Interlace lab, each frame holds two fields. A rate of 25 frames per second gives 50 fields per second.
- Chroma conversion uses the BT.601 weights. Chroma blocks are averaged, as an encoder filter does.
- Most screens show 8 bits per channel, so colour depths above 8 bits cannot be simulated.
- The app keeps a few per-browser preferences in `localStorage`: language, monitor shape, and which tutorials the user has already seen.

## Original version

The original Videolab was written in Processing by Eduardo Morais (2013–2021): <https://github.com/edmorais/VideoLab>
