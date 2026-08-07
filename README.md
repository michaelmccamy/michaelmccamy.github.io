# UF in Singapore — e-Portfolio

Static site, no build step, no dependencies. Deploys to GitHub Pages as-is.

---

## Deploy in about 5 minutes

**1. Make the repo.** On GitHub, create a new **public** repository named:

```
<your-username>.github.io
```

Using that exact name gets you `https://<your-username>.github.io` as the URL — cleaner to submit than a project-page URL with a subpath.

**2. Push the files.**

```bash
cd portfolio
git init
git add .
git commit -m "e-portfolio"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
git push -u origin main
```

If you'd rather not touch the CLI: on the empty repo page click **uploading an existing file**, drag the whole folder contents in (including the `images/` and `files/` folders), and commit.

**3. Turn on Pages.** Repo → **Settings** → **Pages** → Source: **Deploy from a branch** → Branch: `main`, folder: `/ (root)` → Save.

**4. Wait 1–2 minutes,** then open `https://<your-username>.github.io`. Submit that URL.

If you get a 404, give it another minute — the first build is slow. Check the **Actions** tab to confirm the deploy finished.

---

## Before you submit — checklist

- [ ] Every yellow `WRITE THIS` box is gone. Search the HTML for `class="todo"` and `REPLACE` to catch stragglers.
- [ ] LinkedIn URL is real (appears on **every** page — masthead footer and the About page button). Search for `REPLACE-YOUR-HANDLE`.
- [ ] Email is real. Search for `REPLACE@ufl.edu`.
- [ ] All nine images in `images/` are your own photos. **No stock photos** — the assignment says so explicitly.
- [ ] Resume PDF is at `files/michael-resume.pdf`.
- [ ] Cultural Storytelling project is on the Singapore page in full.
- [ ] All four reflection questions are answered on the Singapore page.
- [ ] Goals from the Goal Setting assignment are quoted and answered on the Internship page.
- [ ] Three skills on the Skills page, at least one tagged Transferable.
- [ ] Click all five nav links on the live site.

---

## Swapping in your photos

The `images/` folder already has placeholder files. **Overwrite them keeping the exact same filenames** and you don't have to touch any HTML:

| File | Goes on | Shape |
|---|---|---|
| `about-portrait.jpg` | Home | portrait, tall |
| `singapore-1/2/3.jpg` | UF in Singapore | landscape |
| `internship-1.jpg` | My Internship | landscape |
| `internship-2.jpg` | My Internship | landscape (a screenshot works well) |
| `skill-1/2/3.jpg` | Skills | landscape |

If a photo is over ~1MB, shrink it — the page will feel slow otherwise.

Also fill in the `alt=""` attributes with a short description of each photo. Empty alt text on a content image is an accessibility gap, and it's a nice detail for a CS portfolio.

## Local preview

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

---

## Structure note

This is built as **five separate pages**, one per required section, rather than the single scrolling page the reference portfolio uses. Both satisfy the assignment, but separate pages map 1:1 to the grading rubric — a grader looking for "My Internship" finds a page called My Internship. Contact lives at the bottom of the home page (`index.html#contact`), linked from every footer.

If you'd rather have the one-page scroller, say so and it's a quick conversion — the sections are already self-contained.

## How the design works

Each page carries one MRT line colour — About Me is North South red, Resume is East West green, UF in Singapore is North East purple, My Internship is Circle orange, Skills is Downtown blue. The nav is a route strip: dots on a track, with the current stop filled in. Change a page's colour by swapping the `line-*` class on its `<body>` tag.

Type is Archivo for headings and labels, Newsreader for body prose, JetBrains Mono for captions and data.

Everything lives in `style.css`. No framework, no JavaScript.
