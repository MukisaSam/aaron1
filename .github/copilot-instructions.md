<!-- Auto-generated guidance for AI coding agents -->
# Copilot instructions for this repository

Purpose
- Short, actionable guidance to help AI agents be productive in this repository.

Repository snapshot
- This repo is intentionally minimal. The primary file is `website.html` at the repo root.
- There are no package manifests (`package.json`, `pyproject.toml`) or build scripts present.

Big picture
- Single-file static website: `website.html` is the canonical source. Treat edits as direct changes to that file.
- No server-side code, no tests, and no CI configuration detected. Avoid adding complex toolchains without explicit owner approval.

What an AI agent should assume and check first
- Always open `website.html` and inspect the top-level HTML, inline scripts, and any linked assets.
- If a change touches new tooling (Node, Python, bundlers), ask the user before adding dependencies or new files.

Developer workflows (what works here)
- Run/preview: open `website.html` in a browser or use a simple static server (e.g., VS Code Live Server). No build step required.
- Testing: no automated tests exist. Verify changes by loading the file locally in multiple browsers if needed.

Quick local preview commands
- VS Code Live Server (recommended for quick edits): install the "Live Server" extension, then right-click `website.html` in the Explorer and choose "Open with Live Server" or run the command palette `Live Server: Open with Live Server`.
- Python (works on Windows if Python is installed):

```powershell
cd path\to\repo
python -m http.server 8000
# then open http://localhost:8000/website.html in your browser
```

- Node (if Node is available):

```powershell
npx serve -s . -l 8000
# or
npx http-server -p 8000
```

Windows-specific tips
- Use PowerShell or the integrated VS Code terminal. When using `python -m http.server` ensure the current directory is the repo root so static links resolve correctly.
- If Live Server isn't installed and you plan to add it in instructions, ask the repo owner before adding extensions or dev dependencies.

Conventions & patterns to follow
- Keep changes localized to `website.html` unless instructed otherwise.
- Prefer small, reversible edits and include a short rationale in commit messages.

Integration points and external dependencies
- No external integrations or APIs are present in-repo. If you add integrations, document required secrets and setup steps in a new README.

When to request clarification
- If a proposed change introduces a build system, package manager, or configuration files, ask the repository owner before proceeding.
- If you find references to external services or credentials, request explicit instructions about secrets management and testing credentials.

Examples
- Editing content: update HTML text or modify styles directly in `website.html`.
- Adding assets: place images or other assets under a new `assets/` directory and update `website.html` links accordingly; confirm with the owner first.

If uncertain, ask the user a single clarifying question before making broad changes.

---
If you'd like, I can expand this with repository-specific examples or add a short README describing a local preview workflow.

Project-specific notes (from attached React component `Zentara Tenants reminder.tsx`)
- The attached component is a React/TSX-style tenant reminder UI that illustrates patterns you may encounter:
	- Uses a browser-global `window.storage` API to persist data under the key `zentara-tenants` — this is not a standard Web API; confirm its implementation/location before modifying persistence logic.
	- Constructs WhatsApp reminders using `https://wa.me/<phone>?text=<message>`; phone numbers must include country code (example: `254712345678`).
	- Data model fields: `id`, `name`, `phone`, `propertyAddress`, `rentAmount`, `paymentDay` (1-31), `lastPaymentDate`, `createdAt`.
	- Status logic: `getDaysUntilDue(paymentDay)` and color-coded status classes are used for due/overdue UI states — mirror this when adding features that affect due-date calculations.
	- Styling: component uses Tailwind CSS utility classes; keep styling consistent with that approach.
	- Icons: imports from `lucide-react`; adding or changing icons may require updating dependencies in the host project (ask before adding `npm`/`yarn` changes).

- When you see components like this in attachments or other folders, verify these before editing:
	- Is the component part of this repository? If not, confirm target repo and whether to add dependencies.
	- Where is `window.storage` implemented (host app, browser extension, or injected environment)? Ask the owner before replacing with localStorage or other storage.
	- Does the host project use TypeScript/React build tooling (Vite, CRA, Next)? If you add imports like `lucide-react`, ask before updating package manifests.

Examples of small, safe edits to perform without owner approval:
- Content or copy changes inside UI text (e.g., headings, how-to instructions).
- Non-invasive style tweaks using existing Tailwind classes in `website.html` or mirrored components.

When in doubt, ask one concise question about the environment (e.g., "Where is `window.storage` implemented?" or "Should I add `lucide-react` to package.json?").
