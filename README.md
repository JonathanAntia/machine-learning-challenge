# Machine-Learning-Challenge

# Classifying Exoplanets

 ![Kepler Exoplanets](/images/Exoplanets.png)

Over a period of nine years in deep space, the NASA Kepler space telescope has been out on a planet-hunting mission to discover hidden planets outside of our solar system.

Using the [dataset](https://www.kaggle.com/nasa/kepler-exoplanet-search-results) collected by the Kepler space telescope, this project aims to develop a machine learning classification model to determine if a Kepler Object of Interest (koi) is indeed an exoplanet or not.The dataset has an extensive data dictionary, which can be accessed [here](https://exoplanetarchive.ipac.caltech.edu/docs/API_kepcandidate_columns.html).

## RandomForest Classification

The random forest classification algorithm from scikit-learn returns a model with a 98% accuracy of predictions on test data.

The features in the original dataset were reduced to the list below, showing feature importances.

![Random Forest Feature Importances](/images/FeatureImportances.png)

Three categories are present within the koi_disposition column: CANDICATE, CONFIRMED, and FALSE POSITIVE. Candidate pertains to objects of interest that have potential for being an exoplanet, but they have not yet been confirmed or rejected. Therefore, there is an intrinsic level of uncertainty associated with each candidates, which would impact the accuracy of the prediction model. For this reason, candidates were removed from the list of target features in the training and test dataset. The resulting dataset contains 3,504 FALSE POSITIVES and 1,800 confirmed exoplanets.

Here is the confusion matrix for the default random forest model:

![Confusion Matrix With Default Parameters](/images/ConfusionMatrixDefaultParameters.png)

Obviously the default parameters result in a highly accurate model, yet a round of hyperparameter tuning was tested to see if the accuracy could be improved. The confusion matrix below shows the results of the tuned model:

![Confusion Matrix With Tuned Parameters](/images/ConfusionMatrixHypertunedParameters.png)

Hyperparameter tuning in this case does not have a significant effect on the accuracy of the original model.

Lastly the AdaBoost classification algorithm was tested to see if it may have positive effect. The results are shown below:

![Confusion Matrix With Boosted Parameters](/images/ConfusionMatrixAdaBoost.png)

A very slight increase in the accuracy score occurs after applying the AdaBoost algorithm, from 0.9849 with default parameters to 0.9856 with AdaBoost.