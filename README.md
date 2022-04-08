# Customer Lifetime Value Approximation Using Machine Learning

## Project Overview
>In marketing, customer lifetime value (CLV or often CLTV), lifetime customer value (LCV), or life-time value (LTV) is a prognostication of the net profit contributed to the whole future relationship with a customer. The prediction model can have varying levels of sophistication and accuracy, ranging from a crude heuristic to the use of complex predictive analytics techniques. One of the major uses of CLV is customer segmentation, which starts with the understanding that not all customers are equally important. CLV-based segmentation model allows the company to predict the most profitable group of customers, understand those customers' common characteristics, and focus more on them rather than on less profitable customers. CLV-based segmentation can be combined with a Share of Wallet (SOW) model to identify "high CLV but low SOW" customers with the assumption that the company's profit could be maximized by investing marketing resources in those customers. [**Ref:** https://en.wikipedia.org/wiki/Customer_lifetime_value]

In this project two seperate approaches were chosen to model the CLV. In the [CLV-regression approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Regression.ipynb), a regression model was fit to estimate the individual CLV of each customer. In the [CLV-classification approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Multiclass.ipynb), a binary classifier was fit to assign each customer to either the segment "Low-CLV" or "High-CLV". The machine learning models are build on historical customer data with the CLVs been pre-computed for each customers as shown below. Besides pure building and evaluating machine learnign models the focus was also set on model explainability and model fairness.

![Customer Data Table ](/images/datatable.jpg)

## Regression Modeling Results
### Exploratory Data Analysis (EDA)
The pearson correlation analysis between numeric features and the target (i.e. CLV) reveals moderate correlations for the features "Monthly Premium Auto" and "Total Claim Amount".

![Pearson Correlation Table ](/images/PearsonCorrelation.jpg)

The boxplots show a clear effect of the feature "Vehicle Class" on CLV.

![Boxplot: CLV vs Vehicle Class](/images/CLV_vehicle_class.jpg)

With respect to gender, no apparent effect on CLV can be observed which is an important precondition for model fairness.

![Boxplot: CLV vs Gender](/images/CLV_gender.jpg)

### Model Evaluation
For modeling the CLV, a "Light Gradient Boosting Machine" algorithm (LightGBM) was used explaining 68% (=R2) of the variance on unseen customer data.

![Regression Model result ](/images/CLV_regression_model.jpg)

### Model Explanability
#### Global Explanability
In consistence with the EDA-findings the SHAP values reveal that overall the features "Number of Policies" and "Monthly Premium Auto" have a significant impact on CLV. The feature "Vehicle Class" in return has only moderate impact.

![Regression Model mean abs shap vals ](/images/regression_model_meanshap.jpg)

#### Local Explanability
With focus on local model explanation, the plot below shows the effects of the different features on the CLV of a single customer. We can see that the expected CLV is located around 8400 (base-value). The features "Monthly Premium Auto" and "Number of Policies" push the CLV to lower values of around 5100 whereas other features like "Income" have a positive effect increasing the CLV to the final value of around 5500.  

![Regression Model shap forceplot](/images/regression_model_shaplocal.jpg)

### Model Fairness
#### Unmitigated Model
With respect to model fairness, the figure below shows the gender-biased model performance in terms of R2 towards the female subgroup. This indicates that the model can predict the CLV for women clearly better than for men. 

![Regression Model R2 gender dependence](/images/R2_gender_biased.png)

To mitigate this effect, several models were trained to find the best trade-off between model performance and model fairness, as depicted in the figure.

![Regression Models Mitigated](/images/model_fairness.png)



