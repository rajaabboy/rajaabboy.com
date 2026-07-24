# Content sourcing

This site went through two research passes before real content arrived. This
file documents what came from where, so nothing on the live site is mistaken
for more (or less) verified than it actually is.

## 1. Reference site research (phaniputtabakula.com)

Fetched successfully — both the live site and the local Hugo source
(`~/src/phaniputtabakula.com`). Used only for **layout, tech stack, and design
language**: sticky sidebar + single content column, Hugo static site with
fully custom layouts (no theme templates in actual use), Instrument Serif +
Lora font pairing, warm neutral palette with a `prefers-color-scheme: dark`
variant, `fadeUp` scroll-in animation on sections, and the "label → list of
cards" section pattern (their "Building" section became this site's
"Experience" / "Selected Work" sections).

No personal content, company names, or writing from that site was copied —
only the structural and stylistic approach, per the original brief.

## 2. LinkedIn fetch attempt (superseded — not used in the final site)

An automated fetch of `https://www.linkedin.com/in/raja-abboy-b289228/`
returned a partial, AI-summarized preview (name, "Greater Bengaluru Area",
a fragment suggesting "Celonis" and a "Service Delivery Executive" headline,
education at University of St. Thomas, and a list of certifications). This
came from an unauthenticated fetch of a login-gated page, summarized by a
small model — **not reliable enough to publish as fact**, so none of those
specifics (exact employer, dates, certifications, education) were used on
the site.

This was superseded almost immediately by item 3 below, which is the actual
source of truth for the live site.

## 3. Raja-supplied content brief (authoritative — used throughout)

Raja provided `RAJA_CONTENT_SOURCE.md` directly (a pre-written, copy-ready
content brief consistent with his résumé and LinkedIn). **Everything
substantive on the live site comes from this file**, including:

- Name, title, headline, and value-proposition copy (hero/sidebar)
- Full "About" bio (both short and long versions)
- All three "Experience" entries — Celonis, Wells Fargo, Cognizant — and
  their descriptions
- All three "Selected Work" project entries
- The "By the Numbers" stat strip (21+ years, $30M ARR, 120+ team members,
  99.5% availability, 2015 Retail CG Icon of the Year)
- All skill/focus-area pills, grouped exactly as in the source brief
- Contact details: email (`rajaabboy@gmail.com`) and LinkedIn URL

Nothing in these sections is fabricated or generic filler — it's Raja's own
words, lightly adapted to fit the section format (e.g., turning resume bullets
into short card descriptions).

## What's still a placeholder

Only assets Raja's brief explicitly couldn't supply from documents alone:

| Placeholder | Where | Default in place now |
|---|---|---|
| `RAJA_PHOTO_URL` | `layouts/partials/sidebar.html` | Initials avatar (`static/avatar.svg`) |
| `RAJA_RESUME_URL` | `hugo.toml` (`params.resume`), sidebar, footer | Points to `/resume.pdf` — file not yet added |
| Testimonials section | not built | None yet — source brief has none to use |
| Phone number | not included | Source brief marks it optional/opt-in; left out by default |

The Writing section exists structurally (nav link, `/posts/` list page) but
has no entries, since the source brief doesn't include any real articles.
It will render "Nothing here yet." until posts are added under
`content/posts/`.
