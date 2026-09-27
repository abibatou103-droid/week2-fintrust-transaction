# Feature Engineering Documentation

| Feature | How It Was Created | Why It May Matter |
| --- | --- | --- |
| Transaction_Hour | Extracted from Transaction_DateTime using .dt.hour | Risk review may cluster around specific hours of the day when fraud-like behaviour is more common. |
| Transaction_Day_of_Week | Extracted from the transaction date | Certain days may show higher suspicious activity, especially weekends or payment peaks. |
| Amount_Log | Applied log transformation to Amount_NGN | Logs compress extreme values and reduce skew from high-value transactions. |
| Is_International | Flagged transactions where International_Transaction = Yes | International transactions often carry elevated review risk. |
| Is_Failed | Flagged transactions with Failed status | Failed transactions can reflect abuse, retries, or account-level anomalies. |
| Is_Reversed | Flagged transactions with Reversed status | Reversals may indicate disputes, chargebacks, or suspicious activity. |
| Is_Pending | Flagged transactions with Pending status | Pending transactions might indicate incomplete or risky authorization flows. |
| Customer_Transaction_Count | Count of all transactions per customer | High-frequency account activity can be associated with unusual behavioural patterns. |
| Customer_Avg_Amount | Mean transaction amount by customer | Large deviations from a customer's normal pattern can signal risk. |
| Amount_to_Customer_Avg | Transaction amount divided by a customer's average spending | This contextualizes a transaction relative to a customer's history. |
| Digital_Engagement_Band | Bucketed Digital_Engagement_Score into Low/Moderate/High/Very High | Engagement may correlate with digital channel usage and exposure patterns. |
| Tenure_Bucket | Bucketed Tenure_Months into ranges | Newer or older customers can have different activity patterns. |
| Amount_Band | Grouped transaction dollar amounts into bands | Transaction magnitude is a common pattern indicator in risk analytics. |

These engineered features are intended to capture timing, behavioural context, magnitude, and customer profile signals for the synthetic Risk_Review_Flag target.
