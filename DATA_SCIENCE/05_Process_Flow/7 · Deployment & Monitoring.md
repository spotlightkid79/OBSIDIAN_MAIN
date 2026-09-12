---
id: "nmr50lpkthmbh"
parent: null
position_x: 
position_y: 
color: null
---
# 7 · Deployment & Monitoring

**Folder:** [[🔄 05 · Process Flow]] · **Topic:** #process #mlops

## What it is
Ship the model: batch scoring, REST API (FastAPI), or embedded in an app. Then **monitor**: latency, error rate, prediction drift, data drift, business KPI.

## Key idea
Models decay. Without monitoring, you won't know until the business notices.

## Python
```python
# Save / load
import joblib
# joblib.dump(model, "model.pkl")
# loaded = joblib.load("model.pkl")
# Serve with FastAPI:
# from fastapi import FastAPI
# app = FastAPI()
# @app.post("/predict")
# def predict(features: list[float]): return {"y": loaded.predict([features]).tolist()}
```

## Related
- [[6 · Evaluation]]
- [[Plotly]] (dashboards)
- [[CRISP-DM]] (loop back)
