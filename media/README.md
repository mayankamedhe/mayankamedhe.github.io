# Media

All nine work cards have their media. To swap one, overwrite the file with the same
name and the page picks it up; no code change needed.

## What each card uses

| Card | File(s) | Treatment |
|---|---|---|
| Smartwatch-robot interaction | `work/smartwatch-robot.jpg` + `work/smartwatch-app.jpg` | two photos side by side, cropped to fill |
| Text-guided map retrieval | `work/spatial-rag.jpg` | diagram, fitted whole |
| Gaze-guided video captioning | `work/gaze-method.jpg` + `work/gaze-dataset.jpg` | two diagrams stacked, fitted whole |
| Pointing-gesture stop estimation | `work/pointing.jpg` | figure, fitted whole |
| FAR: faster agentic robotics | `work/far-method.jpg` | diagram, fitted whole |
| Whole-body VR teleop of the G1 | `work/g1-teleop-real.jpg` + `work/g1-teleop-sim.jpg` | two YouTube loops side by side, stills shown until they load |
| Learning manipulation from human video | `work/g1-pick-place.jpg` | YouTube loop, still shown until it loads |
| F1TENTH autonomous racing | `work/f1tenth.mp4` + `work/f1tenth-poster.jpg` | silent looping clip, poster frame shown for reduced motion |
| Who to follow in a crowd | `work/pedestrian.jpg` | figure, fitted whole |

Every image links to its own full-size file, so a reader who wants to actually read a
diagram can click it.

## Video

`f1tenth.mp4` is re-encoded from `images/F1_tenth.mp4` trimmed to the first 13 seconds with no audio. The portrait
frame is cropped to the track and centered on a blurred 16:9 fill, so the whole track shows
(about 1 MB). To redo it:

```sh
ffmpeg -i images/F1_tenth.mp4 -t 13 -an -filter_complex \
  "[0:v]crop=576:610:0:175,split[a][b];[a]scale=960:540:force_original_aspect_ratio=increase,crop=960:540,boxblur=24:2,eq=brightness=-0.1[bg];[b]scale=-2:540[fg];[bg][fg]overlay=(W-w)/2:0" \
  -c:v libx264 -crf 27 -preset slow -pix_fmt yuv420p -movflags +faststart media/work/f1tenth.mp4
```

## YouTube loops

A link with `class="yt"` and `data-yt="<video id>"` gets a muted, looping, control-free
YouTube embed once its card nears the viewport. The `<img>` inside is the still shown
before it loads and for readers with reduced motion; clicking opens the video on YouTube.
Add `yt--right` when the subject sits right of center.

## Photos vs figures

The distinction is in the markup and it matters:

- **Photos** (`card__media` with no `--figure`) are cropped to fill the frame with
  `object-fit: cover`. Fine for photographs, ruinous for diagrams.
- **Figures** (`card__media--figure`) are fitted whole with `object-fit: contain` on a
  white panel that stays white in dark mode, because these diagrams carry their own
  white background and small text that must not be cropped.

Two helper classes anchor a crop when the subject is off-center: `pos-left` and
`pos-high`. `g1-manipulation.jpg` uses `pos-high` so the robot's head survives the crop.

## If you add a new image

- **Photos:** any aspect ratio, 1100px wide is plenty.
- **Figures:** export at 1400 to 1600px wide so the text stays readable when clicked.
- **Flatten transparency onto white before exporting.** Every original here arrived as
  RGBA PNG, and the transparent regions rendered as black bars. Flattening fixed it.
- JPEG at quality 84 keeps files under ~160 KB. The whole media folder is 764 KB; the
  originals were 5.3 MB.

## Originals

Your untouched source files are in `media/_originals/`, kept on disk but excluded from
git so they do not bloat the repo.

## Before posting

Honda material: use only what is already public. Blur bystander faces in street footage.
