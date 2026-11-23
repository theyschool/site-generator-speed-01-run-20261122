# Faster makefun-site — a drop-in static site generator

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/theyschool/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/theyschool/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

`solve.js` is a dependency-free ES module whose `run(input)` returns exactly the output tree makefun-site 1.0.0's `build` returns for the same site — every page's `index.html`, the index and tag pages, `build-report.txt` and each static file, byte for byte — written to be faster: single-pass scanners instead of per-line regex batteries and per-character escaping, memoized slugs and long dates, link resolutions cached per directory, and a template renderer that appends into one buffer per page.

`main.ts` is the harness driver: it reads every case from `/input/cases.json`, answers each with `run`, and writes `/output/answers.json`.

## Files

- `solve.js` — the generator: front matter, permalinks, the Markdown subset, collections, tags, layouts and the report, in the reference's order and with its exact refusal reasons.
- `main.ts` — the driver described above.
- `LICENSE` — MIT.

## Verification

On the kit's practice set (3 cases, 257/348/486 files) the output is byte-identical to the reference's expected answers, and a differential fuzz against makefun-site 1.0.0 itself — front-matter refusals, template parse errors, Markdown edge cases, slug collisions, Unicode titles, shadowed statics and mutated practice sites — shows no difference. Locally (same machine, fresh processes, CPU time over the full practice set) it runs at about 1.6× the house baseline's speed.
