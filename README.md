# mayankamedhe.github.io

Personal site for Mayanka Medhe. Live at <https://mayankamedhe.github.io>.

Static HTML and CSS, no build step and no dependencies, served by GitHub Pages from
`master`. Edit, commit, push, and it deploys.

```
index.html          the whole page
styles.css          design tokens, layout, components
images/             profile photo
data/               CV and thesis PDFs
media/              work card images, see media/README.md
```

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Common edits

**Add a work card image.** Drop a 16:9 JPEG into `media/work/` using the filename listed
in [media/README.md](media/README.md). It appears on its own; no code change needed.

**Update the CV.** Replace `data/Mayanka_Medhe_CV.pdf`, keeping the filename.

**Add a work card.** Copy any `<article class="card reveal">` block in `index.html` and
edit the text. The grid reflows on its own.

**Change the accent color.** Edit `--accent` and `--accent-soft` in `styles.css`, in
both the light block at the top and the two dark blocks below it.
