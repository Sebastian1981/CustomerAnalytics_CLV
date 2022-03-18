# Customer Lifetime Value (CLV) Approximation Using Machine Learning Algorithms

## Project Overview
>In marketing, customer lifetime value (CLV or often CLTV), lifetime customer value (LCV), or life-time value (LTV) is a prognostication of the net profit contributed to the whole future relationship with a customer. The prediction model can have varying levels of sophistication and accuracy, ranging from a crude heuristic to the use of complex predictive analytics techniques. One of the major uses of CLV is customer segmentation, which starts with the understanding that not all customers are equally important. CLV-based segmentation model allows the company to predict the most profitable group of customers, understand those customers' common characteristics, and focus more on them rather than on less profitable customers. CLV-based segmentation can be combined with a Share of Wallet (SOW) model to identify "high CLV but low SOW" customers with the assumption that the company's profit could be maximized by investing marketing resources in those customers. [**Ref:** https://en.wikipedia.org]

We chose two seperate approaches here to model the CLV. In the first approach, the [CLV-Regression Approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Regression.ipynb), we fit a regression model to estimate the individual CLV of each customer. In the second approach, the [CLV-Classification Approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Multiclass.ipynb), we fit a binary classifier to segment customers into two categories (i.e. low and high CLV). The machine learning models will be built using historical customer data with the CLV already been computed for each customers as shown below.

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

### CLV Model Explanation
in consitence with the EDA-findings the SHAP values reveal that the features "Number of Policies" and "Monthly Premium Auto" have a high impact on CLV. The feature "Vehicle Class" in return has only moderate impact. With respect to model Fairness, the sensitive feature "Gender" also has moderate impact on CLV, which we should keep in mind. 

![Regression Model mean abs shap vals ](/images/regression_model_meanshap.jpg)


