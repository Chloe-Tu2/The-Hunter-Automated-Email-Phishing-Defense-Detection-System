# notebooks/ — Jupyter Notebooks

This folder contains two notebooks. The first is the full training and pipeline notebook —
the primary deliverable of the project. The second is a lightweight Colab-ready demo notebook
for live demonstration without re-running training.

---

## Directory Structure

```
notebooks/
├── The Hunter-Automated Email Phishing Defense Detection System.ipynb   # Primary notebook (~1.7 MB)
└── Demo_The_Hunter_App.ipynb                                            # Colab demo notebook (~16 KB)
```

---

## File Details

### The Hunter-Automated Email Phishing Defense Detection System.ipynb

| Property | Value |
|----------|-------|
| **Size** | ~1.7 MB |
| **Runtime** | ~20–40 minutes (GPU recommended for BiLSTM training) |
| **Platform** | Google Colab (recommended) or local Jupyter |
| **Output** | Trains and saves all 5 model artifacts; runs 4-email demo pipeline |

This is the primary project notebook. It implements the full pipeline from raw data
download through model training, ensemble calibration, CrewAI agent definition, and
end-to-end demonstration. All model artifacts in the `models/` folder are generated
by running this notebook.

#### Section-by-Section Guide

| # | Section | Description |
|---|---------|-------------|
| 1 | **Project Overview** | Title, course context, team members, project summary |
| 2 | **Table of Contents** | Clickable index linking to all notebook sections |
| 3 | **Environment Setup** | Colab/local detection; `pip install` cell for all dependencies; dependency verification cell that checks package versions; all standard imports; visualization configuration (seaborn dark theme, plotly renderer); secure credential loading from `.env` or Colab Secrets; logging configuration |
| 4 | **Configuration** | Global constants (vocab size, sequence length, ensemble weights, tier thresholds); file paths for all artifacts; LiteLLM retry settings to handle Groq free-tier rate limits; CrewAI LLM configuration (`temperature=0`, `groq/llama-3.1-8b-instant`) |
| 5 | **Architecture** | Narrative description of the three-agent pipeline and how the BiLSTM ensemble feeds into it |
| 6 | **Data Acquisition - Alam Dataset** | Downloads 82,000+ email dataset from Kaggle via `kagglehub`; standardizes column names and binary labels (`1` = phishing, `0` = legitimate) |
| 7 | **Exploratory Data Analysis** | Visualization 1 — Class distribution bar chart; Visualization 2 — Text length distribution by class |
| 8 | **Feature Engineering** | Defines `extract_features()` function (char count, word count, URL count, exclaim count, urgent keyword count); applies features to full dataset; Visualization 3 — Feature correlation heatmap |
| 9 | **BiLSTM Text Model** | Tokenization (20,000 vocab, 300 max length); index-based 80/20 train/test split; builds two-layer stacked BiLSTM architecture with trainable embeddings and dropout; training loop with early stopping; Visualization 4 — Training history (accuracy + loss curves) |
| 10 | **Logistic Regression Feature Model** | SMOTE oversampling to correct class imbalance; StandardScaler fitting; LogisticRegression training on 5 engineered features |
| 11 | **Ensemble Classifier & Threshold Calibration** | Combines BiLSTM (65%) + LogReg (35%) by weighted probability average; Visualization 5 — Precision-Recall curve; threshold selection at maximum F1; Visualization 6 — Ensemble confusion matrix; saves all 5 model artifacts to `models/` |
| 12 | **Secondary Dataset Analysis - Cratchley** | Standalone Random Forest analysis on 500,000+ email Cratchley dataset; evaluates header and metadata features (domain age, DNS records, etc.) not used in the main pipeline; Visualization 7 — Top 10 feature importances |
| 13 | **CrewAI Tool Implementation** | Tool 1: `email_ingest_tool` — HTML stripping, URL normalization, 5-feature extraction; Tool 2: `phishing_classifier_tool` — runs ensemble, returns score and confidence flag; Tool 3: `deep_analysis_tool` — 6 regex phishing archetypes + 4 structural flags, boosts score up to +0.34; Tool 4: `defense_policy_tool` — maps score to 4-tier action; Tool 5: `threat_memory_tool` — SQLite read/write for repeat-offender detection; Tool unit tests for all five tools |
| 14 | **Agent Definitions** | Agent 1: Email Ingest Specialist; Agent 2: Phishing Risk Analyst; Agent 3: SOC Orchestrator — each with role, goal, backstory, tools, and iteration limits |
| 15 | **Pipeline Integration** | `run_hunter()` function wiring all agents into a `CrewAI` sequential pipeline with retry wrapper for hallucination guards |
| 16 | **Demonstration - Four Test Emails** | Defines 4 test cases: (1) clear phishing, (2) clean legitimate, (3) borderline ambiguous, (4) repeat sender |
| 17 | **Pipeline Execution** | Runs `run_hunter()` on all 4 test emails sequentially with 90-second cooldown between calls; captures terminal traces |
| 18 | **Results Display** | Formatted summary table of all 4 demo results |
| 19 | **Results & Evaluation** | Visualization 8 — Model performance comparison bar chart; Visualization 9 — Interactive risk score distribution by true label; results summary metrics table |
| 20 | **Discussion** | Analysis of results, agent behavior observations, known limitations |
| 21 | **Conclusion** | Final project summary |
| 22 | **References** | Citations for Alam Dataset, Cratchley Dataset, CrewAI, TensorFlow/Keras, Groq/LLaMA |

#### Recommended Runtime Settings (Google Colab)

Go to **Runtime → Change runtime type → Hardware accelerator: T4 GPU**.
The BiLSTM training section benefits significantly from GPU acceleration.
All other sections run on CPU.

#### Execution Order

You must run all sections in order from top to bottom. The notebook is designed
so that each section depends on variables defined in earlier sections. Do not skip
sections or re-run individual cells out of order.

---

### Demo_The_Hunter_App.ipynb

| Property | Value |
|----------|-------|
| **Size** | ~16 KB |
| **Runtime** | ~2–5 minutes |
| **Platform** | Google Colab (primary) or local Jupyter |
| **Purpose** | Launches the Gradio dashboard without re-running training |

This is a lightweight demo notebook intended for demonstration purposes only. It does
not re-train any models. Instead, it loads the pre-trained artifacts from the `models/`
folder (which must already exist) and launches `hunter_gradio_app.py`.

**Use this notebook when:**
- Demonstrating the dashboard to an audience without waiting for training
- Grading or review purposes where the trained artifacts are already available
- Running in Google Colab where you want to mount Google Drive and load cached models

**Prerequisites:**
1. The `models/` folder must contain all 5 artifacts, including the two large files
   (`bilstm_model.keras` and `tokenizer.pkl`) uploaded manually or mounted from Drive
2. `GROQ_API_KEY` must be set in Colab Secrets (left sidebar key icon) or in `.env`

**Steps:**
1. Open in Google Colab
2. Upload the `models/` folder to session storage (or mount Google Drive if stored there)
3. Add `GROQ_API_KEY` to Colab Secrets
4. Run all cells — a public `*.gradio.live` URL will appear in the output
