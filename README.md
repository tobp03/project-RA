# Lending Risk Assessment Modeling 

## Overview
This is my project which was submitted as an answer for semifinal statistics competition held by Universitas Indonesia called STC LOGIKA UI 2024. 

STC Paylater is a fictional BNPL company which primarily gains revenue by lending money. This project is inteded to help the BNPL company to understand the risk associated with each borrower. The goal of this project is understanding the previous customers demographic to decide whom should they lend by assessing customers repayment ability.

Keywords : Data Analysis, K-Means Clustering, Multi-Class Classification, Risk Assessment



## Technical Aspect
This project is mainly split into two steps
1. Customer segmentation with unsupervised learning. In this step, payment history and loan information are thoroughly analyzed and featured engineered to prepare the data. Then Weighted K-Means Clustering is performed on chosen variables in order to segment the custmer by their associated risks. Each cluster is studied to determine its representation.
2. Customer risk assessment with supervised learning. In this step, applicant data with defined labels indicating the past response are used to train models. The models is then used on unseen data to make prediction wheter certain customer have risks associated.
3. 
## Dataset
1. Installment payment history. Past payment data for each previous loan.
2. Previous loan application. Contains information for every loan application made towards the company. Each row represents a single previous application.
3. Applicant demographic and loan information.
   
Dataset 1 and 2 contains the same variabel SK_ID_PREV or sequential previous id. A single applicant could have made more than one loan application. Every applicant have a single unique user ID.

## Results
1. **Customer segmentation**

The variable 'unpaid_debt','years_late','credit_ratio','YIELD_GROUP',and 'NFLAG_INSURED_ON_APPROVAL' are chosen as inputs for Weighted K-Means Clustering, the variables are weighted as [1, 1.15, 0.85, 1, 0.95] in order. Based on Elbow's Method as below:

<p align="center">
  <img src="https://github.com/tobp03/project-RA/assets/83869882/479deb35-4c45-4adf-9746-407371bd680c" alt="Your Image">
</p>

Based on the image above K=3 and K=4 doesnt provide significant gradient difference, however the K=4 are chosen for more fine grained label. 
<p align="center">
  <img src="https://github.com/tobp03/project-RA/assets/83869882/47a223dd-966e-4211-976e-03298b17b4a1" alt="Your Image">
</p>

<p align="center">
  <img src="https://github.com/tobp03/project-RA/assets/83869882/d1e36747-ec2d-42f9-9798-efee2764bd41" alt="Your Image">
</p>

With K=4, based on the image above we can summarize customer as:
* Cluster 0 describe customers that fully payed their bills in time and also applied insurance on previous applications. This cluster could be summarized as low-risk insured customers.
* Cluster 1 describe customers that fully payed their bills in time, however didn't apply for insurance on previous applications. This cluster could be summarized as low-risk uninsured customers.
* Cluster 2 describe customers that payed their bills in time, however have accumulated some amount of debt due to underpayment. This cluster could be summarized as high-risk underpayed customers.
* Cluster 3 describe customers that fully payed their bills, however didn't payed it in time. This cluster could be summarized as high-risk late payment customers.

2. **Modeling**

The cluster from the previous step is then set as label variable on the dataset. The dataset is then split into training and testing data as 85:15. Then the training inputs are oversampled with SMOTE-NC due to imbalance labels. Next the data is then modeled using different methods. The results are as follows: 
<p align="center">
  <img src="https://github.com/tobp03/project-RA/assets/83869882/83b02fc0-bce0-4b73-92a9-b68bbba2835d" alt="Your Image">
</p>
Based on the table above, all the model couldnt predict any Cluster 2 and Cluster 3. This is shown from the low F-1 score on both clusters which could be the result of poor predictive features. In summary, the models above couldn't give accurate assessment towards customers which are high-risk, which isn't desired for a BNPL company. Some ideas which could be implemented in the future:

1. Customer segmentation by using other variables.  The 5 variables chosen might not be the best choice to differentiate applicants associated risks.
2. Applicant demographic and loan information, which servers as the input variables might need a more thorough analysis and data cleaning. Especially identifying which variables impact the most towards the segmented customer.
3. Applying PCA before K-Means might help with dealing with noise and better interpretability.
