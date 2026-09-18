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

## Content corrections

The copy on the live site attributes specific invented statistics to real, checkable papers.
Each figure below was verified against its source and corrected in this preview. The full log is
rendered on the page at [training.html#references](training.html) so Joe sees it in context.

| Claim on the live site | What the source actually says |
|---|---|
| "Neville et al., 2024" | No such paper found. The study described (218 trials, 14,170 participants) is **Noetel et al., 2024**, *BMJ* 384:e075847. |
| "62% reduction in depression symptoms" from strength training | Noetel reports Hedges' g, not percentages. Strength training was **g -0.49** (95% CrI -0.69 to -0.29). The -0.62 figure is **walking and jogging**, a different modality. |
| "Same effect size as antidepressant medications, but without the side effects" | Removed. A clinical equivalence claim is not one a personal training site should make. |
| "23% higher physical self-worth scores (Gordon et al., 2018)" | Gordon 2018 measures **depressive symptoms only**. It does not assess self-worth, self-esteem or self-efficacy. Actual finding: **Δ 0.66** (95% CI 0.48 to 0.83) across 33 trials and 1,877 participants, NNT 4. |
| "Measurable improvements in self-efficacy within 8 weeks (Gordon et al., 2018)" | Same problem, same paper. Replaced with the real finding. |
| "Life expectancy increases of 2 to 5 years (Lee et al., 2012)" | Lee 2012 estimates **0.68 years** (range 0.41 to 0.95) of global life expectancy from eliminating inactivity. Off by roughly 5x. |
| "40% better sleep quality scores" | No citation anywhere. Now stated as Joe's own observation, not a statistic. |
| "Staying inactive can cut your life short by 3 to 5 years" | Conflicts with the 0.68 figure above. Replaced with Lee's "roughly one in ten premature deaths worldwide". |

**Still unverified and needing Joe's sources:** the 250,000 annual US deaths figure, "35% of heart
disease deaths", "19 chronic conditions", and "3% to 8% of muscle mass per decade". These are
plausible and widely repeated, but I could not tie them to the cited papers, so they are left in
place and flagged rather than silently changed.

These are health claims published under Joe's name and certification. Getting them wrong is a
bigger risk to him than any design decision in this repo.

## Contact

The live site's only conversion path is a phone call. No form, no email address, no scheduling
link exists anywhere on it. This preview adds **text message** (`sms:` links) alongside the phone
number, which needs no backend and works today.

A real consult form still needs two things from Joe that do not exist yet: an email address to
send to, and an endpoint to post to (Formspree, Netlify Forms, or similar). Worth doing, since a
fair share of people will not cold-call a stranger about their weight.

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
