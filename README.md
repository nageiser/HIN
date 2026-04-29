# HIN: A/B Testing for Subscription Service Churn & Conversion

Code repository for the Erdös Institute UX Bootcamp, Spring 2025, Project 3.  
**Group HIN:** Han Wang, Issrar Chamekh, and Nicholas Geiser

---

## Project Overview

This project analyzes the effect of a marketing intervention on subscription service outcomes using two complementary approaches:

1. **Real-world A/B test** — revenue data from an existing controlled experiment (Kaggle) is used to test whether the variant treatment produced higher mean revenue than the control.
2. **Synthetic survey analysis** — a simulated subscriber survey (n = 2,000) models churn behavior, satisfaction, NPS, and internal/external factors. A simulated A/B test on this data tests whether the variant group achieves higher conversion rates (5.51% → 7.62%) and greater annual plan adoption.

Key statistical methods: Welch's t-test, Mann-Whitney U test, permutation test, Fisher's exact test, chi-square tests of association, Cochran-Armitage trend test, Somers' D, covariate balance checks (SMDs + Bonferroni-corrected chi-square).

---

## Repository Structure

```
HIN/
├── FinalTesting/
│   └── AB_testing_v2.ipynb   # Primary analysis notebook (start here)
├── InitialModels/
│   ├── ABtesting.ipynb        # Initial exploration of real Kaggle revenue data
│   └── ABtesting_issrar copy.ipynb  # Draft / scratchpad
├── environment.yml            # Conda environment specification
└── README.md
```

**Recommended execution order:**
1. `InitialModels/ABtesting.ipynb` — data cleaning and initial hypothesis tests on real revenue data
2. `FinalTesting/AB_testing_v2.ipynb` — synthetic survey generation, covariate balance, and final A/B test

---

## Setup

### 1. Clone the repository

```bash
git clone <repo-url>
cd HIN
```

### 2. Create and activate the conda environment

```bash
conda env create -f environment.yml
conda activate hin
```

### 3. Configure Kaggle API credentials

Both notebooks fetch data programmatically from Kaggle using `kagglehub`. You must have a Kaggle account and API token configured before running them.

1. Log in to [kaggle.com](https://www.kaggle.com) and go to **Account → API → Create New Token**.
2. This downloads a `kaggle.json` file. Place it at:
   - macOS/Linux: `~/.kaggle/kaggle.json`
   - Windows: `%USERPROFILE%\.kaggle\kaggle.json`
3. Set permissions (macOS/Linux only):
   ```bash
   chmod 600 ~/.kaggle/kaggle.json
   ```

The dataset used is [`sergylog/ab-test-data`](https://www.kaggle.com/datasets/sergylog/ab-test-data) (`AB_Test_Results.csv`).

### 4. Launch Jupyter and run the notebooks

```bash
jupyter notebook
```

---

## Data

Raw data is **not committed** to this repository. It is downloaded automatically at runtime via `kagglehub` (see credentials setup above). The `.gitignore` excludes `*.csv` and `*.json` files.

The synthetic survey data in `FinalTesting/AB_testing_v2.ipynb` is generated with `numpy.random.seed(42)` and requires no external data source.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
