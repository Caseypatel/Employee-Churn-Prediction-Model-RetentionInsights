# Employee-Churn-Prediction-Model-RetentionInsights

### Project Overview

The HR department at Salifort Motors has taken the first step towards addressing employee satisfaction by collecting survey data from employees. However, they now face the challenge of analyzing this data to gain meaningful insights. Their primary objective is to identify the key factors that contribute to an employee's decision to leave the company.

### Project Goal

The goal of this project is to develop a predictive model that can forecast the likelihood of an employee leaving the company. By doing so, Salifort Motors can proactively address the concerns of employees who are at risk of leaving, thereby improving overall employee satisfaction and reducing turnover rates. Additionally, the model will provide valuable insights into the primary drivers of employee attrition, enabling the company to make data-driven decisions to improve employee retention.

### Data Oerview 

- satisfaction_level: The employee’s self-reported satisfaction level [0-1]

- last_performance_rating: Score of employee's last performance review [0-1]
  
- number_of_projects: Number of projects the employee contributes to
  
- avg_monthly_hours: Average number of hours the employee works per month
  
- years_at_company: How long the employee has been with the company (years)
  
- had_work_accident: Whether the employee had an accident at work (yes or no)
  
- has_left_company: Whether the employee has left the company (yes or no)
  
- promoted_in_last_5_years: Whether the employee was promoted in the last 5 years

- department: he department where the employee works
  
- salary_level: The salary category of the employee (low, medium, or high)

### Key Questions to Answer

1) What are the most significant factors that influence an employee's decision to leave the company?
2) How can Salifort Motors identify employees who are at risk of leaving and take proactive measures to retain them?
3) What insights can be gained from the data to inform strategies for improving employee satisfaction and reducing turnover rates?

### The model's impressive performance metrics are as follows:

<b>"RetentionInsights"</b> model has demonstrated exceptional performance in predicting employee churn. Given the significant cost of losing an employee due to false negatives (i.e., predicting they will stay when they actually leave), we opted for the highest Recall model.

##### Final Model Accuracy:
  - 98% for classifying Employee Churn.
##### Recall Score: 
  - 93%: The model accurately identifies a high proportion of employees who are likely to leave, minimizing the risk of false negatives.
##### F1 Score: 
  - 95%: The model strikes a balance between precision and recall, ensuring that it is both accurate and comprehensive in its predictions. These results indicate that the "RetentionInsights" model is well-calibrated and effective in identifying employees at risk of churn.

### <b>EDA (Exploratory Data Analysis)</b> 

1). Visualizing discrete columns 'number_of_projects', 'avg_monthly_hours', 'years_at_company'. 

![image](https://github.com/user-attachments/assets/ce20ce0d-0688-4032-bb6f-64c8b289a047)
![image](https://github.com/user-attachments/assets/3e311f51-9308-4b44-9f74-230cd375e238)

'Years_at_company' has the outliers which is acceptable as people might have stayed longer based on their interaction with internal culture. 

2). Then, I visualized target variable ("has_left_company")

![image](https://github.com/user-attachments/assets/f50eb22a-6756-4e41-9bef-76c3175afac5)

As we can see in the above figure, target variable is imbalanced. 

#### Pairplot Analysis 
![image](https://github.com/user-attachments/assets/b1e376cd-3a6c-4e73-a8dc-abe3055a0850)
![image](https://github.com/user-attachments/assets/3fd0845f-5f1e-48fd-bd7e-728615f4b208)

<b>Preliminary Insights into Employee Turnover:</b>

- <b>Satisfaction Level:</b> A low Satisfaction Level appears to be a strong indicator of an employee's likelihood to leave the company.
- <b>Number of Projects:</b> A high Number of Projects seems to be associated with a higher tendency for employees to leave.
- <b>Average Monthly Hours:</b> Similarly, a high Average Monthly Hours is linked to a greater likelihood of employee turnover.
- <b>Time Spend at the Company:</b> Interestingly, employees who leave the company tend to have spent 5 or fewer years at the organization.

#### Analysis of employees who left the company 

Based on the below scatterplot we can conclude that there are three cohorts of employees who stand out from the rest due to their higher-than-average probability of leaving the company. By analyzing the characteristics and patterns within these cohorts, we can gain a deeper understanding of the factors that drive employee turnover and develop targeted strategies to address their specific needs and concerns.

![image](https://github.com/user-attachments/assets/04c51fd5-8750-4755-86d9-4ba87c7ce46c)

#### Analysis of employees who stay

Notably, the scatter plot reveals a fairly even distribution of satisfaction levels, hours worked, and number of projects among employees who stayed with the company, particularly for those with fewer than 7 projects. This suggests that, within this range, there is no strong correlation between these factors and employee retention.

![image](https://github.com/user-attachments/assets/305c7fbb-238a-48db-9cc4-e2cfafe0c94d)

#### What is the outcome of employees who has higher salary with high projects and hours?

![image](https://github.com/user-attachments/assets/4dbfac27-c855-4607-a1cd-e8ee46c04a91)
![image](https://github.com/user-attachments/assets/cb536b42-2eae-4136-bf4f-04b7f588dcb1)

There is not significat difference between high salary and employees who left company.

### <b>Feature Engineering</b> 
1. <b>Over Worked High Performer (OWHP) Score: </b>
The OWHP score is a calculated metric that quantifies the relationship between long working hours, high evaluation scores, and low satisfaction. The formula is as follows:

- <b>OWHP Score =</b> (Number of Projects × Number of Monthly Hours × Evaluation Score) / Satisfaction Score
- This score provides a numerical representation of the likelihood that an employee will leave due to being overworked and undervalued, despite their high performance.

2. <b>Over 4 Years No Promotion (O4YNP) Flag: </b>
- The <b>O4YNP flag</b> is a binary indicator that identifies employees who have worked for more than 4 years without receiving a promotion. This feature helps to isolate the impact of career stagnation on employee turnover, while excluding newer employees who may not yet be eligible for promotion.

![image](https://github.com/user-attachments/assets/455a18e7-081d-46e8-8bec-1dfb94e11031)

A score exceeding 10000 appears to be a critical threshold, beyond which overworked high performers are highly likely to leave the company

##### Employee Departure Patterns: Identifying Key Factors and Profiles

- Based on the analysis, several key factors contribute to an employee's likelihood of leaving the company. These include:
    - <b>Workload:</b>
      - Employees with an excessive workload, typically exceeding 6 projects, are more likely to depart.
    - <b>Work Hours:</b>
      - Those working an average of 275 hours or more per month tend to leave the company.
    - <b>Job Satisfaction:</b>
      - Employees with a satisfaction level of 0.1 or lower are at a higher risk of departure.

##### Three distinct profiles of employees who tend to leave the company have been identified:

- <b>Unfulfilled High Achievers:</b>
  - High-satisfaction employees who are mid-level performers often leave due to a lack of career progression, typically after 5 years of service without a promotion.
- <b>Underutilized and Unhappy:</b>
  - Mid-satisfaction employees who are underperformers tend to have fewer projects, work below-average hours, and have a tenure of 3 years or less
- <b>Overworked and Undervalued:</b>
  - Low-satisfaction employees who are high performers typically have a heavy workload, work long hours, and have been with the company for 4-5 years without receiving a promotion.

# Model Evalution:
Final Model: <b>Tuned XGBoost Classifier with tuned hyperparameters</b>

### Confusion Matrix:

![image](https://github.com/user-attachments/assets/7975bf7f-3ac1-4ab7-8efd-add406494935)

<b>The accuracy of the model is 98%.</b>

### Overview of Models Compared

<b>Random Forest</b>
  - Default
  - Hyperparameters Tuned
  - Hyperparameters Tuned and Features with Department and Promotion are removed
        
<b>XGBoost</b>
  - Default
  - Hyperparameters Tuned
  - Hyperparameters Tuned and Features with Department and Promotion are removed

### Hyperparameters Tuned

<b>Random Forest</b>
  - Number of Estimators,
  - Max Features,
  - Min Samples Split,
  - Max Depth,
  - Class Weight

<b>XGBoost</b>
  - Learning Rate,
  - Number of Estimators,
  - Max Depth,
  - Min Child Weight,
  - Subsample,
  - Scale Positive Weight

<b>Final Model Parameters:</b>

- <b>XGBoost Tuned All Features</b>
    - Learning Rate: 0.046
    - Number of Estimators: 276
    - Max Depth: 15
    - Min Child Weight: 1
    - Subsample: 0.765
    - Scale Positive Weight: 3

### Business recommendations:
<b>1. Low Satisfaction High Performer Group</b>
  - Identify employees in this group who are likely to leave and offer them a promotion or a reduction in hours/projects, or a combination of both, to better align with their preferences. This will help to address their dissatisfaction and retain their valuable skills.

    - 4-5 years with the company but not promotion
    - Average Monthly Hours greater than 240
    - 6-7 projects
    - High Evaluation Scores
    - Low Satisfaction Scores
      
<b>2. High Satisfaction Mid Performer Group</b>
  - For employees in this group who are likely to leave, consider offering a promotion to recognize their value to the company. As mid-performers, they contribute significantly to the organization, and retaining them is crucial.

    - 3 years with the company
    - Average Monthly Hours less than 165
    - 2-3 projects
    - Low Evaluation Scores
    - Mid Satisfaction Scores
  
<b>3. Mid Satisfaction Low Performer Group</b>
- For employees in this group who are likely to leave, consider reassigning some of the workload from the High Performer group to them. This may increase their job satisfaction, as they may be underutilized and bored with their current projects. Additionally, this will provide an opportunity for them to improve their evaluation scores with their manager. If they still choose to leave, the impact on the company will be minimized, as they are not currently providing high value.

    - Greater than 5 years at the company
    - No Promotion
    - Average Monthly Hours between 215-275
    - 3-5 Projects
  
By implementing these recommendations, HR and management can develop targeted retention strategies to reduce employee turnover, improve job satisfaction, and maintain a high-performing workforce.












