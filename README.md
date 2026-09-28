# Low Risk

A Vibe coded mobile-first web app I built to speed up my daily shift routines as Assistant Lead in the Low Risk area of a food production site. It replaces handwritten notes and mental math with quick taps on the phone.

**Live:** https://lautaroreche.github.io/lowrisk/

## Tabs

### Traceability
Morning picking of ingredients for the production team.
- Products listed in the same order as the paper traceability record, so values can be copied straight across.
- Batch codes in Julian date format (`DDD-SS`): each product keeps its fixed supplier suffix and remembers yesterday's batch, so most days it's just a tap on `+`.
- Multiple batches per product (e.g. `270/271-19`), never ahead of today's date.
- Mark products as done or pending (with the missing quantity). Done items collapse and move to the bottom; open items stay on top.
- kg → boxes calculator for products requested by weight.
- One-tap copy of the current vinegar batch code as a ready-to-send message.

### Handover
Shift handover report for the WhatsApp group.
- Guided form: rice rounds, kitchen porter area, vegetables, back area, afternoon picklist and free notes.
- Business rules built in (e.g. rice steps can't be selected out of order, lines are merged by round number, identical statuses are grouped).
- Live preview and a single **Copy report** button; required fields are validated before copying.

### Stock
Daily stock count.
- Each product starts from the previous day's count; adjust with `+` / `−` or type the number.
- Units per product and automatic equivalences (e.g. `3 BOX = 12 bottles`).
- Configurable **reorder points**: products turn yellow when close and red when below.
- Counter of products still missing a count.

### Tablet
In development: lookup from the names used on the delivery sheet to the product names and codes used on the client reporting tablet.

## How it works
- Single self-contained HTML file: plain HTML, CSS and vanilla JavaScript, no build step, no backend, no dependencies other than the Inter font.
- Each tab is an isolated module (scoped CSS, independent state).
- Data is saved automatically in the browser (`localStorage`). It stays on the device that uses it and is not shared between phones.
- Daily fields reset automatically at the start of a new day; long-lived data (batch codes, reorder points) is kept.

## Usage
Open the link on a phone and add it to the home screen:
- **iPhone (Safari):** Share → Add to Home Screen
- **Android (Chrome):** ⋮ menu → Add to Home screen

## Updating
Replace `index.html` in this repo with the new version and commit. GitHub Pages redeploys in a minute or two.
