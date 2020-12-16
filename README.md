<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100"/>

# Smart Bank
*Víctor Lópesz Jiménez*

*DAFT October 2020, Barcelona, 16/12/2020*

## Content
- [Project Description](#project-description)
- [Hypotheses / Questions](#hypotheses-questions)
- [Dataset](#dataset)
- [Cleaning](#cleaning)
- [Analysis](#analysis)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Workflow](#workflow)
- [Organization](#organization)
- [Links](#links)

## Project Description
My project is a Machine Learning model able to predict if a customer from a bank is going to churn or not. The reason why I choose that topic is
because, on my previous job, **churn** was a very important metric to control, so I wanted to deep dive on that.
Last, what I'm trying to show is finding the best model for categorizing correctly the churned customers.

## Hypotheses / Questions
* Does the attrition is more likely to happen based on one gender or other?
* Is it more likely that the newest customers are more able to churn?
* Low card utilization ratio is an indicator of possible churn?

Mention that, the project was based on ML and those hypothesis are not answered yet. It would be done on the future work.

## Dataset
The data was downloaded from Kaggle (https://www.kaggle.com/sakshigoyal7/credit-card-customers).
The dataset has +10K rows and 21 columns (the last two should be removed at the beggining), being 6 of them categorical and the rest numerical.

## Cleaning
The data was pretty clean, as RegEx wasn't neccesary and there were no missing values. Looking the outliers, I removed them using the IQR and store the new dataframe into a different .csv file to compare it with the original one and see if it improved.
Last, I checked if there was colinearity in some columns, having to drop two of them; and converted the categorical ones to numerical using `OrdinalEnconding` and `OneHotEncoding`.

## Analysis
*Hypothesis part to be answered once it's added*

The methods used in Machine Learning were the **classifiers**. What I first did was initializing several models and loop over them to see which were the top 3 best performers, which resulted to be `GradientBoost`, `AdaBoost` and `RandomForest`. After that, I started tuning the different models and see which was the best for them. Once I got it, `GradientBoost`, I did more tests like increasing/reducing the `test_size`, over and under sampling.

Also, deep learning was present on the project with the aim of training neuronal networks and see their results.

## Model Training and Evaluation
After the best three models were found, I trained them using `RandomizedSearchCV` for having a general idea of best parameters and, after that, I did a deep tuning with `GridSearchCV`, setting the `cv` with `StratifiedKFold`.

The best model was **`GradientBoost`**, and here are the results:
![gradientboost_results](./images.gradient_boost_results.png)

You can see an `accuracy` grater than 97.5%, and although data was imbalanced, the `recall` for the Churned customers is greater than 92%, meaning that the model classifies correctly almost every customer on their bucket. Also, looking into the `cohen_kappa_score` provided very good results.

## Conclusion
Summarizing, the churned customers are detected almost perfectly, although the model might be improved little by little if I had more time for fine tuning.

*More content to be added on the future once the hypothesis testing is done and I can answer the initial questions*

## Future Work
1. Hypothesis testing.
2. Improved deep learning model.
3. Improved the model to reduce miss classifications.

## Workflow
The workflow for the project was the following one:
1. Data cleaning and pre-processing.
2. Find the best classifier models.
3. Tune the top 3 models and identify which is the best.
4. Do further testing with the best model and see if the numbers improve.
5. Build a neuronal network.

For testing the results, as they were imbalanced I always used the `stratify`. Also, instead of focusing on `accuracy`, I was looking more into the `recall` of each label, but without leaving the `precision` being a bad metric; or in other words, the best `recall` possible with the highest `f1-score` possible.

## Organization
The workflow was organized through a Trello Board linked on the below section.

The repository has three different folders:
1. **images**: Images from plots.
2. **data**: Where you can find the different *.csv* files used (or generated) during the project.
3. **code**: Where you can find three different notebooks: *Data Cleaning and Pre-Processing*, where the data is cleaned and pre-processed for the ML; *ML Modeling*, where different models are being tested to find the best one; and *Deep Learning*, where an ANN is created.

## Links
Include links to repository, slides and trello board.

[Repository](https://github.com/VictorLJay/Project-Week-8-Final-Project)  
[Slides](https://slides.com/)  
[Trello](https://trello.com/b/fhImXMkI/final-project-ironhack)  
