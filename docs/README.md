# docs/ — Project Documentation

This folder contains all project documentation: the final project writeup, the original
Midterm blueprint (both PDF and Markdown), the architecture diagram, and the demo video.

---

## Directory Structure

```
docs/
├── FN_Demo_Chloe_Tu_Team_1_ITAI2376.mp4    # 5-minute demo video (~126 MB)
├── Final/
│   └── final_project_writeup.md            # Final project technical writeup
└── Midterm/
    ├── MD_Blueprint_Tu_Chloe_Team_1_ITAI2376.md    # Midterm blueprint (Markdown)
    ├── MD_Blueprint_Tu_Chloe_Team_1_ITAI2376.pdf   # Midterm blueprint (PDF, submitted)
    └── The Hunter Architecture Diagram.png          # System architecture diagram
```

---

## File Details

### FN_Demo_Chloe_Tu_Team_1_ITAI2376.mp4

| Property | Value |
|----------|-------|
| **Size** | ~126 MB |
| **Duration** | ~5 minutes |
| **Format** | MP4 video |
| **In GitHub** | Included locally — **too large to preview on GitHub** |

> **The video file is ~126 MB and cannot be previewed directly on GitHub.**
> **Use the Google Drive link below to stream it in your browser:**

### [Watch Demo Video on Google Drive](https://drive.google.com/file/d/161p0kqwoJIKhUynKDgCN5GdeUNTUhVjh/view?usp=sharing)

> *No download required — click the link above to stream the demo directly in Google Drive.*

---

**What the demo covers — step-by-step walkthrough:**

| Step | Scenario | What You Will See | Pipeline Verdict |
|------|----------|-------------------|-----------------|
| **1** | Clear phishing email | A high-urgency email with a suspicious URL is submitted — all three agents fire sequentially | **QUARANTINE** — BiLSTM score 0.9792, Agent 3 blocks delivery and alerts SOC |
| **2** | Clean legitimate email | A routine team meeting reminder is submitted — agents confirm no threat signals | **ALLOW** — Risk score 0.0, email passes to inbox |
| **3** | Ambiguous borderline email | A cautiously-phrased email triggers the ambiguity zone (0.35–0.75) — Agent 2 invokes `deep_analysis_tool` for extended LLM reasoning | **Deep analysis** — LLM reasoning supplements the BiLSTM score |
| **4** | Repeat offender escalation | An email from a previously flagged sender is submitted — Agent 3 queries SQLite Threat Memory and auto-escalates | **BLOCK** — 5 prior incidents detected, repeat offender auto-escalated |

**What the narration explains:**
- Each agent's role in the sequential pipeline (Ingest → Risk Analyst → SOC Orchestrator)
- How the **BiLSTM + Logistic Regression ensemble** produces a phishing probability score (0.0–1.0)
- How the **4-tier defense policy** (ALLOW / LOG / QUARANTINE / BLOCK) maps score ranges to actions
- How **SQLite Threat Memory** enables persistent repeat-offender detection across sessions

> **Local file:** The `.mp4` is stored at `docs/FN_Demo_Chloe_Tu_Team_1_ITAI2376.mp4` for offline viewing after cloning the repository.

---

## Final/ Subfolder

### final_project_writeup.md

| Property | Value |
|----------|-------|
| **Size** | ~13 KB / 99 lines |
| **Format** | Markdown |
| **Author** | Chloe Tu, Matthew Choo, Franck Kolontchang |

This document is the formal written component of the Final Project submission.
It addresses all required writeup sections:

| Section | Content |
|---------|---------|
| **What Our Agent Does** | Plain-language description of the three-agent pipeline for a non-technical reader |
| **Option Choice and Midterm Upgrade** | Confirms Option B (Multi-Agent System) and traces how the Midterm blueprint was implemented in full |
| **What Changed From the Midterm Blueprint and Why** | Detailed account of 6 significant changes made during development: LLM model deprecation (migrated from `llama3-8b-8192` to `llama-3.1-8b-instant`), simplified tool interfaces due to Groq schema validation issues, Groq free-tier rate limit problems, LLM hallucinating non-existent tools, added reliability guards (retry logic, cooldowns, iteration limits), and a minor spec change to the deep analysis score boost limit |
| **Agent Framework: CrewAI** | Justification for choosing CrewAI over LangGraph and AutoGen; discussion of how role-based agents enabled genuine agentic behavior |
| **Deep Learning Models and How They Fit** | Technical description of BiLSTM (Module 04 — RNN), Logistic Regression with SMOTE, ensemble weighting, threshold calibration, and Cratchley Random Forest analysis |
| **What Worked, What Did Not, and What We Would Improve** | Honest assessment: agent separation worked; infrastructure (rate limits, hallucinations, deprecated models) was the primary challenge |
| **One Thing That Surprised Us About AI Agents** | Reflection on how most debugging time went to API/infrastructure issues rather than agent design |

---

## Midterm/ Subfolder

### MD_Blueprint_Tu_Chloe_Team_1_ITAI2376.pdf

| Property | Value |
|----------|-------|
| **Size** | ~565 KB |
| **Format** | PDF (submitted to Canvas for Midterm) |
| **Purpose** | The original ITAI 2376 Midterm blueprint — the paper design that the Final Project implements |

This is the graded Midterm submission. It documents the full architectural plan
developed before any code was written, including the three-agent design, tool
assignments, dataset selection, 6-week build plan, and deep learning connections
to course modules (Modules 02, 04, and 05).

### MD_Blueprint_Tu_Chloe_Team_1_ITAI2376.md

| Property | Value |
|----------|-------|
| **Size** | ~27 KB |
| **Format** | Markdown |
| **Purpose** | Markdown source of the Midterm blueprint (GitHub-readable version) |

This is the same content as the PDF above, formatted as Markdown so it renders
directly on GitHub. This is the version referenced internally from the README.

### The Hunter Architecture Diagram.png

| Property | Value |
|----------|-------|
| **Size** | ~436 KB |
| **Format** | PNG image |
| **Dimensions** | High resolution — suitable for embedding in documents and presentations |
| **Embedded in** | Root `README.md` — Architecture Overview section |

This diagram illustrates the full system architecture of The Hunter, showing:

- The **three-agent sequential pipeline** (Email Ingest Specialist → Phishing Risk Analyst → SOC Orchestrator)
- The **five CrewAI tools** and which agent owns each tool
- The **BiLSTM + LogReg ensemble** as the scoring core inside Agent 2
- The **SQLite Threat Memory** database connected to Agent 3
- The **4-tier defense policy** (ALLOW / ALLOW AND LOG / FLAG WITH WARNING / QUARANTINE)
- The **Gradio web interface** as the user-facing entry point

The diagram was created for the Midterm blueprint and updated to reflect the final
implementation. It is the same diagram required by the ITAI 2376 assignment and
embedded in the root-level `README.md`.

![The Hunter Architecture Diagram](The%20Hunter%20Architecture%20Diagram.png)
