# How to update the site

Every change is: edit a file, commit, push. The live site updates in about a minute.

## Files

| What | File |
|---|---|
| Home page (headline numbers, project cards, updates, experience, skills) | `index.html` |
| VLA / SO-101 case study | `projects/vla-so101.html` |
| saferl-lab case study | `projects/saferl-lab.html` |
| Deep_NN case study | `projects/deep-nn.html` |
| Colours, fonts, spacing | `assets/css/style.css` (colour tokens at the top) |
| Images | `assets/img/` (use `.webp`, max 1400 px wide) |
| CV | `assets/Lagnesh_Mahapatra_CV.pdf` (replace the file, keep the name) |

## Common updates

**Add an update (most frequent).** In `index.html`, find `<ol class="timeline">`.
Copy one `<li>...</li>` block, paste it at the top of the list, and change the date, text and project tag.
Keep 6–10 entries; delete the oldest.

**Change a headline number.** In `index.html`, find `class="stats"`. Each `<div class="stat">` has a number,
a label and a source. Only use numbers that are in the repo's results files.

**Change a project card's results.** In `index.html`, find the project's `<article class="project">` and edit
its `<ul class="results">` (three lines: value, then what it means).

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
`<article class="project">` card in `index.html`, and add the new page to `sitemap.xml`.

**After any update:** change "Last updated" at the bottom of `index.html` and `lastmod` in `sitemap.xml`.

## Preview before pushing

```
python -m http.server 8765
```
Then open http://localhost:8765.

## Checks

`.github/workflows/check-links.yml` checks every link and image on each push and every Monday.
A red X on a commit in GitHub means a link is broken; open the run to see which.
