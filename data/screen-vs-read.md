# Screen (D3/README) vs full code-read — agreement table

Basis: **2721** clean scored verdicts (scores 1–9). Excludes **60** quarantined deep-reads and **1** unreviewable deleted-upstream repo (score 0). Deep-reads total **2,782** (wave1 1,007 + wave2 1,775). Cloned **3,462**; **680** never deep-read.

Gold standard = deep-read score ≥5 (genuine tool). n_gold = **1192**.

Precision/recall below are computed with the usual definitions (not swapped). D3 comparisons use the **2491** rows that have `d3_gate` scores; screen comparisons use the **2689** rows with a non-null `worth_deep` flag.

## Says-YES style gates

| Screen signal | n | Precision | Recall | Meaning |
|---|---|---|---|---|
| worth_deep (bool) | 2689 | 0.55 | 0.91 | of what it sent for reading, ~55% were real tools; catches ~91% of gold in this basis |
| real_tool (README screen) | 2689 | 0.49 | 0.97 | high recall, ~half precision |
| d3 gate real_bet_tool ≥0.5 | 2491 | 0.50 | 0.92 | same story, cheap |
| d3 gate real_bet_tool ≥0.7 | 2491 | 0.57 | 0.71 | tighter threshold loses gold |
| d3 sports_related ≥0.5 | 2491 | 0.46 | 0.97 | relevance filter works, tool filter weaker |
| d3 has_odds_source ≥0.5 | 2491 | 0.54 | 0.68 | many real tools hide feeds |

## Says-NO residual audit

Stratified ~20% of screened-out repos (seed=7). These audits **are deep-reads** (lane `residual-20pct`, n=138 in meta; 137 clean).

| Result | Value |
|---|---|
| genuine tools in residual sample | 30 / 137 |
| true-tool rate of the "no" pile | **21.9%** |
| never deep-read clones | **680** (= 3,462 − 2,782). Residual audits are **not** inside this 680 |
| extrapolation of residual rate onto 680 unread | ≈ **149** additional genuine tools |
| confirmed ≥5 in deep-reads (clean) | **1192** (already includes the 30 residual finds) |
| implied real-tool stock | **1192 + ~149 ≈ 1341** of 3,462 (**39%**) |

## Bottom line
- Screen says-yes → ~50/50 genuinely useful; keep reading them.
- Screen says-no → about **1 in 5** is still a real tool.
- Do **not** write `680 = 137 + 543`. The 137 residual audits are part of the 2,782 deep-reads.
