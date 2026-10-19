# Videolab 2.0 — web edition

**A laboratory for digital video, in your web browser.**

Videolab plays a moving picture and lets you change its technical properties while you watch. You can reduce the pixels, the frame rate or the colour information. You can also change the aspect ratio, or split the picture into interlaced fields. You see each effect at once.

Videolab is for students and teachers of film, video and multimedia. You can use it alone to learn, or project it in class to demonstrate a concept. The interface and the tutorials are in English and Portuguese.

See it in action at <https://edmorais.github.io/VideoLab-web/>

The original Videolab was written in Processing (2013–2021):
<https://github.com/edmorais/VideoLab>

This web version was remade using Claude Opus 5.5. 


## What you can learn

Videolab has six labs. Each lab simulates one concept and has a short illustrated tutorial.

| Lab | Concept |
| --- | --- |
| 1. Resolution | How many pixels make up the picture, and what happens when there are too few. |
| 2. Frame rate | How many pictures are recorded each second, and how the shutter adds motion blur. |
| 3. Aspect ratio | The shape of the picture, letterbox and pillarbox, and anamorphic formats. |
| 4. Interlaced scanning | Progressive and interlaced video, fields, and the combing effect. |
| 5. Chroma sampling | Luminance, chrominance, and chroma subsampling (4:4:4, 4:2:2, 4:2:0, 4:1:1). |
| 6. Colour depth | Bits per channel, banding, and dithering. |

## Open Videolab

Videolab runs in a web browser. You do not need to install anything. Use a current version of Chrome, Edge, Firefox or Safari. Videolab also works on tablets and phones.

**Published copy.** If you have the address of a published copy, open it in your browser.

**Your own copy.** Videolab must be opened from a web server. If you open `index.html` directly from your disk, the tutorials do not load. To start a server on your computer:

1. Open a terminal in the `videolab-web` folder.
2. Type `python3 -m http.server 8000` and press Enter.
3. Open `http://localhost:8000` in your browser.

You can also copy the folder to any web server, for example GitHub Pages.

## First steps

1. Open Videolab. The welcome tutorial starts automatically.
2. Read the tutorial pages. Use **Next** and **Back**, or the arrow keys.
3. Choose a lab with one of the six **LAB MODE** keys, or press a number from 1 to 6.
4. Read the tutorial for the lab. It opens the first time that you choose each lab.
5. Change the settings on the lab panel and watch the monitor.
6. To see the original picture again, press the lit lab key again, or press 0.

## The monitor

The monitor shows the picture after the simulation. The text in the corners is the on-screen display. It shows the current settings and what they mean, for example "4:2:0 DATA 50%".

The **4:3** and **16:9** keys below the screen change the shape of the monitor.

## The control deck

The control deck has the style of professional video equipment. The labels on the keys are in English in both languages, as on real equipment. The small light on a key comes on when its option is on.

### Source

| Key | Function |
| --- | --- |
| **LIVE** | Uses your webcam. Your browser asks for permission first. |
| **LOAD FILE** | Opens a video or an image from your computer. You can also drag a file onto the control deck. |
| **TEST SIGNAL** | Plays the Videolab test signal. |

Your files stay on your computer. Videolab does not send them anywhere. It plays the video formats that your browser plays, usually MP4 (H.264) and WebM. It also opens JPEG, PNG, GIF and WebP images.

The test signal is made to show every effect in the labs:

- The circle and the square grid show distortion of the aspect ratio.
- The colour bars, grey steps and smooth ramp show colour depth and banding.
- The red and yellow letters on blue and magenta show chroma subsampling.
- The groups of fine vertical and horizontal lines show resolution and interlace problems.
- The moving ball shows motion, combing and judder.
- The wheel turns at a speed that shows the wagon-wheel effect.

### Transport

| Key | Function |
| --- | --- |
| **STILL** | Freezes the picture. Press it again to continue. |
| **SPEED** ◀◀ ▶▶ | Plays the picture slower (down to 1/16) or faster (up to 2×). |

Slow motion makes frames and fields easy to see. The speed keys do not work with the webcam or with a still image.

The display between the key groups shows the time code (hours:minutes:seconds:frames) and the current settings.

### Display

| Key | Function |
| --- | --- |
| **ZOOM** | Magnifies the picture ×2, ×4, ×8 or ×16. From about ×8, a grid shows each pixel. |
| **OSD** | Shows or hides the on-screen display. |
| **SNAP** | Saves the current picture as a PNG file. |
| **?** | Opens the tutorial for the current lab. |
| **LANGUAGE** | Changes the language between English and Portuguese. |

To choose the area to magnify, click the screen. To move the magnified picture, drag it. A double-click switches a ×4 zoom on and off. The mouse wheel also changes the zoom. Zoom is not available in the Aspect ratio lab, because that lab shows the whole screen.

## The six labs

### 1. Resolution

| Control | Settings |
| --- | --- |
| **LINES** | 2160 (UHD), 1080 (Full HD), 720 (HD), 576 (SD), 288, 144, 72 or 36 lines. |
| **SCALING** | **NEAREST** shows each pixel as a block. **BILINEAR** blends the pixels and looks soft. |

**Try this:** Choose fewer lines and look at the fine vertical lines in the test signal. When the lines disappear or make false patterns, you see aliasing. If the source has fewer lines than you choose, the display shows "UPSCALED".

### 2. Frame rate

| Control | Settings |
| --- | --- |
| **FRAMES PER SECOND** | 60, 50, 30, 25, 24, 12, 6 or 2. |
| **SHUTTER ANGLE** | 360° (much blur), 180° (normal blur) or 45° (sharp but jerky). |

**Try this:** Watch the wheel at 24 and at 25 frames per second. At 24 it seems to stop. At 25 it turns slowly backwards. Then set 6 frames per second and compare the three shutter angles on the moving ball.

### 3. Aspect ratio

| Control | Settings |
| --- | --- |
| **PICTURE ASPECT** | 4:3, 16:9, 1.85 or 2.39. |
| **FIT TO SCREEN** | **BOX** adds black bars. **CROP** fills the screen and cuts part of the picture. **STRETCH** fills the screen and distorts the picture. |
| **ANAMORPHIC** | **SQUEEZE** records a wide picture in a 4:3 frame. **UNSQUEEZE** tells the monitor to stretch it back. |

**Try this:** Show a 16:9 picture on a 4:3 monitor with each of the three fit settings. On the test signal, the circle must stay round. Then choose **SQUEEZE**. The small inset shows what the tape records. Switch off **UNSQUEEZE** to see the picture on a monitor that ignores the anamorphic signal.

### 4. Interlaced scanning

| Control | Settings |
| --- | --- |
| **SCANNING** | **PROG** (progressive), **INTER** (two fields woven into one frame), **FIELD** (one field at a time) or **BOB** (one field with doubled lines). |
| **FRAME RATE** | 30 (NTSC), 25 (PAL), 12, 6, 2 or 1 frames per second. Each interlaced frame has two fields. |
| **LINE SIZE** | Makes each line ×1, ×2, ×4 or ×8 thicker, so that the line structure is easy to see. |

**Try this:** Compare **PROG** and **INTER** while the ball moves. With **INTER**, the edges of the ball show teeth (combing). Set 2 or 1 frames per second to watch the two fields alternate.

### 5. Chroma sampling

| Control | Settings |
| --- | --- |
| **CHROMA SUBSAMPLING** | 4:4:4, 4:2:2, 4:2:0 or 4:1:1. |
| **DISPLAY** | **Y** shows luminance (brightness). **CbCr** shows chrominance (colour). Use both for the full picture. |
| **EXAGGERATE** | Makes the colour blocks ×1, ×2, ×4 or ×8 larger, so that the effect is easy to see. At ×1, the simulation is true to scale. |

**Try this:** Switch off **CbCr** to see a black-and-white television picture. Switch off **Y** to see how little detail the colour carries. Then compare the four types of subsampling on the red letters.

### 6. Colour depth

| Control | Settings |
| --- | --- |
| **BITS PER CHANNEL** | 8, 6, 5, 4, 3, 2 or 1 bits for each of red, green and blue. |
| **OPTIONS** | **DITHER** adds a fine pattern that hides the steps. **GRADIENT** puts a chart of colour ramps over the picture. |

**Try this:** Choose fewer bits and look at the sky and the ramps. The smooth areas break into bands. Then switch on **DITHER** and compare.

## Keyboard shortcuts

| Key | Function |
| --- | --- |
| Space | Freeze or play |
| ↑ / ↓ | Play faster or slower |
| 1 to 6 | Choose a lab |
| 0 | Switch the lab off |
| Z / Shift+Z | Zoom in or zoom out |
| M | Change the monitor between 4:3 and 16:9 |
| O | Show or hide the on-screen display |
| Shift+S | Save the picture |
| H, ? or F1 | Open the tutorial |
| ← / → | Previous or next tutorial page |
| L | Change the language |
| Esc | Close the tutorial, or switch the lab off |

## For teachers

- To open Videolab directly in a lab, add the lab name to the address. For example: `http://localhost:8000/#sampling`. The names are `res`, `fps`, `aspect`, `interlace`, `sampling` and `depth`.
- For a projector, switch off the on-screen display with **OSD**. Use **ZOOM** to show details to the whole room.
- Use **SNAP** to save pictures for slides or worksheets.
- Ask students to bring their own clips. Old footage from DV cameras and DVDs shows interlace and chroma subsampling very well.
- Videolab remembers the language, the monitor shape, and the tutorials that each browser has already shown.

## Problems and solutions

**The webcam does not start.**
The webcam works only on `https://` addresses and on `localhost`. Most browsers also block it inside a page that is embedded in another page. Open Videolab at its own address and allow the camera when the browser asks. If your computer has no camera, use the test signal or a file.

**A video file does not play.**
Your browser cannot decode this file format. Convert the file to MP4 (H.264) or WebM, and open it again.

**The message "HELP FILES NOT FOUND" appears.**
You opened `index.html` directly from your disk. Start a web server as described in [Open Videolab](#open-videolab).

**The picture moves slowly.**
Videolab calculates each frame in your browser. Close other tabs and applications to give it more processing power.

## About

Videolab was created by Eduardo Morais in 2013 as a Processing application for the teaching of digital video. This web edition rebuilds it for the browser, with two new labs (resolution and frame rate), anamorphic formats, and new tutorials.

- Original version: <https://github.com/edmorais/VideoLab>
- Notes for developers: [DEVELOPERS.md](DEVELOPERS.md)
