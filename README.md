# Local preview

This repository is a minimal, single-file static site. Use one of the following methods to preview changes locally.

1) VS Code Live Server (recommended)

- Install the "Live Server" extension in VS Code.
- Right-click `website.html` in the Explorer and choose "Open with Live Server", or run `Live Server: Open with Live Server` from the Command Palette.

2) Python built-in server (no extra installs if Python is available)

```powershell
cd path\to\repo
python -m http.server 8000
# Open http://localhost:8000/website.html
```

3) Node-based quick server (if Node.js is available)

```powershell
npx serve -s . -l 8000
# or
npx http-server -p 8000
```

Notes
- There is no build step, package manifest, or tests in this repository. Keep edits localized to `website.html` unless authorized to add files.
- If you plan to add tooling or CI, confirm with the repository owner first and document setup steps in this README.
