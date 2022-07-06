# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Four-Day Work Week Analysis

### Background
A four-day work week has been discussed dating back to the 1970s, and studies have proven productivity and profits increase when a reduced work week is implemented and employees have a positive reaction to it. However, the four-day work week has not taken off, and one main problem is dealing with the world of five-day work weeks ([source](https://doi.org/10.2307/41164622
)).

In recent years, momentum is building around the globe for a four-day working week. The Covid-19 pandemic has shifted workforce perspectives toward work, and employees are calling for a more flexible and shorter work week as well as better work-life balance and mental health according to Adecco Group research ([source](https://www.adeccogroup.com/future-of-work/latest-research/reset-normal/#download-the-global-report)).

The idea of a four-day work week is that employees will work four days a week with a total of 32 hours while earning the same salary and benefits, but with the same workload. Iceland, New Zealand, and Japan have shifted to a four-day workweek scheme and reported higher productivity and better work-life balance ([source](https://sloanreview.mit.edu/article/what-does-the-four-day-workweek-mean-for-the-future-of-work/)). Belgium is one of the recent countries that offers employees a four-day workweek as part of its changes in labour laws in a post-Covid era ([source](https://www.straitstimes.com/world/europe/belgium-permits-four-day-week-to-boost-work-flexibility-post-covid-19)) and UK started piloting the four-day week in June 2022 ([source](https://www.theguardian.com/business/2022/jun/06/thousands-workers-worlds-biggest-trial-four-day-week)).

In Singapore, a recent Indeed survey shows 88% Singaporean surveyed supported a four-day work week with the same pay and employees priorities family, physical health and relaxation and looks for better work-life balance with increased flexibility, better financial compensation, and a less stressful workplace ([source](https://www.humanresourcesonline.net/88-of-singapore-employees-surveyed-support-a-four-day-workweek-with-the-same-pay)). During the pandemic, companies had rolled out flexible work arrangements, including a shorter work week. However, employees are worried that the four-day work week mean clocking longer hours in a compressed work week and that company performance would also suffer as well ([source](https://www.straitstimes.com/singapore/jobs/workers-worried-4-day-week-will-mean-longer-hours-for-them-survey)). There are also concerns on the rise of the mental health issues at work ([source](https://www.straitstimes.com/singapore/health/growing-focus-on-mental-health-at-workplace-as-covid-19-pandemic-takes-toll)) and the great resignation wave ([source](https://www.channelnewsasia.com/commentary/great-resignation-wave-quit-find-job-employer-boss-pay-mental-health-2386761)) in Singapore.


### Problem Statement

The Covid-19 pandemic has sparked the debate over the four-day work week globally with employees in search of better work-life balance and mental health. With more countries reporting better employee well-being and higher productivity with the four-day work week scheme, should Singapore join the trend and introduce a four-day work week trial to reduce mental health issues in the workplace and retain or attract talent? With the pandemic altering the way the world works, the Ministry of Manpower (MOM) has assigned its data scientists to analyze the data and make recommendations regarding the possibility of a four-day week in Singapore. The analysis includes:

- Examining employee sentiments about a four-day work week 
- Assessing whether a four-day workweek would affect the company's productivity
- Build a model to predict company productivity with at least 80% accurate 
- Identify the top 3 factors that significantly impact the productivity of the company.


### Methodology

1. Scrape Glassdoor company reviews data using Selenium and Beautiful Soup.
2. Data cleaning, text preprocessing (removing punctuations and stopwords, text tokenizing, and lemmatizing the text), and visualization.
3. Perform sentiment analysis on the Glassdoor company reviews.
4. Perform modeling using Pycaret and identify the top 3 important features.
5. Perform prediction on test dataset.

Our definition of a good model is one has at least 80% accuracy with a F1 score above 0.8. F1 score will be our primary evaluation metric.

Notebook 1 covers the data collection.
Notebook 2 covers the data cleaning, sentiment analysis and insights from visualizations.
Notebook 3 covers the modeling and provides recommendations, limitations and future plans.


### Data Dictionary

**a) Company Reviews**
|Variable       |Description                                  |
|:--------------|:--------------------------------------------|
|company        |company name                                 |
|review_header  |header of the review provided by the employee|
|rating         |rating provided by the employee              |
|pro            |pro comment provided by the employee         |
|con            |con comment provided by the employee         |
|date_author    |date and author of the review                |

**b) Company Train and Test datasets**
|Variable             |Description                       |
|:--------------------|:---------------------------------|
|company              |company name                      |
|country              |country where company resides     |
|industry             |company industry                  |
|tenure               |employee length of stay           |
|company_size         |size of the company               |
|year_founded         |year of company establishment     |
|no_of_employees      |number of employees in the company|
|growth_rate          |company growth rate for 12 months |
 

### Sentiment Analysis

- Sentiment analysis is a commonly used NLP (natural language processing) technique to determine whether the text is positive, negative, or neutral. We will analyse employee satisfaction towards a four-day work week company based on the review sentiment.

- For this analysis, we will use the Sentiment Intensity Analyser which uses the VADER Lexicon. VADER (Valence Aware and sEntiment Reasoner) is a rule-based sentiment analysis tool that calculates the text emotions and determines whether the text is positive, neutral, or, negative.

- In this analysis, we will use the compound score as the metric.

- The result shows the employee sentiment towards a four-day work week is positive (>90% score).

- A positive employee experience will lead to productivity improvement and better customer service as employees are happy, able to attract better talent and less disruption to the company ([source](https://www.unily.com/insights/blogs/5-reasons-employee-experience-should-be-the-focus-of-your-enterprise-right-now)). Hence, a four-day work week company does not necessarily mean a drop in the company productivity.


### Company Productivity Analysis

- To analyze the four-day work week company productivity, we will look at the employee tenure, company lifespan, and company growth rate and compare each feature with the industry standard.

- The productivity of a four-day work week company is defined as not affected if more than 65% of the companies have comparable or higher data when compared with the industry standard.

**a) Employee Tenure**
- 66.3% of the companies have a higher employee tenure as compared to industry standard.

- This also showed turnover rates for four-day work week companies are generally lower, and higher productivity is associated with low turnover rates.

**b) SME Company Lifespan**
- 95.2% of the SME companies have a higher lifespan as compared to the industry standard.

- The lifespan of an SME company with a four-day work week is typically higher than the industry average. Hence, the productivity of these companies is not affected.

**c) MNC Company Lifespan**
- There are 9 MNC companies with a lifespan greater than 20 years and 12 companies with a lifespan less than 21 years.

- This seems to imply a four-day work week may not be as effective in an MNC company as compared to an SME company. As MNC company is more established and traditional in their thinking, there may be other consideration factors for these organizations.

- However, as the dataset is small (21 MNC companies), we may not be able to conclude if a four-day work week has any effect on the productivity of MNC companies. We will need to obtain more MNC companies’ data for a more conclusive analysis.

**d) Company growth rate**
- 71.1% of the companies (59 out of 83 companies) have a higher company growth rate as compared to the industry standard.

- Hence, the company growth rate of a company with a four-day work week is typically higher than the industry average. This shows most four-day workweek companies are growing and can attract new talent to join the company.


### Model Analysis

**a) Models Comparison and Findings**
- The model evaluation score is summarized in the table below:

|Model                        |Accuracy|F1 Score
|-----------------------------|--------|--------|
|Random Forest Classifier     | 0.8600 | 0.9214 |
|Gradient Boosting Classifier | 0.8233 | 0.8946 |
|Decision Tree Classifier     | 0.8100 | 0.8863 |
|Extra Trees Classifier       | 0.8100 | 0.8885 |
|Ada Boost Classifier         | 0.8067 | 0.8853 |
|Ridge Classifier             | 0.7867 | 0.8676 |
|Logistic Regression          | 0.7367 | 0.8387 |
|K Neighbors Classifier       | 0.6300 | 0.7005 |
|SVM - Linear Kernel          | 0.6000 | 0.6924 |
|Naive Bayes                  | 0.3633 | 0.4536 |


- Based on the results for the 10 models, the best model is Random Forest Classifier with an accuracy of 0.8433 and a F1 score of 0.9123.

**b) Top 3 feature importance**
- The top 3 important features are rating, growth_rate and age.


### Conclusions

Employees working in four-day work week companies have a high positive sentiment. A positive employee experience will lead to productivity improvement, better customer service, better talent, and less disruption. The productivity of a four-day work week company is shown to be not affected based on the comparison of employee tenure, company age, and company growth rate with industry standards. A four-day work week may not be as effective for an MNC company. However, result may not be conclusive due to the small MNC companies dataset. 

Several models were run to analyse which model is the best model to predict the company productivity. Our recommended model based on the F1 score is the Random Forest classifier. The top 3 features that affect company productivity are rating, company growth rate, and lifespan.


### Recommendations

Our analysis found that employees working in a four-day work week have positive sentiments with words like work-life balance and mental health cited. Company productivity is also maintained. In addition, there are many successful cases reported in other countries and companies. Therefore, we recommend Singapore introduce a four-day work week trial with interested companies. A four-day work week in our context refers to 32 work hours with the same salary and benefits and with the same workload.

As a start, MOM can consider: 

- Collaborating in partnership with an external party on a trial
    - E.g. 4 Day Week Global ([link](https://www.4dayweek.com/))
- To learn from other countries who have successfully implemented the four-day work week (e.g. Iceland)
    - How have they done it and what are their challenges etc.
- Set up a task force to lead and manage the trial for government agencies. For the implementation, the task force should consider:
    - Defining the goals and metrics involving both the leaders and employees
    - Communicate clearly to both internal and external stakeholders the reasons for trying out the four-day work week and encourage conversations on how to implement it successfully
    - Have clear qualitative and quantitative metrics to analyze and gain insights from the pilot run.


There is no 'one-size fits all’ approach. The task force may need to adapt and customize the approach so that it fit the industry, employees, and businesses. When implemented with clarity, the four-day work week will be successful and the objectives will be achieved.


### Limitation & Challenges

- As the 4-day work week is relatively new, countries and companies have only implemented it within the last two years, which makes this analysis limited with a small dataset. Because the dataset is small, the analysis for MNC companies may not be conclusive.

- The process of scraping Glassdoor company reviews using Selenium proved challenging. While there are examples of Glassdoor review scraping, they cannot be used in this project since HTML elements change frequently, so the code has to be written from scratch. In addition, there are time-out errors and Webdriver exception errors, which can be resolved by increasing the wait time and switching to a Firefox browser.


### Future Work

Moving forward, the team will:
- Continue to collect more data, especially for MNC companies for a more conclusive analysis. With more data, the team can re-train the model and improve the accuracy and F1 score.
- Expand the scope of collecting employee reviews from other websites (e.g. Indeed).
- Assist the task force with the analysis needed for reports or decision-making.