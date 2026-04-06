# Contributing to The Hunter

Thank you for your interest in contributing to **The Hunter: Automated Email Phishing Defense Detection System**.

This project was developed as part of **ITAI 2376 — Deep Learning in Artificial Intelligence** at Houston City College, Spring 2026.

---

## Project Team

| Name                  | Role                        |
|-----------------------|-----------------------------|
| Chloe Tu              | Team Lead / Developer       |
| Mattew Choo           | Developer                   |
| Franck Kolontchang    | Developer                   |

---

## How to Contribute

### 1. Fork and Clone

```bash
git clone https://github.com/YOUR_USERNAME/the-hunter.git
cd the-hunter
```

### 2. Set Up Your Environment

- **Python >= 3.10** is required.
- Copy `.env.example` to `.env` and fill in your API keys (see the example file for details).
- If running locally, install dependencies:

```bash
pip install crewai>=0.102.0 tensorflow>=2.16.0 scikit-learn>=1.5.0 \
    imbalanced-learn>=0.12.0 kagglehub>=0.3.0 python-dotenv>=1.0.0 \
    plotly>=5.22.0 seaborn>=0.13.0 litellm pandas numpy matplotlib
```

- If running in **Google Colab**, the notebook handles installation automatically in the first cell.

### 3. Run the Notebook

Open `1_working_the_hunter_Notebook.ipynb` in Google Colab or Jupyter and run all cells sequentially. The notebook will:

1. Verify all dependencies
2. Load environment variables
3. Download datasets from Kaggle
4. Train the BiLSTM and Logistic Regression models
5. Build and run the three-agent CrewAI pipeline
6. Process four demonstration emails end-to-end

### 4. Make Your Changes

- Create a feature branch: `git checkout -b feature/your-feature-name`
- Keep changes focused and well-documented
- Follow the existing code style (PEP 8, SCREAMING_SNAKE_CASE for constants)
- Add comments explaining **why**, not just **what**

### 5. Submit a Pull Request

- Push your branch and open a PR against `main`
- Describe what you changed and why
- Include screenshots or output logs if the change affects agent behavior

---

## Code Style Guidelines

| Convention                  | Example                                |
|-----------------------------|----------------------------------------|
| Constants                   | `SCREAMING_SNAKE_CASE`                 |
| Functions                   | `snake_case`                           |
| Classes                     | `PascalCase`                           |
| Tool input schemas          | Pydantic `BaseModel` with `Field()`    |
| No magic numbers            | All tunable values in Configuration cell |

---

## Project Structure

```
the-hunter/
├── 1_working_the_hunter_Notebook.ipynb   # Main notebook (training + agents)
├── MD_Blueprint_TheHunter_ITAI2376_v3_Final.md  # Project blueprint
├── The Hunter Architecture V3.png        # Architecture diagram
├── README.md                             # Project overview and setup
├── LICENSE                               # MIT License
├── .env.example                          # Environment variable template
├── .gitignore                            # Git ignore rules
├── CONTRIBUTING.md                       # This file
├── data/                                 # Downloaded datasets (gitignored)
├── models/                               # Saved trained models (gitignored)
├── figures/                              # Generated plots (gitignored)
└── outputs/                              # Pipeline outputs (gitignored)
```

---

## Reporting Issues

If you find a bug or have a suggestion, please open an issue with:

- A clear description of the problem or feature request
- Steps to reproduce (if applicable)
- Your Python version and runtime environment (Colab, local, etc.)

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
