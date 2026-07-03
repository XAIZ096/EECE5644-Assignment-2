# Predicting Telco Monthly Charges

Predicts a customer's monthly bill based on which add-on services they have
(phone, streaming, security, fiber internet, etc.) using linear regression.

## Dataset

Download `telco.csv` from [Kaggle's Telco Customer Churn dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
and place it in this repo's root folder. (A zipped copy is also included here.)

## Running it

```bash
pip install -r requirements.txt
```

Then open `Assignment2_1-4.ipynb` and run all cells top to bottom.

## Findings

Base plan: ~$24.97/month. Fiber internet is the priciest add-on (+$24.95), most
others add about $5 each. The model predicts monthly charges within ~$0.79 on
average (R² = 0.999), and knowing *which* services a customer has beats just
knowing *how many* by a wide margin. Full details in `Findings_summary.md`.
