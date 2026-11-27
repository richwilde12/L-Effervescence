# L'Effervescence: setup

Two places hold the app: **Apps Script** (data and screens) and **GitHub Pages** (the icon and the home-screen wrapper).

## Files

| File | Goes to | Name there |
|---|---|---|
| `Code.gs` | Apps Script | `Code.gs` |
| `Index.html` | Apps Script | `Index` (HTML file) |
| everything in `github-pages/` | GitHub repo root | same names (`index.html` is lower case) |

## 1. Apps Script

1. Replace the contents of `Code.gs` and `Index` with the new files.
2. In the editor, choose the function **setupLinks** and press Run (approve the permissions). It creates a `Links` tab with a random code each for Serena and Liz. View > Execution log shows them.
3. Deploy > Manage deployments > pencil > Version: **New version** > Deploy. (First time: Deploy > New deployment > Web app, Execute as **Me**, Who has access **Anyone**.)
4. Copy the deployment ID: the long string between `/s/` and `/exec` in the web app URL.

The `Tasting_Log` tab gets two new columns, `Serena Score` and `Liz Score`, by itself the first time the app loads. Your existing rows are untouched.

## 2. GitHub Pages

1. New public repository (for example `effervescence`). Upload the contents of `github-pages/` to its root.
2. Settings > Pages > Deploy from a branch > `main` / root. The site address is `https://YOUR-NAME.github.io/effervescence/`.
3. Open `index.html` in the repo, edit the `EXEC_URL` line, paste your deployment ID, commit.

## 3. Personal links and the home-screen icon

Each person's link is the site address plus their code:

`https://YOUR-NAME.github.io/effervescence/?r=THEIR-CODE`

- **iPhone:** open the link in Safari > Share > Add to Home Screen. Delete any older icon first.
- **Android:** open the link in Chrome > menu > Install app (or Add to Home screen).

Anyone without a valid link sees "This link isn't recognised", and the server refuses reads and writes without a valid code. To cut someone off, change their code on the `Links` tab.

## Real-device check

Emulation is not proof. On each phone:

1. Open the home-screen icon. It opens as you (Serena or Liz is pre-selected on Taste), with no name prompt.
2. The tab bar sits fully above the home bar, with no clipped or overlapping area.
3. Open Cellar, then press Back (Android) or swipe back (iPhone): it returns to Top 5 and stays in the app.
4. Add a bottle on one phone. Bring the other phone to the front: within about a minute it shows the bottle.
5. Type a producer and cuvée you already have in Add bottle: the "Already waiting" or "Tasted before" note appears.
6. Close the app completely and reopen it: still you.

## Known limits

- Google's "created by an Apps Script user" banner still shows inside the wrapper. It can't be removed from here.
- The wrapper's iPhone safe-area handling and the Android install prompt (it uses a manifest built in the page) can only be proven on real phones.
