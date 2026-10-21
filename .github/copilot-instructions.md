# Copilot Instructions

## Architecture

- This is a dependency-free static web prototype. The app lives in `index.html`: semantic page markup, all CSS in one `<style>` block, and app behavior in one inline `<script>`. There is no framework, module bundler, server API, or separate data layer.
- The interface uses a single-page pattern. The Discover view is static markup; `renderPage(section)` builds the other views into `#page-view` from templates and hides/shows the views without navigating away.
- Demo profiles, likes, and matches are in JavaScript arrays near the start of the script. Profile edits, theme preference, and notification preference use browser `localStorage`; `getSavedValue` and `saveValue` centralize access and handle storage errors.

## Build and test

- No package manifest or build, test, or lint scripts are configured.
- To run the prototype, open `index.html` directly in a browser.
- Validate UI changes in the browser at desktop and narrow mobile widths. For behavior changes, exercise the relevant navigation view and interaction; check that dark mode persists after reload.
- There is no automated test runner or single-test command.

## Code conventions

- Keep UI and behavior in `index.html` unless the project is deliberately migrated to a multi-file setup. Reuse the existing CSS custom properties in `:root`; dark-theme overrides are scoped under `html[data-theme="dark"]`.
- Navigation buttons use `data-section` values matching the section names handled by `renderPage`. Because the page view is replaced with `innerHTML`, interactions on generated views are handled by the document-level delegated click, change, and submit listeners; keep those handlers in sync when adding controls.
- Render generated views through `renderPage` and preserve the shared `.page-view` and `.page-header` structure. Keep current view state in the DOM's `data-page` attribute so layout rules continue to apply.
- Use the storage helpers for persisted preferences and profile data. Use DOM `textContent` when inserting user-authored text into rendered elements, as the message composer does.
- Responsive behavior is defined by the existing CSS breakpoints at 1120px, 760px, and 430px. Check the fixed mobile navigation and content width when changing navigation or page layouts.
