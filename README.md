# AI-Driven Personalised Fitness Coach

An intelligent system that generates, optimises, and adapts personalised weekly workout plans using a combination of classical AI search/optimisation techniques and machine learning.

## Overview

Most generic workout plans ignore individual differences in fitness level, recovery capacity, and goals, often leading to poor results or injury. This project builds an adaptive fitness coach that combines multiple AI paradigms — supervised learning, unsupervised clustering, graph search, constraint satisfaction, genetic algorithms, and Bayesian networks — into a single pipeline that produces a personalised, injury-aware weekly workout plan from a user's profile data.

## Pipeline

1. **Exploratory Data Analysis** — Fitbit-style activity and sleep data (`dailyActivity_merged.csv`, `sleepDay_merged.csv`) are cleaned, merged, and visualised (step distribution, calories vs. steps, sleep distribution, activity-level breakdown, sleep vs. activity correlation).
2. **User Profiling (KNN)** — A K-Nearest Neighbors classifier predicts a user's ideal plan category (weight loss / muscle gain / endurance) from age, weight, BMI, active minutes, and weekly workout count.
3. **Fitness-Level Clustering (K-Means)** — Users are grouped into beginner / intermediate / advanced archetypes based on activity level, workout frequency, and BMI.
4. **Weekly Schedule Generation (Genetic Algorithm)** — A population of candidate 7-day workout schedules is evolved using tournament selection, single-point crossover, and mutation, optimising for goal alignment, muscle-group balance, and adequate rest.
5. **Exercise Selection (Graph Search: A\* / BFS)** — For each scheduled workout type (e.g. legs, chest/back), exercises are selected by searching an exercise-dependency graph, using a heuristic that prioritises covering all target muscle groups for the user's goal.
6. **Weekly Scheduling Demo (CSP)** — A standalone constraint satisfaction model assigns workout types to days of the week as an alternative illustration of scheduling (the main pipeline uses the Genetic Algorithm for this).
7. **Injury Risk Assessment (Bayesian Network)** — A Bayesian Network estimates injury risk (Low / Medium / High) from training volume, sleep quality, and soreness, using `pgmpy` for inference. If risk is High, the plan is automatically trimmed.
8. **Interactive Interface (Gradio)** — A Gradio app lets a user enter their profile and get a generated weekly plan along with their predicted goal, fitness level, and injury risk.

## AI Techniques Used

| Technique | Role |
|---|---|
| K-Nearest Neighbors | Predicts the user's plan category from profile features |
| K-Means Clustering | Groups users into fitness-level archetypes |
| Graph Search (A* / BFS) | Selects a coherent sequence of exercises per workout day |
| Constraint Satisfaction Problem | Demonstrates day-of-week workout-type scheduling |
| Genetic Algorithm | Evolves and optimises the 7-day weekly schedule |
| Bayesian Network | Predicts injury risk from training load, sleep, and soreness |
| EDA & Visualisation | Analyses activity/sleep data trends |

## Tech Stack

- **Python 3.x**
- **NumPy / Pandas** — data handling and feature engineering
- **Matplotlib / Seaborn** — EDA visualisations
- **Scikit-learn** — KNN classifier, K-Means clustering, preprocessing, train/test split
- **python-constraint** — CSP scheduling demo
- **pgmpy** — Bayesian Network construction and inference
- **Gradio** — interactive web interface

## Project Structure

```
.
├── main.ipynb                 # Full pipeline: EDA → ML → GA → graph search → Bayesian network → Gradio UI
├── dailyActivity_merged.csv   # Input: daily activity data
├── sleepDay_merged.csv        # Input: daily sleep data
└── README.md
```

## Setup & Usage

1. Place `dailyActivity_merged.csv` and `sleepDay_merged.csv` in the same folder as `main.ipynb` (the notebook auto-detects whether it's running in VS Code or Google Colab).
2. Install dependencies:
   ```
   pip install numpy pandas matplotlib seaborn scikit-learn pgmpy python-constraint gradio
   ```
3. Run all cells in `main.ipynb` from top to bottom. Missing optional packages (`python-constraint`, `pgmpy`, `gradio`) are installed automatically by the notebook if not already present.
4. The final cell launches a Gradio app where you can enter your age, weight, height, activity level, and weekly workout count, plus recovery indicators (training intensity, sleep quality, soreness), and receive:
   - Your predicted goal category and fitness level
   - A generated 7-day workout plan
   - An injury risk assessment, with the plan automatically adjusted if risk is high

## Output

- A personalised 7-day workout plan (exercises, organised by day and workout type)
- Predicted plan category and fitness archetype
- Injury risk score (Low / Medium / High) with automatic plan adjustment
- GA convergence chart (best/average fitness score per generation)
- EDA dashboard of activity and sleep trends
