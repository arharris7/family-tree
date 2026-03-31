# Harris Family Tree Explorer

An interactive family tree spanning 10+ generations of the Harris family, from William Harris and Rebekkah Arret (Generation 1) all the way down to the youngest members today. Built as a single web page — no apps to install, just open it in a browser.

---

## Navigating the tree

The tree opens centred on Generation 1 (William & Rebekkah) at the top, with descendants spreading downward.

**On a phone or tablet**
- **Pan** — drag with one finger to move around the tree
- **Pinch to zoom** — use two fingers to zoom in and out
- **Zoom buttons** — the + and − buttons in the top-left corner
- **Reset View** — tap "Reset View" to jump back to Generation 1

**On a desktop or laptop**
- **Pan** — click and drag to move around
- **Scroll to zoom** — use your mouse wheel or trackpad
- **Zoom buttons** — the + and − buttons in the top-left corner
- **Reset View** — click "Reset View" to jump back to Generation 1

---

## Reading the tree

- **Blue border** — person is living
- **Grey border** — person is deceased
- **Dashed line** between two people — they are married or partnered
- **Solid lines** dropping down — connect parents to their children
- Remarriages are shown by a person appearing with multiple partners on the same row

---

## Adding a family member

All family data lives inside `index.html` in a JavaScript array called `familyData`. There are two parts to update:

**1. Add the person to the `nodes` array:**
```js
{ id: "unique_id", name: "Full Name", dob: "1990", isLiving: true }
```
For a deceased person, add `dod` (date of death) and set `isLiving: false`. If they are a child of existing people, add a `parents` field:
```js
{ id: "unique_id", name: "Full Name", dob: "1990", isLiving: true, parents: ["parent_id_1", "parent_id_2"] }
```

**2. If they have a partner, add a marriage to the `marriages` array:**
```js
{ id: "m_unique", partners: ["person_id", "partner_id"] }
```

Keep IDs short and descriptive — for example `"harris_jane_1990"` — so they're easy to read and reference.

---

## Technical notes

- Single-file app — everything is in `index.html` with no build tools or external dependencies
- Hosted on GitHub Pages, served directly from the `main` branch
- The layout engine automatically positions nodes top-down by generation and adjusts spacing around remarriages and large sibling groups
- Works on all modern browsers on desktop, iOS, and Android