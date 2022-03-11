# Forecasting Covid Cases
This project aims to forecast future COVID-19 cases by building predictive models given past data. COVIDCast Epidata API provides county-level data on the spread and impacts of the pandemic across the United States. We use available data for doctor visits, trends and surveys, google searches, hospital admissions, positive antigen tests, time spent at home, and COVID cases to train the models. After implementing a simple linear regression model on our COVID-19 data, we found that the model performed well regardless of the number of features included in the data. In regards to the neural network, the Long Short-Term Memory (LSTM) model performed the best but struggled with overfitting despite regularization. Looking back on our results, our linear regression model performed slightly better than the complex neural network model. This project is motivated by the lack of previous knowledge surrounding the understanding of COVID, which led to mutations and prolonging of the pandemic period. In regards to data preparation, data were merged by counties and time from February 2020 to November 2021. Focusing on counties in California, multiple datasets were created with various combinations of features and varying amounts of timesteps. To preserve cases with existing missing values, data was imputed by information from the last valid observation day for a maximum gap number of 3 consecutive missing values.

![image](https://user-images.githubusercontent.com/28970539/145730720-0cdcd9d9-e41a-49c2-8155-3ec8afdd940a.png)


For the interpretative model, we decided to use linear regression for forecasting COVID-19 cases due to its simple implementation. To test which combination of features provides the most balanced bias-variance tradeoff, we integrated backward subset selection five times where features that contributed the least to the models were removed. The model with the “confirmed COVID visits” and “volume of Google anosmia searches for the previous day” features removed yielded the lowest magnitude of error (RMSE). As expected, the predictions for the training set were very similar to the true predictions. Because the model was not familiar with the test set, the predictions were not as accurate. Nonetheless, the linear regression model still performed well with a slight underestimation of forecasted COVID cases. We found that with our final linear regression model, no single feature had a larger weight on the result more than any other (i.e. all coefficients were relatively the same). Nonetheless, all features were significant to the predictive model (Pr(t) < 0.05).

![image](https://user-images.githubusercontent.com/28970539/145730765-c605e5f1-cd90-4320-b34a-cb612741294b.png)


For the complex model, we decided to build a neural network. Cross-validation was implemented to choose the best model and an optimal number of time steps and features to include for training the neural network.  From cross-validation, we concluded the  Long Short-Term Memory performed the best out of the six models. Using the test RMSE as the accuracy metric, we concluded that the Google search symptoms (anosmia and ageusia) decreased prediction accuracy and removed these features. Overfitting may have contributed to a higher error in the testing set in comparison to the training set.  For instance, the model performed best on Merced County and worst on predicting San Diego County cases.

![image](https://user-images.githubusercontent.com/28970539/145730787-66af16ce-6e4f-42c9-95d2-e20cdcf9548f.png)


Although the complex model was expected to produce higher accuracy than the interpretive model, linear regression ultimately performed better. Thus, the interpretive model would perform better in a real-world scenario. Despite the ability to build models to forecast the future of the pandemic given past data, the model performances indicate underestimation of COVID cases. Features including COVID cases and deaths, hospital admissions, as well as doctor visits were among the most relevant for forecasting cases. To avoid undercounting, we can increase testing sites and medical resources for low-income areas.

Please see our Research_Poster.pdf for more details on methodologies and results.

