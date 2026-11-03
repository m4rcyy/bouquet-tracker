# Petal Ledger — Chenille Bouquet Tracker

A simple static offline-friendly browser application for tracking chenille bouquet materials, real purchasing costs, bouquet photos, selling prices and remaining stock. No server or build step needed. Currency: Malaysian Ringgit (RM).

## Files
- `index.html` — application layout
- `style.css` — responsive styling
- `script.js` — application logic, IndexedDB and preloaded material data

## Publish using GitHub Pages
1. Sign in to https://github.com and create a new **public** repository, for example `bouquet-tracker`.
2. Choose **Add file → Upload files**, and upload **index.html**, **style.css** and **script.js** directly into the top level (root) of the repository. Commit the files.
3. Open your repository **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**. Set branch **main**, folder **/(root)**, then click **Save**.
5. Open the published URL shown by GitHub Pages. It generally follows `https://YOUR-USERNAME.github.io/bouquet-tracker/`.
6. Save/bookmark this URL on your phone. On iPhone, you can use Safari → Share → Add to Home Screen; on Android, Chrome → menu → Add to Home screen.

## First use
- The materials and orders are already loaded for your first visit in each browser.
- Visit **Materials** to review entries marked **Pack size needed**. Enter the number of pieces/sheets/etc. in each pack.
- The **Local store** has RM9.50 in known chenille packs plus an unitemized RM24 balance to match your RM33.50 payment. The RM24 placeholder is **not verified as the price of the foam**; rename/replace it with actual purchases when you check your receipt.
- Click **New bouquet** and enter quantities used. Select photos to attach; the photos will be compressed and stored in IndexedDB.
- Suggested price uses *gross profit margin* (not markup). A 50% margin means price = cost / 0.5. Enter an actual selling price to see your profit.
- Use **Backup & restore → Download JSON backup** often and save it outside the browser.

## Important storage notes
Your data lives only in **this browser on this device**, not on GitHub or on a cloud server. GitHub Pages serves the website code but does not store your purchases, photos or bouquets. Different devices and browsers have independent data. To transfer records, export JSON from one browser and import it on the other. Importing **replaces** existing records on the target device. Clearing browser data may delete all your records, so keep backups.

Do not browse in private/incognito mode. Large numbers of photos may exceed the browser's storage quota. Export backups periodically. Uploading new versions of these three code files to GitHub does not normally erase data in the same browser at the same URL, but always export a backup before upgrades.

## How costs work
- Listed order total = sum (listed price per pack × packs bought)
- Order factor = actual amount paid ÷ listed order total
- Actual material cost per unit = (listed price per pack × order factor) ÷ units per pack
- Bouquet cost = sum (quantity used × actual unit cost) + optional labour, packaging, delivery and other costs
- Suggested selling price = bouquet cost ÷ (1 − profit margin / 100)
- Actual profit = actual selling price − bouquet cost

The displayed price/cost totals are rounded to two decimals; internal calculations use full precision. Edited material prices or orders recalculate costs in all bouquet records because they reference current catalogue prices.

## Starter order checks
| Order | Listed total | Actually paid | Factor |
|---|---:|---:|---:|
| Cake decorations (online) | RM10.12 | RM9.11 | 0.9002 |
| MOGO MALL | RM10.29 | RM10.27 | 0.9981 |
| Onestep-N | RM47.99 | RM55.21 | 1.1504 |
| EzWrap.my | RM27.78 | RM34.46 | 1.2405 |
| WISHAEARN | RM65.50 | RM52.96 | 0.8085 |
| KKshope | RM29.86 | RM23.97 | 0.8027 |
| Local store | RM33.50 | RM33.50 | 1.0000 |

Five starter material entries have unknown pack size: bouquet lined paper (white/pink), plaid paper (green pink/yellow), and the unitemized RM24 local store purchase.
