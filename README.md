# Neural_Network_Charity_Analysis
## Overview
Alphabet Soup is a non-proft organization that has raised and donated over 10 billion dollars in the last 20 years. The impact of each donation needs to be analyzed to vet potential future recipients. A [CSV file](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/charity_data.csv) contaning more than 34,000 organizations that have recieved funding from Alphabet Soup was used to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup. 
### Resources/Tools
- [charity_data.csv](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/charity_data.csv)
- Pandas
- TensorFlow
- scikit- learn
- Keras

## Results
### Data Preprocessing
Before running the neural network model, our original CSV file needed to be preprocessed. 
1) I **removed** the "EIN" and "NAME" columns since these identification columns would not be important features for our model. 
2) I then looked at the unique values for each column to determine if any columns needed to be binned. Based on the unique value counts, the "Application_Type" and "Classification" columns were binned by creating an "other" type for rare occurences. 
3) I then encoded all of the categorical variables and merged these values with our origial dataframe.

![This is an image](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/Screen%20Shot%202022-07-05%20at%2011.25.01%20AM.png)

4) I split our data into the features and target array. The **target** for this model is the "IS_SUCCESSFUL" variable while the **features** are the "APPLICATION TYPE", "AFFILIATOIN", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", and "ASK_AMT" variables. 
6) This data was then split into training and testing sets and then scaled using the **StandardScalar()** instance.  

### Compiling, Training, and Evaluating the Model
## Summary
