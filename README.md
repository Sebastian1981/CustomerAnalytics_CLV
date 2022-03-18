# Customer Lifetime Value Approximation Using Machine Learning

## Project Overview
>In marketing, customer lifetime value (CLV or often CLTV), lifetime customer value (LCV), or life-time value (LTV) is a prognostication of the net profit contributed to the whole future relationship with a customer. The prediction model can have varying levels of sophistication and accuracy, ranging from a crude heuristic to the use of complex predictive analytics techniques. One of the major uses of CLV is customer segmentation, which starts with the understanding that not all customers are equally important. CLV-based segmentation model allows the company to predict the most profitable group of customers, understand those customers' common characteristics, and focus more on them rather than on less profitable customers. CLV-based segmentation can be combined with a Share of Wallet (SOW) model to identify "high CLV but low SOW" customers with the assumption that the company's profit could be maximized by investing marketing resources in those customers. [**Ref:** https://en.wikipedia.org]

In this project we chose two seperate approaches here to model the CLV. In the [CLV-regression approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Regression.ipynb), we fit a regression model to estimate the individual CLV of each customer. In the [CLV-classification approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Multiclass.ipynb), we fit a binary classifier to assign each customer to either the segment Low-CLV or High-CLV. The machine learning models are build on historical customer data with the CLVs been pre-computed for each customers as shown below.

![Customer Data Table ](/images/datatable.jpg)

Besides pure building and evaluating machine learnign models we also focus on model explainability and model fairness.


## CLV Regression Modeling Results
### Exploratory Data Analysis (EDA)
The pearson correlation analysis between numeric features and the target (i.e. CLV) reveals moderate correlations for the features "Monthly Premium Auto" and "Total Claim Amount".

![Pearson Correlation Table ](/images/PearsonCorrelation.jpg)

The boxplots show a clear effect of the feature "Vehicle Class" on CLV.

![Boxplot: CLV vs Vehicle Class](/images/CLV_vehicle_class.jpg)

With respect to gender, we observe no obvious effect on CLV which is an important precondition for model fairness.

![Boxplot: CLV vs Gender](/images/CLV_gender.jpg)

### CLV Model Evaluation
For modeling the CLV, we used a "Light Gradient Boosting Machine" algorithm (LightGBM) which can explain 68% of the variance (R2) on unseen customer data.

![Regression Model result ](/images/CLV_regression_model.jpg)

### CLV Model Explanation and Model Fairness 
#### Global Explanation
In consistence with the EDA-findings the SHAP values reveal that overall the features "Number of Policies" and "Monthly Premium Auto" have a significant impact on CLV. The feature "Vehicle Class" in return has only moderate impact. With respect to model Fairness, the sensitive feature "Gender" also has moderate impact on CLV, which we should keep in mind. 

![Regression Model mean abs shap vals ](/images/regression_model_meanshap.jpg)

#### Local Explanation
With focus on local model explanation, the force-plot below shows the effect of the different features on the CLV of a single customer. We can see that the expected CLV is located around 8400 (base value). The features "Monthly Premium Auto" and "Number of Policies" push the CLV to a lower value of around 5100. Then there are some features with minor impact (e.g. feature "Income"), however increasing the CLV to the final value of around 5500.  

![Regression Model shap forceplot](/images/regression_model_shaplocal.jpg)



