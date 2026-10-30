# MTG Command Zone

Magic: The Gathering app for Commander (EDH) deck analysis, proxy making, and in-game tracking — a single self-contained HTML file with no server, no build step, and no dependencies beyond a browser. All card data is pulled live from [Scryfall](https://scryfall.com) as you use it; nothing you paste in ever leaves your browser.

## Using it

Open [`index.html`](./index.html) directly in a browser, or enable **GitHub Pages** for this repo (Settings → Pages → Deploy from branch → `main` / root) to get a shareable live link.

The app has four tabs, in this order:

### Print & Card Creator (one page)
Two sub-tabs share one printable sheet shown below them: print a decklist, or design a custom card (see Card Creator below) and add it to the same sheet.

#### Print a decklist
Paste a decklist and print it at **genuine card size** (2.5″ × 3.5″), 9 cards per US Letter page in a 3×3 grid with cut guides — ready to save as a PDF via your browser's print dialog (set scale to 100%, paper size to Letter) for playtesting/proxying. Includes options to skip basic lands and to include/exclude the commander.

**Print style** — a dropdown that picks a matching printing for every card on the sheet: default, oldest (original), newest, borderless, extended art, showcase, full art, retro frame (1993/1997), promo, or textless. Cards with no printing in that style keep their default art, and the sheet tells you which ones. After generating, hover (or tap) any card to pick a specific printing of just that card from a list of every set it's been printed in. Art Series cards and other non-gameplay "memorabilia" printings are never offered. Changed cards get a purple outline on screen; the pickers and outlines never appear on the printed page.

### Low Sodium (inside the Deck Analyzer)
Low Sodium is now part of the Deck Analyzer page: it uses the same commander and decklist boxes, with an "Instant Low Sodium check" button and the "Low Sodium check" and "Low Sodium rules & ban list" sub-tabs.

#### Low Sodium details
Everything about the Low Sodium 2.0 house format in one place (the list is built in, so it all works instantly with no card lookup):
- **Instant check** — paste a commander and a list (Moxfield/Archidekt exports work as-is) and get a verdict, a per-rule tally, and the reason each banned card is banned. Commander-only bans are marked "OK in 99". One click hands the same list to the full analyzer, which also catches misspelled names.
- **Rules breakdown** — the twelve headline rules (no tutors, no mass land denial, no extra turns, no discard, no fast mana, no free interaction, no stax or taxes, no mind control, no commander denial, no removal engines, no locks, no severe resource imbalances) with live card counts, plus how the 99 and command-zone lists differ.
- **The ban list, by rule** — every banned card (~2,900) shown as a card-art grid, in collapsible sections by category (closed until you click one, with Expand all / Collapse all), then under the exact wording of the rule that bans it. Tap a card to enlarge it and read its rule; search by name or rule text; filter by category or "banned everywhere" vs "commander only". Card art loads from Scryfall as you scroll, in batches.

The embedded list is a dated snapshot (shown in the app); refresh it by regenerating the `LOW_SODIUM_2` block in `index.html`.

### Game Tools (tabletop game table)
A full-screen Commander table for phones, tablets and desktops, modeled on apps like Lifetap, Lotus, Mythic Tools and Life Trinket. Pick 2-6 players, starting life (20/25/30/40/custom), names and colors, then start. Your game is saved and can be resumed after a reload.
- **Seat cards** - big life totals; tap the left/right half for -1/+1, hold for -10/+10; a change bubble shows the running total. In tabletop mode seats rotate to face each player (portrait and landscape layouts for every player count); switch to upright for a single shared device.
- **Commander damage** - tracked per opponent commander (partners supported) and optionally subtracted from life automatically; 21 from one commander is lethal. Commander tax tracker included.
- **Counters and status** - Poison (10 is lethal), Energy, Experience, Rad, custom named counters, Monarch, Initiative, City's blessing.
- **Commander art** - type a commander name to use its Scryfall art as the card background.
- **Defeat and winner detection** - life, poison, commander damage or concede; the last player standing is announced. Defeated players can be kept in the game.
- **Center hub menu** - dice (d4-d100, custom), coin flip, roll-for-first-player, random player picker, turn tracker with rounds (skips defeated players), mana pool, action log with undo, day/night, game clock, wake lock and full screen.
- The dice, coin and mana pool also open from the setup screen without starting a game.


### Mana Guide
Dual lands by cycle (original duals, shock, fast, slow, check, pain, temples, surveil, verge, bounce, filter, gain, Guildgates) with card images from Scryfall, filterable by color pair and cycle, plus rules of thumb for land counts, sources per color, pip counting, kinds of fixing and the triomes. Modeled on the [Mana Gathering](https://managathering.com/) dual lands guide.

### Deck Analyzer
**Import from a link:** paste an Archidekt or Moxfield deck link (or paste it straight into the decklist box) and the commander and decklist fill in. The deck must be public. The app first asks the site directly; if the browser blocks that, it retries through a public relay (only the deck link is sent, and the status line says so). If both fail, it tells you to paste the exported list instead. The same link box is on the Print page.

Sub-tabs: **Analysis**, **Mana base**, **Low Sodium check**, **Low Sodium rules & ban list**.

**Mana base optimizer:** after you analyze a deck, the Mana base tab compares the colored symbols your spells need with your lands and mana rocks, gives a target number of sources per color (rules of thumb), suggests a land count, the best split of your basic lands, flags tapped and colorless lands, and lists dual lands, triomes and other fixing you could add.

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

### Card Creator (a sub-tab of Print & Card Creator)
Design your own card: name, mana cost (with symbols, including hybrid, {X}, {T} and {Q}), type line, rarity, frame color (automatic from the cost and type, or chosen), rules text (reminder text in parentheses is italicized), flavor text, power/toughness or loyalty, artist credit, and a footer note. Upload a JPG or PNG for the art (or drag it onto the preview), then zoom and reposition it. Type an existing card's name (with suggestions) to use it as a template, optionally with its art. Finished cards can be downloaded as a 744×1039 PNG (about 2.5×3.5 inches at 300 dpi), saved in the browser, or added to the Print Proxy sheet in any number of copies; they stay on the sheet when you rebuild it and each has a Remove button. The card frame is an original design, not Wizards of the Coast's.

### MTG Lore
The story of Magic, two ways. **By set:** 109 premier sets in release order, grouped into story eras (The Early Years through the Metronome finale, ending with Reality Fracture), each with date, plane, a short spoiler-light summary and featured characters; search by set, plane or character, filter by era or plane, and flip the sort. Set icons load live from Scryfall. **Story order:** an in-universe timeline from before recorded history to the Age of Omenpaths, with Dominaria's AR dates and the sets that tell each stretch (click a set to jump to it). A third section lists Universes Beyond crossovers and the sources used. Dates come from Wikipedia's set list and the community MTG Wiki timeline; some placements are marked approximate.

## Look and feel
- **Mana symbols** (self-drawn SVG, so they work offline) appear wherever colors do: the header, Game Tools mana pool and seat menus, Deck Analyzer color identity and mana-source rows, Random Commander filters and results (including mana costs), and the cEDH tier list.
- **Fantasy theme:** the whole app uses a parchment-and-gold fantasy look (a night-castle variant when your device is in dark mode). Fonts (Cinzel, Crimson Text) load from Google Fonts and fall back to system serif fonts offline. Printing is unaffected.

## Notes

- For playtesting and personal use only — proxies are not tournament-legal cards.
- Card data, legality, and images come from the [Scryfall API](https://scryfall.com/docs/api).
