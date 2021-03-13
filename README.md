# Neural_Network_Charity_Analysis

## Overview
The purpose of this analysis was to create a binary classifier to predict if applicants seeking funding would be successful or not based on certain application parameters. 

## Results

### Data Preprocessing
 - The target variable was whether or not the applicant was successful or not, with data noted in the column, IS_SUCCESSFUL.
 - The features used in the initial analysis were: application type, affiliation, classification, use case, organization type, income amount, special considerations, and ask amount. 
 - Data removed from the analysis included the EIN (identifier) and NAME columns. These features had no bearing on the result.
 - Binning: for the application_type and classification features, I reduced the number of categories and put into an 'other' category those with low values.
 - Encoding categorical columns: For the categorical variables, I encoded them using the OneHotEncoder feature. 

### Compiling, Training and Evaluating the Model
- **Scenario A**: The first model, which is in the AlphabetSoupCharity.ipynb file, used two layers with a combined number of neurons of 110 (80 for layer 1 and 30 for layer 2). The model used was tf.keras.models.Sequential. Activation models used for both layers were relu and the output activation layer used was sigmoid. I also used 100 epochs. The result of runnign this model was a loss of .5756 and accuracy of .7247. See screenshot below.
- 
![Screenshots](https://user-images.githubusercontent.com/72076683/111047249-950f0780-8412-11eb-82e3-d8e686a8f264.png)

- **Scenario B**: In this model, I left everything constant except I changed the output activation layer to softmax (which the model name is saved). The result was worse - with 7.1311 loss and .5324 accuracy (screenshot below). I used this because I read that it is good for mutually exclusive categories (this or that) but in talking through the results with a TA, it is better for multiclass analysis (evaluating two or more inputs/targets). 

![Screenshots](https://user-images.githubusercontent.com/72076683/111050784-46626d00-8414-11eb-80dc-5f7de480883b.png)

- **Scenario C**: In this scenario, I left everything constant as in scenario A execpt I removed two features. To determine which features to use, I used a correlation matrix. I ended up removing the features: STATUS and ASK_AMT since they did not seem to have any correlation to IS_SUCCESSFUL. After running this model, the resulting output was slightly better with .56 loss and .7258 accuracy. Screenshot below.

![Screenshots](https://user-images.githubusercontent.com/72076683/111050994-8d9d2d80-8415-11eb-9c17-70b5f5b653d3.png)

- **Scenario D**: The last experiment I tried was increasing the number of neurons off the parameters used in Scenario C, which was best performing so far. Since the number of features was 114, I used 230 neurons split into two layers with layer 1 having 160 and layer 2 with 70 neurons. The result of this model was worse than Scenario A with loss of .5697 and .7236 accuracy.  

![Screenshots](https://user-images.githubusercontent.com/72076683/111051014-b02f4680-8415-11eb-8c73-870834f5d1ba.png)

## Summary
The goal of this deep learning model was to get to accuracy at or above 75%. I did not meet that goal with my experiments. Changes made to the model only marginally improved the outcome from Scenario A and Scenario B had a worse result. 

Instead of using a neural network model, I may instead use a different machine learning model for this analysis. The machine learning model I would try is the random forest model which can handle non-linear data and it is good at sorting out the importance of features. This data set had a lot of features to analyze - that is why random forest may be a better fit. This model would also run faster, allowing for more testing of variables to improve results. 

