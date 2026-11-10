# How we compare, and what we refuse to claim

The comparison with paid tools (Topaz Video AI / Photo AI, and the Windows "DLSS 5" enhancers) is a feature of this project, not a marketing page. It has one rule that makes it usable:

> **Every cell is either a fact we can link to, or a number we measured on a file we are allowed to publish. There is no third kind.**

## Part 1 — Facts anyone can check (no measurement needed)

These cells are filled from the vendor's own page, with the date read.

| Field | Us | Topaz (photo/video) | Windows "DLSS 5" enhancers |
|---|---|---|---|
| Source available | yes, Apache-2.0 | no | varies; several are closed binaries |
| Runs on macOS / Linux | yes (target) | macOS yes; Linux — check their page | Windows only, in practice |
| Needs an NVIDIA card | no | no (CPU/GPU modes; speed varies) | yes |
| Patches a game's rendering | no | no | yes |
| Subscription | none | paid licence — read the current price from their page at comparison time | free, no support |
| Video temporal model (flicker control) | **no** (v1.0) | yes | n/a |
| Redistributes model weights | no, links + hashes only | no | varies |

Fields marked "check their page" are filled on the day of publishing and stamped with that date; a stale cell is deleted rather than guessed.

## Part 2 — Quality claims (only with a protocol)

We do not say "better than X". We publish pairs, and the reader judges.

1. **Fixtures.** Public-domain or our own files only. No vendor sample images, no screenshots from someone else's video, no frames lifted from a trailer.
2. **Same input, same crop, same output size.** If a tool cannot hit the exact output size, the deviation is printed.
3. **Full-size crops, not thumbnails.** A 100 × 100 crop at 4× next to the source crop, plus the whole frame for context.
4. **Time and hardware named.** "42 s on an Intel i9-9880H, 8 threads, no GPU" beats "fast".
5. **Failures kept.** The frames where our output invents texture, smears hair, or turns text into soup stay in the set. A comparison with only the wins is an advertisement.
6. **Reproduce line.** Each pair ships the exact command and the recipe JSON, so a reader can rerun it and disagree with us.

## Part 3 — What we will never publish

- A "sharper" claim from a downscaled-then-upscaled pair.
- Timing from a warm cache presented as first-run time.
- Someone else's benchmark table copied in as our result.
- A Topaz screenshot passed off as our render, or the reverse.

*This document is the acceptance test for any comparison page we ship. If a page cannot satisfy Part 3, the page does not go out.*
