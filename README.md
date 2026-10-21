# MTG Command Zone

Magic: The Gathering app for Commander (EDH) deck analysis, proxy making, and in-game tracking — a single self-contained HTML file with no server, no build step, and no dependencies beyond a browser. All card data is pulled live from [Scryfall](https://scryfall.com) as you use it; nothing you paste in ever leaves your browser.

## Using it

Open [`index.html`](./index.html) directly in a browser, or enable **GitHub Pages** for this repo (Settings → Pages → Deploy from branch → `main` / root) to get a shareable live link.

The app has four tabs, in this order:

### Print Proxy Sheets
Paste a decklist and print it at **genuine card size** (2.5″ × 3.5″), 9 cards per US Letter page in a 3×3 grid with cut guides — ready to save as a PDF via your browser's print dialog (set scale to 100%, paper size to Letter) for playtesting/proxying. Includes options to skip basic lands and to include/exclude the commander.

**Print style** — a dropdown that picks a matching printing for every card on the sheet: default, oldest (original), newest, borderless, extended art, showcase, full art, retro frame (1993/1997), promo, or textless. Cards with no printing in that style keep their default art, and the sheet tells you which ones. After generating, hover (or tap) any card to pick a specific printing of just that card from a list of every set it's been printed in. Art Series cards and other non-gameplay "memorabilia" printings are never offered. Changed cards get a purple outline on screen; the pickers and outlines never appear on the printed page.

### Low Sodium
Everything about the Low Sodium 2.0 house format in one place (the list is built in, so it all works instantly with no card lookup):
- **Instant check** — paste a commander and a list (Moxfield/Archidekt exports work as-is) and get a verdict, a per-rule tally, and the reason each banned card is banned. Commander-only bans are marked "OK in 99". One click hands the same list to the full analyzer, which also catches misspelled names.
- **Rules breakdown** — the twelve headline rules (no tutors, no mass land denial, no extra turns, no discard, no fast mana, no free interaction, no stax or taxes, no mind control, no commander denial, no removal engines, no locks, no severe resource imbalances) with live card counts, plus how the 99 and command-zone lists differ.
- **The ban list, by rule** — every banned card (~2,900) shown as a card-art grid, in collapsible sections by category (closed until you click one, with Expand all / Collapse all), then under the exact wording of the rule that bans it. Tap a card to enlarge it and read its rule; search by name or rule text; filter by category or "banned everywhere" vs "commander only". Card art loads from Scryfall as you scroll, in batches.

The embedded list is a dated snapshot (shown in the app); refresh it by regenerating the `LOW_SODIUM_2` block in `index.html`.

### Game Tools
Everything you need at the table during a game, with state that survives a page reload:
- **Dice roller** — d4, d6, d8, d10, d12, d20, d100, or a custom side count; roll up to 20 dice at once, see each face plus the total, and a scrollable history of recent rolls
- **Mana pool** — a simple floating-mana tracker for all five colors plus colorless
- **Life total** — quick ±1/±5 buttons and a resettable starting life
- **Commander damage** — a tracker per opponent (add/remove/rename freely), with lethal (21+) highlighted
- **Counters** — built-in Poison (lethal at 10), Experience, and Energy, plus free-form custom counters for anything else (Rad, Ascend, Shield, Ki, Ticket, etc.)
- A single "Reset all" button zeroes life/mana/counters for a new game while keeping your named opponents and custom counters

### Deck Analyzer
Paste a commander and a decklist to get:
- Legality, singleton, and color-identity checks (official Commander rules, or a stricter "Low Sodium 2.0" house ban list you can toggle on — results come with a compliant / not-compliant verdict, a per-rule tally, and the exact reason each card is banned)
- Card art for every card in the list, including the commander
- Mana curve and a color-source/land-base analysis (hypergeometric odds of hitting your colors on curve)
- Known 2–3 card infinite combo detection
- A "functional balance" breakdown (ramp, draw, removal, wipes, protection, recursion, tutors) against typical Commander ratios
- Card suggestions pulled from what's popular in your color identity, each with an explanation of why it was suggested
- A generated markdown deck primer

### cEDH Guide
A guide to competitive Commander, split into sub-tabs: a primer, a metagame tier list (top commanders with entries and points-per-game from cedhstats.org, a dated snapshot), deck archetypes, common combos, staple cards with art, banlist and bracket context, and a glossary with sources. Card art and Commander legality are fetched live from Scryfall, so a banned card is flagged automatically; Low Sodium bans are marked on the staples.

### Random Commander
Rolls a random card that is legal as a commander right now (via Scryfall's random endpoint). Filter by color identity (exact, within, or at least), maximum price, partner commanders, and legendary creatures only. Each result shows the card, type, mana cost, colors and price, optional Oracle text, and an EDHREC link, with one-click hand-off to the Deck Analyzer and a history of recent rolls. Inspired by randomcommander.com.

## Look and feel
- **Mana symbols** (self-drawn SVG, so they work offline) appear wherever colors do: the header, Game Tools mana pool, Deck Analyzer color identity and mana-source rows, Random Commander filters and results (including mana costs), and the cEDH tier list.
- **Fantasy theme:** the button in the top-right switches between the classic look and a parchment-and-gold fantasy look (a night-castle variant when your device is in dark mode). The choice is remembered in your browser. Fonts (Cinzel, Crimson Text) load from Google Fonts only when the theme is on, and fall back to system serif fonts offline. Printing is unaffected.

## Notes

- For playtesting and personal use only — proxies are not tournament-legal cards.
- Card data, legality, and images come from the [Scryfall API](https://scryfall.com/docs/api).
