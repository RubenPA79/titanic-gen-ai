# 🚢 Titanic Reimagined: GenAI & Viral Features

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![Status](https://img.shields.io/badge/Status-Viral-FF4B4B)
![Kaggle](https://img.shields.io/badge/Kaggle-Top%20Percentile-20BEFF?logo=kaggle&logoColor=white)

> **"Data Science isn't just about accuracy. It's about the story hidden in the missing values."**

Welcome to a **reimagined case study** of the classic Titanic dataset. Instead of the standard "fill with mean" approach, this project uses **GenAI-inspired logic** and **Explainable AI (XAI)** to uncover the real social dynamics of survival.

---

## 🧠 The GenAI Touch: "Smart Imputation"

Most kernels fill missing `Age` with the global average. We asked: *Can the title tell us the age?*

In `1_data_wrangling.ipynb`, we implement a logic that treats `Master` (children), `Miss` (young women), and `Dr` (educated adults) differently.

| Title | Imputed Age | Logic |
| :--- | :--- | :--- |
| **Master** | ~4.0 years | Always a child |
| **Miss** | ~21.0 years | Unmarried, usually younger |
| **Mrs** | ~35.0 years | Married, likely older |
| **Dr** | ~46.0 years | Professionals |

---

## 🧬 Viral Feature: "Did your family make it?"

Survival wasn't random—it was tribal. In `2_advanced_features.ipynb`, we engineered the **`Family_Survival_Rate`**.

Instead of looking at individuals, we grouped passengers by **Surname** and **Ticket**.
*   If your family survived, your chance of survival skyrocketed.
*   If your group perished (like the "Sage" family with 11 members), your odds dropped to near zero.

---

## 🔮 Explainable AI (XAI)

We don't trust black boxes. Using **SHAP (SHapley Additive exPlanations)** in `3_modeling_xai.ipynb`, we proved that **Family Survival Rate** forces the model's decision more than Class or Fare for many passengers.

### 🎨 Visual Insights
Run the notebooks to generate the **Interactive EDA** (`interactive_eda.html`) to explore the clusters of survival by Age vs Price.

---

## 🚀 How to Reproduce

1.  **Clone the repo**
    ```bash
    git clone https://github.com/RubenPA79/titanic-gen-ai.git
    cd titanic-gen-ai
    ```

2.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the analysis**
    ```bash
    # Run all notebooks to generate data and models
    jupyter nbconvert --to notebook --execute 1_data_wrangling.ipynb
    ```

---

> "Data confirms what history forgot: on the Titanic, people didn't die by class, they died by heart. My model captures that bond."
*Built with ❤️ and 🤖 using Antigravity IA methodology.*
