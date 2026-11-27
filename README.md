# Data and Protocol Package — "Conformational Deviation Limits Interface Localization from Apo Structures but Not Residue Plasticity"

This package accompanies the manuscript submitted to the *Journal of Chemical Information and Modeling* (JCIM). It contains the benchmark data, residue-wise labels, evaluation outputs, preregistered protocols, analysis code, and figures needed to reproduce every number reported in the main text and Supporting Information.

## Contents

### `data/` — Benchmark datasets and evaluation outputs

| File | Description | Reported in |
|---|---|---|
| `pair_table_main_83pairs.csv` | Master pair table of the main benchmark: 83 strictly paired apo–holo structure pairs from human metabolic-inflammation receptor proteins (14 families / 14 homology clusters), with global/interface RMSD, coverage, PeSTo apo AUPRC | Table S18 |
| `pair_table_augmented_226pairs.csv` | Augmented sensitivity set: 226 apo pairs used for out-of-sample recomputation of every main-set conclusion | Tables S7B, S12B, S13D |
| `residue_wise_displacement_labels.csv` | 19,861 residue-wise apo-to-holo conformational displacement labels (main set), the plasticity ground truth | Methods 2.1.3 |
| `structure_qc_main.csv`, `structure_qc_augmented.csv` | Structure-level quality control for both sets | Table S13D |
| `resolution_strata.csv` | apo resolution stratification of AUPRC | Table S8A |
| `tradeoff_curve.json` | Numbers behind the strict-ranking triage tradeoff curve | Table S8B / Figure S1 |
| `cross_method_consistency.json` | Cross-method consistency summary (PeSTo / GAPS / ScanNet) | Tables S9, S10 |
| `pair_level_with_gaps.csv` | Per-pair GAPS results on the apo panel (frozen official weights) | Table S9 |
| `pair_level_with_scannet.csv` | Per-pair ScanNet (MSA-free weights) results on the apo panel | Table S10 |
| `pesto_overlap_audit.json`, `overlap_stratified.json` | Audit of benchmark entries against PeSTo official train/validation/test splits | Table S4 |
| `sensitivity_summary.csv` | Augmented-set recomputation and stratification summary | Tables S7B, S12B |
| `expansion_stats.json`, `expansion_stats_independence.json`, `record_level_ci.json` | Augmented-set statistics, independence checks, and apo-level record confidence intervals | Tables S6C, S13D |
| `leave_one_cluster_out_main.csv`, `leave_one_cluster_out_sens.csv`, `power_analysis.json` | Cluster-level robustness and statistical power | Tables S6B, S6C |
| `sidechain_sensitivity.json`, `sidechain_rmsd_per_pair.csv`, `holo_selection_rule.json` | Sensitivity matrix: all-heavy-atom vs Cα displacement; alternative bound-state selection rule | Table S8C, S8D |
| `anm_per_pair.csv` | Anisotropic network model (ANM) flexibility per pair | Table S12 |
| `interface_vs_noninterface_pairs.csv` | Per-pair median displacement, interface vs noninterface residues | Table S13A |
| `disease_variants/` | UniProt natural-variant screening, interface mapping, and Fisher test inputs | Tables S15A–S15B |

### `protocols/` — Preregistered confirmatory protocols

Confirmatory hypotheses, evaluation gates, and analysis units were frozen before results were seen.

| File | Protocol ID | Status |
|---|---|---|
| `preregistered_protocol_v3.json`, `预注册协议v3.md` | APO-DOMAIN-2026-10-30-v3 | Frozen; C1 single-run authorized |
| `预注册协议H1.md`, `h1_confirmation_result.json`, `protocol_sha256.txt` | PRE-FORM-H1-2026-10-30 | Confirmed (conformational-association hypothesis) |
| `预注册协议H2.md`, `h2_confirmation_result.json`, `protocol_sha256.txt` | PLASTICITY-H2-2026-10-30 | Confirmed (plasticity-prediction hypothesis) |

SHA-256 hashes of the frozen protocol documents are provided to verify integrity.

### `code/` — Analysis scripts

- `code/pipeline/` — stepwise analysis scripts (dataset construction `Step02–Step03, Step76`, displacement labels `Step86*`, H1/H2 confirmations `Step82, Step89*`, GAPS `Step106*, Step122`, ScanNet `Step125*, Step126*`, power/robustness `Step107`, expansion `Step108–Step111`, sensitivity `Step121–Step126`, variants `Step96`, ANM `Step101`, supervised baselines `Step104, Step57, Step60, Step65`).
- `code/paper/` — scripts that assembled the JCIM supplements, sensitivity matrix, and 600-dpi figures.
- External frozen models: PeSTo (i_v4_1 weights, training-free inference), GAPS and ScanNet official weights (used without retraining; not redistributed here — see respective repositories).

### `figures/` — Publication figures (TIFF, 600 dpi, RGB)

Main-text Figures 1–5, Supporting Figures S1–S4, and the graphical abstract (English versions).

## Reproduction

1. Python ≥ 3.10 with `biopython`, `numpy`, `pandas`, `scipy`, `scikit-learn`.
2. Run pipeline scripts in step order (see `code/INDEX.txt` for the mapping from script to output file).
3. Confirmatory results in `protocols/*_confirmation_result.json` should be regenerated verbatim from the frozen protocol documents.

## License and citation

- Data and figures: CC BY 4.0. Code: MIT.
- If you use this package, please cite the manuscript (DOI to be added upon acceptance) and this dataset (Zenodo DOI, to be minted on upload).

*Correspondence: Yonge Feng, College of Science, Inner Mongolia Agricultural University, Hohhot 010018, PR China. E-mail: yefeng@imau.edu.cn.*

*Authors: Xiaoyu Niu, Yonge Feng. This work was supported by the Inner Mongolia Natural Science Foundation of China (2026MS0721 and 2023MS06007) and the Interdisciplinary Research Fund of Inner Mongolia Agricultural University (BR231514).*
