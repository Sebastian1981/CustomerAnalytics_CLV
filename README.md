# Customer Lifetime Value (CLV) Approximation Using Machine Learning Algorithms

## Project Overview
>In marketing, customer lifetime value (CLV or often CLTV), lifetime customer value (LCV), or life-time value (LTV) is a prognostication of the net profit contributed to the whole future relationship with a customer. The prediction model can have varying levels of sophistication and accuracy, ranging from a crude heuristic to the use of complex predictive analytics techniques. One of the major uses of CLV is customer segmentation, which starts with the understanding that not all customers are equally important. CLV-based segmentation model allows the company to predict the most profitable group of customers, understand those customers' common characteristics, and focus more on them rather than on less profitable customers. CLV-based segmentation can be combined with a Share of Wallet (SOW) model to identify "high CLV but low SOW" customers with the assumption that the company's profit could be maximized by investing marketing resources in those customers. [**Ref:** https://en.wikipedia.org]

We chose two seperate approaches here to model the CLV. In the first approach, the [CLV-Regression Approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Regression.ipynb), we fit a regression model to estimate the individual CLV of each customer. In the second approach, the [CLV-Classification Approach](https://github.com/Sebastian1981/CustomerAnalytics_CLV/blob/main/CustomerLifetimeValue_Multiclass.ipynb), we fit a binary classifier to segment customers into two categories (i.e. low and high CLV). The machine learning models will be built using historical customer data with the CLV already been computed for each customers as shown below.  
![Customer Data Table ](/images/datatable.jpg)
Besides pure building and evaluating machine learnign models we also focus on model explainability and model fairness.


## CLV Regression Modeling Results
### Exploratory Data Analysis
The table below reveals moderate linear correlations between the target variabel (i.e. CLV) and the two numeric variables "Monthly Premium Auto" and "Total Claim Amount".  
![Pearson Correlation Table ](/images/PearsonCorrelation.jpg)
Besides pure building and evaluating machine learnign m
