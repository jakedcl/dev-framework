# UX and interaction

- **Contact details are tappable:** `tel:`, `mailto:`, and the whole address as one Maps link. (Abis)
- **Search behaves as expected.** Tapping the field opens the keyboard, a suggestion acts on tap, Enter searches and closes the keyboard, and suggestion lists sit on top. (compactpickup, drewdella)
- **Every data surface has empty, loading and error states,** and every action shows loading until the server confirms. (drewdella, bannquet)
- **Destructive actions confirm or offer undo, and stay out of the way.** (bannquet)
- **Members-only actions send logged-out users to sign in, then back to the same page.** (bannquet)
- **Rows never wrap; truncate with "…".** Lists don't re-sort under someone's cursor. (bannquet)
- **Mobile inputs are at least 16px.** Why: iOS zooms in and hides the keyboard. (731photography)
- **Respect reduced motion.** On weak devices, drop quality automatically. (metrotapes)
- **Show content as soon as it's ready.** Pause off-screen animation, and animate only transform and opacity. Why: scroll lag and slow first paint on 3D sites. (metrotapes, jakedcl.com)
- **Heavy media loads light:** thumbnails first, and no autoplaying embeds. (drewdella, metrotapes)
- **Pick the simplest interaction that works,** like one timer instead of event-driven animation logic. (headsuptrucker)
- **Sticky headers never cover content:** scroll targets land below them, and mobile menus sit above everything. (Abis, bannquet)
