# Emotion-Aware Financial Misinformation Detection

**MSc Artificial Intelligence Dissertation**
University of Manchester | Supervisor: Professor Sophia Ananiadou | 2026

## Overview

This project investigates whether incorporating explicit emotion and 
affective features improves the detection of financial misinformation 
compared to purely semantic approaches.

**Research Questions:**
- RQ1: How do emotional patterns differ between credible and misleading 
  financial content?
- RQ2: Do emotion features improve financial misinformation detection 
  over a semantic-only baseline?

## Pipeline

Input Text → Preprocessing → [Branch A: BERT/RoBERTa] + [Branch B: EmoLLaMA]
→ Feature Fusion → Classifier → True / False / NEI

## Datasets

| Dataset | Size | Labels | Source |
|---------|------|--------|--------|
| FinFact | 3,369 claims | True / False / NEI | Rangapur et al. (2025) |
| FinGuard | 5,000 articles | Real / Fake | Carlos-Martin et al. |
| RFC-Bench | 1,826 pairs | True / False | Jiang et al. (2026) |

## Models

- **Model 1 (Baseline):** Fine-tuned BERT/RoBERTa — semantic features only
- **Model 2 (Emotion-aware):** Semantic + EmoLLaMA affective features (fused)

## Results

*To be updated after experiments*

| Model | Dataset | Accuracy | F1 | Macro-F1 |
|-------|---------|----------|-----|----------|
| Baseline | FinFact | - | - | - |
| Emotion-aware | FinFact | - | - | - |

## Setup

```bash
git clone https://github.com/YOUR-USERNAME/emotion-aware-financial-misinformation-detection
pip install -r requirements.txt
```

## Key References

- Liu et al. (2025) FMDLlama — WWW 2025
- Liu et al. (2024) ConspEmoLLM — ECAI 2024
- Liu et al. (2024) EmoLLMs — SIGKDD 2024
- Rangapur et al. (2025) Fin-Fact — WWW 2025
