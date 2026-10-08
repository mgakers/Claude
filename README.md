# Sat Logo

A minimal static web app that shows the Sat logo on all six faces of a slowly rotating 3D cube, on a black background (pure CSS, no libraries).

- `index.html` – the page
- `logo.svg` – vector logo, converted from the original Illustrator EPS
- `keepawake.webm` / `keepawake.mp4` – tiny silent video used as a keep-awake fallback

While the page is open and visible it keeps the screen from sleeping, using the
browser's Screen Wake Lock API, or a hidden muted looping video where that isn't
available. If the browser blocks autoplay, click once on the page to enable it.

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
```

## Video

`sat-logo-cube.mp4` is a 5-minute 1920×1080, 30fps recording of the animation.
The animation repeats every 30 seconds, so one cycle is rendered frame by frame and looped:

```sh
node tools/render-cycle.mjs file://$PWD/index.html cycle.mp4   # needs playwright + ffmpeg
ffmpeg -stream_loop 9 -i cycle.mp4 -c copy -movflags +faststart sat-logo-cube.mp4
```
