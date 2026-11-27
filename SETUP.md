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
2. In the editor, choose the function **setupLinks** and press Run (approve the permissions). It creates a `Links` tab with one shared code. View > Execution log shows it. (If you ran the earlier version, the old Serena and Liz rows stay and keep working; delete them from the tab if you want them switched off.)
3. Deploy > Manage deployments > pencil > Version: **New version** > Deploy. (First time: Deploy > New deployment > Web app, Execute as **Me**, Who has access **Anyone**.)
4. Copy the deployment ID: the long string between `/s/` and `/exec` in the web app URL.

The `Tasting_Log` tab gets two new columns, `Serena Score` and `Liz Score`, by itself the first time the app loads. Your existing rows are untouched.

## 2. GitHub Pages

1. New public repository (for example `effervescence`). Upload the contents of `github-pages/` to its root.
2. Settings > Pages > Deploy from a branch > `main` / root. The site address is `https://YOUR-NAME.github.io/effervescence/`.
3. Open `index.html` in the repo, edit the `EXEC_URL` line, paste your deployment ID, commit.

## 3. The one link and the home-screen icon

There is a single link for both of you: the site address plus the shared code.

`https://YOUR-NAME.github.io/effervescence/?r=SHARED-CODE`

The first time it opens, the app asks **Who's this?**. Pick Serena or Liz and confirm "Yes, that's me". The wrapper remembers it on that phone, so it opens as you every time after.

- **iPhone:** open the link in Safari > Share > Add to Home Screen. Delete any older icon first. Then open the new icon and pick your name there.
- **Android:** open the link in Chrome > menu > Install app (or Add to Home screen). Then open the app and pick your name.
- **Wrong person picked, or sharing a phone:** on Top 5 tap **Not you?** and choose again.

Anyone without the code sees "This link isn't recognised", and the server refuses reads and writes without it. To cut off everyone who has the old link, change the code on the `Links` tab. Whoever opens the link and taps a name is treated as that person, which is fine for the two of you.

## Real-device check

Emulation is not proof. On each phone:

1. Open the home-screen icon the first time: it asks Who's this?. Pick your name and confirm. Close the app fully and reopen it: no question this time, Top 5 says "Signed in as ...", and Taste has you pre-selected.
2. The tab bar sits fully above the home bar, with no clipped or overlapping area.
3. Open Cellar, then press Back (Android) or swipe back (iPhone): it returns to Top 5 and stays in the app.
4. Add a bottle on one phone. Bring the other phone to the front: within about a minute it shows the bottle.
5. Type a producer and cuvée you already have in Add bottle: the "Already waiting" or "Tasted before" note appears.
6. Delete the icon, add it again from the link, and open it: it asks once more (a new icon starts fresh), and remembers again after that.

## Known limits

- Google's "created by an Apps Script user" banner still shows inside the wrapper. It can't be removed from here.
- The wrapper's iPhone safe-area handling and the Android install prompt (it uses a manifest built in the page) can only be proven on real phones.
