# GingL.github.io

Personal homepage of Xuejing Liu. Plain static HTML + CSS: no build step, no external fonts, no trackers, no JavaScript.

The layout follows the common academic homepage style: one column, white background, dense text, no cards, no icons, no navigation bar.

## Files

```
index.html          the whole page: intro / news / publications / experience
assets/style.css    all styling, including dark mode and small screens
.nojekyll           tells GitHub Pages to skip Jekyll
README.md           this file
```

## Preview locally

```bash
cd GingL.github.io
python3 -m http.server 8000
# open http://localhost:8000
```

## Editing

### 1. Email

Search for `xuejing.liu@example.com` in `index.html` and replace it with the real address.

### 2. Add a news item

Copy a line inside `<ul class="rows">`:

```html
<li><span class="when">2026.11</span><span class="what">Something happened.</span></li>
```

`when` is the date column, `what` is the text.

### 3. Add a publication

Copy a block inside the matching `<ul class="pubs">`:

```html
<li>
  <p class="ptitle"><a href="https://arxiv.org/abs/xxxx.xxxxx">Paper title</a></p>
  <p class="pauthors">A. Author, <b>X. Liu</b>, B. Author</p>
  <p class="pvenue">Venue · Year</p>
  <p class="pdesc">One sentence on what the work does.</p>
</li>
```

- Wrap your own name in `<b>`.
- Mark first-author papers with `<span class="flag">first author</span>`, placed inside `pvenue`.
- `pdesc` is optional. For papers without a public link, drop the `<a>` from `ptitle`.

### 4. Add a photo (optional)

Put the image in `assets/`, then add one line inside `<header>`, just before `<h1>`:

```html
<img class="photo" src="assets/photo.jpg" alt="Xuejing Liu">
```

and add to the end of `assets/style.css`:

```css
.photo { float: right; width: 160px; margin: 0 0 14px 24px; border-radius: 6px; }
@media (max-width: 620px) { .photo { width: 104px; margin-left: 14px; } }
```

That is the usual arrangement in academic homepages: photo at the top right, text flowing around it.

### 5. Cache busting

The stylesheet is linked as `assets/style.css?v=4`. When you change the CSS, bump that number (`v=5`, …) so browsers pick up the new file instead of a cached copy.

## Deploy

Push to `master`; GitHub Pages serves the repository root.

```bash
git add -A
git commit -m "update homepage"
git push
```

## Note

Only public information belongs here: published papers, public model releases, public job titles. Do not include internal dataset names, project codenames, internal paths, or internal benchmark counts.
