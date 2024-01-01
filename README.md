# Impact-of-funding-and-funding-rounds-on-Startups-growth

Project_link: https://prajivinn.github.io/2023/12/31/Impact-of-funding-and-funding-rounds-on-startup-growth.html

## DOMAIN: Startup ecosystem

### Overview:

Company X, a leading Indian online publisher dedicated to startup industry insights, is driven by a mission to empower its audience with actionable knowledge. In the dynamic world of startups, the company recognizes the crucial need to answer a pivotal question: What financial factors differentiate thriving, currently operating startups from those that ultimately cease operations? 

### Objective:

This project seeks to address the critical questions of whether there is a statistically significant difference in the mean funds raised by startups that are currently operating compared to those that have ceased operations. Additionally, we aim to investigate whether there exists a significant disparity in the number of funding rounds between currently operating startups and startups that have closed.


*Note*:

*- Dataset Credits --> https://www.kaggle.com/datasets/yanmaksi/big-startup-secsees-fail-dataset-from-crunchbase
Filter on country and status column*

*- Unauthorised use or distribution of this project prohibited @dataanalystduo*


### Actions

We removed incorrect or irrelevant values from the dataset & formatted it for proper analysis. Based on the problem statements, we filtered the data aka the variables of our interest such as funding_total_usd, status and funding_rounds.

For the problem mean funds raised by startups, we applied the Independent Two Sample T-test because the two groups aka ‘operating’ & ‘closed’ startups are separate and independent. Also we used levene’s test, a key assumption to determine whether the variance of the two sample groups are same or not. The results turned out to be positive that the variance of the sample means are equal, thus meeting the assumption for the independent sample t-test.

We set out our hypotheses and Acceptance Criteria for the test, as follows:

* Null Hypothesis: There is no statistically significant difference in the mean funds raised by currently operating startups and startups that have closed. They are independent.
* Alternate Hypothesis: There is a statistically significant difference in the mean funds raised by currently operating startups and startups that have closed. They are not independent.
* Acceptance Criteria: 0.05

We fed this into the algorithm (using the scipy library) to calculate the T-Statistic, p-value.

For the problem number of funding rounds for startups, As it is focused on comparing the funding rounds of two groups aka ‘operating’ & ‘closed’ startups - we applied the Chi-Square Test For Independence. Full details of this test can be found in the dedicated section below.

Note: Another option when comparing “funding rounds” is a test known as the Z-Test For Proportions. While, we could absolutely use this test here, we have chosen the Chi-Square Test For Independence because:

* The resulting test statistic for both tests will be the same
* The Chi-Square Test can be represented using 2x2 tables of data - meaning it can be easier to explain to stakeholders
* The Chi-Square Test can extend out to more than 2 groups - meaning the client can have one consistent approach to measuring signficance

We isolated startups data that are “Operating” and “Closed”.

We set out our hypotheses and Acceptance Criteria for the test, as follows:

* Null Hypothesis: There is no statistically significant difference in the number of funding rounds between currently operating startups and startups that have closed. They are independent.
* Alternate Hypothesis: There is a statistically significant difference in the number of funding rounds between currently operating startups and startups that have closed. They are not independent.
* Acceptance Criteria: 0.05

As a requirement of the Chi-Square Test For Independence, we aggregated this data down to a 2x2 matrix for rounds of funding category by status and fed this into the algorithm (using the scipy library) to calculate the Chi-Square Statistic, p-value, Degrees of Freedom, and expected values.


### Results

Independent Two Sample T-Test gives us the following statistics:

p-value: 0.5429592211146083
The p-value for our specified acceptance criteria or alpha of 0.05 is 0.54.

Based upon these statistics, we retain the null hypothesis, and conclude that There is no relationship between the mean funds raised by the two groups i.e. startups which are operating & startups. They are independent.

The Chi-Square Test gives us the following statistics:

p-value: 0.2908506204110049
The p-value for our specified acceptance criteria or alpha of 0.05 is 0.29.

Based upon the above statistics, we retain the null hypothesis, and conclude that: There is no relationship in the number of funding rounds between currently operating startups and startups that have closed. They are independent.


### Growth/Next Steps

Due to probabilistic nature of the hypothesis testing, Our results here also do not say that there definitely isn’t a difference in the mean funds/number of funding rounds between the two status groups aka ‘operating’ & ‘closed - we are only advising that we should not make any rigid conclusions at this point.

Running more tests like this, gathering more data, and then re-running this test may provide us, and the client more insight!
