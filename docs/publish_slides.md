# Publishing Individual Lecture Slides to GitHub Pages

This guide describes how to manually publish a single Reveal.js slide deck so it can be viewed on a phone using GitHub Pages.

## Prerequisites

Generate the slides first:

```bash
jupyter-book build .
```

Confirm the slide file exists:

```bash
ls Lectures/Lecture0.slides.html
```

## Step 1: Fetch and switch to the GitHub Pages branch

```bash
git fetch origin gh-pages
git checkout gh-pages
```

## Step 2: Copy the slide deck into the published site

Assume we want to publish `Lecture0.slides.html`.

Copy it somewhere temporary before switching branches:

```bash
git checkout main
cp Lectures/Lecture0.slides.html /c/temp/
```

Switch back to the Pages branch:

```bash
git checkout gh-pages
```

Copy the file into the `Lectures` folder:

```bash
cp /c/temp/Lecture0.slides.html Lectures/
```

## Step 3: Commit and push

```bash
git add Lectures/Lecture0.slides.html
git commit -m "Add Lecture0 slides"
git push origin gh-pages
```

## Step 4: Open the published slides

URL:

```text
https://nilsjakob.github.io/TSE3080_2026/Lectures/Lecture0.slides.html
```

For Reveal.js navigation:

```text
https://nilsjakob.github.io/TSE3080_2026/Lectures/Lecture0.slides.html#/
```

---

# Publishing another lecture

Example for Lecture 1:

```bash
git checkout main
cp Lectures/Lecture1.slides.html /c/temp/

git checkout gh-pages
cp /c/temp/Lecture1.slides.html Lectures/

git add Lectures/Lecture1.slides.html
git commit -m "Add Lecture1 slides"
git push origin gh-pages
```

URL:

```text
https://nilsjakob.github.io/TSE3080_2026/Lectures/Lecture1.slides.html
```

---

# Checking the location on GitHub

The file must appear in the `gh-pages` branch as:

```text
TSE3080_2026
└── Lectures
    └── LectureX.slides.html
```

If the file appears somewhere else, the URL must match the repository path.

---

# Updating an existing slide deck

If you regenerate a lecture and want to replace the published version:

```bash
git checkout main
cp Lectures/Lecture0.slides.html /c/temp/

git checkout gh-pages
cp /c/temp/Lecture0.slides.html Lectures/

git add Lectures/Lecture0.slides.html
git commit -m "Update Lecture0 slides"
git push origin gh-pages
```

Wait a minute and refresh the page.