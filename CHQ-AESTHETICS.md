# CHQ Aesthetics — start here

Written Oct 8 2026 for the new **CHQ Aesthetics** chat. That chat is only for looks: things not lining up, pills not perfectly round, an X off-center, a menu not in the family, spacing that doesn't match. Every fix goes **module first** (Frank sees it, full screen on his phone), **then into the app** as the next version.

Current app: **CollisionHQ v5.183** (Desktop › Collision HQ › Collision HQ v5).

---

## 1. Read these first (in this project)

**`modules/chq-family.html` — CHQ Family.** The newest and complete picture of how everything looks: every button, box, menu, icon and mark drawn at real size next to its rule (matches app 5.183). If the app doesn't match it, the app is wrong. Also on the phone site as `family.html`.


**Design rules (the "family")**
- `modules/button-module-main-page.html` — the **base layer module**. Never erase it; it must always match the app.
- `modules/family-rulebook.html` — the family rules in one page.
- `specs/collisionhq-design-rules.md` and `specs/collisionhq-design-rules-measured.md` — measured sizes, colors, rounds.
- `specs/collisionhq-size-module.md`, `specs/collisionhq-button-sizes.md`, `specs/collisionhq-button-module.md`
- `specs/collisionhq-menu-module.md` — dropdowns and pop-up menus.
- `specs/collisionhq-motion-module.md` — how things open ("Grow From The Click").
- `specs/collisionhq-icon-family.md` — arrows, X, check marks.
- `specs/collisionhq-notes-family.md`, `specs/phone-spacing-rules.md`, `specs/phone-layout.md`
- `specs/collisionhq-polish-list-2026-10-07.md` — the running polish list.
- `specs/collisionhq-phone-and-hosting-plan.md` — phone previews, the GitHub module site, the native iPhone plan.

**Interactive modules (project › modules/)**
Base and family: `button-module-main-page`, `family-rulebook`, `header-text-module`, `layout-module`, `columns-tab-module`, `arrange-mode-module`, `screen-fit-module`.
Windows and menus: `details-module`, `settings-module`, `account-menu-module`, `sign-in-module`, `estimate-window-module`, `estimate-reader-module`, `search-results-module`, `read-flash-module`.
Board pieces: `dates-column-module`, `status-column-module`, `board-note-module`, `notes-working-module`, `leads-buttons-module`, `top-left-logo-module`, `logo-variations-module`.
Phone: `glass-phone-module`, `job-status-phone-module`.

**Version logs:** `logs/collisionhq-v5.NNN.md` — one per version; the newest say what changed and how it was built.

---

## 2. The family — rules that are already decided

Shape and size
- **"The family is a circle."** Fully round ends (semi-circles) on pills; rounded-square icons.
- Standalone buttons 44 pixels tall; grouped pills 36 to 40 pixels tall; cards and windows 22 pixel corners.
- **10 pixel gap** between any two separate buttons (the Update / Save gap is "the spacing"). Separate pills each keep a soft glow and never look joined by gray.
- Undo / Redo = one pill the size of one button, split by a thin vertical line.
- The lit row behind an open menu has the **same round as the search pill**.
- A clicked board cell's orange highlight has rounded corners like the family highlight.

Words and numbers
- Words in **Inter**. Numbers (money, dates, claim and VIN numbers, job numbers, totals) in **Courier New bold** ("the MATLAB font") so they line up.
- Everything that repeats must **line up in columns**: e.g. "1 day" under "13 days", month | year | count in month lists, a one-digit month or day keeps its slot without showing a 0.
- Title Case labels. No acronyms in labels.
- Blank, not "TBD", when a date isn't set (board).

Color
- **Orange only on the main action** (Add Job, Save). Black / white / orange app.
- Adding buttons green, remove red (red X in a circle; trash needs two clicks).
- Money: bold green when paid / in, red when owed.

Icons
- One icon family: the **thin line arrows and X from the base module's month menu** — never change how they look; every other arrow and X gets replaced with those. Dropdowns show the family chevron.
- A dropdown box always shows its chevron so it reads as a dropdown.

Menus and windows
- Every dropdown lives in the same family (month menu, Source, Status, Location, Board Month).
- Form dropdowns in a window drop **straight down** from their box, same left edge and width, check mark on the chosen row.
- **Month lists: oldest at the top, newest at the bottom**, opened scrolled to the chosen month; only 2 months ahead of today.
- Pop-up editors: icon top-left, the name in the pill where Search sits, round X at the end of the pill; no "Edit …" title; just Cancel and Save; the X goes back to the list, it doesn't close everything.
- Windows, menus and tabs open with **Grow From The Click** at real speed; no blurred background behind windows.
- When an edit box opens, don't select the text — orange ring, typing line blinking at the end.
- Switching Ledger / Leads must be instant.

Phone
- Edge to edge on every iPhone; Apple's 16 pixel side margin; iPhone Settings look.
- Liquid Glass look: buttons bevelled at the edges, see-through in the middle like a bubble; behind the clock and the bottom bar a **plain fade** that gets more solid toward the edge (words still barely readable), **no blur**.
- Phone pages scroll as a normal page; only the bars are pinned (never lock a page in a fixed box).
- Order: **desktop first**, get it perfect, then the phone (the phone is for photos and quick looks).

---

## 3. How a fix goes from module to app

1. **Module first.** Build or update the module page; show Frank. For phone review, push it to the GitHub site (section 4).
2. **Into the app.** The build source is a zip on Frank's computer: `Collision HQ v5 › Build Source › CollisionHQ-v5.NNN-build-source.zip`. Unzip it into the workspace; it holds `m/` (base file `CollisionHQ v4.164.html`, `add50.css`, `add50.js`, `add50c.js`, `carriers.js`, `signin.css`, `v50.py`) and `add/` (`p.css`, `p.js`, `patch.py`) plus `build.sh`. New work is appended as a dated block to `add/p.js` / `add/p.css` (or as a checked replacement in `build.sh`); bump the version in `build.sh` (`'5.172','5.NNN'`); run `bash build.sh`.
3. **Test** in the demo shop with Playwright (localStorage `chq_demo = '1'`, all web requests blocked), check for page errors, look at a screenshot.
4. **Ship** (before shipping, check Desktop › Collision HQ › Collision HQ v5 for a newer version from another chat and build on top of it):
   - `Collision HQ v5\CollisionHQ v5.NNN.html` (move the previous one to `Older Versions`)
   - `Desktop\Collision HQ\CollisionHQ v4.html` (the desktop icon)
   - `CollisionHQ Live Site - Drag To Netlify\index.html` (Frank drags it to Netlify himself; Claude never uploads)
   - `Backups\CollisionHQ versions\CollisionHQ v5.NNN.html`
   - the build-source zip to `Build Source` (previous to `Build Source\Older`)
   - check all 4 html copies have the same md5, then write `logs/collisionhq-v5.NNN.md` in this project.

---

## 4. Full-screen previews on Frank's phone (GitHub)

- Site: **directautomotive.github.io/chq-modules** — home-screen icon **CHQ Modules**. Project: GitHub `directautomotive/chq-modules` (Claude app installed on that one project).
- Pages: `index.html` (the list), `family.html` (CHQ Family), `glass.html`, `dates.html`, `status.html`, `status-column.html`, `icon.png`.
- Every page shows its **version and time in orange**; bump it every upload. Each page has the glass "‹ Modules" pill back to the list.
- GitHub lets phones keep a page up to 10 minutes; to see the newest right away open it in Safari with `?v=` and a new number.

---

## 5. Open aesthetic items (carry over)

- Settings › Privacy page rows undecided; Night theme marked "Soon".
- Add Job estimate-review window not in the family yet.
- Photo Report "Make" label.
- "Move the one…" item from the Oct 7 polish list — ask Frank what it was.
- Phone: glass board tweaks (clearer or more frosted middle), dates module rebuilt in the page-scroll way, then Leads / Status / Details phone screens as modules.

---

## 6. Standing rules for every chat

- Never ask for, type or write down a password, key or token. Never read secret files. Don't rotate keys.
- Nothing gets deleted without Frank's yes. Never write to the Leads Google Sheet. Don't send messages for him.
- Customer documents are for learning layouts only — no customer details in notes or modules.
- Test only in the demo shop.
- Talk to Frank in plain words: every number with its unit and what it measures, no acronyms, few questions.

---

## 7. Starter message for the new chat

> This chat is **CHQ Aesthetics** for CollisionHQ. Read `start-here/chq-aesthetics.md` in the project first, then the family rules and modules it lists. I'll send screenshots of things that don't line up or aren't in the family; jot each one down, fix it as a module first, show me, then put it in the app as the next version and ship it the usual way. Phone modules go on my CHQ Modules site on GitHub.
