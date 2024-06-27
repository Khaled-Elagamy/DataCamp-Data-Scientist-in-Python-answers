
# Managing machine learning projects

### Identify machine learning mistakes

```
Answer: Defining business requirements before building the model.
```

### Data needs pyramid

```
Machine Learning in production
Prtototype & Testing ML
Analysis
Prepartation and cleaning
Storage
Collection
```

### Match ML mistakes by their types

|  Not enough data  |  Late testing, no impact                   | Feature selection               |
| ------------------------------------ | ---------------------------------------------------- |------------------------------------------ |
|The team has reviewed customers data: 3% of customers have data captured in a structured format, the rest is sitting in the back-end systems.| The model has been tested in the market and has not shown any results, the team says that they need another 6 months to perfect the model algorithm.|The team said they're going to use all data possible for the inferential model and that they don't need an input from the business team.|
|The team has reviewed the data sources: the systems are not capturing the data correctly and cannot be used in building the model.| The team spent 2 months in building the prototype model. They need 8 more months to perfect it before running the A/B test in the market.|The team wants to get all the possible data before building a prototype. They need 8 months to aggregate data from all different sources.|

### Business communication focus

```
Answer: Discussing machine learning algorithm nuances.
```

### Market testing

```
Define the target variable
Build a machine learning model predicting the outcome
Select customers with the predicted values and split into 2 groups (A/B)
Run certain actions e.g. marketing campaign, for group A and no actions for group B
Measure group A performance vs. group B and conclude if there was an impact on the desired outcome
```

### Production systems

```
Answer: Weekly business report stored as a spreadsheet file in company's shared drive.
```

| Customer relationship management   |   Fraud prevention system                   | Autonomous car                   |
| ------------------------------------ | ---------------------------------------------------- |------------------------------------------ |
|An automated product promotion email is triggered by a realtime machine learning model predicting which product the customer might be interested in.| The customer receives an email requesting information about their money transfer. The system identified a potentially risky transaction.|The sensor readings predict a potential collision and automatically hit the car brakes of the car to avoid it.|
|A high-value customers get a number of promotional discounts when the system predicts they are at risk of churning.|A transaction is passed to the team for a manual review after the system flags it as 'risky'.|The car should turn right at the next crossing. The road is closed; the system automatically re-calculates the journey to offer an alternative path.|


### ML in production launch

```
Launch to a small set of customers
Track initial results
Make sure the results are consistent over time
Scale up the model coverage
```

