# MTG Command Zone

Magic: The Gathering app for Commander (EDH) deck analysis, proxy making, and in-game tracking — a single self-contained HTML file with no server, no build step, and no dependencies beyond a browser. All card data is pulled live from [Scryfall](https://scryfall.com) as you use it; nothing you paste in ever leaves your browser.

## Using it

Open [`index.html`](./index.html) directly in a browser, or enable **GitHub Pages** for this repo (Settings → Pages → Deploy from branch → `main` / root) to get a shareable live link.

The app has three tabs:

### Deck Analyzer
Paste a commander and a decklist to get:
- Legality, singleton, and color-identity checks (official Commander rules, or a stricter "Low Sodium 2.0" house ban list you can toggle on)
- Card art for every card in the list, including the commander
- Mana curve and a color-source/land-base analysis (hypergeometric odds of hitting your colors on curve)
- Known 2–3 card infinite combo detection
- A "functional balance" breakdown (ramp, draw, removal, wipes, protection, recursion, tutors) against typical Commander ratios
- Card suggestions pulled from what's popular in your color identity, each with an explanation of why it was suggested
- A generated markdown deck primer

### Print Proxy Sheets
Paste a decklist and print it at **genuine card size** (2.5″ × 3.5″), 9 cards per US Letter page in a 3×3 grid with cut guides — ready to save as a PDF via your browser's print dialog (set scale to 100%, paper size to Letter) for playtesting/proxying. Includes options to skip basic lands and to include/exclude the commander.

### Game Tools
Everything you need at the table during a game, with state that survives a page reload:
- **Dice roller** — d4, d6, d8, d10, d12, d20, d100, or a custom side count; roll up to 20 dice at once, see each face plus the total, and a scrollable history of recent rolls
- **Mana pool** — a simple floating-mana tracker for all five colors plus colorless
- **Life total** — quick ±1/±5 buttons and a resettable starting life
- **Commander damage** — a tracker per opponent (add/remove/rename freely), with lethal (21+) highlighted
- **Counters** — built-in Poison (lethal at 10), Experience, and Energy, plus free-form custom counters for anything else (Rad, Ascend, Shield, Ki, Ticket, etc.)
- A single "Reset all" button zeroes life/mana/counters for a new game while keeping your named opponents and custom counters

## Notes

- For playtesting and personal use only — proxies are not tournament-legal cards.
- Card data, legality, and images come from the [Scryfall API](https://scryfall.com/docs/api).
