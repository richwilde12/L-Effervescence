# L'Effervescence: setup

Two places hold the app: **Apps Script** (data and screens) and **GitHub Pages** (the icon and the home-screen wrapper).

There are no codes and no personal links. Everyone uses the same address, and the app asks "Who's this?" once on each phone.

## Files

| File | Goes to | Name there |
|---|---|---|
| `Code.gs` | Apps Script | `Code.gs` |
| `Index.html` | Apps Script | `Index` (HTML file) |
| everything in `github-pages/` | GitHub repo root | same names (`index.html` is lower case) |

## 1. Apps Script

1. Replace the contents of `Code.gs` and `Index` with the new files.
2. Deploy > Manage deployments > pencil > Version: **New version** > Deploy. (First time: Deploy > New deployment > Web app, Execute as **Me**, Who has access **Anyone**.)
3. Copy the deployment ID: the long string between `/s/` and `/exec` in the web app URL.

The `Tasting_Log` tab gets two new columns, `Serena Score` and `Liz Score`, by itself the first time the app loads. Your existing rows are untouched. The old `Links` tab is no longer used; you can delete it.

## 2. GitHub Pages

1. New public repository (for example `effervescence`). Upload the contents of `github-pages/` to its root.
2. Settings > Pages > Deploy from a branch > `main` / root. The site address is `https://YOUR-NAME.github.io/effervescence/`.
3. Open `index.html` in the repo and click the pencil. Near the top of the script, replace `YOUR_DEPLOYMENT_ID` in the `EXEC_URL` line with your deployment ID. Commit and wait a minute for the site to update.

## 3. Using it on each phone

Share the site address with each other. That is the only link.

1. Open the address.
2. The app asks **Who's this?**. Pick Serena or Liz, then confirm "Yes, that's me".
3. Add it to the home screen:
   - **iPhone:** Safari > Share > Add to Home Screen. Delete any older icon first. Open the new icon and pick your name there if it asks.
   - **Android:** Chrome > menu > Install app (or Add to Home screen).
4. From then on the icon opens as you. On Top 5, **Not you?** lets you switch.

Opening the plain Apps Script address (the `.../exec` one) also works, but it can't remember who you are, so it asks every time. Use the GitHub address day to day.

## Privacy

There is no lock. Anyone who has the site address, or finds the Apps Script address, can open the app and add tastings. For a private two-person app that is usually fine, but don't share the address widely. If it leaks, redeploy as a new deployment: the old address stops working and you only need to update the `EXEC_URL` line.

## Real-device check

Emulation is not proof. On each phone:

1. Open the home-screen icon the first time: it asks Who's this?. Pick your name and confirm. Close the app fully and reopen it: no question this time, Top 5 says "Signed in as ...", and Taste has you pre-selected.
2. The tab bar sits fully above the home bar, at the bottom of the screen, with no clipped or overlapping area.
3. Open Cellar, then press Back (Android) or swipe back (iPhone): it returns to Top 5 and stays in the app.
4. Add a bottle on one phone. Bring the other phone to the front: within about a minute it shows the bottle.
5. Type a producer and cuvée you already have in Add bottle: the "Already waiting" or "Tasted before" note appears.
6. Delete the icon, add it again, and open it: it asks once more (a new icon starts fresh), and remembers again after that.

## Known limits

- Google's "created by an Apps Script user" banner still shows inside the wrapper. It can't be removed from here.
- The wrapper's iPhone safe-area handling and the Android install prompt can only be proven on real phones.
- Hand edits made directly in the Sheet can take up to 2 minutes to appear in the app.
