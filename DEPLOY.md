# Deploying this site

Three blockers must be cleared first. Both are machine-level, neither is about this repo.

## 0. Fix git (required, one time)

Git is currently non-functional on this Mac:

```
You have not agreed to the Xcode license agreements.
```

```sh
sudo xcodebuild -license
```

Scroll to the bottom, type `agree`. Verify with `git --version`.

## 1. Authenticate the GitHub CLI (required, one time)

```sh
gh auth login
```

Choose GitHub.com, HTTPS, and authenticate in the browser.

## 2. Publish

```sh
cd ~/portfolio
git init
git add .
git commit -m "Portfolio site"
git branch -M main
gh repo create portfolio --public --source=. --remote=origin --push
```

## 3. Turn on Pages

```sh
gh api -X POST repos/rickygole/portfolio/pages \
  -f 'source[branch]=main' -f 'source[path]=/'
```

Or in the browser: repo, Settings, Pages, Source: Deploy from a branch, `main` / root.

Live within about a minute at **https://rickygole.github.io/portfolio/**

## If you want the canonical URL instead

`rickygole.github.io/portfolio/` is a project page. Your resume and career-ops config
already point at `https://rickygole.github.io/`, the user page, which is served from a
repo that must be named exactly `rickygole.github.io`.

To use that instead, name the repo `rickygole.github.io` in step 2, then update two lines
in `index.html`:

```html
<link rel="canonical" href="https://rickygole.github.io/">
<meta property="og:url" content="https://rickygole.github.io/">
```

That repo name already exists on your account and currently holds a template site, so
publishing there overwrites what is live now. Archive or back it up first.

## Two things to decide before you publish

**1. The CV PDF is not in this repo.** `~/Desktop/Ricky Gole CV.pdf` has your phone number
in its header. Publishing it puts your cell on a permanently crawlable URL for scrapers.
The file is held at:

    /private/tmp/claude-501/-Users-rickygole/b407eb0e-f5aa-44b8-9833-ebdd3546f7bd/scratchpad/held/Ricky_Gole_CV.pdf

If you want it on the site, drop a phone-free version at `assets/Ricky_Gole_CV.pdf` and add
this line back to the header nav in `index.html`:

    <a class="btn" href="assets/Ricky_Gole_CV.pdf">CV (PDF)</a>

**2. Confirm the two "In submission" manuscripts.** DART and the knowledge-tracing audit are
listed with no venue on purpose, so nothing goes stale and nothing can be contradicted. If
either has landed, move it up to "Accepted and published" with its venue.

## An unverified lead

A web search surfaced a claim that you were on "Team Striker," 1st place in a Human-AI
Collaboration Challenge at Morgan State. It came from a search snippet, not a primary
source, so it is deliberately NOT on the site. If it is real, it is a genuine recruiter
signal and worth adding. Confirm it first.
