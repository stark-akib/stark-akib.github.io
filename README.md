# Shaikh Akib Shahriyar — academic website

A single-page, static academic homepage built for GitHub Pages. It uses no framework, build step, npm packages, trackers, or cookies. Every piece of content is in `index.html` and renders with JavaScript disabled.

```text
index.html                  all content and CSS (one file)
.nojekyll                   serve files as-is (no Jekyll processing)
README.md                   this file
assets/
  img/Akib_Headshot.jpg     headshot (circular "SA" initials show if it fails to load)
  pdf/
    CV_Shaikh_Akib_Shahriyar.pdf
    Research_Statement_Shaikh_Akib_Shahriyar.pdf
    Teaching_Statement_Shaikh_Akib_Shahriyar.pdf
    padnet-2026.pdf                          ACM TOPS version of record, CC BY 4.0
    practical-robustness-frontier-2026.pdf   author draft (working paper)
```

All paths are relative, so the site also works under a project subpath such as `https://<user>.github.io/<repo>/`.

## Preview locally

From this folder:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000/>. Opening `index.html` directly also works.

## Editing content

Everything is in `index.html`. Each section is marked by an HTML comment and an `id`:

| Section | Anchor | Notes |
|---|---|---|
| Introduction | `#top` | Name, title, affiliation, advisor, pitch, faculty-search line, CV/email/Scholar links |
| Biography | `#about` | Bio paragraph, education, appointments |
| Research | `#research` | Two current-work anchors and four agenda directions |
| Publications | `#publications` | Selected peer-reviewed → preprints & working papers → earlier (collapsed) → posters (collapsed) |
| Teaching & Mentoring | `#teaching` | Philosophy, teaching history, mentoring, future teaching |
| Service | `#service` | One line; the full list is in the CV |
| Contact | `#contact` | Email, profiles, documents |

- **Faculty-search line.** Delete the single `<p class="callout">` paragraph. Nothing else depends on it.
- **Update date.** Edit the footer text (`Updated October 2026`) whenever you change content.
- **Colors and fonts.** These are CSS variables at the top of the `<style>` block. All text and button states meet WCAG AA: body 15.6:1, muted 7.2:1, links 8.4:1, CV button 8.8:1.

### Adding a publication

Copy an existing `<li class="pub">` block. Then:

1. Wrap your own name in `<strong>`. Keep every coauthor, in publisher order.
2. Use a status tag only where it applies: `Journal`, `Conference`, `Workshop`, `To appear`, `Preprint`, `Working paper`, or `Poster`.
3. For each link, keep the visually hidden `<span class="vh">: Paper title</span>` so screen readers can tell repeated "PDF"/"DOI" links apart.
4. **Add a PDF link only when the file is in `assets/pdf/` and is a version you may post** (author-accepted manuscript, open-access version of record, or arXiv). Never use `href="#"` or a placeholder.
5. Move a preprint into the peer-reviewed list only after acceptance is public.
6. Update the count shown in the `<summary>` if you change a collapsed list.

### Paper PDF slots (not yet present, so no link is shown)

| Paper | Path to use when an approved PDF exists |
|---|---|
| IVORY (FG 2025) | `assets/pdf/ivory-fg-2025.pdf` (IEEE policy allows the accepted manuscript, not the IEEE-formatted final version) |
| Sequence-based deepfake detectors (WDC 2022) | `assets/pdf/sequence-deepfake-wdc-2022.pdf` (author version) |
| DOT audio attack (IJCB 2026) | `assets/pdf/dot-audio-2026.pdf` (optional; arXiv PDF linked now) |
| Task contracts (preprint) | `assets/pdf/task-contracts-2026.pdf` (optional; arXiv PDF linked now) |
| Dysphonia (CSSE 2023) | `assets/pdf/dysphonia-2023.pdf` |
| Discrete Spider Monkey Optimization (ASOC 2020) | `assets/pdf/discrete-spider-monkey-2020.pdf` |
| DNA cryptography speech security (2021) | `assets/pdf/dna-speech-security.pdf` |
| DOC-BLOCK (ICICV 2021) | `assets/pdf/doc-block-2021.pdf` |
| E-mail classification with FastText (TENSYMP 2020) | `assets/pdf/email-fasttext-2020.pdf` |
| Bangla numeral recognition (ICBSLP 2019) | `assets/pdf/bangla-numeral-2019.pdf` (no verified DOI yet) |
| Spider Monkey Optimization (ECCE 2019) | `assets/pdf/spider-monkey-ecce-2019.pdf` |
| Speech enhancement (ECCE 2019) | `assets/pdf/speech-denoising-2019.pdf` |
| Multi-label image classification (ICCIT 2018) | `assets/pdf/multilabel-cnn-2018.pdf` |
| Successive parity generation (iCEEiCT 2018) | `assets/pdf/successive-parity-2018.pdf` |
| Chaotic neural network + DNA encryption (ICCIT 2017) | `assets/pdf/chaotic-dna-encryption-2017.pdf` |
| PRF poster (USENIX Security 2026) | `assets/pdf/prf-usenix-poster-2026.pdf` |
| DiffTranPure poster (USENIX Security 2024) | `assets/pdf/difftranpure-usenix-poster-2024.pdf` |

## Publishing on GitHub Pages

The preferred address is **https://stark-akib.github.io/**. It works only if the GitHub account `stark-akib` belongs to you. A user site must be in a repository named exactly `<username>.github.io`.

1. Sign in as `stark-akib`. Create a public repository named `stark-akib.github.io`, without a README so the history stays clean.
2. Push the contents of this folder (not the parent folder) to the `main` branch:

   ```bash
   git init -b main
   git add .
   git commit -m "Initial academic website"
   git remote add origin https://github.com/stark-akib/stark-akib.github.io.git
   git push -u origin main
   ```

3. In the repository, go to **Settings → Pages**. Set **Source** to *Deploy from a branch*, then choose `main` and `/ (root)`.
4. Wait for the Pages build to finish. Then open the URL and confirm that the page, headshot, and every PDF load.

**Updating the live site:** edit files, then `git add -A`, `git commit -m "..."`, and `git push`. Pages rebuilds in about a minute.

**If you use a different account,** the address becomes `https://<that-username>.github.io/`. The repository must then be named `<that-username>.github.io`. Your displayed name on the page does not change. Alternatively, publish this as a project repository (`https://<username>.github.io/<repo>/`; the relative paths already support this) or attach a custom domain under **Settings → Pages → Custom domain**.

### Canonical URL and social metadata

The site is live at https://stark-akib.github.io/. `index.html` already contains the canonical link, `og:url`, `og:image`, and the JSON-LD `url`/`image` for that address. If the site ever moves (for example, to a custom domain), update those four places.

## Launch checklist

- [x] GitHub account and repository name confirmed.
- [ ] CV in `assets/pdf/` is the approved public copy, with no phone number or home address.
- [ ] Research and teaching statement PDFs are the approved public versions.
- [ ] Every linked paper PDF is a version you may post.
- [ ] Faculty-search line and footer date are current.
- [ ] Publication statuses are current; preprints are not labeled as accepted.
- [x] After deployment: canonical/OG lines added and live links rechecked.
- [ ] No private material is in the repository (source application files, evaluations, review notes, drafting briefs).

## Design notes

- One scrolling page, ordered for search committees: identity → research → publications → teaching & mentoring → contact. The CV is in the header and the introduction.
- System fonts only, with a serif for headings. Body text is 17px with a 1.65 line height.
- The navigation wraps instead of collapsing into a hamburger menu. On screens at least 768px wide and 600px tall, the header is sticky.
- The earlier publications and posters use native `<details>` elements. The browser's find-in-page searches inside them. When printing, they expand (CSS `::details-content` plus a small `beforeprint` script), and the print stylesheet hides the navigation.
- The only JavaScript is the print expansion and the headshot fallback. The site reads the same without it.
