## INN-Hotels Bookings Cancellations Prediction

![inn-hotels-official-color](https://github.com/hayasalman/INN-Hotels-Bookings-Cancellations-Prediction/assets/71796909/16b49fac-df67-49e2-9a92-ea5e638122c9)

## Overview

 A significant number of hotel bookings are called off due to cancellations or no-shows. Typical reasons for cancellations include change of plans, 
 scheduling conflicts, etc. This is often made easier by the option to do so free of charge or preferably at a low cost. This may be beneficial to 
 hotel guests, but it is a less desirable and possibly revenue-diminishing factor for hotels to deal with. Such losses are particularly high on 
 last- minute cancellations.
 The new technologies involving online booking channels have dramatically changed customers’ booking possibilities and behavior. This adds a further 
 dimension to the challenge of how hotels handle cancellations, which are no longer limited to traditional booking and guest characteristics.
 This pattern of cancellations of bookings impacts a hotel on various fronts:
  1. Loss of resources (revenue) when the hotel cannot resell the room.
  2. Additional costs of distribution channels by increasing commissions or paying for publicity to help sell these rooms.
  3. Lowering prices last minute, so the hotel can resell a room, resulting in reducing the profit margin.
  4. Human resources to make arrangements for the guests.

 ### **Objective**

 This increasing number of cancellations calls for a Machine Learning based solution that can help in predicting which booking is likely to be 
 canceled. INN Hotels Group has a chain of hotels in Portugal - they are facing problems with this high number of booking cancellations and have 
 reached out to data-driven solutions. we have to analyze the data provided to find which factors have a high 
 influence on booking cancellations, build a predictive model that can predict which booking is going to be canceled in advance, and help in 
 formulating profitable policies for cancellations and refunds.

 ### **Dataset Features Description**

 The data contains the different attributes of customers' booking details. The detailed data dictionary is given below:

**Data Dictionary**

 - **Booking_ID**: Unique identifier of each booking.
 - **no_of_adults**: Number of adults.
 - **no_of_children**: Number of children.
 - **no_of_weekend_nights**: Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel.
 - **no_of_week_nights**: Number of weekday nights (Monday to Friday) the guest stayed or booked to stay at the hotel.
 - **type_of_meal_plan**: Type of meal plan booked by the customer:
   - **Not Selected** – No meal plan selected.
   - **Meal Plan 1** – Breakfast.
   - **Meal Plan 2** – Half board (breakfast and one other meal).
   - **Meal Plan 3** – Full board (breakfast, lunch, and dinner).
 - **required_car_parking_space**: Does the customer require a car parking space? (0 - No, 1- Yes).
 - **room_type_reserved**: Type of room reserved by the customer. The values are ciphered (encoded) by INN Hotels.
 - **lead_time**: Number of days between the date of booking and the arrival date.
 - **arrival_year**: Year of arrival date.
 - **arrival_month**: Month of arrival date.
 - **arrival_date**: Date of the month.
 - **market_segment_type**: Market segment designation.
 - **repeated_guest**: Is the customer a repeated guest? (0 - No, 1- Yes).
 - **no_of_previous_cancellations**: Number of previous bookings that were canceled by the customer prior to the current booking.
 - **no_of_previous_bookings_not_canceled**: Number of previous bookings not canceled by the customer prior to the current booking.
 - **avg_price_per_room: Average price per day of the reservation**: prices of the rooms are dynamic. (in euros).
 - **no_of_special_requests**: Total number of special requests made by the customer (e.g. high floor, view from the room, etc).
 - **booking_status**: Flag indicating if the booking was canceled or not.

## About The Dataset

- In total, this dataset has 36,275 observations and 19 features.
- Data source stored as CSV file and can be accessed through this link : [Dataset](https://raw.githubusercontent.com/hayasalman/INN-Hotels-Bookings-Cancellations-Prediction/main/INNHotelsGroup.csv)

## Coding

-  Python Integrated Development Environment (IDE) : Jupyter Notebooks.

   **Packeges used**
   
  * **pandas - numby** : used for data manipulation.
  * **matplotlib - seaborn** : used for data visualization.
  * **sklearn** : used to any preprocessing steps required before feeding the dataset into the machine learning algorithm, training the dataset in 
      ML models , and to evaluate the performance of the models.

## Approaches & Methodologies

- Performed a quick overview about the dataset like the dataset shape , data types, detected any missing or duplicated values, and dropped 
  unnecessary columns like : ids.
- Performed exploratory data analysis (EDA) : univariate analysis, and bivariate analysis that will help us to describe and summarize the dataset 
  characteristics, identify associations between the variables or recognize any patterns , or even to reveal some important insights, and detect the if there are any abnormalities in this dataset.
- Prepared data before modeling by : define the independent variables and target variable, encoding categorical variables by creating dummy 
  variables, scaling the numerical variables to be in the same range, and finally split our dataset into train-test datasets **(train dataset size : 
  70% - test dataset size : 30%)**.

  ### **Important points must be consider before we moving to the modeling**
  
  *From our earlier analysis we found that 67.2% of the bookings weren't canceled by the customers and 32.8% of the bookings were canceled by the 
   customers which suggests imbalance classes.*
  
  - Some classification problems can exhibit a large imbalance in the distribution of the target classes: for instance there could be several times 
    more negative samples than positive samples. In such cases it is recommended to use the stratified sampling technique to ensure that relative 
    class frequencies are approximately preserved in each train and validation fold.

  - INN Hotel Group is interested to know when the customer he/she will cancel the booking , therefore we should look at the class 1 metrics more 
    carefully since this class means canceled booking status(target variable).*
    
  - If the model isn't predict very-well it may ends up predict that a booking will not be canceled and the booking gets canceled then the 
    hotel will lose resources and will have to bear additional costs of distribution channels, or it may predict that a booking will get canceled 
    and the booking doesn't get canceled the hotel might not be able to provide satisfactory services to the customer by assuming that this booking 
    will be canceled, and this might damage brand equity.

  ## Modeling

  In order to solve this binary classification problem, we need training our data on machine learning algorithms for classification.Thus, we called 
  out for sklearn functions:

  1. Logistic Regression.
  2. Support Vector Machine (SVM).
  3. Decision Tree Classifier.
  4. Random Forest Classifier.
 
  ## Performance Evaluation & Draw Conclusions

In terms of determining which of the models have the best performance results and will be used as a final solution. And as it's classification task we will be using these following metrics that embedded within sklearn package or we can use user-defined function to compute the results:

1. **Classification report** : accuray, precision, recall, F-score.
   - **Sensitivity** is the metric that evaluates a model's ability to predict true positives of each available category.
   - **Specificity** is the metric that evaluates a model's ability to predict true negatives of each available category.
       And the best model is the model which has a high percentage of (precision and recall) for both categories.
     
2. The optimal threshold for the model using the Precision-Recall Curve.

3. **Confuestion matrix**
   - Based on that we are interested to reduce two errors of the prediction : Type I Error (FP) & Type II Error (FN), so we should select the model 
     which achieved the highest recall of predicted the class 1 (Canceled) and performed well in predicted unseen data (test data) and training 
     data, Also we will take the other metrics in considerations.
  
**Conclusion : after comparison between these multiple models performance results**

*Tuned decision tree has higher recall scores compared to other models, with F1-Score, Accuracy and Precision values are good. Also SVM with RBF kernel with optimal threshold has a good performance.*

**This screenshot of the optimal threshold for the SVM with rbf kernal model using the Precision-Recall Curve**

![optm_thresh](https://github.com/hayasalman/INN-Hotels-Bookings-Cancellations-Prediction/assets/71796909/152366d0-17fd-4d54-b0c2-23e5021e103e)

**This screenshot of the performance results of the tuned decision tree model**

![dt_confmx](https://github.com/hayasalman/INN-Hotels-Bookings-Cancellations-Prediction/assets/71796909/8e6c3a06-93b9-41b7-ac45-07b9087306fd)

## Business Insights & Recommendations

- If the duration between the booking date and arrival date is long, it's more likely customers tend to cancel their booking because of that long 
  duration that allows customers to explore other options or just change their plans, even in other cases customers may forget about the booking at 
  all because of the lack of engagement.
  
    *In such situations, the customer care team should keep in touch with those clients in advance of their scheduled arrival day to reduce the 
     likelihood of cancellation*

- It's better to provide flexible payment solutions like installments, especially for the online market segment, where the customers have a chance 
  of cancellation about 40% .

    *Also, providing fair deals and within the range of the market prices that will help to avoid cancellation. cancellations may happen due the 
     high prices with less services included with this price, especially if the hotel has competitors who provide the same services with offers or 
     discounts. And as we know customers always want to pay less and have more and once that option is available to them they will easily change 
     their mind.*

- From our earlier analysis, we know that the customers who have a few special requests are more likely to cancel their booking at some point. In 
  such a situation, INN hotel staff can be initiative and ask the customers if they need any special requests regard their booking and they can offer 
  to them, moreover they can encourage those customers who are more likely will cancel the booking for these reasons, and of course without exaggeration 
  by offer them special treatments i.e. if the customer show up at their scheduled booking, they will get another night to stay at the room with 
  the view without any charges and in the date they will select, ...etc, hopefully they can drive those customer to stay.

- It's INN hotel responsibility for setting the rules and conditions regarding their cancellation policy. Therefore, the customers who booked will have a clear view of the hotels bookings policy 
  when they agree to it in advance. whereas, they can set conditions like that the booking fees will not be refunded after 48 hours has passed from the scheduled booking. In fact, providing such 
  a cancellation policy will preserve the rights for both parties.

## Refernces

[INN Hotels Bookings Cancellations Prediction Project File](https://github.com/hayasalman/INN-Hotels-Bookings-Cancellations-Prediction/blob/main/INN-Hotels%20Bookings%20Cancellations-Prediction.ipynb)

## Suggestions

- We could use hypertuning to determine the best parameters for the random forest model.
- We may also try the neural networks and see if we can improve the performance further.





  
