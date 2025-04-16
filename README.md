# Predicting Employee Departure at Salifort Motors using Machine Learning

## Project Overview

This project analyzes employee data from Salifort Motors to understand the factors influencing employee departure and to build a predictive model identifying employees likely to leave. Utilizing a dataset containing information on employee satisfaction, evaluations, workload, tenure, and demographics, various classification models were explored. A Random Forest model was ultimately selected, demonstrating strong performance in identifying key predictors of attrition. The insights derived aim to equip the Salifort Motors HR department with data-driven strategies to improve employee retention.

## Business Understanding

Salifort Motors, like many companies, faces challenges related to employee retention. High turnover rates are costly due to expenses associated with recruitment, hiring, onboarding, and lost productivity. The Human Resources (HR) department sought to move beyond anecdotal evidence and utilize data to understand the specific drivers of attrition within their workforce. The primary business problem was to identify **"What's likely to make the employee leave the company?"** Addressing this allows HR to develop targeted interventions, improve employee satisfaction, and ultimately reduce costly turnover.

## Data Understanding

The analysis used an internal dataset provided by Salifort Motors HR, containing records for approximately 15,000 employees (based on typical project data size, adjust if known). Key features included:

*   `satisfaction_level`: Employee self-reported satisfaction [0-1].
*   `last_evaluation`: Score from the last performance review [0-1].
*   `number_project`: Number of projects assigned.
*   `average_monthly_hours`: Average hours worked per month.
*   `time_spend_company` (Tenure): Years at the company.
*   `Work_accident`: Binary flag for experiencing a workplace accident.
*   `left`: Target variable, binary flag indicating if the employee left (1) or stayed (0).
*   `promotion_last_5years`: Binary flag for promotion in the last 5 years.
*   `Department`: Employee's department (categorical).
*   `salary`: Salary level (categorical, ordinal: low, medium, high).

Exploratory Data Analysis (EDA) revealed key patterns, including distinct workload profiles associated with leaving employees and potential dissatisfaction among employees with specific tenures (e.g., 4 years). Categorical features (`Department`, `salary`) were appropriately encoded for modeling. Feature engineering was employed, notably creating an `overworked` binary feature based on `average_monthly_hours` to better capture workload impact, especially after identifying potential data leakage concerns with using raw `satisfaction_level` in predictive models intended for proactive use.

<img width="1271" alt="image" src="https://github.com/user-attachments/assets/bcad75f9-4174-4bf6-a673-81047c93027b" />

<img width="1284" alt="image" src="https://github.com/user-attachments/assets/152e925c-45c3-46c2-996d-9536f6f7fee3" />

## Modeling and Evaluation

Given the binary classification task (predicting `left`), both Logistic Regression and Tree-based models (Decision Tree, Random Forest) were considered.

*   **Model Selection:** The Random Forest model demonstrated slightly superior performance compared to the Decision Tree and was chosen as the final model. It effectively handles non-linear relationships and interactions between features.
*   **Feature Importance:** The Random Forest model identified the following features as most influential in predicting employee departure:
    1.  `last_evaluation`
    2.  `number_project`
    3.  `tenure` (`time_spend_company`)
    4.  `overworked` (engineered feature)
    5.  `salary_low` (indicating lower salary level)
    6.  `work_accident`
*   **Evaluation:** The model was evaluated using metrics appropriate for classification, such as Accuracy, Precision, Recall, and F1-Score (specific scores should be mentioned if readily available from your notebook/final evaluation). Cross-validation was used during hyperparameter tuning to ensure robustness and prevent overfitting. The final model showed consistent performance between validation and test sets.

* Results on Unseen Data:

<img width="603" alt="image" src="https://github.com/user-attachments/assets/b119c01a-fad6-4d29-9026-56990b3facec" />

* Confusion Matrix:

<img width="323" alt="image" src="https://github.com/user-attachments/assets/83ee560f-8257-4f99-a09b-de0acddcc583" />

* Feature Importance

<img width="341" alt="image" src="https://github.com/user-attachments/assets/4020c793-cb57-40ef-bb7b-c84ee26f2a98" />


## Conclusion & Recommendations

The Random Forest model successfully identifies employees at risk of leaving and highlights key contributing factors. Based on the analysis and model insights, the following recommendations are proposed for Salifort Motors HR:

1.  **Manage Workload:** Cap the maximum number of projects assigned simultaneously, as `number_project` is a strong predictor. Address the `overworked` status, potentially by reviewing hour expectations or rewarding appropriately, rather than demanding excessive hours without recognition.
2.  **Address Tenure Milestones:** Investigate dissatisfaction among employees around the four-year tenure mark. Consider targeted engagement or development programs for mid-tenure employees. Promote fairly, especially for those with longer tenure.
3.  **Review Performance Evaluations:** Re-evaluate the link between long hours (`overworked`) and high `last_evaluation` scores. Ensure evaluations are fair and not solely based on hours worked. Consider proportionate rewards for significant contributions.
4.  **Improve Communication:** Clarify company policies regarding workload, overtime, and time off. Foster open communication channels (e.g., town halls, team discussions) to understand and address workplace culture concerns.

**Future Steps:** Further analysis could involve building separate models for different departments, incorporating qualitative data from exit interviews, or exploring survival analysis to predict *when* an employee might leave.

---
