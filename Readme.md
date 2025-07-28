# Pharmacovigilance Adverse‑Event Summarizer  
*An MVP that turns raw drug‑safety reports into clear, GraphQL‑queryable insights powered by vLLM*

---

## What this repo contains
| Layer | What it does | Key Tech |
|-------|--------------|----------|
| **Data & Stats** | Normalises free‑text adverse‑event reports to MedDRA‑like terms and calculates a proportional‑reporting‑ratio (PRR) signal for every *(drug, event)* pair | `pandas`, `psycopg2`, Python |
| **Storage** | Persists raw cases and aggregated signals | PostgreSQL |
| **API** | Exposes data through a typed GraphQL schema; the `summary` field lazily calls an LLM via vLLM | FastAPI + Strawberry |
| **LLM Service** | Generates regulator‑toned, one‑paragraph safety narratives; ready for LoRA domain‑finetuning | vLLM (serving Mistral‑7B/Llama 3 with optional LoRA adapters) |
| *(Optional)* **UI** | Simple Streamlit demo to explore top signals | Streamlit |




## Why this matters

Manual pharmacovigilance is drowning in unstructured, inconsistent text.  
This MVP automatically **cleans, codes, scores and summarises** reports so safety scientists and regulators spot true safety signals earlier—protecting patients while reducing human triage load.
