# aqv-public

Public-facing assets for the AquaVentus n8n form. Everything in this folder is safe to push to the `aqv-public` repository; keep private-only files outside of this directory.

## Contents
- `n8n-form-aquaventus.css`: Standalone form theme that inlines the logo via a data URI.
- `AQ-Logo.png`: Source logo for updates or alternative hosting.

## How to publish to GitHub
1) Create the public repo `aqv-public` on GitHub.  
2) From this folder:
```
git init
git checkout -b main
git remote add origin <git@github.com:you/aqv-public.git>
git add README.md n8n-form-aquaventus.css AQ-Logo.png
git commit -m "Initial public assets"
git push -u origin main
```

## Refreshing the inlined logo
If `AQ-Logo.png` changes, regenerate the base64 string used in `--brand-logo`:
```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes("AQ-Logo.png"))
```
Replace the `data:image/png;base64,...` value in the CSS with the new output.
