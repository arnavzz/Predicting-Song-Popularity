# Predicting-Song-Popularity
This repository contains the comparison of different ML models to predict the popularity of songs. The goal of this project was to compare the machine learning models studied in class on the dataset of Spotify songs' popularity. Models contain both classifiers and regressors, which informed the models chosen for study.

## Introduction
What is the best machine learning algorithm for predicting the popularity of songs?

The last three decades of the information age have radically changed how we access music. The creation, distribution, and proliferation of music have never been easier, resulting in an information overload. In short, there is too much choice when it comes to enjoying music. At the same time, a core function of the modern platform streaming service is the expectation that recommendations from the platform match what the user wants.

## Learning points
Throughout the project, we covered a wide range of data manipulation and visualization techniques. Some of the key learning points include:

 **1. Checking Hygiene**: We learned how to identify and investigate missing or NaN values in the dataset, ensuring data integrity and making informed decisions about how to handle them.

**2. Data Type Conversion**: We explored converting object and string data types to numeric values, preparing the data for analysis and visualization.

**3. Plotly Visualizations**: We created  histogram plots, scatter plots, and choropleths using Plotly to visualize Spotify's song data, allowing for interactive and engaging representations of the data.

**4. Feature Selection Exploration**: Looking closely at the features, there are some features to consider whether to include in the final model or not. Eliminating the duplicates and null values 

**5. Seaborn Visualizations**: We employed Seaborn to create various visualizations, such as Sunburst charts, bar charts with different segments, and histogram plots to explore the popularity of songs in the particular timeline.

## Preliminary Results
Before tuning, Logistic Regression remains in the lead, with the Random Forest Classifier in close pursuit. Given that only all models managed to cross a 50% threshold, all are valid for hyperparameter tuning to produce the most optimized model.

Afterward, the most promising models were tested for reliability using a Chi-squared test, wherein the H0: the model in question is not a random guesser at a 99% confidence interval. Given that the classifier can be prone to Type I or Type II errors, a higher interval was selected at 99% confidence.

## Hyper-Parameter Tuning

For the Logistic Regression, Decision Tree, and Random Forest models, a grid search cross-validation was performed to find the best parameters using the .getparams method. These initial F1 accuracy scores were then compared to the optimized models (using best parameters) scores.

The optimized Logistic Regression experienced a growth in accuracy for both classification labels, with a marginal increase in overall F1 score after optimization.

The Decision Tree failed to optimize with the grid search cross-validation and also by selecting a model by looking at the decline in RMSE. Other permutations were tested with very little variation, and none was upward in the F1 score. While the RMSE leveled out after greater depth, the accuracy score did not increase. As such, this model was dropped from the final analysis.

The Random Forest optimized successfully with the grid search cross-validation. However, this was extremely computationally intensive with a depth of 64 and 512 required estimations. Actual estimations were even higher at the > 512 level, but this was not sensible to pursue, and somewhat expected of Random Forest classifiers. The RMSE did not decline any further once the number of estimators > 12, suggesting that the accuracy of the optimized model where the number of estimators = 256 might be needlessly complex.

The KNN model optimized between values of 5 (the default) and up to 30 using the elbow method of plotting RMSE as seen in Figure 4. However, while the accuracy of classifying 0 or 1 increased, overall F1 accuracy did not significantly increase. With no other option to use KNN without dramatically increasing RMSE, this model was not furthered to the final analysis.

## Interpretation and testing

Given the proximity of the F1 accuracy scores in the initial model comparison, a lenient confidence interval was selected to account for the limits placed on the Random Forest classifier, which showed higher accuracies through computationally expensive increases in the number of estimators.

In a dramatic turn, we were able to reject H0 at all confidence levels. As the final comparison between the models was conducted using the test dataset using the optimized models, the mean F1 score of the Random Forest classifier rose significantly from its initial and optimal values while there was only a small deviation in the Logistic Regression score. It could still be argued that the result is inconclusive until the models are also tested on different datasets of similar composition but greater size. Given the final validation was performed on the test data, it could be investigated whether Random Forest performs better at smaller scales, which seems unlikely, but could account for the large increase.

## Contributions

Contributions to this project are welcome! If you have any suggestions, improvements, or additional analyses, feel free to open an issue or submit a pull request.

When contributing to this repository, please ensure that your code adheres to best practices and is well-documented. Clearly explain the purpose and approach of your contribution.
