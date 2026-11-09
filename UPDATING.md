# How to update the site

Every change is: edit a file, commit, push. The live site updates in about a minute.

## Files

| What | File |
|---|---|
| Home page (intro, research interests, latest video, projects, publications, updates, bio) | `index.html` |
| VLA / SO-101 case study | `projects/vla-so101.html` |
| saferl-lab case study | `projects/saferl-lab.html` |
| Deep_NN case study | `projects/deep-nn.html` |
| Colours, fonts, spacing | `assets/css/style.css` (colour tokens at the top) |
| Videos | `assets/video/` (H.264 MP4, under ~2 MB, plus a `.webp` poster frame) |
| Images | `assets/img/` (use `.webp`, max 1400 px wide) |
| CV | `assets/Lagnesh_Mahapatra_CV.pdf` (replace the file, keep the name) |

## Common updates

**Add an update (most frequent).** In `index.html`, find `<ol class="updates">`.
Copy one `<li>...</li>` line, paste it at the top, and change the date and text. Keep about 8; delete the oldest.

**Change a project's key result.** In `index.html`, find the project's `<li class="entry">` and edit the
`<p class="hl">` line (the orange line). Only use numbers that are in the repo's results files.

**Add a result table to a case study.** Copy an existing `<div class="table-wrap">...</div>` block.
Mark the best row with `<tr class="best">`. Numbers go in `<td class="n">` so they align.

**Add a video (recommended for real-robot results).** Convert to MP4 (H.264, under ~5 MB, 10–20 s), put it in
`assets/video/`, then use:

```html
<figure class="wide">
  <div class="frame flush">
    <video src="/assets/video/NAME.mp4" autoplay muted loop playsinline width="1280" height="720"></video>
  </div>
  <figcaption>What the clip shows.</figcaption>
</figure>
```

**Add a new project.** Copy a file in `projects/`, rename it, edit the content. Then copy one
`<li class="entry">` in `index.html` (thumbnail: a 360×360 `.webp`), and add the new page to `sitemap.xml`.

**After any update:** change "Last updated" at the bottom of `index.html` and `lastmod` in `sitemap.xml`.

## Preview before pushing

```
python -m http.server 8765
```
Then open http://localhost:8765.

## Checks

`.github/workflows/check-links.yml` checks every link and image on each push and every Monday.
A red X on a commit in GitHub means a link is broken; open the run to see which.
