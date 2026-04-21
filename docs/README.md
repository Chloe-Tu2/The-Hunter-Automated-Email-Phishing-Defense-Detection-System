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
| **Duration** | 3–5 minutes |
| **Format** | MP4 video |
| **In GitHub** | Included (large file — may require Git LFS if re-uploaded) |

**What it shows:**
This is the full project demonstration video required by the ITAI 2376 assignment.
It covers all four required demo scenarios:

1. Launching the Gradio web dashboard locally
2. Submitting a **clear phishing email** — the pipeline returns a QUARANTINE verdict
3. Submitting a **clean legitimate email** — the pipeline returns an ALLOW verdict
4. Submitting an **ambiguous borderline email** — Agent 2 escalates to deep analysis
5. Demonstrating **repeat offender escalation** — the same sender previously flagged
   is automatically escalated by Agent 3 via SQLite Threat Memory

The video includes narration explaining each agent's role, the risk score computed
by the BiLSTM ensemble, and how the 4-tier defense policy is applied.

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
