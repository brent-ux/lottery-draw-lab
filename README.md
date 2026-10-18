# Lottery Draw Lab — Safari / iPad deployment

A static Powerball + Mega Millions interactive mechanical-draw simulator.

## Publish with GitHub Pages

1. Create a **new public** repository named `lottery-draw-lab` in your GitHub account (separate from investment repositories). Initialize with README if GitHub requests it.
2. Upload the contents of this ZIP to the **repository root**, replacing the placeholder README. `index.html` must be in the root, not inside a folder.
3. Go to **Settings → Pages → Build and deployment → Deploy from a branch**. Select `main` and `/(root)`, then **Save**.
4. Visit `https://YOUR-USERNAME.github.io/lottery-draw-lab/` after publishing finishes. On iPad use **Safari**; optional: Share → Add to Home Screen.

## Important notes

- HTML, CSS and JavaScript are fully client-side. No personal data or ticket choices are transmitted to us.
- Saved ticket history uses **the current browser's local storage** and does not sync between iPad and desktop. Use Export CSV or Export JSON for backups, especially before clearing Safari data.
- The published site is public. Do not upload private files or secrets to the repository.
- The simulator reproduces an **illustrative, estimated 2D mechanical process**. Exact official machines, operating parameters, and current loading sequences are not verified. It **does not improve the odds** of a particular ticket.
- Current user-selected Powerball main-ball load order: 50–59, then 20–29, then others in ascending order; bonus order unchanged.

Version: Web build based on simulator v3.9. Ticket Lab runs now yield periodically so Safari remains responsive during calculations.