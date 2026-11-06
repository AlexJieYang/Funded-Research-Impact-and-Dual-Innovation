# Funded Research Impact and Dual Innovation

Research code for **Unveiling the Impact and Dual Innovation of Funded Research**,
by Alex J. Yang. The analysis compares NIH-funded, NSF-funded, and other research
using impact, novelty, and disruption measures.

## Workflow

Configure `data_dir` for the study's paper-level analysis and field lookup tables.
Each notebook loads its own tables and saves separate SVG panels under its
notebook subdirectory within `output_dir`.

| Entry point | Analysis |
| --- | --- |
| `fig 1.ipynb` | Funding-group counts and distributions by year and field |
| `fig 2.ipynb` | Novelty and disruption distributions |
| `fig 3-4.ipynb` | Impact and innovation comparisons by year and field |
| `fig SM 2.ipynb` | Paper groups with positive patent/tweet counts |
| `Main Reg.R` | Fixed-effects regression tables |

The supplementary notebook derives binary patent/tweet indicators from their
count columns. Yearly count series use the complete 2000–2015 range, and field
labels follow the field lookup table. Impact regressions use the logarithmic
transformations shown in `Main Reg.R`.

For regression, install R packages `fixest` and `data.table`, start R in the
repository root, and run `source("Main Reg.R")`. `FUNDED_ANALYSIS_CSV` selects
the analysis CSV; `FUNDED_OUTPUT_DIR` selects the output directory. Their defaults
are `data/analysis.csv` and `outputs/regression`. Outputs are `citations.csv`,
`patents_tweets.csv`, and `novelty_disruption.csv`.

## Installation and configuration

Use Python 3.10 or 3.11. Create and activate a virtual environment with the command
for your operating system, then install the packages:

```bash
python -m venv .venv
python -m pip install -r requirements.txt
```

Copy `config.example.json` to `config.json`. Set `data_dir` to the study-data
directory and `output_dir` to the figure destination. Relative paths resolve
from the repository root; absolute paths are accepted. `RESEARCH_CONFIG` selects
another configuration file.

Start `jupyter lab` inside the repository and open the desired notebook. Each
Python notebook includes its own initialization and data loading. The output
directories are created automatically. R entry points use the environment
variables described in their workflow sections.

## Source validation

```bash
python scripts/check_sources.py
```

This command validates Python syntax, notebook JSON, configuration JSON, and
empty notebook execution state. The GitHub Actions workflow performs the same
static checks, including R parsing when R is available. R entry points use an
R installation and their listed packages.

## Citation and license

See `CITATION.cff` for repository metadata and cite the associated research.
The MIT license covers code and documentation. Data, publications, and
third-party materials retain their respective source rights.

## Research abstract

In the relentless pursuit of scientific advancement, comprehending the profound impact and innovation nature inherent in funded research projects assumes paramount significance. To illuminate this matter, I delve into the realm of research supported by the National Institutes of Health (NIH) and the National Science Foundation (NSF). The evaluative framework encompasses a spectrum of metrics, including citations by papers, patents, and Tweets, as markers of research impact. Moreover, I embrace ex-ante innovation (Novelty) and ex-post innovation (Disruption) as dual indispensable yardsticks for evaluating the innovative nature of research projects. Novelty denotes the manifestation of atypical combinations of existing knowledge, while Disruption signifies the extent of paradigm-shifting potential and the ability to exert a disruptive influence on future research endeavors. First, the analysis reveals that funded research projects manifest a conspicuously heightened impact in comparison to their non-funded counterparts. Second, I uncover a noteworthy finding: funded research demonstrates significantly higher levels of ex-ante innovation (Novelty). However, in a surprising twist, the impact of funding on ex-post innovation (Disruption) appears to be faint. Additionally, I undertake a meticulous scrutiny of the robustness of the research findings by scrutinizing patterns across years and fields. Despite the uneven distribution of NIH and NSF funded research and inconspicuous heterogeneity across fields, the patterns of the impact and dual innovation of funded research are consistent across almost all fields.
