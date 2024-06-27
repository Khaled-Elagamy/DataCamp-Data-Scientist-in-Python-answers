

# Machine learning types

## Inference and prediction differences

```
Answer:Inference models are more accurate than prediction machine learning models.
```


### Identify inference vs. prediction use cases


|                     Inference (Causal)                |     Prediction         | 
| --------------------------------------------------------------- | ----------------------------------------- |
|What kind of symptoms are indicating a potential heart attack? | Which of the patients are at risk of a heart attack?          |
|Which gaming behaviors are the most predictive of the next month gaming hours?| Which of these banknotes are likely to be counterfeit? |
|What are the main indicators of transaction's probability to be fraudulent?|Which of these customers are likely to spend the most in the next 12 months? 
|What are the main drivers of high customer satisfaction?|Which of these transactions are most likely to be fraud? |

### Experiments and causal models

```
Answer:Whenever possible, causal models are preferred over experiments.
```

### Identify non actionable variables

```
Answer: The most impactful variables are highly correlated with the desired outcome (interest in a product leads to product purchase) but they are not actionable. The machine learning model needs to be rebuilt using actionable inputs that the business can impact
```

### Supervised modeling principles

```
Answer:Supervised machine learning uses inputs features to discover outliers.
```

### Identify classification and regression models

|                     Classification               |     Regression         | 
| --------------------------------------------------------------- | ----------------------------------------- |
|A car manufacturer wants to use sensor data to identify which of the parts in the production line are potentially faulty and need manual inspection. | A bank wants to predict how much money will the customers spend on different services in the next year.   |
|An online toy shop wants to predict which customers are likely to buy a bike next month.                | A gaming company wants to predict how much time each gamer will likely spend playing video games in the next month.  |




### Unsupervised modeling use cases

```
Answer:Unsupervised learning is used to identify patterns in data, build clusters or detect outliers
```


### Classification, regression or unsupervised models


|  Classification   |   Regression                     | Unsupervised learning                                |
| ------------------------------------ | ---------------------------------------------------- |------------------------------------------ |
|Identify which customers are likely to click on this banner. | Predict our product demand for the next month. |Group our customers based on the similarity of their purchasing patterns.|
|Predict what is the object in the uploaded picture - human, car, animal or other. |    Predict agricultural raw material prices to inform our pricing decisions.|Group our products together based on sensor readings, then flag outlier items which don't fall within any cluster for manual inspection.|

