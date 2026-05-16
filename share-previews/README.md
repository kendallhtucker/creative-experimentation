# Share Previews

What people see when the Internet Taste Test or hiring page gets shared.

## Two layers of "preview"

### Layer 1: OG card (Slack / iMessage / X / LinkedIn link-unfurl)

When someone pastes a URL into a chat or social post, the platform fetches the page's Open Graph (`og:*`) meta tags and shows a card. **Right now every URL on this site shows the same OG card** — hash routing (`#result/8`, `#hiring`, etc.) can't change `<head>` tags on a static page.

- **OG image:** `og-share-card.jpg` in this folder (hot-pink/gold starfield card)
- **OG title:** *RAMP :: Creative Experimentation Team — now hiring*
- **OG description:** *Take the taste test. Score 9 or 10 to unlock the application. We're hiring a viral creative producer.*

So if Alex pastes `kendallhtucker.github.io/creative-experimentation/#result/8` in Slack, they see the same card as if they'd pasted the homepage URL. The unique-per-score experience only happens after the click, not in the preview.

> If you want per-score OG previews, that needs server-side rendering (Vercel / Ramplify), not GitHub Pages.

### Layer 2: User-generated screenshots (what people actually share)

People are sharing screenshots of the result card itself — not link unfurls. Each card looks distinct per score. Screenshots of all 11 are in `result-cards/`:

| File | Score | Persona |
|---|---|---|
| `result-10.png` | 10 | Megan Stalter |
| `result-09.png` | 9 | Elle Fanning |
| `result-08.png` | 8 | Hudson & Connor |
| `result-07.png` | 7 | Rebecca Black |
| `result-06.png` | 6 | Timothée Chalamet |
| `result-05.png` | 5 | Chet Hanks |
| `result-04.png` | 4 | The All-In Guys |
| `result-03.png` | 3 | JoJo Siwa |
| `result-02.png` | 2 | Jimmy Fallon |
| `result-01.png` | 1 | Katy Perry |
| `result-00.png` | 0 | Hilaria Baldwin |

Also in `result-cards/`:
- `page-hiring.png` — full Viral Creative Producer hiring page
- `homepage-planets.png` — the planet homepage

## Layer 3: Share button text

When someone clicks "share my score" on the result card, this text gets copied to clipboard (or passed to native share):

**Score 8 or higher:**
> i scored {N}/10 on the internet taste test. they said i'm like {persona}. bet you can't beat me: kendallhtucker.github.io/creative-experimentation/#result/{N}

**Score below 8:**
> i scored {N}/10 on the internet taste test. they said i'm like {persona}. i'm ashamed, can you do better: kendallhtucker.github.io/creative-experimentation/#result/{N}

Examples filled in:

- **10/10:** "i scored 10/10 on the internet taste test. they said i'm like megan stalter. bet you can't beat me: kendallhtucker.github.io/creative-experimentation/#result/10"
- **8/10:** "i scored 8/10 on the internet taste test. they said i'm like hudson & connor. bet you can't beat me: kendallhtucker.github.io/creative-experimentation/#result/8"
- **5/10:** "i scored 5/10 on the internet taste test. they said i'm like chet hanks. i'm ashamed, can you do better: kendallhtucker.github.io/creative-experimentation/#result/5"
- **0/10:** "i scored 0/10 on the internet taste test. they said i'm like hilaria baldwin. i'm ashamed, can you do better: kendallhtucker.github.io/creative-experimentation/#result/0"

## Notes

- The `#result/N` deep link works — clicking lands viewer directly on that score's card.
- If you want a richer share-link experience (e.g., the URL preview shows the actual score + persona, not the generic OG card), you'd need to host per-score HTML files OR move to a server platform (Ramplify, Vercel, Cloudflare Pages with workers).
- All screenshots captured at 1100×1700 viewport. Real-world phone screenshots will be portrait-shaped and crop differently — these are best-case full-card captures.
