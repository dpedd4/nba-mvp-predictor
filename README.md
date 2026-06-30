# NBA MVP Predictor

A machine learning project that predicts NBA Most Valuable Player (MVP) winners using historical player statistics and team performance data from 1980 to 2025.

---

## Overview

NBA MVP voting is influenced by a combination of individual statistical dominance, team success, and narrative factors. This project builds a Random Forest classifier to identify MVP winners using historical box score statistics, advanced metrics, and team performance, then analyzes where and why the model succeeds or falls short.

---

## Dataset

Data was sourced from the **NBA Stats (1947-present)** dataset on Kaggle by Sumitro Datta.

Files used:

- **Player Award Shares.csv** — MVP voting history and winner labels
- **Player Per Game.csv** — Per-game player statistics
- **Advanced.csv** — Advanced metrics (PER, WS, BPM, VORP)
- **Team Summaries.csv** — Team win totals by season

---

## Features Used

| Feature | Description |
|---------|-------------|
| `pts_per_game` | Points per game |
| `ast_per_game` | Assists per game |
| `trb_per_game` | Total rebounds per game |
| `stl_per_game` | Steals per game |
| `blk_per_game` | Blocks per game |
| `mp_per_game` | Minutes per game |
| `g` | Games played |
| `meets_games_threshold` | 1 if player played 65+ games |
| `per` | Player Efficiency Rating |
| `ws` | Win Shares |
| `bpm` | Box Plus/Minus |
| `vorp` | Value Over Replacement Player |
| `w` | Team wins |

---

## Model

- **Algorithm:** Random Forest Classifier
- **Trees:** 100
- **Class imbalance handling:** `class_weight='balanced'`
- **Train/Test Split:** 80% / 20%
- **Random State:** 42

The balanced class weighting helps compensate for the rarity of MVP seasons (approximately 46 MVP seasons among more than 20,000 player-seasons).

---

## Results

| Metric | Score |
|---------|------:|
| AUC | **1.00** |
| MVP Precision | **0.60** |
| MVP Recall | **0.30** |

The model correctly ranked **Shai Gilgeous-Alexander** as the top MVP candidate for the 2025 season, matching the actual NBA MVP result.

---

## Key Findings

### Strengths

- Achieved a perfect **AUC of 1.00**, indicating excellent ranking ability.
- Successfully identifies statistically dominant MVP-caliber seasons.
- Advanced metrics were substantially more predictive than traditional box score statistics.
- **Win Shares (WS)**, **PER**, and **BPM** were the three most important features.

### Limitations

- MVP Recall of **0.30** indicates the model misses several historical MVP winners.
- Missed MVPs include:
  - Hakeem Olajuwon (1994)
  - Magic Johnson (1990)
  - Larry Bird (1986)
  - Tim Duncan (2002, 2003)
  - Dirk Nowitzki (2007)
- Many of these MVPs benefited from factors not included in the dataset, such as narrative, leadership, media perception, era-specific voting tendencies, and historical context.
- Performance is noticeably weaker on older-era MVPs (pre-2000), where league-wide statistical environments differed from the modern NBA.

---

## Visualizations

The project includes:

- Confusion Matrix
- ROC Curve
- Feature Importance Chart

---

## Technologies Used

- Python
- pandas
- scikit-learn
- matplotlib
- seaborn
- Jupyter Notebook

---

## Author

**David Peddapanga**  
Information Sciences & Data Science  
University of Illinois Urbana-Champaign
