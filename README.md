# Neural_Network_Charity_Analysis
## Overview
Alphabet Soup is a non-profit organization that has raised and donated over 10 billion dollars in the last 20 years. The impact of each donation needs to be analyzed to vet potential future recipients. A [CSV file](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/charity_data.csv) containing more than 34,000 organizations that have received funding from Alphabet Soup was used to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup. 
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
2) I then looked at the unique values for each column to determine if any columns needed to be binned. Based on the unique value counts, the "Application_Type" and "Classification" columns were binned by creating an "other" type for rare occurrences. 
3) I then encoded all of the categorical variables and merged these values with our original dataframe.

![This is an image](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/Screen%20Shot%202022-07-05%20at%2011.25.01%20AM.png)

4) I split our data into the features and target array. The **target** for this model is the "IS_SUCCESSFUL" variable while the **features** are the "APPLICATION TYPE", "AFFILIATOIN", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", and "ASK_AMT" variables. 
6) This data was then split into training and testing sets and then scaled using the **StandardScalar()** instance.  

### Compiling, Training, and Evaluating the Model
The target predictive accuracy of the model was higher than 75%. Multiple models were compiled and trained to reach this predictive accuracy. 
- The first model had 2 hidden layers, with 80 neurons in the first hidden layer and 30 in the second. 80 neurons were chosen since this was about 2 times the count of the input features. The relu activation function was chosen for both the input and hidden layers since we are looking for non-linear characteristics on mostly categorical data. The output function chosen was the sigmoid function since our output was binary (0 or 1). This model achieved an **accuracy score of 42%**.
![This is an image](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/Screen%20Shot%202022-07-05%20at%201.54.27%20PM.png)
- For the second attempt, I decided to use the Keras Tuner. I created a method that would return the optimal amount of neurons in the first layer, the number of hidden layers, the number of neurons in the hidden layers, and which activation function to use in the hidden layers. This model was able to achieve an **accuracy score of 73%**. 

![This is an image](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/Screen%20Shot%202022-07-05%20at%202.52.30%20PM.png)

- I tried another model in which I increased the number of neurons in the hidden layers. I used about three times as many neurons as inputs in my first hidden layer, which was about 120. I then used 40 neurons for the second hidden layer. This model produced an **accuracy score of 60%**. 
![This is an image](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/Screen%20Shot%202022-07-05%20at%201.56.16%20PM.png)

- Finally, I tried one last model in which I added an extra hidden layer. I included 80 neurons in the first hidden layer, 30 in the second, and 10 in the third. This model had an **accuracy score of 50%**. 
![This is an image](https://github.com/dsilvaggio/Neural_Network_Charity_Analysis/blob/main/Resources/Screen%20Shot%202022-07-05%20at%201.58.15%20PM.png)

## Summary
The closest I was able to get to the target predictive accuracy was with the Keras Tuner. This model received an accuracy score of 73%. However, it is possible that this model overfitted the data. I would recommend testing a different model for this data set since we were unable to achieve the target accuracy. A Random Forest model could be tested in this data since our data is tabular and nonlinear. We would also test an SVM model since we know our data is testing a binary classification problem.   
