# Fate & Commentary — Perplexity Deploy Guide
*How Jaylon's personal blog readings differ from client readings*

---

## What This Is

**Fate & Commentary** is Jaylon's personal reading blog — not a client page. It has its own permanent GitHub repo (`jaylon-jackson.github.io/fate-and-commentary` or similar), its own HTML template, its own expiry rules, and its own writing voice. Do NOT treat this like a client reading output.

---

## The Core Differences at a Glance

| | Client Readings | Fate & Commentary (Jaylon) |
|---|---|---|
| **HTML source** | Generated fresh by the builder each week | `FateAndCommentary/index.html` — permanent template, updated in place |
| **Repo** | New repo per client, per reading | Same permanent repo every week |
| **What changes weekly** | Entire HTML file replaced | `[INJECT]` markers replaced + `week-reading.jpg` swapped + expiry date updated |
| **Expiry** | Sunday midnight (standard) | **5 days from publish date** (strictest) |
| **Writing voice** | Per-client tone (Natalie, Naomi, etc.) | The Annotator — see `ANNOTATOR_VOICE_BRIEF.md` |
| **Greeting** | None | `"Welcome, Star Child."` — already in HTML, do NOT add it in prose |
| **Perspective** | Second-person ("you have...") | **First-person throughout** ("I pulled...," "I found...") |
| **Audience** | The named client | Natalie, Naomi, Mani — close friends watching Jaylon read himself |
| **Hero images** | Vary per client/reading | `hero-main.jpg` and `hero-reveal.jpg` are **permanent** — do not replace |

---

## Weekly Deploy Checklist

Each week, Perplexity does the following:

**1. Update the expiry date**
Find this line in `index.html`:
```js
const EXPIRY_DATE = new Date('2026-04-11T23:59:00');
```
Change the date to **5 days from today** at 23:59.

**2. Swap the spread photo**
Replace `week-reading.jpg` in the repo with the new processed image Jaylon provides. Filename stays the same every week.

**3. Fill the `[INJECT]` markers**
The template has clearly labeled `[INJECT]` placeholders throughout the reading body. Replace each one with generated reading text written in the Annotator voice (see below).

**4. Commit and push**
Same repo, same URL. No new repo creation needed.

---

## The [INJECT] Markers

Each `[INJECT]` block is labeled in an HTML comment directly above it. Example:
```html
<!-- INJECT: Key Influence -->
<p>[INJECT: Key Influence — intro paragraph]</p>
```

Fill each one with the corresponding reading section in Annotator voice. The `[INJECT]` text gets replaced entirely — no placeholder text should remain in the published page.

---

## Writing the Content: The Annotator Voice

**Read `ANNOTATOR_VOICE_BRIEF.md` first.** Full persona spec is there.

Quick reference:
- First-person throughout. "I pulled this card." Not "you have this card."
- Register: Jaylon talking to Natalie at brunch. Analytical when mechanism matters. Personal when emotion matters. Never precious.
- `"Welcome, Star Child."` is already rendered by the HTML as a styled heading — **do not write it again in the prose**
- The Key Influence opens the reading. Frame it as: *"Before we get into the week — this card is the quiet energy running underneath everything. Keep it in mind as we go through each section."* Then move into the 7 positions.
- Every synthesis section ends with one concrete sentence about what Jaylon is actually going to do.
- Callout blocks (`<div class="callout">`) are for personal admissions, not just insights.

**Important caveat on archetypes:** Jaylon may not know exactly who person cards (Enemy, Widower, etc.) are pointing to in real life. Do NOT write as though he has identified the real-world target. Write as though he recognizes the archetype but has only skimmed the surface of who or what it might apply to. Uncertainty is honest here.

---

## What NOT to Do

- Do not generate a new HTML file from the builder — the blog uses its own permanent template
- Do not change `hero-main.jpg` or `hero-reveal.jpg` — these are permanent brand assets
- Do not use second-person ("you feel," "your week") — it's always first-person
- Do not add motivational sign-offs ("trust the process," "you've got this") — not the Annotator's register
- Do not explain the deck systems to the reader — the audience knows or figures it out from context
- Do not duplicate "Welcome, Star Child." in the text — it's already in the HTML element
- Do not use Sunday midnight as the expiry — it's always **5 days from publish date**

---

## File Map

```
FateAndCommentary/
├── index.html                  ← permanent template; update [INJECT] blocks + expiry + push
├── hero-main.jpg               ← permanent brand image (eyes closed / reaching / gold locs)
├── hero-reveal.jpg             ← permanent brand image (green eyes open / Oracle section + expired screen)
├── week-reading.jpg            ← swap this each week with processed spread photo
├── ANNOTATOR_VOICE_BRIEF.md    ← voice spec for writing reading content
└── PERPLEXITY_DEPLOY_GUIDE.md  ← this file
```

---

## Expiry Behavior (FYI)

When the reading expires:
- The live reading content is hidden
- The expired screen shows: `hero-reveal.jpg` (green eyes) + the message *"This reading has closed. Bookmark this link."*
- The URL stays live permanently — readers can always find where the blog lives, even between readings

---

## Summary

Every week: update expiry date → swap `week-reading.jpg` → fill `[INJECT]` markers in Annotator voice → push. Same repo, same URL, same images. That's it.
