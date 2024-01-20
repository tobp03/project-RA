# Lending Risk Assessment Modeling 

## Overview
This is my project which was submitted as an answer for semifinal statistics competition held by Universitas Indonesia called STC LOGIKA UI 2024. 

STC Paylater is a fictional BNPL company which primarily gains revenue by lending money. This project is inteded to help the BNPL company to understand the risk associated with each borrower. The goal of this project is understanding the previous customers demographic to decide whom should they lend by assessing customers repayment ability.

Keywords : Data Analysis, K-Means Clustering, Multi-Class Classification, Risk Assessment

## Dataset
1. Installment payment history. Past payment data for each previous loan.
2. Previous loan application. Contains information for every loan application made towards the company. Each row represents a single previous application.
3. Applicant demographic and loan information. Training and testing data.
Dataset 1 and 2 contains the same variabel SK_ID_PREV or sequential previous id. A single applicant could have made more than one loan application. Every applicant have a single unique user ID.

## Technical Aspect
This project is mainly split into two steps
1. Customer segmentation with unsupervised learning. In this step, payment history and loan information are thoroughly analyzed and featured engineered to prepare the data. Then Weighted K-Means Clustering is performed on chosen variables in order to segment the custmer by their associated risks. Each cluster is studied to determine its representation.
2. Customer risk assessment with supervised learning. In this step, applicant data with defined labels indicating the past response are used to train models. The models is then used on unseen data to make prediction wheter certain customer have risks associated.

## Results
