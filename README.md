# Daily routine assistant

A password-protected, mobile-first web app I built to speed up my daily routine as Assistant Lead in the Low Risk area of a food production site. It replaces paper notes, mental math and retyped WhatsApp messages with a few taps on the phone.

**Live:** https://lautaroreche.github.io/lowrisk/ (password required)

**Version:** 2.0.0

## Sections

### 🗓️ Roster
Weekly work roster. Upload the PDF (or a photo) once a week; PDFs are converted to images on the phone so they open instantly and offline. Shows how old the current roster is.

### To Do
Opens by default.
- **Daily tasks** that come back unticked every day, editable and reorderable from *Manage*.
- **Extra tasks** added on the fly; they stay until ticked.
- Ticked tasks move to a collapsed **Done** section at the end instead of being deleted.

### Traceability
Morning picking of ingredients for the production team.
- Batch codes in Julian date format (`DDD-SS`) with a fixed supplier suffix per item; adjust with `+` / `−` or type the day.
- Several batches per item when needed; at the start of each day only the newest one is kept.
- **Given** box for the quantity handed over so far, done tick, and items pinned as *always done*.
- kg → boxes calculator for items requested by weight, and a one-tap batch report message.
- *Manage*: add, rename or remove items, change supplier codes, pin always-done items.

### Handover
Shift handover report for the WhatsApp group.
- Guided form with dropdowns, chips and checkboxes; required fields are checked before copying.
- Business rules built in (rice steps in order, lines merged by round, identical statuses grouped).
- Header switches automatically from the *estimated* report to the final one once the report time (14:00, or 14:30 on Saturdays) has passed.
- Everything returns to its defaults every day.

### Stock
Daily stock count, alphabetical.
- Starts from the previous day's count; `+` / `−` or type the number.
- Unit per product and automatic equivalences (e.g. `3 BOX = 13.5 kg`).
- Reorder points: products turn yellow when close and red when below.
- *Manage*: reorder points, editable equivalences, add or remove products.

### Packing
- **Picklist**: trays, boxes and other packaging, colour-coded by type, with a photo of each carton and an overview photo of all trays.
- **Sushi**: every sushi tray with its photo and contents (pieces in bold); *Manage* to rename, edit contents, add or remove items and take or replace photos.

## How it works
- A single self-contained HTML file: plain HTML, CSS and vanilla JavaScript. No backend, no build tools, no dependencies other than the Inter font and pdf.js (loaded only when a PDF roster is uploaded).
- Each section is an isolated module (scoped CSS, independent state); an error in one section can't break the others.
- Data is stored on the device (`localStorage` and IndexedDB for photos). It never leaves the phone and is not shared between devices.
- The published page is encrypted with [StatiCrypt](https://github.com/robinmoisson/staticrypt) (AES-256): the repository only contains ciphertext, and the app opens after logging in. Sessions last 10 hours; the log-out button at the end of the tab bar forgets the password on that phone without touching the data.

## Usage
Open the link on the phone, log in, and add it to the home screen (Chrome: ⋮ menu → *Add to Home screen*).

When clearing the browser history, untick *Cookies and site data* to keep the app's data.

## Updating
Replace `index.html` with the new encrypted version and commit. GitHub Pages redeploys in a minute or two.
