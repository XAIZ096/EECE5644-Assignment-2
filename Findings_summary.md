# Findings Summary

## 1

The estimated base-plan charge is $24.97 per month.

## 2

Based on the multivariable linear regression model, each service contributes approximately the following amount to the monthly bill:

| Service | Estimated Contribution |
|---|---:|
| InternetService_Fiber optic | $24.95 |
| PhoneService | $20.04 |
| StreamingTV | $9.98 |
| StreamingMovies | $9.95 |
| OnlineSecurity | $5.05 |
| TechSupport | $5.03 |
| MultipleLines | $5.01 |
| DeviceProtection | $5.01 |
| OnlineBackup | $4.98 |
| InternetService_No | $-25.05 |

## 3. Most and least expensive add-ons

Fiber optic internet is the priciest add-on, adding about $24.95 to the monthly
bill. On the other end, online backup is the cheapest at just $4.98. So fiber costs
roughly five times more than backup, which lines up with how much more infrastructure
and bandwidth fiber actually requires.

## 4. Fiber + both streaming services

If a customer adds fiber internet along with StreamingTV and StreamingMovies, we'd
expect their bill to go up by about $44.88 a month.

## 5. Phone service + multiple lines + tech support

A customer who signs up for phone service, multiple lines, and tech support would be
expected to pay around $55.05 a month.

## 6. Which services vs. how many services

Our model explains 99.9% of the variation in monthly charges
(R² = 0.999) and is off by less than a dollar on average (MAE = $0.79). A simpler model
that just counts the number of add-ons only gets to 70% (R² = 0.70) and misses by over
$14 on average. That gap makes sense once you think about it like this if two customers can both
have "2 services," but if one picked fiber and phone while the other picked backup and
device protection, their bills would differ by around $35 even though the count model
treats them as identical.

## 7. Prediction accuracy on unseen customers

Tested on customers the model never saw during training, predictions land within about
$0.79 on average, and the RMSE comes out to $1.05. Since bills in this dataset range
from about $18 to $119 a month, being off by less than a dollar is a tight fit.

## 8. Do the coefficients match Telco's price list, and anything surprising?

The coefficients come out very close to round numbers like $5, $10, $20, and $25,
which strongly suggests the model has essentially recovered Telco's real per-service
pricing. The one number that looks odd at first is InternetService_No, which sits at
negative $25.05. That's not a discount for skipping internet but it is just a side effect of
how internet type was one-hot encoded, customers with no internet service don't pay the
internet-related portion of the base charge, and that shows up mathematically as a large
negative adjustment.
