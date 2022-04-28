# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

### Overview

In United States, the SAT and ACT are standardized tests used by colleges and universities in college acceptance decision in addition to other materials such as grade point average (GPA). In 2016, College Board has made major changes and introduced a new SAT format that has similarities to the ACT ([*source*](https://blog.prepscholar.com/complete-guide-to-the-new-sat-in-2016#:~:text=Format%20Changes,still%20scored%20out%20of%20800.)). This analysis will review the 2017 to 2019 SAT and ACT participation and score data for insights and to make recommendation to the College Board to improve the SAT participation rate.

### Problem Statement

Analyse the SAT and ACT participation rates and scores from 2017 to 2019 and provide recommendations to improve SAT participation rates.


### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|*object*|sat_act.csv|US States|
|region|*object*|sat_act.csv|US Regions|
|sat_participation_2019|*float*|sat_act.csv|Percentage of SAT participation rate (2 decimal places) in 2019|
|ebrw_2019|*integer*|sat_act.csv|Evidence based reading and writing score in 2019. Score range is 200 to 800|
|math_2019|*integer*|sat_act.csv|Math score in 2019. Score range is 200 to 800|
|sat_total_2019|*integer*|sat_act.csv|SAT Total score in 2019. Score range is 400 to 1600|
|sat_participation_2018|*float*|sat_act.csv|Percentage of SAT participation rate (2 decimal places) in 2018|
|ebrw_2018|*integer*|sat_act.csv|Evidence based reading and writing score in 2018. Score range is 200 to 800|
|math_2018|*integer*|sat_act.csv|Math score in 2018. Score range is 200 to 800|
|sat_total_2018|*integer*|sat_act.csv|SAT Total score in 2018. Score range is 400 to 1600|
|sat_participation_2017|*float*|sat_act.csv|Percentage of SAT participation rate (2 decimal places) in 2017|
|ebrw_2017|*integer*|sat_act.csv|Evidence based reading and writing score in 2017. Score range is 200 to 800|
|math_2017|*integer*|sat_act.csv|Math score in 2017. Score range is 200 to 800|
|sat_total_2017|*integer*|sat_act.csv|SAT Total score in 2017. Score range is 400 to 1600|
|act_participation_2019|*float*|sat_act.csv|Percentage of ACT participation rate (2 decimal places) in 2019|
|act_composite_2019|*float*|sat_act.csv|ACT Composite score in 2018. Score range is 1 to 36|
|act_participation_2018|*float*|sat_act.csv|Percentage of ACT participation rate (2 decimal places) in 2018|
|act_composite_2018|*float*|sat_act.csv|ACT Composite score in 2018. Score range is 1 to 36|
|act_participation_2017|*float*|sat_act.csv|Percentage of ACT participation rate (2 decimal places) in 2017|
|act_composite_2017|*float*|sat_act.csv|ACT Composite score in 2017. Score range is 1 to 36|
|sat_diff_1819|*float*|sat_act.csv|Percentage difference in 2018 and 2019 SAT participation rate|
|sat_diff_1718|*float*|sat_act.csv|Percentage difference in 2017 and 2018 SAT participation rate|
|act_diff_1819|*float*|sat_act.csv|Percentage difference in 2018 and 2019 ACT participation rate|
|act_diff_1718|*float*|sat_act.csv|Percentage difference in 2017 and 2018 ACT participation rate|
|ave_sat_participation|*float*|sat_act.csv|Average SAT participation rate for 2017, 2018, and 2019 (in percentage)|
|ave_act_participation|*float*|sat_act.csv|Average ACT participation rate for 2017, 2018, and 2019 (in percentage)|

### Key Findings

- There is an increase in the number of states that has 100% SAT participation rate since 2018 with Midwest region showing a better performance in 2019. This can be attributed due to growth of SAT School Day, a program where students take the SAT in their own school on a weekday, rather than taking it on a Saturday in a different school than the one they attend and benefits of the fee wavier ([source](https://www.edweek.org/teaching-learning/sat-scores-rise-as-number-of-test-takers-tops-2-million/2018/10)).

- In general, ACT participation rate is observed to better than SAT participation rate. There are more states with 100% participation rate for ACT. ACT seems to be a preferred choice as more states made it mandatory and provide for the students. 

- Northeast region fares better in SAT while Midwest, South and West regions seem to fares in ACT than the other 3 regions. 

- In general, states with higher participation rate tends to score lower in the test while those with lower participation rate have a better score. However, this does not means the the state has the mostly the top performing students it is a small representative of students taking the test.

- The relationship for each test has a strong correlation year by year. This implies state that has done well this year is likely to do well again in the next year. This correlation is stronger for the ACT test as the scores are relatively similarly across the years.

- The participation rate and score is inversely related. A higher participation rate has a lower score while lower participation rate has a higher score.

- Colorado and Illinois are two examples where their participation rate improved tremendously when both states implemented compulsory SAT test.

### Conclusions

- From the data, there is an increase in the SAT participation rates since 2017. Other than the change in the SAT format, the SAT School Day and  benefits of the fee wavier attributed to the success of increasing participation. However, ACT is currently still the preferred choice.

- The test score is inversely related to the participation where a high participation rate implies a lower test score. With a higher participation, the test score may have a bigger spread which will affects the average of the score.

- The relationship for either SAT or ACT test has a strong correlation year by year. This implies state that has done well this year is likely to do well again in the next year.

- SAT fares better in Northeast region while ACT fares better in the other 3 regions. We can see the impact of the compulsory test on the participation rate. Colorado and Illinois are two cases where SAT participation rate improved tremendously when the states require the students to take the SAT test.

### Recommendations

To further increase the SAT participation rate, the College Board may consider:

- To work with the states to offer SAT as a mandatory requirement and provide programs to help the school to administer the test in an efficient way and allows the students to sit for the test conveniently. College Board can consider focusing on states that have 40 to 70% SAT participation rates. Some suggested states are Texas, Virginia and California.

- To work with states that currently require students to take either SAT or ACT. North Carolina is recommended as it has ~ 50% participation rate even though it ACT participation rate is 100%. South Carolina is also recommended as it SAT participation rate has increased in 2019.