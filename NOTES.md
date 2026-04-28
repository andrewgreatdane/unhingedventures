# Unhinged Ventures — Site Notes for Claude Code

## File Structure
```
index.html        — Homepage
principles.html   — 11 principles + 3 pillars (Truth, Goodness, Beauty)
process.html      — 5-step process page
NOTES.md          — This file
```

## Tech Stack
- Pure HTML/CSS/JS — no frameworks, no build step
- Fonts: Barlow Condensed (headings), Instrument Serif (italic accents), DM Mono (body/mono)
- Deployed on Vercel via GitHub — push to main = live in ~30 seconds

## Design System
```
--bg: #ffffff
--surface: #f5f5f3
--border: #e0e0dc
--text: #0a0a08
--muted: #555550
```
- Never use lime green or any accent color — palette is black/white/grey only
- Headings: Barlow Condensed 900, uppercase
- Section labels: DM Mono, 10px, 0.25em letter-spacing, uppercase, muted color
- All sections have `padding: 120px 40px` and `border-top: 1px solid var(--border)`

## Nav Links
```
Team → #team (homepage anchor)
Portfolio → #projects (homepage anchor)
Principles → principles.html
Process → process.html
Contact → #contact (homepage anchor)
```

## Homepage Sections (index.html)
1. **Hero** — Big Barlow Condensed title "UNHINGED / VENTURES®", EST. 2017, stats (18 ventures, 8+ years, 3 categories), scroll hint
2. **About strip** — id="team" — two-column: left headline, right body copy
3. **Portfolio** — id="projects" — 3-column grid, filter bar (All / Apps / Ecommerce / Consulting / World Changing)
4. **Contact** — id="contact" — two-column: left heading + email, right contact form

## Portfolio Cards

### Live Cards (visible, hover to reveal details)
| Card | Category | Description (chip) |
|------|----------|-------------------|
| CaiT | app | AI ops for food businesses |
| SPCT | ecommerce | Skate culture coffee tables |
| LastStep | app, world-changing | Last-mile address intelligence |
| Flock | world-changing | Infrastructure for the robotaxi era |
| AEO Consulting | consulting | Get cited by AI, not just Google |
| Cramp Daddy | app | The app we can't describe here |

### Locked Cards (frosted blur cover, description visible through blur)
| Card | Category | Description |
|------|----------|-------------|
| Alberta Snax | ecommerce | Canadian snack brand gone DTC |
| Men of the West | ecommerce | Tallow grooming for men who don't moisturise |
| Son of a Vet | ecommerce | Breed-specific dog longevity supplements |
| Butt Bowls | ecommerce | CNC wooden bowls shaped by the human form |
| Alarm Cock | ecommerce | The novelty alarm clock that actually works |
| The Influencer | ecommerce | Collectible art toy. Limited. Modular. |
| Energy | app | Todo app built around your energy, not the clock |
| Memory Lane | app | Digital memoir platform for people worth remembering |
| AutoAI | consulting | AI playbook built for car dealerships |
| Moore Headboards | ecommerce | Heritage-style headboards for men with taste |
| Great Dane Coffee | world-changing | Independent coffee shop. 13 years running. |
| Sweet Obsession | world-changing | Neighbourhood bakery. 287 SKUs. Zero shortcuts. |

## How to Unlock a Card
Find the locked card in index.html. It looks like this:
```html
<div class="project-card locked reveal" data-category="ecommerce" data-launched="false">
  <div class="project-placeholder" style="background:#d8d8d4;">
    <div class="project-placeholder-icon" ...>AB</div>
  </div>
  <div class="lock-cover">
    ...
    <div class="lock-desc">Canadian snack brand gone DTC</div>
  </div>
</div>
```

To unlock it:
1. Remove `locked` from the class list
2. Change `data-launched="false"` to `data-launched="true"`
3. Remove the entire `<div class="lock-cover">...</div>` block
4. Replace `project-placeholder` with an actual image OR keep placeholder
5. Add a `<div class="project-overlay">` with name, desc, tags
6. Add a `<div class="project-chip">` with description and status

## How to Add a New Locked Card
Copy this template and paste into the projects grid in index.html:
```html
<div class="project-card locked reveal" data-category="CATEGORY" data-launched="false">
  <div class="project-placeholder" style="background:#d8d8d4;">
    <div class="project-placeholder-icon" style="color:rgba(10,10,8,0.18);">XX</div>
  </div>
  <div class="lock-cover">
    <svg class="lock-icon" viewBox="0 0 24 24" fill="none" stroke="#0a0a08" stroke-width="1.5"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
    <div class="lock-desc">One line description of the idea</div>
  </div>
</div>
```
Categories: `app`, `ecommerce`, `consulting`, `world-changing` (space-separated for multiple)

## How to Add a New Principle (principles.html)
Copy an existing principle card and increment the number:
```html
<div class="principle-card reveal">
  <div class="principle-num">12</div>
  <div class="principle-title">Title in italic serif.</div>
  <div class="principle-body">Body copy. 2-4 sentences. Direct, no fluff.</div>
</div>
```

## Contact
- Email: hello@unhingedventures.com
- Form is cosmetic (no backend) — swap in a Formspree or similar endpoint when ready

## Things to Do Eventually
- [ ] Add real images to live portfolio cards
- [ ] Wire up contact form to Formspree or similar
- [ ] Build individual venture pages as ventures launch
- [ ] Add team.html when ready to show faces
