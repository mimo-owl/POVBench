# Paper Project Page Template

A lightweight, reusable project-page template for academic papers (NLP / ML / CV).
Plain **HTML + CSS + JS** — no build step, no framework, no Jekyll. Just edit the
placeholders and push to GitHub Pages.

It includes the parts a paper page usually needs: title + authors block, action
buttons (Paper / arXiv / Code / Dataset / Demo), teaser figure, abstract, method
and results sections, an image carousel, a video embed, a copy-to-clipboard
BibTeX block, and social-preview (Open Graph) tags.

---

## Quick start (new paper → live page)

1. **Make a copy.** If you publish this repo as a GitHub *Template repository*
   (Settings → General → check "Template repository"), then for each new paper
   just click **"Use this template" → Create a new repository**.
   A good name is `myproject-page` or `paper-name`.

2. **Fill in the placeholders.** Open `index.html` and replace every `{{...}}`
   marker. See the full list below. Tip: search the file for `{{` — when there
   are no matches left, you're done.

3. **Add your figures** to `static/images/` (see the figure list below) and
   make sure the `<img src="...">` paths match your filenames.

4. **Preview locally.** From the project folder:

   ```bash
   python3 -m http.server 8000
   ```

   Then open <http://localhost:8000>. (Opening `index.html` directly also works,
   but a local server matches how GitHub Pages serves the site.)

5. **Publish on GitHub Pages.**
   - Push the repo to GitHub.
   - Go to **Settings → Pages**.
   - Under *Build and deployment*, set **Source = Deploy from a branch**,
     **Branch = `main`**, **Folder = `/ (root)`**, then **Save**.
   - Wait ~1 minute. Your page is live at
     `https://<username>.github.io/<repo-name>/`.
   - Put that URL back into the `{{PROJECT_PAGE_URL}}` tag (for the social card)
     and in your repo's "About" section.

---

## Placeholder reference

Everything in `index.html` wrapped in `{{ }}` is meant to be replaced.

### Header / metadata
| Placeholder | What to put |
|---|---|
| `{{PAPER_TITLE}}` | Full paper title |
| `{{SHORT_DESCRIPTION}}` | One sentence for SEO / social preview |
| `{{KEYWORD_1..3}}` | Comma-separated keywords |
| `{{PROJECT_PAGE_URL}}` | The final GitHub Pages URL (for the social card) |
| `{{VENUE}}` | e.g. `EMNLP 2025` — or delete the `<p class="venue">` line while under review |

### Authors
| Placeholder | What to put |
|---|---|
| `{{AUTHOR_N_NAME}}` | Author display name |
| `{{AUTHOR_N_URL}}` | Link to homepage / Scholar (or `#`) |
| `{{AFFILIATION_N}}` | Institution name |
| `{{AUTHOR_NOTE}}` | e.g. "* Equal contribution" — or delete the line |

Add/remove authors by duplicating or deleting a `<span class="author">` block.
The `<sup>` number ties an author to an affiliation.

### Links (delete any button you don't have)
`{{PAPER_PDF_URL}}`, `{{ARXIV_URL}}`, `{{CODE_URL}}`, `{{DATASET_URL}}`, `{{DEMO_URL}}`

### Body content
| Placeholder | What to put |
|---|---|
| `{{ABSTRACT_TEXT}}` | Your abstract |
| `{{SECTION_1_TITLE}}` / `{{SECTION_1_TEXT}}` | e.g. "Method" |
| `{{SECTION_2_TITLE}}` / `{{SECTION_2_TEXT}}` | e.g. "Results" |
| `{{*_CAPTION}}`, `{{*_ALT_TEXT}}` | Figure captions and alt text |
| `{{YOUTUBE_VIDEO_ID}}` | The id after `watch?v=` — or delete the Video section |
| `{{BIBTEX_ENTRY}}` | Your full BibTeX entry |
| `{{ACKNOWLEDGEMENTS_TEXT}}` | Funding / thanks — or delete the section |
| `{{YOUR_NAME_OR_LAB}}`, `{{YEAR}}` | Footer + LICENSE |

### Figures expected in `static/images/`
- `teaser.png` — main teaser/headline figure
- `method.png` — method/architecture diagram
- `result1.png`, `result2.png`, `result3.png` — carousel images
- `social_preview.png` — 1200×630 px social card (Open Graph)
- `favicon.ico` — optional browser tab icon

Don't have one yet? Either remove the corresponding `<figure>` / `<section>`
block, or drop in a placeholder image.

---

## Publishing your dataset

The page links to a dataset via the `{{DATASET_URL}}` button. Where to host it:

- **Small (< ~100 MB), code-adjacent:** commit it into the code repo, or attach
  it to a GitHub Release.
- **ML datasets / want easy loading:** [Hugging Face Datasets](https://huggingface.co/datasets)
  (`datasets.load_dataset(...)` works out of the box, supports versioning).
- **Want a citable DOI / archival:** [Zenodo](https://zenodo.org) — it can mint a
  DOI and auto-archive a GitHub release. Good for "please cite the dataset".

Whatever you choose, also add a short **data card / README** next to the data
that states: what it contains, how it was collected, licensing/terms, and how to
load it. Reviewers and users will look for this.

---

## Customizing the look

Open `static/css/style.css` and edit the variables at the top
(`--accent`, fonts, max width, etc.) to rebrand. The whole page reflows from
those. No recompile needed — just refresh the browser.

---

## File structure

```
.
├── index.html              # the page — edit the {{placeholders}}
├── README.md               # this file
├── LICENSE                 # MIT for code; page content is CC BY-SA 4.0
├── .gitignore
└── static/
    ├── css/style.css       # styles + theme variables
    ├── js/main.js          # carousel + copy-BibTeX (no dependencies)
    └── images/             # put your figures here
```

---

## Credits

Design inspired by the widely used academic project-page conventions
(Nerfies / Academic-Project-Page-Template). Rebuilt as a self-contained,
dependency-free template you can keep reusing across papers.
