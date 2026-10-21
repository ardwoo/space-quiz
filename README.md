# kindred

kindred is a responsive dating-app UI prototype for discovering profiles, sharing likes, finding matches, and starting conversations. It also includes an editable profile, notification preferences, and a saved light/dark theme.

## Run locally

No dependencies or build tools are required. Open `index.html` directly in a browser, or serve this folder with any static file server.

## GitHub Pages

The site is deployed from the `main` branch with the GitHub Actions workflow in `.github/workflows/pages.yml`. The workflow packages `index.html` as a Pages artifact and deploys it to GitHub Pages; there is no framework compilation step.

The UI is a front-end prototype. Profile and preference data is stored in the browser, and there is no backend for accounts, matching, or messages.
