# Prompt for Local AI: Fix Lewis Energy Enterprises Website

Paste everything below into your local AI coding tool.

---

## Context

I'm working on the codebase for lewisenergyenterprises.com, a landing page for a solar/battery sales program in Central Valley, California. I need you to find the relevant files (index.html and associated CSS — likely a single-page site with a hero carousel, an about/intro section, a feature list, a "what's included" grid, and an application form) and make the changes below.

## Problem 1: Hero section has too much text and isn't mobile responsive

Current hero is a 3-slide carousel with headlines like "Power your home Pocket the savings," "$0 down | no lease no loan," and "Beat your PG&E bill for $0 down," followed immediately by a dense intro paragraph and an 8-item bulleted feature list before any visual breathing room.

**Fix:**
- Cut the hero to ONE strong, short headline (5-8 words max) + one short subheadline (under 15 words) + a single CTA button. No walls of text above the fold.
- Remove or drastically shorten the intro paragraph currently sitting below the hero — turn it into 3-4 short icon+text bullet points instead of a paragraph, or move detailed copy further down the page.
- Audit every font-size, padding, and margin value in the hero and top sections and make sure they use responsive units (clamp(), vw, rem with media queries) instead of fixed px, so text doesn't overflow or wrap awkwardly on mobile.
- Add/verify proper mobile breakpoints (max-width: 480px, 768px, 1024px) for the hero: stack text and image vertically, reduce font sizes proportionally, ensure the CTA button is thumb-friendly (min 44px tap target) and not cut off.
- Test the hero carousel specifically on a 375px-wide viewport — if the carousel text or nav dots overflow or overlap the image, fix the layout (likely needs flexbox/grid stacking + reduced text length rather than just smaller fonts).
- Reduce the number of hero slides from 3 to 1-2 max, since 3 rotating headlines dilutes the message and makes mobile users wait for the right slide to load before seeing key info.

## Problem 2: Messaging hierarchy is backwards — solar is leading, but battery/protection should lead

Right now "Solar Panel Installation" is listed FIRST in the "Everything You Need To Go Solar" grid, and the hero headlines emphasize generic "$0 down" and "power your home" messaging rather than the actual differentiators.

**Fix the messaging priority across the ENTIRE page (hero, intro, feature list, "what's included" grid, and footer) to this order:**

1. **Battery backup / blackout protection** — this is the #1 hook. Homeowners fear losing power. Lead with this everywhere.
2. **Protection from rate hikes / PG&E being too high** — second biggest pain point. Reference rising utility rates directly.
3. **No credit check needed** — this is a BIG differentiator that's currently buried in a bulleted list. It needs to be visually prominent — treat it like a trust badge, not a bullet point. Consider a standalone callout box or badge near the CTA, not just inline text.
4. **EV charging savings** — currently barely mentioned once ("save on charging costs for your EV"). Make this a full talking point with its own section or feature card — EV owners are a distinct high-intent audience and this is currently underused.
5. **Partnered with PG&E and SoCal Edison, sell energy back to the grid and earn credits** — currently just one line in a paragraph. Elevate this to its own section or feature card — "partnered with" language builds trust/legitimacy and should be visible, not buried.
6. **Solar panels themselves** — solar should be framed as the mechanism that MAKES the battery/EV/bill-savings benefits possible, not the headline product. Move "Solar Panel Installation" down in the "Everything You Need" grid — battery backup should be first or second in that grid, not solar.

**Specific content changes:**
- Rewrite the hero headline to lead with battery/blackout protection or rate-hike protection instead of generic "$0 down" messaging. Example directions (adapt tone to match existing brand voice): something like "Keep the Lights On When PG&E Can't" or "Stop Overpaying PG&E — Battery Backup at $0 Down" — pick language that foregrounds battery + rate protection, not solar.
- In the "Everything You Need To Go Solar" grid, reorder cards so Battery Backup Storage comes before Solar Panel Installation.
- Add a new feature card or section specifically for EV charging savings if one doesn't cleanly exist yet — don't leave it as a single clause in a paragraph.
- Add a new feature card or trust-badge element specifically for "Sell energy back to the grid & earn credits" with PG&E/SCE partnership called out.
- Pull "No Credit Check" out of the plain feature list and give it its own visual treatment — badge, icon callout, or a short standalone line near the Apply Now CTA (e.g., directly under the button: "No credit check. No loan. No pressure.").

## Problem 3: General mobile responsiveness audit

Beyond the hero, do a full pass on:
- The feature list/bullet section (currently rendering as a long flat list of short phrases — check that it wraps into a clean 2-column or stacked grid on mobile, not a single long unreadable column or overflow).
- The "Everything You Need To Go Solar" 6-card grid — verify it collapses to 1 column cleanly on mobile with readable image sizes (images currently appear to be full-width JPGs/PNGs that may not be optimized/responsive — add max-width: 100%, height: auto, and consider srcset or compressed versions if file sizes are large).
- The application form — check that all form fields, radio buttons, and dropdowns are easily tappable and don't require horizontal scrolling on mobile.
- Run the page through a mobile viewport test (Chrome DevTools responsive mode at 375px and 414px widths) and fix any horizontal overflow, tiny tap targets, or text that's too small to read without zooming (minimum 16px body text on mobile).

## Deliverable

After making these changes, give me a summary of every section you touched and why, so I can review before this goes live. Do not change the phone number, email, service area, or the actual application form fields/logic — only content ordering, copy, layout, and responsiveness.
