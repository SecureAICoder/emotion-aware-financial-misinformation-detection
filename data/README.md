# Datasets

This project uses three publicly available financial misinformation datasets.
Raw data files are **not stored in this repository** due to size constraints.

## Dataset 1: FinFact
- **Source:** Rangapur et al. (2025)
- **Size:** 3,369 expert-annotated financial claims
- **Labels:** True / False / NEI (Not Enough Information)
- **Topics:** Income, Economy, Budget, Taxes, Debt
- **Download:** https://github.com/IIT-DM/Fin-Fact
- **Load in notebook:**
```python
import pandas as pd, requests, json
url = "https://raw.githubusercontent.com/IIT-DM/Fin-Fact/main/finfact.json"
lines = requests.get(url).text.strip().split('\n')
finfact_df = pd.DataFrame([json.loads(l) for l in lines])
```

## Dataset 2: FinGuard
- **Source:** Carlos-Martin et al.
- **Size:** 5,000 financial news articles
- **Labels:** Real / Fake
- **Download:** https://github.com/carlos-gmartin/Financial-Truth-Guard
- **Load in notebook:**
```python
finguard_df = pd.read_csv(
"https://raw.githubusercontent.com/carlos-gmartin/Financial-Truth-Guard/main/data/train.csv"
)
```

## Dataset 3: RFC-Bench
- **Source:** Jiang et al. (2026) — from supervisor's research group
- **Size:** 1,826 original–perturbed paragraph pairs
- **Labels:** True / False
- **Perturbation types:** Directional Flipping, Numerical Perturbation,
  Sentiment Amplification, Causal Distortion
- **Hosted at:** https://huggingface.co/datasets/Shreya-1912/EmotionAwareModel
- **Load in notebook:**
```python
from huggingface_hub import hf_hub_download
import json
path = hf_hub_download(repo_id="Shreya-1912/EmotionAwareModel",
                        filename="Training/train.json", repo_type="dataset")
rfc_df = pd.DataFrame(json.load(open(path)))
```

## Why these three datasets?

| Dataset | Domain | Format | Unique contribution |
|---------|--------|--------|-------------------|
| FinFact | Fact-checked claims | Short claims + evidence | 3-way classification, expert annotations |
| FinGuard | Financial news | Full articles | Binary, news-level detection |
| RFC-Bench | Stock market paragraphs | Perturbed pairs | Tests detection of *subtle* manipulation |

Using all three tests whether emotion-aware detection generalises
across different financial misinformation formats and difficulty levels.
