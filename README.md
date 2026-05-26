# Hotel Booking Cancellation Risk Prediction

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-0F766E?style=for-the-badge)
![Random Forest](https://img.shields.io/badge/Random%20Forest-2563EB?style=for-the-badge)
![Project Completed](https://img.shields.io/badge/Project-Completed-16A34A?style=for-the-badge)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter%20Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

## Key Results

- Random Forest achieved 88% accuracy.
- ROC-AUC reached 0.94.
- Nearly 1 in 3 bookings were cancelled.
- Lead time was a major cancellation-risk signal.
- Model supports occupancy and revenue planning.

## Business Problem

Hotel cancellations create operational and revenue uncertainty. When a customer cancels close to the stay date, hotels can lose expected revenue, misallocate rooms, and make weaker staffing, pricing, and inventory decisions.

This project uses machine learning to predict whether a booking is likely to be canceled so hotel teams can identify high-risk reservations earlier and take targeted action.

## Project Objective

Build a cancellation-risk prediction model using hotel booking, customer, pricing, stay, and channel-related features. The goal is to support proactive business decisions such as customer follow-up, confirmation reminders, retention offers, and cancellation policy review.

## Dataset Overview

| Item | Value |
|---|---:|
| Cleaned bookings used for modeling | 36,248 |
| Cancellation rate | 32.8% |
| Target variable | `is_canceled` |
| Final model | Random Forest |
| Final accuracy | 88% |
| Final ROC-AUC | 0.94 |

The original dataset is not included in this repository. See [data/README.md](data/README.md) for placement instructions.

## Project Preview

### Project Workflow

![Project workflow](assets/project_workflow.svg)

### Feature Importance

![Top 15 feature importance - Random Forest](assets/charts/notebook_chart_21.png)

## Workflow

1. Import required libraries
2. Load the hotel booking dataset
3. Inspect data structure, missing values, and date quality
4. Remove invalid reservation dates
5. Perform exploratory data analysis
6. Engineer booking-level features
7. Create the cancellation target variable
8. Split data into training and test sets
9. Fit preprocessing only on the training set
10. Apply SMOTE only to the training set
11. Train and compare classification models
12. Select the best model using ROC-AUC
13. Evaluate final model performance
14. Interpret business insights and recommendations

## Tools and Libraries

| Category | Tools |
|---|---|
| Language | Python |
| Notebook | Jupyter Notebook |
| Data manipulation | pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Preprocessing | RobustScaler, OneHotEncoder |
| Class balancing | SMOTE |
| Machine learning | scikit-learn |
| Model saving | joblib |

## EDA Summary

The exploratory analysis reviewed cancellation behavior across booking status, market segment, lead time, average price, and reservation month. The cleaned dataset contained 36,248 bookings after invalid reservation dates were removed.

Key patterns from the notebook:

| Area | Business Insight |
|---|---|
| Target distribution | Cancellations represented 32.8% of cleaned bookings. |
| Market segment | Online bookings showed the highest cancellation rate among major segments at approximately 36.5%. |
| Seasonality | Cancellation rates varied by booking month, with higher cancellation rates in several mid-year months. |
| Lead time | Lead time was treated as an important risk signal because customers booking further in advance may have more opportunity to cancel. |
| Price and requests | Average price and special requests were included as booking behavior indicators. |

## Feature Engineering Summary

The notebook created and prepared features suitable for classification:

| Feature Area | Transformation |
|---|---|
| Guest composition | Created `total_guests` from adult and child counts. |
| Stay duration | Created `total_nights` from weekend and week-night stays. |
| Reservation date | Extracted booking month, day, and year. |
| Target | Converted booking status into `is_canceled`. |
| Numeric preprocessing | Applied RobustScaler to numeric features. |
| Categorical preprocessing | Applied OneHotEncoder to categorical features. |
| Class imbalance | Applied SMOTE only to the training data. |

The workflow avoided data leakage by splitting the data before scaling, encoding, and SMOTE resampling.

## Skills Demonstrated

- Data cleaning
- Exploratory data analysis
- Feature engineering
- Classification modeling
- Model evaluation
- Business analytics storytelling
- Revenue and occupancy decision support

## Models Tested

The project compared four supervised classification models:

| Model |
|---|
| Logistic Regression |
| Decision Tree |
| Random Forest |
| Gradient Boosting |

## Model Performance

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Random Forest | 0.884 | 0.819 | 0.829 | 0.824 | 0.941 |
| Gradient Boosting | 0.824 | 0.706 | 0.797 | 0.749 | 0.908 |
| Logistic Regression | 0.779 | 0.635 | 0.769 | 0.695 | 0.861 |
| Decision Tree | 0.858 | 0.766 | 0.816 | 0.790 | 0.849 |

Random Forest was selected as the final model because it achieved the strongest ROC-AUC score.

## Final Model Results

| Metric | Result |
|---|---:|
| Best model | Random Forest |
| Accuracy | 88% |
| ROC-AUC | 0.94 |
| True negatives | 4,437 |
| False positives | 436 |
| False negatives | 407 |
| True positives | 1,970 |

Confusion matrix:

| Actual / Predicted | Not Canceled | Canceled |
|---|---:|---:|
| Not Canceled | 4,437 | 436 |
| Canceled | 407 | 1,970 |

## Business Interpretation

The Random Forest model correctly identified a large share of both non-canceled and canceled bookings. The ROC-AUC of 0.94 indicates strong ability to rank bookings by cancellation risk.

From a business perspective, the model can help hotel teams:

| Use Case | Value |
|---|---|
| Identify high-risk bookings | Prioritize outreach and confirmation workflows. |
| Reduce missed cancellations | Act earlier on bookings likely to cancel. |
| Improve revenue planning | Support more informed room inventory and pricing decisions. |
| Segment risk by channel | Monitor higher-risk booking sources such as online channels. |
| Support policy decisions | Apply targeted retention or stricter policy rules during higher-risk periods. |

## Business Recommendations

1. Monitor bookings with long lead times and use automated reminders or confirmation checks before arrival.
2. Pay close attention to online bookings because the notebook shows higher cancellation behavior in that segment.
3. Use cancellation-risk scores to trigger targeted customer retention actions, such as confirmation calls, reminders, or non-refundable discount offers.
4. Review cancellation policies during months with higher cancellation rates.
5. Use important model features such as lead time, average price, special requests, and market segment to support revenue management decisions.

## Future Improvements

- Deploy the model as a dashboard or web app.
- Validate the model on newer booking data.
- Build an automated cancellation-risk monitoring dashboard.
- Add real-time booking and pricing signals.
- Test additional models or hyperparameter tuning.

## Final Conclusion

This project shows how machine learning can translate hotel booking data into actionable cancellation-risk intelligence. With 88% accuracy, 0.94 ROC-AUC, and strong performance across both canceled and non-canceled bookings, the Random Forest model provides a practical foundation for earlier intervention, more reliable occupancy forecasting, and stronger revenue planning.

The model should be treated as a decision-support tool rather than an automated decision-maker. In a business setting, its value would come from combining risk scores with operational rules for outreach, retention offers, room inventory planning, and cancellation policy review.

## How to Run the Notebook

1. Clone or download this repository.
2. Create and activate a Python virtual environment.
3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Place the dataset file named `booking.csv` in the notebook folder or repository root.
5. Open the notebook:

```bash
jupyter notebook notebooks/Booking_Cancellation_New.ipynb
```

6. Run the notebook cells from top to bottom.

## Repository Structure

```text
hotel-booking-cancellation-prediction/
├── README.md
├── requirements.txt
├── .gitignore
├── LinkedIn_Post.txt
├── project_summary.md
├── notebooks/
│   └── Booking_Cancellation_New.ipynb
├── presentation/
│   └── Hotel_Booking_Cancellation_Prediction_Analytics_Storytelling_Improved.pptx
├── assets/
│   ├── project_workflow.svg
│   └── charts/
│       ├── notebook_chart_01.png
│       ├── notebook_chart_21.png
│       └── ...
└── data/
    └── README.md
```
