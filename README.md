# walkingdead-rpg

A standalone character generator for **The Walking Dead Universe Roleplaying
Game** (the Year Zero Engine tabletop game by Free League Publishing / Fria
Ligan AB, under license from AMC). Built as a community fan tool.

Single self-contained static page: `index.html` (no build step, no
dependencies, no CDN - all CSS, JS and game data are inline, and the official
character sheet is embedded as a base64 image).

## The engine (Year Zero Engine)

Unlike the POTA generator (D6 Magnetic), the Space: 1999 generator (2d20), and
the Judge Dredd generator (WOIN / N.E.W.), this game runs on Free League's
**Year Zero Engine**, in the "no-XP-at-start, point-buy" configuration the
book's own character-creation walkthrough (core rulebook p.24) lays out:

- **d6 dice pools** - attribute dice + skill dice, plus optional stress dice,
  rolled against successes; 6s succeed.
- **Point-buy creation** in a fixed order: choose an archetype, name, Issue and
  Drive; distribute **13 points** across four attributes (2-4, key attribute up
  to 5); distribute **12 points** across twelve skills (max 2, key skill up to
  3); choose one of the archetype's three talents; roll gear; define
  relationships; choose two Anchors (one PC, one NPC); describe a haven.
- Health is a flat **3** (Unharmed / Bruised / Battered / Broken), Stress and XP
  start at 0, and encumbrance is **Strength + 2**.

All 12 archetypes (key attribute/skill, three talents, suggested Issues/Drives,
D6 gear tables, relationships), all 12 skills, 59 talents, the weapon and gear
tables, the full D666 Scavenging table, the Scar table, and the three example
starting havens are transcribed verbatim from the core rulebook character
chapters.

## Hosting

Deployed as its own Vercel project. It is surfaced at
`https://thetapestry.distemperverse.com/walkingdead-rpg` via a proxy rewrite in
the TheTapestry app, so the public URL is unchanged while the code lives here,
out of the commercial TheTapestry repo (per that repo's AGENTS.md rule against
mixing in unrelated projects).

Because the rewrite is a proxy, the page runs on the
`thetapestry.distemperverse.com` origin, so the built-in visit beacon (bottom of
`index.html`) posts a `page='/walkingdead-rpg'` visit to the shared `log-visit`
edge function - the `/walkingdead-rpg-log` dashboard in TheTapestry reads those.

## Features

- Light (aged parchment) and Dark (charcoal night) themes, saved to
  `localStorage` and applied before paint to avoid a flash.
- Print output (`@media print`) overlays the character onto the official AMC /
  Free League character sheet page image, positioned in percentages.
- Portrait upload (drops into the sheet), Randomize-all for quick builds,
  point-allocation gating, and archetype-aware talent/gear pickers.
- Fully self-contained: inline everything, ASCII-only source, min 12px fonts.

## Notes

- Visit logging respects the owner opt-out (`localStorage tapestry_no_log = '1'`).
- Copyright: The Walking Dead Universe (C) 2023 AMC Film Holdings LLC. All Rights
  Reserved. The Walking Dead Universe Roleplaying Game (C) 2023 Fria Ligan AB
  (Free League Publishing), published under license from AMC. This is an
  unofficial fan tool, not affiliated with or endorsed by the rights holders.
