# Project Hub

A dead-simple way to publish single-file HTML/JS/CSS pages, each at its own URL,
with no build step and no local tools required.

## One-time setup

1. Create a new GitHub repository (public, unless you have GitHub Pro/Team for a private Pages site).
2. Upload everything in this folder to the repo (drag-and-drop on github.com works, or `git push`).
3. Go to **Settings → Pages** in the repo.
4. Under "Build and deployment", set **Source** to "Deploy from a branch".
5. Set **Branch** to `main` and folder to `/ (root)`. Save.
6. Wait 1–2 minutes. Your site is now live at:
   `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

## Adding a new project (no coding tools needed)

1. On github.com, open the `projects` folder in your repo.
2. Click **Add file → Create new file**.
3. Name it something like `birthday-invite.html` (must end in `.html`).
4. Paste in code — start from `projects/_template.html` if you're not sure where to begin.
5. Scroll down, click **Commit changes**.
6. Your page is live within a minute or two at:
   `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/projects/birthday-invite.html`
7. (Optional but recommended) Open `index.html` at the repo root, click the pencil/edit icon,
   and add one line to the list so people can find the new page from the homepage:
   ```html
   <li><a href="projects/birthday-invite.html">Birthday Invite</a></li>
   ```

## Folder structure

```
/
├── index.html              ← homepage listing all projects
├── .nojekyll                ← tells GitHub Pages not to run Jekyll processing
└── projects/
    ├── _template.html       ← starting point to duplicate for new pages
    └── example.html         ← working demo (counter button)
```

## Using React (or any npm package) in a specific project

The template and example above are plain HTML/CSS/JS on purpose — that's what keeps
"add a new page" a copy-paste-commit operation with zero setup. If you want React in
one project specifically, you have two options:

- **No build step:** add these three lines inside `<head>` and use `type="text/babel"`
  on your script tag — React works via CDN, still just one file, still drag-and-drop:
  ```html
  <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  ```
- **npm + real build:** if you actually `npm install react` and use JSX tooling/bundlers,
  that project needs its own build process, and you'd commit the *built* output (usually
  a `dist/` folder) into `projects/your-project-name/` rather than a single raw file. This
  is heavier and breaks the "just paste code into GitHub" workflow for non-technical
  contributors, so it's worth only doing for projects that truly need it.
