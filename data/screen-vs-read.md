# Screen (d3/README) vs full code-read — agreement table

Basis: 2,722 non-quarantined code-read verdicts (of 2,782 total; 203 quarantined excluded).
Gold standard = deep-read score ≥5 (genuine tool). Both waves complete: 1,007 + 1,775.

## Says-YES rows (screen flagged worth-deep; n≈2,585)

| Screen signal | Precision | Recall | Meaning |
|---|---|---|---|
| worth_deep (bool) | 0.55 | 0.92 | of what it sent for reading, 55% were real tools; it catches 92% of gold |
| real_tool (README screen) | 0.49 | 0.98 | near-perfect recall, half-precision |
| d3 gate real_bet_tool ≥0.5 | 0.50 | 0.92 | same story, cheap |
| d3 gate real_bet_tool ≥0.7 | 0.57 | 0.71 | tighter = loses 29% of gold |
| d3 sports_related ≥0.5 | 0.46 | 0.97 | relevance filter works, tool filter weak |
| d3 has_odds_source ≥0.5 | 0.54 | 0.68 | worst signal — many real tools hide their feeds |

## Says-NO rows — residual 20% audit (stratified by type, seed=7; n=137 read)

| Result | Value |
|---|---|
| genuine tools found in screened-out sample | 30 / 137 |
| **true-tool rate of the "no" pile** | **21.9%** |
| notable misses (screen said no, code says 6–8) | dime-ai (production SaaS; vendored .claude tree fooled gate), livesports-bot (7.6k-line Rust Kelly bot, null struct), matchday-ai-ml-api, vladiskiva dbt tool, stephenaleje61 Express server |
| extrapolation to 543 unread screened-out repos | ≈ **119 additional genuine tools** we never opened |

## Bottom line
- Screen says-yes → ~50/50 genuinely useful; keep reading them.
- Screen says-no → **1 in 5 is still a real tool**; the README-only screen systematically misses code-heavy/no-README repos (vendored trees, null structs, Rust/Express backends).
- Corpus: 1,187 confirmed genuine tools read + ~119 estimated hidden ≈ 1,300 real tools in 3,462 sports-betting repos (37%).
