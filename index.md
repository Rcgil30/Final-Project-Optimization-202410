# Final Project - Optimization 202410

## Team Members

### Justine Barreto

![Picture of Justine](assets/TeamPictures/Justine.jpeg)

Bio: Justine Barreto Angarita is a student who belongs to the Systems Engineering program in Universidad del Norte. She graduated from Politécnico de Soledad school in 2020 during the pandemic. At first, she was not completely interested in any engineering. However, as time passed by, Justine decided to check out some of the areas where engineers play a big role in. 

Justine is currently interested in Cybersecurity and Proyect Management in IT. She also hopes to showcase her talents and abilities in order to make the engineering field a better environment.

### Luis Espinel

![Picture of Luis](assets/TeamPictures/Luis.jpeg)

Bio: Luis Guillermo Espinel Luna is a Universidad del Norte student majoring in systems engineering since 2021. He initially started at Univeridad EIA in Envigado, Colombia, achieving 2 approved semesters. These studies were interrupted by the COVID-19 pandemic, which motivated him to move back to continue his studies in his home town. He's a hard-working young man who's been working at a customer service company since 2022, with the motivation to pay for his own studies and to provide for and help at home. He's a friendly and caring person who believes in relationships as the path to success. Luis is passionate about the engineering behind things of daily use and his thirst for useful knowledge in applied science.

### Roberto Gil

![Picture of Roberto](assets/TeamPictures/Roberto.jpeg)

Bio: Roberto Carlos Gil García is a 7th semester student of systems engineering at Universidad del Norte in Barranquilla, Colombia, he is currently 20 years old. He's passionate about artificial intelligence, data science and data visualization and analysis, looking forward for higher education in that field. Roberto also has experience in building software projects, especially in the modeling of databases and backend development, deployig large datasets into a database engine and using the connections for data visualization. 

### David Maury

![Picture of David](assets/TeamPictures/David.jpeg)

Bio: David Andrés Maury Muñoz is a seventh semester student of Systems Engineering at the Universidad del Norte (UniNorte), Barranquilla, Colombia. He finished his high school studies (2020) at the Francisco Javier Cisneros Commercial Technical Educational Institution, Puerto Colombia, Colombia. Throughout his career in Systems Engineering, David has developed in a general way in terms of programming, even making functional rustic video games.

### Mateo Suarez

![Picture of Mateo](assets/TeamPictures/Mateo.jpeg)

Bio: Mateo David Suarez Paez, is a Systems Engineering student who joined the Universidad del Norte in 2021, initially as
industrial engineering student, later he changed his program starting in the third semester due to his affinity, tastes, passion
and goals with which he identified by being part of systems engineering. He graduated from high school in 2020 from the institution 'Colegio Americano de Barranquilla'.

Mateo, apart from his studies, works based on his sports supplementation business, and offers his services/knowledge as an engineer to a Colombian company (freelance).

## Dataset selection

The dataset we selected for this project is the California Housing Prices Data, which can be found in the following [link](https://www.kaggle.com/datasets/fedesoriano/california-housing-prices-data-extra-features/code).

The reason we selected this dataset is because it has a great variety of variables that we can work with, making it a great tool for learning predictive machine learning algorithms. Also, this could have applications in real life scenarios, for example, building companies could benefit of a model that could predict the value of a house given the variables, using this to evaluate the potential profitability of a building. This could also be used by potential home buyers to estimate a price for a house given the characteristics that they want in that house.

## Visualization and statistical insights

Using Google Colab, we built the file that can be found in our repository as [Optimization_202410_FP](assets\DatasetVisualization\Optimization_202410_FP.ipynb), with this we gathered some information from the dataset to get better statistical insights:

![Dataframe info](assets/DatasetVisualization/DatasetInfo.png)

Firstly, we took a look into the information that pandas provides us about the dataset, in this we can see that all 14 rows have all non-null values, which is great, because we don't have any gaps in the information and don't have to make any decisions about what we should do about missing values. Also, we can see that all variables are numerical, either integers or floats, so our models won't depend on any categorical values, so we won't need to drop any of this information or build a different model depending on the categorie (because sometimes they are incompatible).

![Histogram](assets/DatasetVisualization/Histogram.png)

Histogram: With this plot, we aimed to take a look at the distribution of frecuency of the house prices, which is our variable of interest, and the one we will try to predict in the future. For this we decided to change the amount of bins (which is 10 by default) to the amount proposed by the Sturges law, this is automatically done by pyplot, and we can see that there is a tendency for a shift to the left in the prices of the houses, and also an unusual amount in the last bin, with this we can rule out that the houses have a well defined probability distribution.

![Correlation Heat Map](assets/DatasetVisualization/CorrelationHeatMap.png)

Correlation Heat Map: Using pandas, we calculated the correlation between all of the variables, our interest is centered in the ones that are placed in the first row, because they are related to our variable of interest. In this we see that the most influential parameter is the median income of households around the area, which makes sense because we would normally expect an expensive house to be located in an expensive neighborhood, so the correlation is clear. The second biggest correlation is with the distance to the coast, which is surprising because it has a big negative correlation, so the further away a house is from the coast, its going to be more expensive, and we thought that it wouldn't have a lot of impact. The rest of the variables

![Displot](assets/DatasetVisualization/Displot.png)

Displot: The displot shows both the histogram plot and a kde plot, the kde shows a prediction of the probability distribution based on the behavior of the data, again confirming that it doesn't follow conventional probability distributions.

![Scatter and Kde plot](assets/DatasetVisualization/ScatterKdePlots.png)

Scatter and Kde Plot: We created a pair grid of Scatter and Kde plots, the first one helps us visualize the pattern of frecuency of the different variables in our set, in which we can clearly observe how correlated these are in the variability of the plots, the Kde on the other hand shows how the gradient of that two variable function of frecuency behaves, showing that for some variables we have a lot of critical points of concentration, which could probably be used for neural networks algorithms.

## Hypothesis 

Out of the statistical insights we got of the dataset, we would like to explore the idea of working with the different variables we have to construct a predictive machine learning model, using the correlation between the data to our advantage to predict the prices of a hose given user input, as well as considering creating predictive models for other variables like the median income in the zone, which are most likely unknown by a normal user who's looking to buy a house, especially because we saw that the median income had the biggest correlation to the price.

We would also like to check how different machine learning algorithms perform given the dataset, identifying the key differences that make one model perform better than the others.

That said, the main objective of this project is to learn the implementation of different machine learning algorithms in Python, using the patterns in data to create predictive models that could be useful in real life scenarios.