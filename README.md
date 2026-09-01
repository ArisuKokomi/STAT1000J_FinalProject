# Social Media Addiction Among Students

A data science final project (Group 9) exploring how social media usage relates to academic performance, sleep, mental health, and interpersonal relationships among students across different countries. The analysis combines **exploratory data analysis (EDA)**, **hypothesis testing**, and **linear regression**.

## Overview

Social media is deeply integrated into students' daily lives, but heavy usage is often linked to worse academic outcomes, poorer sleep, and lower mental well-being. This project investigates those relationships using a survey-style dataset of 705 students, aiming to answer three questions:

1. Does average daily social media usage differ between students whose academic performance is affected and those whose isn't?
2. Is social-media addiction score higher for students in "complicated" relationships than in "simple" ones?
3. Can we predict a student's addiction level from their behavior and demographics?

**Key findings**

- Instagram is the most-used platform, and students in the USA report the longest daily usage.
- Addiction score is **negatively correlated** with sleep hours and mental-health score.
- Long usage hours are associated with **lower academic performance** (permutation test rejects the null hypothesis).
- Students in complicated relationships show a **significantly higher addiction score** than those in simple relationships (t-test, p = 0.015).
- A linear model explains addiction score from conflicts-over-social-media and sleep hours:
  `AddictedScore = 1.272 × ConflictsOverSocialMedia − 0.345 × SleepHoursPerNight + 5.182`

## Repository Contents

### Data

| File | Description |
| --- | --- |
| `Students Social Media Addiction.csv` | Main dataset (705 students, 13 features). |
| `Students Social Media Addiction.xlsx` | Excel copy of the dataset (used for the F-test / t-test in Excel). |

### Notebook

| File | Description |
| --- | --- |
| `Social Media.ipynb` | **Primary analysis** — data overview, EDA, hypothesis testing (permutation test, F-test, t-test), and regression. |

### Reports & Presentation

| File | Description |
| --- | --- |
| `Final Project.pptx` | Presentation slides. |
| `Speech.docx` | Speaker script for the presentation. |
| `FinalProjectG9.zip` | Archived copy of the group project. |

### Figures

| File | Description |
| --- | --- |
| `F-Test.png`, `t-Test.png` | Excel output for the relationship-status hypothesis test. |
| `Regression.png` | Regression summary (coefficients, p-values, R²). |
| `Conflict_Fit_Plot.png`, `Conflict_Residual_Plot.png` | Fit / residual plots for `Conflicts_Over_Social_Media`. |
| `Sleep_Fit_Plot.png`, `Sleep_Residual_Plot.png` | Fit / residual plots for `Sleep_Hours_Per_Night`. |

## Dataset

13 columns, one row per student:

| Column | Type | Description |
| --- | --- | --- |
| `Student_ID` | Integer | Unique identifier per student. |
| `Age` | Integer | Student's age in years. |
| `Gender` | Categorical | Gender of the student. |
| `Academic_Level` | Categorical | Current level of study (e.g., Undergraduate, Postgraduate). |
| `Country` | Categorical | Country of residence. |
| `Avg_Daily_Usage_Hours` | Float | Average hours per day on social media. |
| `Most_Used_Platform` | Categorical | Primary platform (e.g., Instagram, TikTok). |
| `Affects_Academic_Performance` | Categorical | Whether the student thinks social media hurts their grades. |
| `Sleep_Hours_Per_Night` | Float | Average nightly sleep. |
| `Mental_Health_Score` | Integer | Mental well-being, 0 (poor) – 10 (excellent). |
| `Relationship_Status` | Categorical | Single / In a relationship / Complicated. |
| `Conflicts_Over_Social_Media` | Integer | Arguments/issues caused by social-media use. |
| `Addicted_Score` | Integer | Addiction level, 1 – 10 (higher = more addicted). |

## Methodology

1. **EDA** — distributions of demographics and addiction score; average addiction by age, academic level, gender, country, and relationship status; correlations between usage, sleep, and mental health.
2. **Hypothesis testing**
   - *Academic performance vs. usage hours* — a permutation test (5,000 shuffles) on the difference in group means.
   - *Relationship status vs. addiction score* — an F-test for equal variances, followed by a two-sample t-test assuming equal variances.
3. **Predictive modeling**
   - *Regression* — ordinary least squares predicting `Addicted_Score` from `Conflicts_Over_Social_Media` and `Sleep_Hours_Per_Night` (chosen to reduce multicollinearity).

## Dependencies

- Python 3
- `numpy`, `pandas`, `matplotlib`, `seaborn`
- Microsoft Excel (for the F-test / t-test calculations)

## How to Run

1. Clone the repository and open `Social Media.ipynb` in Jupyter (or VS Code).
2. Ensure `Students Social Media Addiction.csv` is in the same directory as the notebook.
3. Run the cells top-to-bottom.
