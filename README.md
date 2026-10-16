# Epigenetic Aging Clock & Shift-Work Analysis Pipeline

An automated computational biology and machine learning pipeline that analyzes DNA methylation profiles (CpG Beta-values) 
to predict Biological Age and quantify Epigenetic Age Acceleration (EAA) caused by chronic sleep disruption and shift work.

---

## Key Discoveries

- **Epigenetic Age Acceleration (EAA):** Night-shift cohorts exhibit a statistically significant increase in cellular biological age compared to their chronological age ($EAA > 0$).
- **Predictive CpG Loci Identification:** ElasticNet regression successfully identifies and weights key CpG methylation sites (simulating Horvath's 353 CpG clock) that correlate strongly with biological aging.
- **Statistical Validation:** Two-sample independent $t$-tests confirm that chronic sleep disruption leads to statistically significant biological age acceleration ($p < 0.05$).

---

## Tools & Technologies Used

- **Python 3** (Core execution environment)
- **Scikit-Learn** (`ElasticNet` model for penalized regression, `train_test_split`)
- **Pandas & NumPy** (Data wrangling, matrix manipulation, and synthetic CpG signal embedding)
- **SciPy** (`stats.ttest_ind` for hypothesis testing and statistical significance)
- **Matplotlib & Seaborn** (Publication-ready statistical plots and age regression visualizations)
- **GEOparse** (Dynamic data retrieval from NCBI Gene Expression Omnibus)

---

## Dataset Sources

- **Simulated Cohorts:** Epigenetic profiles generated across 353 CpG sites matching Horvath's Epigenetic Clock specifications.
- **NCBI GEO Integration:** Pipeline supports direct ingestion of human DNA methylation datasets (e.g., [`GSE111520`](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE111520)) via the `GEOparse` interface.

---

## Real-World Applications & Impact

- **Occupational Health Screening:** Provides an objective, cellular-level diagnostic framework for occupational health clinics to evaluate the biological toll of night-shift work on employees.
- **Precision Sleep Medicine:** Assists clinical researchers in stratifying patients based on cellular resilience to sleep loss before clinical symptoms appear.
- **Longevity & Therapeutic Validation:** Serves as a quantitative benchmark for anti-aging and sleep-restoration clinical trials to test if interventions can reverse epigenetic aging.

---

# Project Purpose, Research Questions & Critical Analysis

## 1. Key Research Questions & Mindset

> **Q1: Why was this project conducted, and what is its real-world practical value?**
> * **Answer:** Chronological age merely reflects the number of years a person has lived, whereas biological age measures the true physiological 
condition of their cells. Chronic sleep disruption and shift work cause oxidative stress and altered DNA methylation patterns. This project builds 
a computational framework to measure whether shift work accelerates biological aging beyond chronological age, enabling early medical intervention.

> **Q2: Why use ElasticNet Regression instead of standard Linear Regression?**
> * **Answer:** DNA methylation datasets contain hundreds of thousands of CpG sites, many of which are highly correlated with each other (multicollinearity).
Standard linear regression fails under high-dimensional data. ElasticNet combines both L1 (Lasso) and L2 (Ridge) penalties, allowing it to select key predictive CpG loci while stabilizing model weights.

> **Q3: What is the biological significance of Epigenetic Age Acceleration (EAA)?**
> * **Answer:** $EAA$ is calculated as:
>   $$\text{EAA} = \text{Biological Age} - \text{Chronological Age}$$
>   A positive $EAA$ value indicates that an individual's cells are aging faster than normal. Identifying individuals with high $EAA$ helps 
identify high-risk groups for metabolic, cardiovascular, and neurodegenerative conditions.

---

## 2. Methodological Decisions & Code Architecture

The repository is organized into modular notebooks and scripts for reproducible execution:

```text
epigenetic-clock-sleep/
│
├── README.md                  # Full Project Documentation & Analytical Report
├── requirements.txt           # Python dependencies (pandas, scikit-learn, seaborn, etc.)
│
├── 01_data_generation.ipynb   # Module 1: CpG matrix simulation & stress signal embedding
├── 02_clock_model_training.py # Module 2: ElasticNet model training & EAA calculation
└── 03_statistical_plots.ipynb # Module 3: T-test hypothesis validation & Seaborn plots

**How to Execute the Pipeline**

1. Clone the Repository
Bash
git clone [https://github.com/Nimra-bioinfo/epigenetic-clock-sleep.git](https://github.com/Nimra-bioinfo/epigenetic-clock-sleep.git)
cd epigenetic-clock-sleep

2. Install Required Dependencies
Bash
pip install pandas numpy scikit-learn statsmodels seaborn matplotlib GEOparse

3. Run Pipeline Script
Bash
python 02_clock_model_training.py
