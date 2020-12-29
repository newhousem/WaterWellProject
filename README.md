# Water Pump Project

## Purpose
The purpose of this project is to create a model that can predict the functionality of water pumps using data from Taarifa and the Tanzania Ministry of Water. This project will approach the prediction using binary classifications and ternary classifications. One model will be made to predict whether a pump is functional or not functional. Another model will predict on three classes, whether the pump is functional, needs repairs, or doesn't work at all. Feature importances will be drawn from the final models. 

## Data
* The data used in this project was provided by Taarifa and the Tanzania Ministry of Water.
* The data was found on drivendata.org;
https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/23/
* The original target class is ternary, with about 54% of the data representing functional pumps, 38% representing non functional pumps, and 7% representing pumps that are functional but need repair. 
* For the binary model the non functional pumps and pumps needing repair were combined.

## EDA
From my exploratory data analysis certain features appeared to impact pump functionality.

Location of Water Pumps

![alt text](Images/Map%20of%20Water%20Pumps.png)

In this map green represents functional water pumps, red represents non functional water pumps, and yellow represents pumps that need repair. 

We can see that location may have an impact on functionality 

Quantity of Water

![alt text](Images/Status%20Group%20vs%20Quantity%20of%20Water.png)

In the above graph we can see that the water quantity group, dry, is significantly represented in the non functional pumps. 

Construction Year

![alt text](Images/Pump%20Functionality%20vs.%20Construction%20Year.png)

In the above graph we can see that construction year may have some correlation to the functionality of the pump. 

## Final Models Used

The best two models I used were a K nearest neighbors model, and a decision tree model.

* K nearest neighbors model works by finding the distances between a query and the examples in the data, using the specified number of examples closest to the query, and predicts the classification by voting for the most frequent label. 
* A decision tree model breaks down a data set into smaller and smaller subsets while an associated decision tree is incrementally developed. 

## Final Binary Model
The best final binary model was a KNN model. 

![alt text](Images/KNN%20Binary%20Model.png)
![alt text](Images/KNN%20Binary%20Class%20Matrix.png)

## Final Ternary Model
The best choice for the ternary model was less straight forward. Ultimately I chose the KNN ternary model over the decision tree model

KNN Model and Classification Matrix

![alt text](Images/KNN%20Ternary%20Model.png)
![alt text](Images/KNN%20Ternary%20Class%20Matrix.png)


Decision Tree Model and Classification Matrix

![alt text](Images/DT%20Ternary%20Model.png)
![alt text](Images/DT%20Ternary%20Confusion%20Matrix.png)

## Interpretation of Models
* Both models had specific strengths and weaknesses. 
* Binary KNN model had the highest scores overall.
* Ternary KNN model had higher recall and F1 while Ternary DT model had higher precision and accuracy. 
    * This means that the KNN model was better at finding all the positive samples, a lower false negative rate, whereas the DT model had a lower false positive rate. However the KNN model had the best ratio of recall and precision represented in the F1 score.
    * As explained on scikit-learn.org “A system with high recall but low precision returns many results, but most of its predicted labels are incorrect when compared to the training labels. A system with high precision but low recall is just the opposite, returning very few results, but most of its predicted labels are correct when compared to the training labels.”
    * The KNN model was better at predicting pumps that were functional but needed repair, which was a more difficult target to classify due to the class imbalance. 

## Feature Importance

Using my decision tree model I can look at which features were the most significant when training the model. 

![alt text](Images/Feature%20Importance%201.png)
![alt text](Images/Feature%20Importance%202.png)

## Conclusion

* The KNN model performed the best on the binary classification data in all scores
* The ternary KNN model had the best F1 score, the ratio between precision and recall, and predicted pumps that were *functional but need repair* the best. F1 score represents the balance between returning many results and all the results labeled correctly. 
* Some of the features with the most importance for the decision tree model included;
    * Dry water quantity
    * Location
    * Year constructed

## Next Steps

* Further feature analysis could be done such as grouping similar features to create a smaller set of data
* This project used SMOTE to address class imbalance, however I would also look into trying other methods to address class imbalance such as under sampling. 
