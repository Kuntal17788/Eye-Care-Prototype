# Eye Clinic App — Clickable Static Prototype

A linked, static HTML mockup of the Eye Clinic application. No server, no build step —
just open `index.html` in a browser and click through.

## How to use
1. Unzip the folder.
2. Double-click `index.html` (this is the login screen).
3. Use the three shortcut buttons ("Doctor" / "Reception" / "Admin") to jump straight
   into a role, or use the "Doctor / Receptionist / Admin" switcher in the top bar of
   any screen to hop between role contexts. This switcher is a prototype convenience —
   the real app would route this by logged-in account, not by a visible switch.
4. All navigation is real `<a href>` links between static pages — no JavaScript routing,
   no backend, no data persistence. Forms don't submit; buttons that "save" just link to
   the next logical screen.

## Screens included (23 + login)

**Doctor**
- Today's Queue (landing) — `doctor-queue.html`
- Patient Profile (doctor view) — `patient-profile-doctor.html`
- Patient Timeline — `patient-timeline.html`
- Image Detail / Comparison — `image-detail.html`
- Voice-to-Text Notes — `voice-notes.html`
- Structured Test Results Entry — `test-results-entry.html`
- Trend Graphs — `trend-graphs.html`
- New Prescription — `prescription-create.html`
- Prescription History — `prescription-history.html`
- PDF Export / Summary — `pdf-export.html`

**Receptionist**
- Patient Registration — `patient-registration.html`
- Registration Confirmation — `registration-confirmation.html`
- Patient Search / List — `patient-search-receptionist.html`
- Patient Profile (receptionist view, no clinical data) — `patient-profile-receptionist.html`
- Appointment Scheduling — `appointment-scheduling.html`

**Admin**
- Audit Log — `audit-log.html`
- User & Role Management — `user-management.html`
- Clinic Settings — `clinic-settings.html`
- Subscription & Licensing — `subscription-licensing.html`

**Cross-cutting**
- Global Search results — `search-results.html`
- Notifications — `notifications.html`
- Empty / Error / Loading states (style reference, not a real destination screen) — `empty-states.html`

## Mobile
All screens are responsive down to phone widths:
- The left sidebar collapses into a fixed bottom tab bar (icons only) under ~860px.
- Multi-column layouts (stat grids, forms, side panels) stack to a single column.
- Wide tables scroll horizontally instead of squeezing columns unreadably.
- The top search bar drops to its own full-width row under the title bar.

Resize your browser window or open the prototype on your phone to see it — no separate
mobile files, it's the same HTML/CSS responding to screen width.

## Notes on the design
- Dark, low-glare interface — a deliberate nod to ophthalmology exam rooms, which are
  kept dim for pupil dilation.
- Status "ring" indicator (hollow / half-filled / solid) used consistently across the
  Queue, Timeline, and Image views — reads like a pupil/iris, doubles as a fast visual
  scan pattern for a busy clinic.
- Same navigation shell and component styles reused across all three roles; only menu
  items and visible data change — matches the "single app, role-gated views" decision.
- Fonts (Inter, IBM Plex Mono) and Tabler Icons are loaded from public CDNs — an internet
  connection is needed the first time each font/icon loads in your browser.

## File structure
```
index.html                 ← login / entry point
doctor-queue.html
patient-profile-doctor.html
...(all screens above)
css/styles.css              ← shared design system (colors, type, components)
build.py                    ← generator script used to produce these pages (for reference/editing)
```

To make future edits, it's easiest to modify `build.py` (one shared header/nav/CSS,
content blocks per page) and re-run `python3 build.py` rather than hand-editing each
HTML file individually.
