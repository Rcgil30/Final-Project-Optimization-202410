---
title: Linear Regression Code
---

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
```

```python
df = pd.read_csv("/content/California_Houses.csv")
df.columns
```

Output: ['Median_House_Value', 'Median_Income', 'Median_Age', 'Tot_Rooms','Tot_Bedrooms', 'Population', 'Households', 'Latitude', 'Longitude','Distance_to_coast', 'Distance_to_LA', 'Distance_to_SanDiego', 'Distance_to_SanJose', 'Distance_to_SanFrancisco']

```python
inputs = ['Median_Income', 'Median_Age', 'Tot_Rooms',
       'Tot_Bedrooms', 'Population', 'Households', 'Latitude', 'Longitude',
       'Distance_to_coast', 'Distance_to_LA', 'Distance_to_SanDiego',
       'Distance_to_SanJose', 'Distance_to_SanFrancisco']
output = ['Median_House_Value']
```

```python
coefficients = [[] for _ in range(len(inputs))]
intercept = []
score = []
```

```python
regression = LinearRegression()
for state in range(1000):
  dfTrain, dfTest = train_test_split(df, test_size=0.3, random_state=state)
  regression.fit(dfTrain[inputs], dfTrain[output])
  for i in range(len(inputs)):
    coefficients[i].append(regression.coef_[0][i])
  intercept.append(regression.intercept_[0])
  score.append(regression.score(dfTest[inputs], dfTest[output]))
```

```python
parameters = coefficients.copy()
parameters.append(intercept)
labels = inputs.copy()
labels.append("Intercept")
```

```python
fig, axs = plt.subplots(7,2, figsize=(13, 25))

fig.suptitle("Distribution of the parameters", fontsize=16)

plt.tight_layout(rect=[0, 0.03, 1, 0.96])

for i in range(7):
  for j in range(2):
    sns.kdeplot(parameters[2*i+j], ax=axs[i, j])
    axs[i, j].set_title(labels[2*i+j])
```

Output:

![Parameters Distribution](assets/Model1/Parameter%20Distribution.png)

```python
sns.kdeplot(score)
plt.title("Score distribution")
plt.plot()
```

Output:

![Score Distribution](assets/Model1/Score%20Distribution.png)

```python
averageParameters = []
for parameter in parameters:
  averageParameters.append(sum(parameter)/len(parameter))

averageParameters
```

Output:
[39095.34892081878,
875.9204660648958,
-5.656416742203111,
103.01601611774895,
-40.06757341720093,
47.3433739173305,
-44150.016541996825,
-27483.993737647885,
-0.23251373388424657,
-0.14787555342303052,
0.23746090579377754,
0.16255053758368895,
-0.13963448726289057,
-1737749.239923306]

```python
regression.coef_ = np.array(averageParameters[:-1])
regression.intercept_ = averageParameters[-1]
ypred = regression.predict(df[inputs]).flatten()
yactu = df[output].values
regression.score(df[inputs], df[output])
```

Output: 0.6465617542482369

```python
sns.regplot(x=ypred, y=yactu)
```

Output:

![Regplot image](assets/Model1/Regplot.png)

```python
finalScores = []
for state in range(1000):
  dfTrain, dfTest = train_test_split(df, test_size=0.3, random_state=state)
  finalScores.append(regression.score(dfTest[inputs], dfTest[output]))
```

```python
sns.kdeplot(finalScores)
plt.title("Score distribution with average parameters")
plt.plot()
```

Output:

![Score Distribution with average Parameters](assets/Model1/Average%20Score%20Distribution.png)

```python
print("Average score improved by:", sum(finalScores)/len(score) - sum(score)/len(score))
```

Output: Average score improved by: 0.0017014752125713573

## [Go back to Model 1 Page](./model1)
