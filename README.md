# Vyapaar Pay – what's in this folder

Prototype for the **Paytm Innovation Challenge 2026, Track B**, by Velocity Squad, IIM Bangalore.
It is a plain static website: no build step, no server and no installs. Upload the folder and it works.

---

## 1. Folder map

```
vyapaar-pay-site/
├── index.html        ← the full Vyapaar Pay app (6 business types, shop + supplier views)
├── demo/
│   └── index.html    ← the guided field demo for shop owners (records reactions)
├── FEATURES.md       ← what every feature does and why (concept document)
└── README.md         ← this file
```

| File | Open it when you want to… | Size |
|---|---|---|
| `index.html` | Show the complete product: all screens, sample data for six businesses, both sides of a credit agreement | ~300 KB |
| `demo/index.html` | Sit with a real shop owner: explain features one by one, let them set up their own shop, and record what they think | ~90 KB |
| `FEATURES.md` | Understand or present the concept – every feature explained in plain words | – |
| `README.md` | Understand the files, deploy, edit or troubleshoot | – |

Each HTML file is **self-contained**: styles, code, icons and the Paytm logo are all inside it. The only outside request is the Mukta font from Google Fonts; if that fails (no internet), the system font is used and everything still works.

The two apps link to each other:
- **Main app → demo:** the **Field demo** button in the top bar, the banner on the business-type screen, and Menu → Demo controls.
- **Demo → main app:** **Open the full app** on the demo home screen.

---

## 2. Put it online

### Option A – GitHub + Vercel (recommended)
1. Create a new repository on GitHub, for example `vyapaar-pay`.
2. Click **Add file → Upload files** and drag in **the contents** of this folder: `index.html`, the `demo` folder, and the two `.md` files. `index.html` must be at the top level of the repo, not inside another folder. Click **Commit**.
3. Go to vercel.com and sign in with GitHub. Click **Add New → Project** and pick the repo.
4. Set **Framework preset** to *Other*. Leave the build command empty and set the output directory to `/` (or leave it blank). Click **Deploy**.
5. You get a link like `https://vyapaar-pay.vercel.app`.
   - The main app is at `/`.
   - The field demo is at `/demo/`.
6. Every change you commit to GitHub redeploys automatically.

### Option B – GitHub Pages
In the repo, go to **Settings → Pages**. Set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, and save. The site appears at `https://<username>.github.io/vyapaar-pay/`.

### Option C – no internet / on a laptop
Unzip and double-click `index.html` (or `demo/index.html`). Everything works offline except the font.

---

## 3. How the main app (`index.html`) is organised

Everything is in one file: styles at the top, then one `<script>`. The script is built in three layers, each marked with a comment banner. Later layers replace earlier functions of the same name.

| Layer | Look for this comment | What it contains |
|---|---|---|
| Base (v2) | `/* ---------- personas ---------- */` | Icons, helpers, the six business types (`PERSONAS`), sample data (`seedForV2`), and screens: Pay, Dues, Book, Rate memory, Returns, Customer udhaar, Perks, Help, Settings, Agent setup; the pay flow (amount → PIN → success/pending/failed) |
| Two-sided khata (v3) | `v3 – two-sided khata` | The supplier each business switches to (`COUNTER`), credit agreements, interest maths, part payments, chat, the supplier view, score breakdown (`scoreParts`), lender offers, dashboard and forecast, re-tagging, cash and cheques |
| Cleaner shell (v4) | `v4 – cleaner shell` | Top bar with the Display menu, menu button at top-left, trimmed sidebar, simpler Home, simpler due rows, perks based on value paid |

### Things you may want to edit

| To change… | Edit |
|---|---|
| A business type's name, owner, suppliers, dues, bills, quote | `PERSONAS.<type>` (search `const PERSONAS`) |
| Which supplier the "Supplier" view shows, and its customers | `COUNTER.<type>` (search `const COUNTER`) |
| Score weights or wording | `scoreParts()` |
| Interest rules | `agrInt()` (interest), `applyPay()` (interest first, then bill) |
| Perk levels | `const LEVELS` |
| Words on the Home screen | `function homeScreen()` in the v4 layer |

After editing, open the file in a browser. Use **Menu → Demo controls → Reset data** to reload the sample data for that business.

---

## 4. How the field demo (`demo/index.html`) is organised

One file with five parts, plus home, guide and saved-session screens:

| Part | Screen function | What happens |
|---|---|---|
| Before we begin | `setup()` | Interviewer details and consent (required to continue) |
| 1 · See the features | `tour()` | 8 feature screens with a picture, Hinglish line and reaction buttons |
| 2 · Try it yourself | `tryShop()` → `trySups()` → `tryDues()` → `tryApp()` | Starts empty: shop → suppliers → udhaar → their own app (pay part, more days, supplier's view) |
| 3 · Feedback | `feedback()` | 9 questions plus interviewer task ratings and notes |
| Saved | `done()`, `sessions()` | Summary, list of sessions, CSV/JSON download |

### Things you may want to edit

| To change… | Edit |
|---|---|
| Feature screens (title, Hinglish line, text, picture) | `const F = [...]` (and the `mock…()` functions for pictures) |
| Feedback questions | `const Q = [...]` (types: `one`, `many`, `scale`, `text`) |
| Tasks the interviewer rates | `const TASKS` |
| Business types and supplier suggestions | `const TYPES`, `const SUGGEST` |
| Ways people pay today (asked when adding a supplier) | `const PAYVIA` |

---

## 5. Where data is saved

Everything is saved **only in the browser on that device**, using `localStorage`. Nothing is sent anywhere.

| App | Storage key | What |
|---|---|---|
| Main app | `vyapaar-pay-v4-prefs` | Chosen business type, Shop/Supplier, language, view, theme |
| Main app | `vyapaar-pay-v4-data-<type>` | That business's data (payments, agreements, chats) |
| Field demo | `vyapaar-field-demo-v1` | All demo sessions (answers, reactions, what they entered) |
| Field demo | `vyapaar-field-demo-v1-interviewer`, `-area`, `-theme` | Remembered interviewer name, area and theme |

### Getting demo results out
1. Open the demo → **Saved sessions** → **Download all (CSV)**. You get one row per session, 52 columns.
2. The CSV opens in Excel or Google Sheets.
3. Columns are grouped as:
   - session details;
   - `react_*` / `note_*` per feature;
   - what they entered (shop, suppliers, udhaar);
   - `did_*` – what they tried;
   - `task_*` – interviewer ratings;
   - the feedback answers.

**Download at the end of every field day.** Clearing browser data, or using private/incognito mode, removes saved sessions. **Reset** in Saved sessions deletes them on purpose.

Use the **same phone and browser** for a whole field day, so all sessions sit in one list.

---

## 6. Troubleshooting

| Problem | Fix |
|---|---|
| Blank page on Vercel | Make sure `index.html` is at the top of the repo, not inside `vyapaar-pay-site/`. |
| `/demo/` shows "404" | The `demo` folder must be uploaded with its `index.html` inside it. |
| Download button does nothing | Some in-app previews block downloads. Open the link in Chrome or Safari directly. |
| Sessions disappeared | The browser was in private mode or its data was cleared. Download CSVs after every session day. |
| Want fresh sample data | Main app → Menu → Demo controls → **Reset data** (resets the current business only). |
| Voice (Soundbox) is silent | Browsers only speak after a tap, and some phones have no Hindi voice. The on-screen Soundbox card still shows the text. |

---

## 7. Notes

- All names, amounts, lenders, interest rates and scores are **illustrative demo data**. No real payments happen.
- The design follows the Paytm for Business look (navy, cyan, Paytm wordmark), with light and dark themes and readable contrast.
