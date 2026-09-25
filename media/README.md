# Media

All six work cards have their images. To swap one, overwrite the file with the same
name and the page picks it up; no code change needed.

## What each card uses

| Card | File(s) | Treatment |
|---|---|---|
| Smartwatch-robot interaction | `work/smartwatch-robot.jpg` + `work/smartwatch-app.jpg` | two photos side by side, cropped to fill |
| Text-guided map retrieval | `work/spatial-rag.jpg` | diagram, fitted whole |
| Gaze-guided video captioning | `work/gaze-method.jpg` + `work/gaze-dataset.jpg` | two diagrams stacked, fitted whole |
| Pointing-gesture stop estimation | `work/pointing.jpg` | figure, fitted whole |
| Learning manipulation from human video | `work/g1-manipulation.jpg` | photo, cropped to fill |
| Who to follow in a crowd | `work/pedestrian.jpg` | figure, fitted whole |

Every image links to its own full-size file, so a reader who wants to actually read a
diagram can click it.

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
