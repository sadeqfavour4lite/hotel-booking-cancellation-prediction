# Project Summary: Hotel Booking Cancellation Risk Prediction

Built a machine learning project to predict hotel booking cancellations using cleaned booking, customer, pricing, stay duration, and market segment data.

The project used 36,248 cleaned bookings with a 32.8% cancellation rate. After preprocessing, feature engineering, and model comparison, Random Forest was selected as the best model, achieving 88% accuracy and 0.94 ROC-AUC.

The model correctly classified 4,437 non-canceled bookings and 1,970 canceled bookings in the test set, with 436 false positives and 407 false negatives.

Business value:

- Helps hotels identify bookings with higher cancellation risk
- Supports proactive customer follow-up and confirmation workflows
- Improves revenue forecasting and room inventory planning
- Highlights cancellation patterns by channel, seasonality, lead time, and booking behavior
- Provides decision support for targeted retention and cancellation-policy strategies

Tools used: Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, imbalanced-learn, SMOTE, Random Forest, Jupyter Notebook.
