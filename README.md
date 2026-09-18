# Average Joe Fitness design preview

A redesign preview of [averagejoe.fitness](https://averagejoe.fitness/), built as a static site.
**This is not the live site.** Every page carries a "Design preview" pill, a `noindex, nofollow`
meta tag, and `robots.txt` disallows everything.

Live preview: https://odyssey-jotun.github.io/averagejoe-preview/

## What this is

The current site is a single WordPress/Divi page. This preview keeps Joe's copy and claims
almost verbatim and rebuilds the presentation:

| | Current site | This preview |
|---|---|---|
| Structure | One long page | Three pages: Home, The Training, Meet Joe |
| Stack | WordPress + Divi + jQuery | Hand-written HTML/CSS/JS, no build step, no dependencies |
| Palette | Light, default Divi blue links | Near-black with an ember accent drawn from Joe's own `#b35a44` |
| Type | Bebas Neue + Poppins | Bebas Neue (kept, it is his brand) + Inter Tight |
| FAQ | Divi toggles | Native `<details>` elements, works without JS |
| Stat counters | Divi number counter | ~40 lines of vanilla JS, respects `prefers-reduced-motion` |

## Structure

```
index.html      Home: hero, the cost of inactivity, stats, approach, results, steps, Joe teaser
training.html   The method, what a 12 week program includes, the honest check, FAQ, references
about.html      Joe's story, credentials, who he works with
styles.css      All styles, one file, CSS custom properties at the top
main.js         Mobile menu, scroll reveal, stat counters
img/            Photos pulled from the current site, resized and recompressed
```

## Running it

No build step. Any static server works:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Things Joe should look at before any of this goes live

These are content issues carried over from the current site, not design decisions:

1. **The references section on the live site is placeholder text.** It literally reads
   "1. text 2. text 3. text 4. text". I have written out the five real citations on
   [training.html#references](training.html) based on the author names and years used in the
   body copy, but Joe should confirm each one.

2. **"Neville et al., 2024" appears to be a misattribution.** The study described in the copy
   (a 2024 meta-analysis of 218 studies and 14,170 participants on exercise and depression) is
   Noetel et al., 2024 in the *BMJ*. There is no Neville paper matching that description that I
   could find. The reference list uses Noetel and flags the discrepancy on the page.

3. **The "62% reduction in depression symptoms" figure needs a source check.** Noetel et al.
   reported effect sizes as standardised mean differences, not as a percentage reduction, so
   the 62% number does not obviously come from that paper. It is repeated three times across
   the site, including as a headline claim, so it is worth getting right.

4. **The only conversion path is a phone call.** There is no booking form, no email address,
   and no scheduling link anywhere on the current site. The preview uses `tel:` links
   throughout. If Joe wants a consult form or a Calendly embed, that is a real addition, not a
   restyle, and should be decided before build.

5. **All photography except the headshot is stock.** Real client and session photos would do
   more for this design than anything else on the list. Joe's own gym, his own clients, his
   own sessions. That is the single highest-value thing he could hand over.

## Photography

The photos on the current site are generic paid-stock, and the hero was a full-bleed shot of an
unidentified man, which on a solo trainer's site reads as "this is Joe." It is not Joe, so it has
been replaced.

The hero is now gym equipment, with Joe's actual headshot as a captioned portrait card carrying
his name and credentials. Nobody in the imagery is standing in for the trainer.

Everything else is **CC0 / public domain**, so there is no attribution requirement and no
licensing risk for commercial use. Sources, for verification:

| File | Source | Credit |
|---|---|---|
| `hero-gym.jpg` | [rawpixel](https://www.rawpixel.com/image/5903386/photo-image-public-domain-free-workout) | public domain |
| `plates.jpg` | [rawpixel](https://www.rawpixel.com/image/6029749/photo-image-public-domain-free-plates) | public domain |
| `kettlebells.jpg` | [rawpixel](https://www.rawpixel.com/image/6038425/photo-image-public-domain-free-sport) | public domain |
| `back.jpg` | [StockSnap](https://stocksnap.io/photo/girl-woman-ZFIQC5CZRP) | Scott Webb, CC0 |
| `mirror.jpg` | [StockSnap](https://stocksnap.io/photo/girl-woman-XBU0JECP7E) | Scott Webb, CC0 |
| `bwbar.jpg` | [StockSnap](https://stocksnap.io/photo/girl-woman-EHS7NJY7KT) | Alexandre Vanier, CC0 |
| `cable.jpg` | [StockSnap](https://stocksnap.io/photo/man-workout-KZROPA98J8) | Bruce Mars, CC0 |
| `joe.jpg`, `img/wordmark.png` | Joe's own site | his own assets |

Found via [Openverse](https://openverse.org), filtered to licenses permitting commercial use and
modification. CC0 needs no credit line on the site itself; the table is here so the provenance is
checkable.

## Notes

- Fonts load from Google Fonts. Everything else is local.
- No analytics, no tracking, no cookies.
- Built to be moved: if this direction gets approved it ports cleanly to Astro, matching the
  odyssey setup.
