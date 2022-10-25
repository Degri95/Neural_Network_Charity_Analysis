# Neural_Network_Charity_Analysis
Using machine learning and neural networks to create a binary classifier to predict success in charity applications.

## Overview

In this project a binary classifier is created to help predict whether applicants who apply for funding though the company AlphabetSoup will be successful. AlphabetSoup provides donations to companies who's goals are to protect the enviroment, improve peoples well being, and unify the world.

## Results

AlphabetSoup's dataset was provided for the analysis. Link available [here](https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-online/module_19/charity_data.csv). The data provided is a CSV file with 34299 rows of data.

- Data Preprocessing
    - The target variable for our model is the `IS_SUCCESSFUL` column. This column tells us if the applicant was successful with the donation.
    - The feature variables are columns in the dataframe that will provide measureable data that can be used for our analysis. The columns used were `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`
    - `EIN` and `NAME` will be removed as they provide no measurable data. `EIN` is a identification number and `NAME` is a categorical value that is irrelevant to our target value.

The categorical data was checked for unique value counts and binning was applied if greater than 10.

![unique](/Resources/unique.PNG)

![binning_1](/Resources/binning_1.PNG)

![binning_2](/Resources/binning_2.PNG)

After the data was binned, `OneHotEncoder` was used to transform the categorical data to binary values. This data was merged into the original DataFrame and the original features were dropped, leaving the DataFrame with all integer values.

![encoded](/Resources/encoded.PNG)

The data is now ready to be scaled and split into training and testing datasets for the model.

![scale_train](/Resources/scale_train.PNG)

- Compiling, Training, and Evaluating the Model
    - The first model created had 2 hidden layers. The first layer had **80** neurons and used the activation function "**relu**". The second layer had **30** neurons and also used the activation function **relu**. The output layer used the **sigmoid** function since we are creating a binary classifier. 
    - The first model did not achieve the target performance of 75% accuracy. A total accuracy of 72.8% was achieved. There was an additional attempt to optimize and reach 75% accuracy, but was overall unsuccessful reaching only 72.7% accuracy.
    - To optimize the model, additional columns were dropped in the preprocessing phase. Columns `STATUS` and `SPECIAL_CONSIDERATIONS` had very uneven data distributions between the binary values. 

    ![dropped](/Resources/dropped.PNG)

    The model also had additional hidden layers, neurons, and functions added. 

    ![optimize](/Resources/optimize.PNG)

    The optimization overall failed and performed worse than the original.

## Summary