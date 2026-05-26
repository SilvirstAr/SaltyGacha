# Prompt History - Slaty Gacha Simulator

## 1. Requirement Reading

Prompt:

> Read the Thai exam workbook for Gacha Drop Rate Simulator. Ignore the English version. Summarize must-have, advanced, bonus, file requirements, tech constraints, and scoring rubric.

Purpose:

- Identify what the final submission must include.
- Confirm that the deliverable must be a single HTML file.

Output used:

- Must-have checklist for rate settings, item pool, single simulation, result display, CSV export, and validation.
- Advanced checklist for Player POV Monte Carlo and free roll rule.
- Bonus checklist for pity, history, chart, and UI polish.

## 2. Product and Theme Setup

Prompt:

> Build a single-file HTML/CSS/JS gacha simulator named "Slaty Gacha Simulator". Theme: fantasy adventure, 8-bit, 80s-90s game feeling, cute icons/symbols, pastel nature colors with green/brown/floral accents. Currency: THB plus a generic in-game currency called Leaf with a cute 8-bit leaf symbol.

Purpose:

- Define product identity, visual direction, and default currency system.

Output used:

- Nature-fantasy UI with pixel-inspired decorative style.
- Leaf currency icon built in CSS.
- Pastel green/brown/floral palette.

## 3. Original Item Pool Design

Prompt:

> Create original 8-bit style placeholder character names for SSR, SR, R, and N. Do not use copyrighted game characters or external assets. Make sure each rarity has at least one item so the simulator works immediately.

Purpose:

- Avoid copyrighted assets.
- Provide a ready-to-test default item pool.

Output used:

- SSR: Princess Clovera, Verdant Dragon Pup
- SR: Moss Witch Miri, Bloom Archer Nola, River Bard Lute
- R: Acorn Scout, Petal Rogue, Twig Guardian
- N: Leaf Slime, Mushroom Page, Sprout Sprite, Pebble Snail

## 4. Gacha Logic

Prompt:

> Implement gacha logic that first rolls rarity by configured rates, then randomly chooses an item from that rarity's pool. Use Math.random and do not hardcode results. Validate that total rate is exactly 100 and every active rarity has an item.

Purpose:

- Build correct gacha simulation behavior.
- Prevent invalid or impossible item pools.

Output used:

- `weightedRarity()`
- `pickItem()`
- `validateCore()`
- Result summary and actual percentage table.

## 5. Free Roll and Pity Logic

Prompt:

> Add a free roll rule: after X paid rolls, grant Y free rolls. Free rolls must not generate more free rolls. Add optional pity: guarantee SSR after a configured number of rolls without SSR. Ensure these rules work in both single simulation and Player POV Monte Carlo.

Purpose:

- Cover advanced and bonus scoring requirements.

Output used:

- Free roll toggle and inputs.
- Pity toggle and threshold input.
- Shared roll sequence logic for single simulation and Monte Carlo.

## 6. Player POV Monte Carlo

Prompt:

> Build Player POV Simulator. User inputs budget in THB, price per roll, Leaf per roll, simulation count, and target item. Calculate paid rolls, free rolls, total rolls, chance of at least one SSR, chance of zero SSR, chance of target item, average SSR, best SSR, and worst SSR.

Purpose:

- Show player-facing probability and spending insight.

Output used:

- Monte Carlo summary cards.
- Human-readable insight text.
- Probability bars.
- Player POV CSV export.

## 7. CSV Export

Prompt:

> Add CSV export in browser without backend. Export latest pull result with roll number, rarity, item name, cost type, THB cost, Leaf cost, and pity flag. Export Player POV summary with budget, paid rolls, free rolls, probability, averages, and total Leaf cost.

Purpose:

- Meet mandatory CSV export and advanced CSV requirements.

Output used:

- `downloadCsv()`
- `exportLatestPullCsv()`
- `exportPovCsv()`

## 8. UI Validation and Polish

Prompt:

> Add clear validation messages for invalid rates, negative values, missing item pools, too many rolls, and missing simulation results. Make the UI responsive, readable, and playful without requiring external libraries or build tools.

Purpose:

- Improve usability and meet validation/UI scoring.

Output used:

- Validation message box.
- Responsive panels.
- Rounded cards, pixel sprites, Leaf token, history table, empty states, and chart bars.

## 9. Final Verification Prompt

Prompt:

> Verify the final single HTML file: JavaScript syntax is valid, default item pool covers all rarities, CSV buttons exist, single simulation and Player POV controls exist, and all must-have/advanced/bonus sections are present.

Purpose:

- Check readiness before submission.

Output used:

- Local syntax check.
- Final submission checklist.

## 10. Visual Direction Update

Prompt:

> Add the provided pixel forest sword image as the overall background, adjust colors to fit the nature fantasy theme, and change the hero text to: "ทดสอบโชคในโลกแฟนตาซี 8-bit ปรับเรท เพิ่มตัวละคร ลองงบประมาณ และดูว่าการสุ่มแต่ละครั้งคุ้มกับ Leaf (สกุลเงิน) แค่ไหน"

Purpose:

- Make the page feel more like an 8-bit fantasy adventure while keeping text readable.

Output used:

- Embedded the provided image as a data URI so the HTML remains self-contained.
- Added soft cream/green overlays, translucent panels, and updated hero copy.
