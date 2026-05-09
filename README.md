# 🏋️ AI-Driven Personalised Fitness Coach

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-app-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![Course](https://img.shields.io/badge/AI-AL--2002-7F77DD?style=flat)
![Team](https://img.shields.io/badge/Team-3%20members-63992?style=flat)

An intelligent fitness assistant that generates, adapts, and optimises personalised workout and nutrition plans using **Genetic Algorithms**, **Bayesian Networks**, **K-Means Clustering**, and **Supervised Classification**.

---

## Overview

Most people rely on generic workout plans that ignore individual differences in fitness level, recovery capacity, and goals. This system bridges that gap — it takes a user's profile and applies four distinct AI techniques to produce a personalised, evolving weekly plan that adapts based on weekly feedback.

---

## System Flow

```
User Profile → Classifier → K-Means Cluster → Genetic Algorithm → Injury Check → Final Plan
```

| Step | Component | Description |
|------|-----------|-------------|
| 1 | User Profile | Age, weight, height, fitness level, goal, available days |
| 2 | Supervised Classifier | Predicts optimal plan category (Weight Loss / Muscle Gain / Endurance) |
| 3 | K-Means Clustering | Groups user into a fitness archetype with peer benchmarking |
| 4 | Genetic Algorithm | Evolves a personalised 7-day workout plan |
| 5 | Bayesian Network | Checks injury risk and adjusts volume if needed |
| 6 | Final Plan | Displayed to user with diet tips and progress tracking |

---

## AI Techniques

### 🧬 Genetic Algorithm — `Lab 6`
Evolves a population of candidate 7-day workout plans using selection, crossover, and mutation. The fitness function rewards goal alignment, balanced muscle group coverage, and adequate rest days.

### 🔵 K-Means Clustering — `Lab 11`
Groups users into fitness archetypes — **Beginner**, **Intermediate**, **Advanced** — using unsupervised learning on 200 synthetic user profiles, with peer benchmarking stats shown per cluster.

### 📊 Supervised Classification — `Lab 11`
A Decision Tree classifier predicts the most suitable plan category from user input features like age, weight, fitness level, and available training days.

### ❤️ Bayesian Network — `Lab 9`
Models injury probability as a function of training volume, sleep hours, soreness score, and consecutive training days. Outputs a **Low / Medium / High** risk rating and reduces volume automatically when risk is High.

---

## Installation & Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/fitness-coach-ai.git
cd fitness-coach-ai

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch the app
streamlit run app.py
```

---

## Project Structure

```
fitness-coach/
├── app.py                  # Main Streamlit entry point
├── genetic_algorithm.py    # GA plan generation
├── clustering.py           # K-Means user profiling
├── classifier.py           # Plan category prediction
├── bayesian.py             # Injury risk Bayesian network
├── data/                   # Synthetic user dataset (auto-generated)
├── logs/                   # Weekly user progress CSVs
├── requirements.txt
└── README.md
```

---

## Libraries

| Library | Purpose |
|---------|---------|
| `numpy` / `pandas` | Data handling and numerical operations |
| `scikit-learn` | K-Means clustering, Decision Tree classifier |
| `pgmpy` | Bayesian Network construction and inference |
| `matplotlib` / `seaborn` | Progress charts and EDA visualisations |
| `streamlit` | Interactive user interface |

Install all at once:

```bash
pip install numpy pandas scikit-learn pgmpy matplotlib seaborn streamlit
```

---

## App Pages

- **Home** — User profile input form
- **My Plan** — Generated 7-day workout plan + diet suggestion
- **Injury Check** — Bayesian risk assessment with sliders
- **Progress** — Weekly volume bar chart from logged data

---

## Team

| Name | Student ID |
|------|------------|
| Abeeha Binte Aamer | 24K-0940 |
| Laiba Khan | 24K-0644 |
| Aamna Rizwan | 24K-0695 |

**Course:** Artificial Intelligence — AL-2002  
**Instructor:** Ms. Suraksha Sadhwani  
**Institution:** Namal University · 2026

---

## Submission Checklist

- [x] Project folder with all source files
- [x] `requirements.txt`
- [x] Word report (methodology, flow, screenshots)
- [x] Member contributions section in report
- [x] System flow diagram
- [x] `README.md`

---

> *No external dataset needed — synthetic training data is generated inside the code itself.*
