# Car Price Prediction Using Machine Learning
## Introduction
<strong>Problem Statement:</strong> For my final project, I aim to develop a predictive model capable of accurately estimating the prices of different cars and analyzing the trends and patterns within these prices of cars. A large percentage of people end up buying a car at least once in their life, and it is generally a significant and thoughtful purchase. This model may be useful for people buying a car for the price time and wanting to know how much they should pay for it, given a set of feature parameters. These predictions will allow them to make informed financial decisions that optimize their choice, receiving a car that is worth the amount they are paying. The successful development of a model will not only enhance predictive capabilities for car prices but will also empower stakeholders in the car industry with actionable insights. Car salesmen can align their prices with customer preferences, learning what features people are willing to pay more for.

## Data Description
<strong>Dataset Description:</strong> Data for this project is sourced from Kaggle in CSV format, providing comprehensive information about various titles cars with different brands and models. Challenges may arise in constructing an accurate regression model due to the inherent volatility of the data due to metrics not monitored, such as location and therefore cost of living. However, I believe that certain predictive variables will be able to at least somewhat predict car prices with some degree of accuracy.

This dataset contains comprehensive information about various cars and their prices, including brand, year, engine size, fuel type, transmission mileage, condition, and model. It contains 8 columns representing their different features and attributes, which I can use to help predict prices.

## Exploratory Data Analysis (EDA)
Before diving into machine learning, we performed a detailed exploratory analysis to identify which features are most strongly correlated with car prices.

The grid of bar plots showcases the average car prices of different models in each car brand. As illustrated above, all of the different brands seem to have similar prices on average. However, it is important to note that <strong>BMW, Mercedes, and Tesla have slightly higher average prices.</strong> This would align with the idea that more luxurious brands like BMW and Mercedes will be more expensive. With Tesla's boost through its electric vehicles, it is also understandable that the brand is in the top three most expensive brands listed here.

In the bar plot, we see how manual and automatic transmission cars compare to price, with them also being sorted by fuel type. <strong> Diesel-fueled cars seem to be the most expensive fuel type,</strong> which agrees with the idea that diesel is better for fuel efficiency and less available than petrol. A lower supply of diesel drives its cost higher, making it more expensive.

<strong>Another point to note is that electric automatic cars seem to be more expensive than electric manual cars.</strong> This can be because combining electric cars with automatic transmissions can be a complex process, and there is a higher demand for this style rather than electric manual cars. Meanwhile, electric manual cars are less in demand, however, they might be more affordable, or cheaper.

From the scatterplot, we learn that there is <strong>no correlation between engine size and prices,</strong> making it not useful during the predictive modeling section.

The table shows the average year produced and the average price of cars grouped by the condition of the car. As expected, <strong>cars in a ‘New’ condition have the highest average year, meaning that they were produced more recently.</strong>

<strong>An interesting deviation from what is expected comes in the form of average prices for the ‘New’ condition.</strong> While the average price of cars in the ‘Like New’ is higher than used cars, ‘New’ cars actually have a lower price than both other conditions. This can possibly be due to a biased data set from different locations and therefore different costs of living.

## Model and Evaluations
To predict car prices, I decided to use multiple different regression models and see which one performs the best in predicting these prices and accounting for the variation in my data and the fluctuations in price. For each of these models, I decided to utilize an 80-20 train-test split, training my model on 80% of the data and then testing it on the remaining 20%.

<strong>Baseline:</strong> I evaluated the success of each of my models by comparing its performance metrics, such as the model's mean squared error, against this baseline's mean squared error. To get my baseline value, I simply took the mean car price of my dataset. The mean squared error of the baseline model is around 784046723. The root mean squared error (RMSE) helps put things in perspective as it shows that on average, the model's predictions are off by about $28,001.

<strong>Multiple Regression Model:</strong> I chose to build a multiple regression model because I wanted to use independent variables to predict the dependent variable, as I believed these predictors may have collectively influenced the car price. Multiple linear regression allowed me to model the relationships between the price and each of these predictors while also considering their combined effect.

The results were a training MSE of around 730377931 and a testing MSE of around 784095348, with the testing RMSE being around 28002.

Overall, my multiple regression model performed better than my baseline in the training data, but not the testing data. Only the training data outperformed the baseline, with the testing data performing very similar to the baseline. I think this may be due to similarities between the brand and model features.

The inputs that were the most important in this scenario were the brand and model features. Fuel type was the least important for predicting the car prices in this model.

<strong>K-Nearest Neighbors Regression Model:</strong> I chose to try the k-nearest neighbors regression evaluation metric next because KNN makes predictions based on the similarity of instances in the feature space. If car prices were influenced by local patterns or clusters of similar cars with comparable features, KNN would be effective in capturing these localized relationships.

The results were a training MSE of around 725471107 and a testing MSE of around 776192791, with the testing RMSE being around 27860.

The K-Nearest Neighbors regression model performed better than both my baseline and my multiple regression model. While my training data performed much better than my testing data, my testing data still performed very well in comparison to my previous models. I think this was due to the fact that the KNN model captured non-linear patterns in the data, which might be present within the car prices data. Additionally, using grid search for hyperparameter tuning within this model may have led to its better overall performance. By selecting the optimal number of neighbors to use, I was able to fine-tune the model for better results.

This time, the most important feature in this scenario was the fuel type, followed by brand. The least important feature was the model feature.

<strong>XGBoost Regression Model:</strong> For my last model, I also chose to build an XGBoost model which builds an ensemble of decision trees, where each tree is a weak learner trained to correct the errors of the previous ones. Trees are added sequentially, and each tree focuses on improving the predictions made by the ensemble so far. I chose this model because, like k-nearest neighbors, decision trees can capture non-linear relationships within the car price data. XGBoost also excels at handling complex interactions, which is important when car prices depend on intricate features like Fuel Type, Brand, and Model.

The results were a training MSE of around 732104074 and a testing MSE of around 768095558, with the testing RMSE being around 27715.

Overall, my XGBoost model performed the best in comparison to all of the other models I developed. This model also had a smaller disparity between my mean squared errors for my testing data compared to my training data, and the testing data's mean squared error was the lowest out of all the models, which means it was the most successful in predicting car prices.
Fuel Type was the most important feature, with Brand and Model not contributing as much towards this model.

## Summary
In my analysis of car prices, all the models I constructed demonstrated improved performance over the baseline predictor, except for the multiple regression model, which had a similar success rate. This signified their utility and significance. The models ranked in terms of performance are as follows: XGBoost Regression, K-Nearest Neighbors Regression, and Multiple Linear Regression.

<strong>Key Findings:</strong>

</strong>1) Success of XGBoost Regression:</strong> The XGBoost regression model emerged as the most effective, showcasing the best predictive capabilities out of all the models. Its robust performance suggests its suitability for capturing complex relationships within the car pricing data. XGBoost is an ensemble learning method based on decision trees, and its boosting technique, which focuses on correcting errors from previous models, allowed it to capture non-linear relationships and complex interactions between features that other models struggled to represent. Its ability to combine multiple decision trees, each focusing on a different aspect of the data, contributed to its superior performance. The model was able to detect subtle patterns in the data, such as the impact of fuel types on car prices, and account for interactions between features that would otherwise be missed in simpler models.

<strong>2) Feature Impact:</strong> Feature importance in all of these models was changing, with the Brand and Model features having a similar impact in each model, most likely due to the similarity between the features and price pattern.

<strong>3) Variable Influence:</strong> In the XGBoost model, the Brand and Model impact was negative, showing that while these insights were helpful in the other two models, they were not contributing positively to this predictive model.
In conclusion, the ensemble nature of the XGBoost model, incorporating diverse decision trees, proved advantageous in capturing intricate patterns within the data. The changing emphasis on different features shows how different models treat features differently. The findings provide a nuanced understanding of feature importance and model performance, offering valuable insights for future analyses and predictive modeling in the realm of car prices.

## Next Steps
To further enhance the predictive capabilities of the models and gain deeper insights into the factors influencing car prices, several additional features and data sources should be incorporated. These will allow the model to not only provide more accurate price predictions but also give a more holistic view of the various elements that drive the car market. Below are the key features that can be integrated:

<strong>1. Economic Conditions Data</strong>

Incorporating broader economic conditions into the model would add a significant layer of insight. Economic factors, such as interest rates, GDP growth, regional economic performance, and even inflation, play a key role in determining car prices. The economic environment directly influences consumer affordability and demand for vehicles. For example, when interest rates rise, car loans become more expensive, which could lead to a decrease in car sales, particularly in price-sensitive segments like used cars. Similarly, a growing GDP or regional economic growth could increase disposable income and stimulate demand for cars, driving prices higher.

By integrating this data into the model, I would be able to assess how fluctuations in the economy influence buyer behavior, making the predictions more dynamic and adaptable to real-time changes. For instance, a dip in consumer confidence during an economic downturn might reflect a sudden drop in demand for luxury cars, or a rise in GDP might suggest greater demand for mid-range vehicles. This could also help identify market trends that impact both new and used car prices, which is valuable for predicting future price movements.

<strong>2. Location Data</strong>

Incorporating location-specific data is another crucial next step for enhancing the model. The geographical region in which a car is sold can have a significant effect on its price. This can be due to various factors such as climate, terrain, and local preferences. For example, SUVs and trucks might be more popular and hold higher value in rural or mountainous regions due to their ability to handle rough terrain, while compact cars or sedans may be more common and valued in urban areas where fuel efficiency and space efficiency are prioritized.

Additionally, location data could account for regional economic conditions. Cars in affluent cities like New York or San Francisco might generally command higher prices due to higher income levels and greater demand for luxury and premium brands. Conversely, cars in rural areas might be priced differently based on local demand, car type preferences, and regional market conditions. Adding this data would make the model more adaptable to the geographical realities of car pricing and offer insights into regional pricing trends.

By including location data, the model could highlight the role of regional preferences in pricing, as well as geographic factors like weather that influence the types of cars in demand (e.g., convertibles might have lower prices in colder climates due to limited demand). This added layer would help identify pricing variances based on the location and make the predictions more tailored to specific areas.

<strong>3. Luxury Features</strong>

Including luxury features in the analysis would significantly improve the accuracy of car price predictions, especially in the premium car market. Modern vehicles come equipped with a variety of luxury features such as advanced safety systems, high-end infotainment technologies, premium interiors, and autonomous driving capabilities. These enhancements can have a profound impact on a car’s resale value.

By analyzing how these luxury features contribute to a car’s price, the model could provide a clearer understanding of the demand for premium offerings and the price elasticity of luxury cars. For instance, cars equipped with state-of-the-art safety systems or AI-powered navigation might command a premium, while cars with basic features may not see such high returns. In addition, features like leather seats, premium audio systems, and sunroofs could increase the car’s appeal and price, especially in markets where buyers are willing to pay for comfort and style.

</strong>4. Private Seller vs. Dealership</strong>

One aspect that is often overlooked in car price predictions is the type of seller. There is often a price difference between vehicles sold by private sellers and those sold by dealerships. Cars sold by dealerships are typically priced higher due to the added value of warranties, certifications, and the perceived trustworthiness of the seller. Additionally, dealerships may offer financing options or other services, which can make the car appear more valuable.

On the other hand, private sellers may price their cars lower due to a desire for a quicker sale and the lack of overhead costs. However, some buyers might still be willing to pay a premium for cars sold through dealerships, especially if they trust the car’s condition or value the dealership’s warranty. By differentiating between private sellers and dealerships, I would be able to identify specific pricing trends based on seller type, which could lead to more accurate price predictions. For example, a car sold by a luxury dealership may fetch a higher price than the same car sold privately, even if the condition and mileage are identical.

## Conclusion

By integrating these additional features<strong>—economic conditions data, location-specific insights, luxury features, and seller type—</strong>into the model, I would be able to further refine its accuracy and gain a more nuanced understanding of car pricing dynamics. Each of these features offers a deeper look at the factors influencing vehicle valuations, helping to create a more holistic prediction framework.

 - <strong>Economic conditions</strong> would allow the model to adapt to macroeconomic shifts, giving it predictive power in fluctuating markets.
 - <strong>Location data</strong> would improve the model’s ability to account for regional preferences and market differences.
 - <strong>Luxury features</strong> would enhance the model’s ability to predict high-end vehicle prices, allowing it to capture the nuances of the premium market.
 - <strong>Seller-type</strong> data would help differentiate between prices in different sales channels, offering insights into buyer behavior and pricing strategies.

Incorporating these additional features into the model would result in more accurate predictions, making it an even more valuable tool for buyers, sellers, and industry stakeholders looking to make informed decisions in the dynamic used car market. With these refinements, the model would be well-positioned to provide actionable insights that go beyond simple price predictions, offering a more comprehensive understanding of what drives the used car market.




