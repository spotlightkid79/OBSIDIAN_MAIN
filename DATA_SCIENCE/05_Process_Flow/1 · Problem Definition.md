---
id: "nmr50lpktg4wp"
parent: null
position_x: 
position_y: 
color: null
---
# 1 · Problem Definition

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process

## What it is
Translate a business question into a **measurable** ML problem. Decide: regression vs classification, target variable, success metric, baseline, constraints (latency, interpretability).

## Key idea
"Reduce churn" → "predict probability a customer churns next 30 days, optimize for ROC-AUC ≥ 0.80, with model running daily on the warehouse."

## Checklist
- [ ] Stakeholders & decisions the model will inform
- [ ] Target variable + how it's labeled
- [ ] Success metric ([[Classification Model Evaluation]])
- [ ] Baseline (current rule / heuristic)
- [ ] Latency / cost / interpretability constraints

## Related
- [[CRISP-DM]] · next → [[2 · Data Collection]]
