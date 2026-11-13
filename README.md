# Santhosh — Portfolio

A single-page portfolio for Santhosh, Software Engineer (QA Automation, AI-Powered Testing, Application Development).

Built as one self-contained `index.html` (HTML, CSS and vanilla JavaScript, no build step), so it deploys to GitHub Pages as-is and loads fast.

## Folder structure

```
santhosh-portfolio/
├── index.html      # the whole site: markup, styles, scripts
├── README.md
└── assets/         # put your resume PDF (and any images) here
```

## Run locally

Open `index.html` in a browser, or serve it (recommended, so fonts and links behave like production):

```bash
cd santhosh-portfolio
python3 -m http.server 8080
# then open http://localhost:8080
```

or `npx serve .` if you have Node.js.

## Deploy to GitHub Pages

1. Create a repo, e.g. `S-Santhoshperumal.github.io` (gives you `https://s-santhoshperumal.github.io`) or any repo name.
2. Push `index.html`, `README.md` and the `assets/` folder to the `main` branch.
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch → `main` / root**.
4. Wait a minute and open the URL GitHub shows.

## Adding links later (resume, repos, demos)

Open `index.html`, find the `CONFIG` object near the top of the `<script>` at the bottom:

```js
const CONFIG = {
  resumeUrl: "",      // e.g. "assets/Santhosh_Resume.pdf"
  apexRepoUrl: "",    // e.g. "https://github.com/S-Santhoshperumal/apex"
  emartRepoUrl: "",
  emartDemoUrl: ""
};
```

- **Resume:** copy your PDF into `assets/` and set `resumeUrl`. A "Download resume" button appears in the hero automatically.
- **Repos and demos:** set the URL and the "coming soon" label becomes a real button. Leave a value empty and the placeholder stays.

## Adding the extra Playwright project

In `index.html`, search for `ADD MORE PROJECTS HERE`, copy the Emart `<article class="card project tilt reveal">` block and edit its title, description, stack and links.

## Editing content

- **Text** (about, skills, projects, experience, education): plain HTML in `index.html`, one `<section>` per area with `id`s `about`, `skills`, `projects`, `apex`, `experience`, `education`, `contact`.
- **APEX agent descriptions:** the `AGENTS` object in the script.
- **APEX demo run log:** the `script` array inside the APEX block. The run is labelled illustrative on the page.
- **Hero terminal lines:** the `lines` array inside `terminal()`.
- **Colors:** CSS variables at the top of `<style>` (`:root` for light, `[data-theme="dark"]` for dark).

## Features

- Dark/light theme toggle, remembered across visits (dark by default)
- Animated terminal hero running a "career test suite", with replay
- Interactive network background that reacts to the cursor
- Interactive APEX six-agent diagram: click any agent for details, or run an illustrative pipeline with a failure, self-heal and retry
- Animated metric counters, scroll reveals, 3D card tilt, cursor spotlight
- Contact form with validation that opens the visitor’s email app (no backend; nothing is "sent" silently)
- Responsive down to small phones; APEX diagram turns vertical on narrow screens
- Accessibility: semantic sections, skip link, keyboard-operable controls, visible focus, status shown with text and symbols (not color alone), `prefers-reduced-motion` turns off the canvas, typing, tilt and cursor effects

## Tested

Chromium at 1440×900 and 390×844: no JavaScript errors, no horizontal overflow, theme switching, APEX interactions and run simulation, form validation states.
