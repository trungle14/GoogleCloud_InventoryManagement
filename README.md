# GoogleCloud_InventoryManagement_ML_Forecasting

Abstract: The project introduces a comprehensive solution for enhancing inventory management in the e-commerce domain. Leveraging the robust capabilities of Google Cloud Platform, our system integrates Big Data and Machine Learning to optimize inventory levels. The core of our analytics pipeline resides in Google BigQuery, where data summarization and analysis take place, providing dynamic insights into inventory availability and accurate demand forecasting. The culmination of our efforts is a user-friendly dashboard developed on Google's Looker Studio. This platform empowers end-users and clients to intuitively visualize product inventory counts and forecasts, facilitating informed decision-making and efficient inventory control.

# Dataset 

The [eCommerce dataset](https://console.cloud.google.com/marketplace/product/bigquery-public-data/thelook-ecommerce?project=galvanic-portal-404814) contains information about customers, products, orders, logistics, web events and digital marketing campaigns. The contents of this dataset are synthetic, and are provided to industry practitioners for the purpose of product discovery, testing, and evaluation.

# Improve inventory management with sales forecasting deployed by BigQuery ML and AI Platform Training & Prediction

In the e-commerce sector, effectively managing inventory is crucial: you need to maintain the right balance, ensuring you have enough stock without overstocking. For large e-commerce companies, this involves managing inventory levels for a vast array of products.

To guide inventory decisions, historical sales data is invaluable. By analyzing past customer purchase patterns, you can predict future buying trends, helping to determine optimal inventory levels. Time series forecasting is an essential tool in this process.

For data science teams supporting e-commerce inventory management, this entails generating numerous forecasts and managing the infrastructure required for machine learning (ML) model development and deployment. However, by utilizing BigQuery ML in Google Cloud Platform (GCP), you can streamline this process. BigQuery ML allows you to train, evaluate, and deploy ML models directly using SQL statements, bypassing the need for a separate ML infrastructure. This approach can significantly save time and resources in your e-commerce sales forecasting project.



# Set up time series modeling works in BigQuery ML
A time series model with BigQuery ML, multiple components are involved, including an Autoregressive integrated moving average (ARIMA) model. For this project, The BigQuery ML model creation pipeline uses the following components:

Pre-processing: Automatic cleaning adjustments to the input time series, inspect the most appropriate training data which addresses issues like missing values, duplicated timestamps. There are multiple levels we can also consider for time series, easily customized function on demand:
1. Product category level
2. Specific products level
3. Store level

Holiday effects: Time series modeling in BigQuery ML can also account for holiday effects. By default, holiday effects modeling is disabled. But since this data is from the United States, and the data includes a minimum one year of daily data, you can also specify an optional HOLIDAY_REGION. 
Seasonal and trend decomposition using the Seasonal and Trend decomposition using Loess (STL) algorithm. Seasonality extrapolation using the double exponential smoothing (ETS) algorithm.
Trend modeling using the ARIMA model and the auto.ARIMA algorithm for automatic hyper-parameter tuning. In auto.ARIMA, dozens of candidate models are trained and evaluated in parallel. The best model comes with the lowest Akaike information criterion (AIC).
We can use a single SQL statement to train the model to forecast a single product or to forecast multiple products at the same time. For more information, see The CREATE MODEL statement for time series models.



# Deployment quick guide:
1. Create a new project on GCP platform
2. Enable BigQuery, Vertex AI, AI platform, LookerStudio services and create new instance and new notebook with python kernel -- You are ready to run sales forecast
3. Prepare training dataset
3.1. Upload/Import dataset in Cloud storage and BigQuery, create training dataset under your project or
3.2. Enable Streamming by Dataflow for data training preparation
4. Develop and train model followed by making prediction
5. Export output as predicted sales for further usage as monitoring dashboard

Here is the example how we can integrate forecasted sales into current dashboard:

<img src="[https://i.ibb.co/RhC6V4R/googletrends-81-1-1.png](https://ibb.co/51NCZF8"><img src="https://i.ibb.co/D1xmdpC/Picture1.png)" alt=""></a>
    </td>



## Suggestion for further deployment
1. Adding lagging and rolling features to the model for each training window
2. Considering using advanced models like XGBoost or LightGBM 
3. Adding insightful features like Top 25 Rising queries from **Google Trends** <td>
      <a href="https://console.cloud.google.com/marketplace/product/bigquery-public-datasets/google-search-trends?_ga=2.261190030.2019434361.1656948847-1975246695.1656948843&project=galvanic-portal-404814">
        <img src="https://i.ibb.co/RhC6V4R/googletrends-81-1-1.png" alt=""></a>[dataset Google trends on Google BigQuery](https://console.cloud.google.com/marketplace/product/bigquery-public-datasets/google-search-trends?_ga=2.261190030.2019434361.1656948847-1975246695.1656948843&project=galvanic-portal-404814)
    </td>

## Docoments
Presentation Recording: [https://drive.google.com/file/d/1Roq84Chgowoh7PfVIuHarL1su3gnZMOA/view?usp=drive_link\
Interactive dashboard: https://lookerstudio.google.com/reporting/ebea5752-963e-4a55-aa45-ebb846519557/page/p_057twy79bd?s=nIzjhrMlO8g



