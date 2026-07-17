# Pull-tab anatomy muslin — NOTES

> Built 2026-07-17 against Hallie's "Proposal for UPDATED CARD BEHAVIOR"
> (`scratch/drawer-contents.md`, 2026-07-17). Former reference implementation:
> `api/static/muslins/pull-tab-anatomy-muslin.html` — PERISHED into this spec,
> see `FUNERAL.md` in this directory. MUSLIN-grade while it lived — cheap
> cotton, seams showing, hardcoded fake data. Do not mistake this NOTES.md for
> anything other than the standalone spec; there is no HTML left to defer to.

The reference HTML no longer exists (funeral 2026-07-17, see `FUNERAL.md`).
This file is now the whole standalone spec — every ruling plus enough
behavioral description that a builder never needs the muslin's HTML.

## Status at a glance (2026-07-17 10:38 round)

- **Two-zone anatomy (exterior drawer / interior section per pole) — RULED
  SETTLED ("GORGEOUS").** Not re-litigated this round.
- **Now-line vertical order (Future → Present → NOW → Past) — RULED,
  ontology not taste** (see question 4, 10:08 addendum).
- **Tab travel + fold-over + close↓/close↑ + drop-opens-pinned — RULED
  ("Close is good on the muslin")**, with two follow-on rulings this round
  (see question 6 addendum): headroom above/below the folded-over close tab,
  and the open-state tab's color now keyed to its own drawer's palette,
  one shade darker.
- **Tab width — RULED (10:38, Hallie verbatim: "tab width = 120px WINS").**
  Fork 1 is closed. The narrow (56px) / medium (88px) / wide (120px)
  three-variant comparison is retired; every card now wears the single
  120px tab (`.tw-wide`, the only width class left). Per-card
  `tab width variant: …` captions are removed from the muslin.

## The five questions, and what to try with your hand

### 1. Pull tabs — discoverable and hittable?
> **RULED 2026-07-17 09:39 (Hallie, hands-on pass):** tabs are FILE-FOLDER TABS —
> wider, and STICKING OUT of the card silhouette, not pills hugging inside the
> corners. The card is the folder body; the tab breaks the card's own rectangle.
> Future tab protrudes from the **top edge**, past tab from the **bottom edge**
> (left/right offset within that edge, mirrored). This superseded the original
> pill-in-corner build (34×14 painted pill sitting just inside the corner) —
> that version is what's described as "little tabs... top-left and bottom-right"
> below and is now retired. Exact width/protrusion amount is still Hallie's
> hand's call — see the three width variants shipped side by side in the muslin
> (narrow 44px / medium 72px / wide 104px, one per card, labeled above each
> card) so she can compare at a glance rather than tune one number blind.
> Separately ruled: **the pull/drag-out interaction feel on card-open stays as
> built** — nothing about the click grammar, hit-zone generosity, or
> independence of the three doors changed, only the tab's shape/placement.

Tabs replace the full-width drawer strip, now protruding from the **top edge**
(future) and **bottom edge** (past) of each card like manila-folder tabs. The
visible paint is wider than before; the hit zone matches the paint's footprint
and extends slightly past it. Check the **"show hit-zone outlines"** box to
see the dashed red rectangle around each tab — that's the real target, not
just the painted folder tab.

**Try**: compare the three cards top to bottom — narrow (44px), medium
(72px), wide (104px) — same content, only the tab width differs. Which reads
as "grabbable" without looking too big for the card? With the debug box OFF,
try to click a tab without seeing the hit zone. Then turn it ON and compare —
does the generous hit zone feel like cheating (too easy) or does it feel
necessary (tabs alone would get missed constantly)? Also try dragging card 3
("reorg the muslin seams") over a tab — it should glow amber (`.drag-over`)
before you release.

### 2. Click grammar — three independent doors
> **UPDATED 2026-07-17 09:51 (Hallie, hands-on pass):** the top and bottom of
> an expanded card now each have TWO distinct zones instead of one — see
> question 4 below for the full four-zone anatomy. The three-door grammar
> itself (drawer / drawer / expand, wired never to touch each other) is
> unchanged; what changed is that "pulling the future drawer" now visibly
> folds a block OUTSIDE the card open (attached to the tab), while "opening
> the interior" reveals a DIFFERENT, separately-collapsible block just INSIDE
> that same edge. Two blocks, one edge, two different toggles.

Three ways into a card, wired NOT to touch each other:
- **Top tab** (folder tab protruding from the top edge) → pulls the exterior
  FUTURE drawer only — the AFTER bucket, what prehends this card from
  outside it. Takes real space in the list (pushes siblings down), does not
  touch the interior.
- **Bottom tab** (protruding from the bottom edge) → pulls the exterior PAST
  drawer only — the BEFORE bucket. Same independence.
- **Center "expand" tab** (bottom edge of the face row) → opens the INTERIOR
  only — both interior-future and interior-past sections at once, each with
  its OWN collapse toggle inside. Never opens an exterior drawer.
- When the interior is open, small **"open future" / "open past" buttons**
  appear directly on the corner tabs (per proposal item 6: "the button to
  expand the drawer is clearly visible on the tabs").
- **New**: each interior section (interior-future, interior-past) has its own
  collapse caret in its header — a FOURTH layer of independence, nested
  inside the "expand" door. Collapsing interior-future does not touch
  interior-past, the Now line, or either exterior drawer.

**Try**: open card 1's future drawer, then its interior, then its past
drawer — all three should be independently toggleable in any order, and
closing one should never silently close another. Then, with the interior
open, collapse just the interior-future section — interior-past and the Now
line should hold still. Watch the list length change (drawers reflow the
page; the interior does too, but they're separate reflows). Does misclicking
a drawer for the expand tab happen? Are the hit zones for the corner tabs and
the center expand tab too close together on a narrow card? Does having FOUR
independently-toggleable things stacked at one edge (exterior drawer, interior
section, its collapse caret, the Now line) start to feel like too many knobs
in one place?

### 3. No hover auto-expand
Default is **click-gated**: hovering does nothing except (when the toggle is
on) a quiet glow around a tab, no functional highlight. Check **"hover-shown
drop regions"** to feel the alternative Hallie is also considering — hovering
a tab then shows the same quiet glow proactively rather than only while
dragging.

**Try**: toggle between click-gated and hover-shown and mouse across cards
in each mode. Which one feels safer against misclicks? Note: this muslin's
"hover-shown" is deliberately a weak stub (a glow, not an auto-open) — the
real fork is about whether ANY passive signal should show before a click or
drag, not about auto-expanding on hover (which the proposal already rules
out).

### 4. Interior geometry — FOUR ZONES per edge, outside/inside made legible
> **RULED 2026-07-17 09:51 (Hallie, hands-on pass):** the top of an expanded
> card is now TWO sections, not one — same for the bottom. This is "the
> bucket read made visible: drawer = outside the poles, section = inside the
> interval" (her words). Reading a card top to bottom:
> 1. **Exterior FUTURE drawer** `[after / outside]` — attached to the top
>    pull tab, folds OUT of the card's top edge, outside the silhouette.
>    What prehends this card from OUTSIDE it (the next day, steering
>    stories, sublimes affordance).
> 2. **Interior Future section** `[interior-future]` — just inside the top,
>    above the Now line. In-interval items, still contained BY this card.
>    Has its own collapse caret in the header.
> 3. **NOW line + Present** — the hinge, not a bucket, not collapsible.
> 4. **Interior Done/Past section** `[interior-past]` — just inside the
>    bottom. This card's own finished work. Own collapse caret.
> 5. **Exterior PAST drawer** `[before / outside]` — attached to the bottom
>    pull tab, folds OUT of the card's bottom edge. What this card prehends
>    OUTSIDE itself.
> All four bucket-name debug labels render as small dashed-border text next
> to each zone's own header, in the [bracket] vocabulary Hallie asked for, so
> the outside/inside mapping is legible without guessing from position alone.
>
> **RULED 2026-07-17 10:08, Now-line reorder (ontology, not taste — verbatim):**
> "Can you put now BELOW the present? Its more honest to the ontology. the
> full event prehends the now but events in it are prehended by now. so the
> events relationship to the now is above now, not below it." Vertical order
> inside the interior is now **Interior Future → Present → NOW line →
> Interior Done/Past**. Present items sit wholly ABOVE the line (begun, not
> yet gathered by Now); the Now line sits directly above Interior Past,
> because gathered-by-Now = prehended = past. The straddler item no longer
> sits ON the band — it lives in Present, above the line, labeled "begun, not
> yet gathered by Now — lives ABOVE the line." Prehension order IS the
> vertical order: below the Now line reads as "prehended by it," i.e. past.
> This is settled as ontology, not a layout preference — do not re-litigate
> as a taste question.

Open card 1's interior (expand tab) AND pull both exterior drawers to see
all five layers at once. Bottom-up inside the interior:
- **Interior Future** (top) — items that prehend nothing yet, collapsible.
- **NOW line** — the hard band, not collapsible.
- **Present** — items straddling Now. Card 1 has one **imperfective
  straddler** ("wire pointer-drag ghost + drop receipt", marked ◐, bold
  border) sitting directly on the Now band, per your ask.
- **Interior Done/Past** (bottom) — completed items, collapsible. One item
  ("find the owner frame") is marked `[born future, now past — struck +
  floated to top]`: it's struck through AND sorted above the plain
  past-born item, per the proposal's "anything that started as a future...
  has a strike through" + "past event... filtering to the top of the
  section."

**Try**: read the whole card top to bottom with both exterior drawers AND
the interior open — five stacked zones at each pole (exterior drawer,
interior section, [Now line], interior section, exterior drawer). Does the
outside/inside distinction hold up visually, or does it start to look like
one undifferentiated stack once everything is open at once? Does the Now
line read as a hard fact, or does it get lost against the Present section
around it? Does the struck-through item look "done" or does it read as an
error state (should struck-through mean success here, or does that collide
with other struck-through conventions elsewhere in the product)?

### 5. Drawer filter inheritance (stub)
Card 2 ("card anatomy spec pass 2") is `filterable: true` with
`parentFilterTag: 'design'`. Check **"drawer filter chip active on card 2"**
— items tagged `design` stay full-opacity; items tagged `open-question` gray
out and desaturate. A `[inherits parent filter — TODO real read]` label sits
next to the chip.

**Try**: toggle the filter on/off with drawers open and watch which items
fade. Does graying-and-hiding read as "filtered by inheritance" or does it
just read as "half-loaded"? Is a filter chip on the card face the right
place, or should it live on the drawer itself?

### 6. Tab travel + fold-over-close + drop-opens-pinned
> **RULED 2026-07-17 10:07 (Hallie, verbatim):** "the pull tab should travel
> with the drawer, fold over, and indicate down (folds over toward the
> player, says 'close' on it with arrow pointing down now. Also they could
> stand to be a little wider."
>
> **RULED 2026-07-17 10:09, clarified (Hallie, verbatim):** "the tab isnt
> visible folded down currently, i was thinking it would look like mostly the
> tab as is, but * -1 over the top of the drawer in terms of the shape." The
> open-state tab keeps the SAME folder-tab silhouette/width as closed — it is
> NOT a different control — just vertically mirrored (`scaleY(-1)`) and laid
> visibly OVER the drawer's own outer/far edge, overlapping it like a flap
> folded down onto that surface. Not hidden, not detached.
>
> **RULED 2026-07-17 10:10, confirmed (Hallie, verbatim):** "And vice versa
> for bottom." The arrow always points back TOWARD the card (the direction
> that folds the drawer closed): future/top tab → "close ↓" (folds down
> toward the card below it); past/bottom tab → "close ↑" (folds up toward
> the card above it). One piece-of-paper metaphor, mirrored per pole.
>
> **RULED (width), same round:** all three tab-width variants shifted up one
> notch — narrow 44→**56px**, medium 72→**88px**, wide 104→**120px** — "they
> could stand to be a little wider." (Superseded 2026-07-17 10:38 — see fork
> 1: 120px won outright and the comparison itself is now retired.)
>
> **RULED 2026-07-17 10:13, drop-opens-pinned (Hallie, verbatim, folded from
> scratch/drawer-contents.md):** when something is dragged onto a tab, the
> drawer PULLS OUT showing the newly-dropped item as the single visible row,
> and REMAINS OPEN pinned to that item — "pinning an event in the tab open"
> — with a `…more (N)` stub row below that expands the rest of the drawer's
> contents on click. The tab of course rides out folded per the travel/mirror
> spec above (same "close ↓"/"close ↑" dress as any other open drawer).
> Implemented as `S.pinned` / `S.pinnedExpanded` state, keyed per drawer;
> pin clears automatically when the drawer is next closed by any means (edge
> tab, traveling tab, or drawer-open button) so a fresh open shows the plain
> list, not a stale pinned row.

Try: pull a drawer open manually (edge tab) — the tab should ride out to the
drawer's far edge, flip to the mirrored "close ↓"/"close ↑" dress, and
clicking it should close the drawer and return the tab to its plain
unmirrored dress pinned at the card edge. Then drag "reorg the muslin seams"
(card 3) onto a closed tab — the target drawer should pull open showing ONLY
the dropped item (marked `[dropped]` / `[just dropped — pinned]`) plus a
`…more (N)` row; click `…more` to reveal the rest. Does the fold-over read as
"this flap belongs to the drawer, not a floating extra control"? Does
"close ↓" vs "close ↑" (arrow direction flipping per pole) feel intuitive, or
does it need a fixed universal arrow instead? Does the drop-and-pin move read
as "filed and shown," or does hiding the rest of the drawer's contents behind
`…more` feel like data went missing?

> **RULED 2026-07-17 10:37 (Hallie, verbatim): "Close is good on the muslin,
> needs a little more headroom to not overlap and can we make it the same
> color as the drawer it's on but maybe one darker?"** Close-affordance
> itself (travel/fold-over/arrow-direction) is confirmed good — not
> re-litigated. Two follow-on fixes made this round:
> 1. **Headroom.** The folded-over open-state close tab was overlapping the
>    drawer's first content row. Fixed by reserving clearance on the
>    drawer's far edge only — `padding-top` on `.drawer.future
>    .drawer-inner`, `padding-bottom` on `.drawer.past .drawer-inner` — sized
>    to the tab's own footprint, so the tab occupies dead space rather than
>    painting over the label/first item. Applies to both poles (future/top
>    drawer, past/bottom drawer).
> 2. **Color kinship.** The open-state (traveling) close tab no longer uses
>    the neutral charcoal dress — it now takes its OWN drawer's palette
>    family, one shade darker than that drawer's band. Future drawer band is
>    the blue family (`#f0f5fb` bg / `#4a7ec2` label) → close tab darkens to
>    `#b7cbe8` fill / `#2c5da0` border. Past drawer band is the amber family
>    (`#f7edd9` bg / `#c2723a` label) → close tab darkens to `#e0bd82` fill /
>    `#8a6508` border. The CLOSED-state tab dress (`.tab-hitzone.future` /
>    `.tab-hitzone.past`, the plain folder tab pinned at the card edge) is
>    UNCHANGED — this ruling only touches the open/traveling tab.
> Verified in Chrome at `localhost:8015`: opened both future and past drawers
> on card 1, zoomed on the tab/content boundary in each — clearance holds,
> no overlap; color reads as "this drawer, darker" rather than a generic
> dark control.

## Known forks (not resolved here — that's the point)

1. **Tab size / hit-zone ratio — RULED 2026-07-17 10:38 ("tab width = 120px
   WINS").** Hallie's hands-on verdict: tabs are wider AND protrude out of
   the card silhouette like file-folder tabs (top edge / bottom edge),
   replacing the earlier pill-hugging-the-inside-corner build — settled
   09:39. The width comparison itself (narrow 56px / medium 88px / wide
   120px, shown side by side so her hand could pick) is now ALSO closed:
   **120px wins outright**, every card wears it, the other two widths and
   the per-card comparison captions are removed from the muslin. Fork fully
   resolved, nothing left open here. Watch for in the real implementation:
   does a wide tab start reading as "another card" rather than a handle on
   this one? Does the protrusion amount eat into the margin between adjacent
   cards (this build widened card margins to `3rem` to give the 24px
   protrusion clearance — a real layout will need to reserve that margin
   everywhere cards stack).
2. **Click-gated vs hover-shown drop regions.** Toggle is in the muslin.
   Hallie is "actively considering" the stricter (click-gated) option per
   her proposal — this muslin defaults to it but makes both feel-able.
3. **Drawer-open-on-collapsed-card legality.** Nothing in this muslin
   blocks pulling a drawer while the interior is closed (in fact that's the
   main path tested). But is it legal/desirable to have a drawer open WHILE
   the card itself is collapsed and sitting in someone else's drawer (i.e.
   nested, nested-open state)? Not modeled here — cards don't nest inside
   drawers in this muslin, only flat top-level cards. Real implementation
   needs to decide whether drawer state persists/resets when a card's own
   container collapses.
4. **What "drag-over a tab" should DO.** Right now it's a console.log +
   on-page toast stub (`[does nothing yet]`, non-blocking so it doesn't
   freeze automated verification the way an `alert()` did in an earlier
   pass). Does dropping onto a tab mean "file this into that drawer"
   (matches the tab's kind — future tab = becomes a future item) or
   something else entirely (e.g. re-parent the whole card)?
5. **Struck-through as "done" vs struck-through elsewhere.** The proposal
   uses strikethrough for "started as future, now past" — worth checking
   this doesn't collide with a different strikethrough convention already
   in the product (e.g. "deleted" or "superseded").
6. **Four-zone stack density (NEW, 2026-07-17 09:51).** Each pole now has an
   exterior drawer AND an interior section, each independently toggleable,
   plus the interior section has its OWN collapse caret nested one level
   further in. That's up to four independent open/closed states per edge (two
   per pole × two poles), on top of the interior-as-a-whole toggle. Not
   resolved here: is that too many knobs for one corner of a card, or does
   the outside/inside split actually reduce cognitive load once it's
   learned (two clearly different KINDS of thing, not four peers)? Watch
   Hallie's hand for hesitation or wrong-door clicks when all zones compete
   for attention at once (see question 4's "try" for the all-open stress
   test).
7. **Section collapse toggle scope (NEW).** The interior-future/interior-past
   collapse caret currently lives INSIDE the interior — meaning it's a level
   deeper than the exterior drawer pull and the top-level expand tab. Is that
   the right depth, or should a section be collapsible even while the
   interior as a whole is closed (i.e., should section-collapse state persist
   and matter even when not visible)? Not modeled: this muslin resets nothing
   on interior-close, so collapsed-ness silently persists in state even
   while hidden — worth deciding if that's the intended behavior or a stub
   gap to close later.

## IMPLEMENTATION HINTS (not law — tricks the dead HTML used, worth not re-discovering)

These are things the muslin's markup did that were non-obvious and made the
rulings above actually work. They are hints for whoever builds the real thing,
not additional rulings — Hallie ruled on behavior/appearance, not on DOM shape.

- **Exterior drawers as in-flow siblings, not absolutely-positioned overlays.**
  Each card lived inside a `.card-slot` wrapper (`display:flex;
  flex-direction:column`) alongside its own future/past drawer `<div>`s as
  real siblings before/after `.card`, not children of `.card` positioned
  absolutely over other cards. That's what let an open exterior drawer
  actually reserve list space and push the next card-slot down (ruling 7 in
  `scratch/drawer-contents.md`: "Once expanded the Drawer takes up space in
  the list") without a separate spacer hack.
- **Negative-margin flush-attach.** `.drawer.future { margin-bottom:-2px }` /
  `.drawer.past { margin-top:-2px }` lapped the drawer's border under the
  card's own 2px border, so an open drawer reads as *emerging from* the card
  edge (attached to the pull tab) rather than a detached block floating next
  to it. Small trick, easy to lose if a rebuild uses gap-based spacing instead
  of adjoining borders.
- **Traveling tab positioned relative to `.drawer-inner`, not the viewport.**
  The mirrored "close" tab was `position:absolute` inside `.drawer-inner`
  (itself `position:relative`), anchored `top:0` (future) or `bottom:0`
  (past) — i.e. the drawer's own far edge. That's the whole trick behind "the
  tab travels with the drawer": it's simply parented to the drawer and pinned
  to its far edge, so it moves because the drawer's box does, not because of
  any JS position tracking.
- **Headroom via drawer-far-edge padding, not tab z-index tricks.** Once the
  traveling tab overlapped the first content row, the fix was
  `padding-top`/`padding-bottom` on `.drawer-inner` sized to the tab's own
  footprint (~1.9rem) — reserving dead space rather than trying to shrink or
  reposition the tab. Simplest fix, kept here so it isn't rediscovered the
  hard way.
- **Re-mirroring the label inside a flipped tab.** The traveling tab's outer
  shape used `transform:scaleY(-1)` for the fold-over look, but its inner
  text/arrow needed a second `scaleY(-1)` on `.tab-paint > *` to read upright
  again — mirror the container, un-mirror the content.
- **Closed tab kept in the DOM (visibility:hidden), not removed, when open.**
  When a drawer opens, the closed-state tab isn't deleted or `display:none`'d
  — it's `visibility:hidden; pointer-events:none` so it still holds its
  layout slot / hit-zone geometry stable for when the drawer closes again.
  Avoids a reflow jump on toggle.
- **Drop-opens-pinned as two small state maps.** `S.pinned` (keyed
  `"cardId:kind"`) held the just-dropped `{tag, text}`; `S.pinnedExpanded`
  was a separate boolean flag per key for whether "…more" had been clicked.
  Pin cleared automatically on ANY close path (edge tab, traveling tab, or
  drawer-open button) so a fresh open never showed a stale pinned row from a
  previous drop. Cheap and easy to port: two maps, cleared together, checked
  together.
- **Pointer events only, never HTML5 Drag-and-Drop** — a house law, not
  specific to this muslin, but worth restating: the drag-ghost/drop-target
  logic was built entirely on `pointerdown`/`pointermove`/`pointerup` plus
  `document.elementFromPoint`, no `dragstart`/`dragover`/`drop` events
  anywhere. If a real build reaches for HTML5 DnD it will fight the rest of
  the app's drag conventions.

## Tear this apart.

## GOOD TO GO (Hallie, 2026-07-17 10:47) — the muslin has answered its questions

"Muslin is Good to Go, we just need to make sure the explanatory text doesn't creep into
the interface." The anatomy is RULED COMPLETE: 120px file-folder tabs, travel+mirror-fold
close (drawer-family one darker, with headroom), two-zone poles (exterior drawer +
interior collapsible section), Future → Present → NOW → Past, drop-opens-pinned.

THE GUARD FOR THE BUILDERS: everything here that EXPLAINS is muslin cotton, not product —
the [after/outside]-style bucket labels, debug hit-zone outlines, width captions,
[does nothing yet] stubs, the banner. NONE of it ships. The real build carries the
anatomy silently; the seams were for finding the shape, and the shape is found. (A
muslin that survives into production was never a muslin — this one perishes into spec.)
