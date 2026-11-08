# Screen (D3/README) vs full code-read — agreement table

Basis: **2,721** clean scored verdicts (scores 1–9). Excludes **60** quarantined deep-reads and **1** unreviewable deleted-upstream repo (score 0). Deep-reads total **2,782** (wave1 1,007 + wave2 1,775). Cloned **3,462**; **680** never deep-read.

Gold standard = deep-read score ≥5 (genuine tool). n_gold = **1,192**.

Precision/recall use the usual definitions. D3 comparisons use the **2,491** rows with `d3_gate` scores; screen comparisons use the **2,689** rows with a non-null `worth_deep` flag. Two-decimal recalls round half-up (so D3 `real_bet_tool ≥ 0.5` raw recall **0.925** → **0.93**).

## Says-YES style gates

| Screen signal | n | Precision | Recall | Meaning |
|---|---|---|---|---|
| worth_deep (bool) | 2689 | 0.55 | 0.91 | ~half of says-yes are real tools; catches ~91% of gold in-basis |
| real_tool (README screen) | 2689 | 0.49 | 0.97 | high recall, ~half precision |
| d3 gate real_bet_tool ≥0.5 | 2491 | 0.50 | 0.93 | raw 0.925, shown as 0.93 |
| d3 gate real_bet_tool ≥0.7 | 2491 | 0.57 | 0.71 | tighter threshold loses gold |
| d3 sports_related ≥0.5 | 2491 | 0.46 | 0.97 | relevance filter works, tool filter weaker |
| d3 has_odds_source ≥0.5 | 2491 | 0.54 | 0.68 | many real tools hide feeds |

## Says-NO residual audit

These audits **are deep-reads** (lane `residual-20pct`, n=138 in meta; 137 clean). If the screened-out pool for that draw is 137 audited + 680 unread = **817**, then 137/817 ≈ **17%** (not ~20%).

| Result | Value |
|---|---|
| genuine tools in residual sample | 30 / 137 |
| true-tool rate of the "no" pile | **21.9%** |
| never deep-read clones | **680** (= 3,462 − 2,782). Residual audits are **not** inside this 680 |
| extrapolation of 21.9% onto 680 unread | ≈ **149** additional genuine tools |
| assumption | the 680 were **screen-rejected**. This release does not include the unread roster with screen flags; if some unread clones were screen-accepted, expect a **higher** hidden count (~50% real-tool rate on says-yes) |
| confirmed ≥5 in deep-reads (clean) | **1,192** (already includes the 30 residual finds) |
| implied real-tool stock | **1,192 + ~149 ≈ 1,341** of 3,462 (**39%**) under the screen-rejected assumption |

## Bottom line
- Screen says-yes → ~50/50 genuinely useful; keep reading them.
- Screen says-no → about **1 in 5** is still a real tool.
- Do **not** write `680 = 137 + 543`. The 137 residual audits are part of the 2,782 deep-reads.
