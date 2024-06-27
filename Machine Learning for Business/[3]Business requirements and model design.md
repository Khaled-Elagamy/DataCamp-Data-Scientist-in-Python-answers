
# Business requirements and model design

## Identify situation, opportunity and action

|  Business situation   |   Business opportunity                     | Business action                   |
| ------------------------------------ | ---------------------------------------------------- |------------------------------------------ |
|The number of customer service requests has increased by over 300% driving the time-to-answer up and resulting in more escalations. | Increase the engagement and the click through rate of the emails from 2.5% to the previous levels of 5%.|Run a series of AB tests targeting customers with relevant email content based on machine learning predicted product interest.|
|The company started seeing much lower click through rate of its promotion emails.| Reduce the time-to-answer customer requests back to previous levels and potentially even lower.|Build a machine learning solution to guide customers requests with step-by-step customer chat and call process automation.|

### Identify successful experiments

```
Answer:A beauty products company started seeing a lower number of customers reaching their "Gold Status" which requires meeting certain level of annual spending and other criteria. The competition has been much more active lately. The company decided to build an ML model identifying potential "Gold Status" customers early after they joined the company, and giving them extra discounts, more focused customer service and other incentives. The company ran a test on half of its customers using ML prediction. The conversion rate to "Gold Status" has increased for all customers.
```

### Model training process


```
Answer:Model is built on the training dataset, then its performance is validated on the validation dataset, and finally on the test dataset.
```

### Training, validation and test


|                     Traning            |                        Test         | 
| --------------------------------------------------------------- | ----------------------------------------- |
|This dataset is used to train the model. | This is the last step in the ML process before reporting the final model performance metric.|
|This dataset contains input features and the target variable for the model to learn the patterns on (model training).| Once the final ML model is trained, its performance is measured on this dataset.|


### Poor performance examples

```
Answer:The manufacturing company wants to predict which items on its production line are faulty. The model is built and it identifies 50% of total faulty products (50% recall), and from the ones identified as faulty around 95% actually are (95% precision). The company decides to continue the manual process as identifying only half of faulty products is not going to help. They need 100% recall and 100% precision.
```
### Identiy performance metrics

|  Precision   |   Recall                     |                        Error                  |
| ------------------------------------ | ---------------------------------------------------- |------------------------------------------ |
|Of all customers predicted likely to buy, 25% actually bought the product.|The model gives a list of patients likely to suffer from a second heart attack in the next 24 hours. It captures only 20% of all patients at risk.|The weekly demand prediction model is on average wrong by 7% compared to the actual demand.|
|The model predicts a list of patients likely to suffer from a second heart attack in the next 24 hours. 50% of the predicted patients actually did.|    The model gives a list of customers likely to purchase. When performance is measured, it captures 45% of all the customers that were going to buy.|The stock price prediction model on average misses the actual stock price by 2.5 USD.|


### Fixing non performing models

```
Answer: Continue using the same machine learning predictions, because it is based on complex algorithms.
```

### Non-actionable models

```
Answer: Half of the customers with a high predicted probability to churn have been getting promotions and discounts on the items they were interested in (also predicted by ML). The company has observed a reduction in churn for that group by at least 3% and increase in overall purchase frequency.
```

### Identify actionable recommendations


```
Answer: Reduce the price for the add-ons to zero.
```

