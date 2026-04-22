# Critical Reproducibility: What ML Actually Learns from MOF CO₂ Adsorption Data

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## Overview

This repository critically reproduces the study by **Li et al. (2023)** on machine learning prediction of CO₂ adsorption in metal-organic frameworks (MOFs).

### Key Findings

| Model | R² | What It Actually Measures |
|:---|:---|:---|
| Full (with P, T) | 0.90 | Thermodynamic interpolation |
| No P, T | 0.28 | MOF chemistry + confounding |
| Standard conditions only | **0.17** | **True MOF chemistry** |

### The Critical Insight

While Li et al. report R² = 0.90, **~73% of feature importance comes from Pressure and Temperature**—variables that are trivial thermodynamic controls, not MOF-specific properties.

When we fix P and T at standard conditions (298K, 100 kPa), the model explains only **17%** of variance in CO₂ uptake. This reveals the true scientific challenge: standard textural properties (BET surface area, pore volume) and metal type are insufficient to predict CO₂ capture performance.

## Repository Structure
├── MOF_CO2_Critical_Reproducibility.ipynb # Main analysis notebook
├── Table_S3.csv # Imputed dataset from Li et al.
├── data_exploration.png # Data distributions
├── feature_importance_full.png # Full model importance
├── feature_importance_chemistry.png # Chemistry-only importance
├── feature_importance_standard.png # Standard conditions importance
└── README.md

text

## Quick Start

```bash
git clone https://github.com/vahidsafarifard/MOF-CO2-Critical-Reproducibility.git
cd MOF-CO2-Critical-Reproducibility
jupyter notebook MOF_CO2_Critical_Reproducibility.ipynb
Dependencies
pandas

numpy

scikit-learn

matplotlib

seaborn

Key Lessons for ML in Materials Science
Dataset design > Algorithm choice

Always ask: "What is the model actually learning?"

Confounded variables create misleading metrics

Low R² can be more honest than high R²

Reference
Li, X., et al. (2023). Applied machine learning to analyze and predict CO₂ adsorption behavior of metal-organic frameworks. Carbon Capture Science & Technology, 9, 100146.

Author
Vahid Safarifard

License
This project is licensed under the MIT License—see the LICENSE file for details.
