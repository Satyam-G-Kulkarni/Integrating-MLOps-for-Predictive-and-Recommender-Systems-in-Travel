# Flight Price Prediction — MLOps Pipeline

A machine learning project for predicting flight ticket prices, containerized with Docker and orchestrated with Kubernetes, with MLflow experiment tracking integration in progress.

---

## Overview

Flight pricing is dynamic and influenced by multiple factors — route, airline, booking window, seasonality, and more. This project builds a regression pipeline to predict flight prices, compares multiple ML models with rigorous validation, and packages the solution into a containerized deployment-ready system.

---

## Tech Stack

| Component | Technology |
|---|---|
| Language | Python |
| ML Models | Linear Regression, Decision Tree, Random Forest |
| Libraries | scikit-learn, pandas, numpy, matplotlib, seaborn |
| Experiment Tracking | MLflow *(in progress)* |
| Containerization | Docker |
| Orchestration | Kubernetes |
| Notebook | Jupyter |

---

## Pipeline

```
Raw Flight Data
      │
      ▼
Data Preprocessing & Feature Engineering
(Missing value handling, encoding, scaling)
      │
      ▼
Model Training & Comparison
(Linear Regression | Decision Tree | Random Forest)
      │
      ▼
Evaluation & Validation
(MSE, RMSE, MAE, R²)
      │
      ▼
Docker Container → Kubernetes Deployment
```

---

## Model Performance

| Model | MSE | RMSE | MAE | R² |
|---|---|---|---|---|
| Linear Regression (Baseline) | 47187.19 | 217.23 | 166.21 | 0.642 |
| Linear Regression (Tuned) | 47023.26 | 216.85 | 165.35 | 0.643 |
| Random Forest (Tuned) | 18908.33 | 137.51 | 71.15 | 0.857 |

Random Forest with tuning achieves R² of **0.857**, explaining 85.7% of variance in flight prices — a significant improvement over the linear baseline.

> **Note:** Decision Tree and Random Forest baseline models showed near-perfect training metrics (R² ~0.999) due to data leakage during baseline evaluation. Tuned results with proper train-test validation are reported above.

---

## Key Findings

- **Random Forest** significantly outperforms linear models, capturing non-linear pricing patterns that linear regression cannot
- **Hyperparameter tuning** on Linear Regression yields marginal gains, confirming the problem requires non-linear modeling
- **Data leakage** was identified and corrected during baseline evaluation — an important validation step often overlooked in regression pipelines

---

## Deployment

### Run with Docker

```bash
# Build the image
docker build -t flight-price-prediction .

# Run the container
docker run -p 5000:5000 flight-price-prediction
```

### Deploy on Kubernetes

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

---

## Project Structure

```
Flight-Price-Prediction-MLOps/
├── Flight Price Prediction/    # Notebooks, models, and pipeline code
├── requirements.txt            # Python dependencies
└── README.md
```

---

## Roadmap

- [x] Flight price prediction with model comparison
- [x] Docker containerization
- [x] Kubernetes deployment configuration
- [ ] MLflow experiment tracking and model registry
- [ ] CI/CD pipeline with GitHub Actions
- [ ] REST API with FastAPI for model serving
- [ ] Model performance monitoring dashboard

---

## Author

**Satyam Kulkarni**
ML Engineer | MSc AI & ML
[LinkedIn](https://www.linkedin.com/in/satyam-kulkarni-92004215b/) • [GitHub](https://github.com/Satyam-G-Kulkarni)
