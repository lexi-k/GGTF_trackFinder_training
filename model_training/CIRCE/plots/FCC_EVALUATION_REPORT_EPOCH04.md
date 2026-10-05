# CIRCE Performance on IDEA Drift Chamber KeepAll (Epoch 4, genStatus in [0, 1], 50 000 events, 100 seeds, tb = 0.60, td = 0.10)

Evaluated on all reconstructable tracks across the full 100-seed `eval-keepall` holdout ($15^\circ < \theta < 165^\circ$, $p_\mathrm{T} > 0.1$ GeV, genStatus $\in$ [0, 1] at champion operating point $t_\beta=0.60, t_d=0.10$):

## 1. Complete Benchmark Metrics Mapping: Raw Unmerged vs. Fragment Merged ($t_\mathrm{m}=0.10$)

| Metric | Evaluation Selection / Protocol | Raw Unmerged | Fragment Merged ($t_\mathrm{m}=0.10$) | Benchmark Target | Status |
|---|---|:---:|:---:|:---:|:---:|
| **Tracking Efficiency ($N_\mathrm{hits} > 10$, 1-to-1)** | Double Majority (Purity $\ge 50\%$, Hit Eff $\ge 50\%$) | **94.76%** | **94.82%** | $> 90.0\%$ | **Exceeded (+4.82%)** |
| **Tracking Efficiency ($N_\mathrm{hits} > 10$, Majority)** | Standard IDEA tracks, Purity $> 75\%$ | **93.88%** | **93.24%** | $> 90.0\%$ | **Exceeded (+3.24%)** |
| **Tracking Efficiency ($N_\mathrm{hits} > 3$, 1-to-1)** | Inclusive recovery down to 4 hits, Double Majority | **93.14%** | **93.17%** | — | High inclusive recovery |
| **Tracking Efficiency ($N_\mathrm{hits} > 3$, Majority)** | Inclusive recovery, Purity $> 75\%$ | **91.58%** | **90.90%** | — | High inclusive recovery |
| **Fake Rate ($N_\mathrm{hits} > 10$, 1-to-1 Hungarian)** | Unassigned candidates in 1-to-1 match ($N > 10$) | **6.38%** | **4.71%** | $< 8.0\%$ | **Exceeded (beats 8% target)** |
| **Fake Rate ($N_\mathrm{hits} > 10$, Majority)** | Spurious fakes without multi-track ($N > 10$) | **0.50%** | **0.41%** | — | Ultra-pure |
| **Fake Rate ($N_\mathrm{hits} > 3$, 1-to-1 Hungarian)** | Unassigned candidates in 1-to-1 match ($N > 3$) | **10.79%** | **8.18%** | — | Standard `min_hits=3` |
| **Fake Rate ($N_\mathrm{hits} > 3$, Majority)** | Spurious fakes without multi-track ($N > 3$) | **2.81%** | **2.48%** | — | CLD paper convention |
| **Multi-Track Merge Rate ($N_\mathrm{hits} > 10$)** | Clusters swallowing $\ge 2$ particles ($>75\%$ eff) | **7.23%** | **7.54%** | — | Clean separation |
| **Multi-Track Merge Rate ($N_\mathrm{hits} > 3$)** | Clusters swallowing $\ge 2$ particles ($>75\%$ eff) | **12.93%** | **13.40%** | — | Clean separation |
| **Candidates / Event ($N_\mathrm{hits} > 10$)** | Reconstructed high-purity tracks | **25.46** | **25.04** | — | Benchmark tracks |
| **Candidates / Event ($N_\mathrm{hits} > 3$)** | Inclusive track candidates | **31.86** | **30.93** | — | Normal multiplicity |
| **Evaluated Sample Size** | 100 seeds, 50,000 events | **1,672,188 targets (1,115,146 with N > 10, 1,169,642 with N > 3)** | — | Full statistics |

## 2. Key Physical Highlights for PR #3

- **Impact of Fragment Merging ($t_\mathrm{m} = 0.10$):** Fragment merging suppresses the Hungarian 1-to-1 fake rate on benchmark tracks from **6.38% down to 4.71%** (and from 10.79% down to 8.18% on inclusive candidates), while preserving outstanding tracking efficiency (**94.82%** 1-to-1 and **93.24%** Majority).
- **Conformal Geometric Representation:** Conformal geometric algebra ($Cl(4,1)$) natively represents drift chamber measurement circles (wire center, wire direction, drift radius). This eliminates the discrete left/right point ambiguity upstream and achieves high tracking efficiency on standard benchmark tracks ($N_\mathrm{hits} > 10$).
- **Consistent High Acceptance:** Tracking efficiency starts high across the full momentum spectrum and reaches a 98–99.5% plateau above 1 GeV, remaining high across the entire polar angle acceptance ($15^\circ \le \theta \le 165^\circ$).

Generated figures: `head_to_head_keepall_efficiency.png` and `fcc_comprehensive_suite.png` (with vector PDF siblings).

