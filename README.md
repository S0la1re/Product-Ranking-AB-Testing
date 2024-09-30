# Product Ranking Optimization | A/B Testing Project



## Project Overview
This project simulates an A/B testing scenario for an online grocery store, “Rimi,” to assess the impact of a new product ranking algorithm on user behavior.

![screenshot from Rimi website ](images/rimi.png)



## Methodology
1. **Problem statement** - What is the goal of the experiment?
    - Understanding the nature of the product
    - Asking clarifying questions:
        - What is the user journey?
        - What is the success metric? It should be:
            - Measurable
            - Attributable
            - Sensitive
            - Timely
2. **Hypothesis testing** - What result do you hypothesize from the experiment?
    - Set up: 
        - Null hypothesis 
        - Alternative hypothesis 
        - Significance level
        - Statistical power
        - Minimum detectable effect (MDE)
3. **Design the Experiment** - What are your experiment parameters?
    - Determine:
        - Randomization unit
        - Target population in the experiment
        - Sample size
        - Duration of the experiment
4. **Data Generation** - What are the requirements for running an experiment?
    - Determine: 
        - Key columns
        - Probability distributions 
    - Write code to generate data
5. **Validity Checks** - Did the experiment run soundly without errors or bias?
    - Check for:
        - Instrumentation Effect
        - External Factors
        - Selection Bias
        - Sample Ratio Mismatch
        - Novelty Effect
6. **A/B Testing** - Is the observed change in the metric both statistically and practically significant?
    - Run statistical tests
    - Assess the observed lift:
        - P-value
        - Confidence intervals
7. **Launch Decision** - Based on the results and trade-offs, should the change be launched?
    - Consider:
        - Metric Trade-Offs
        - Cost of Launching



## Step 1 - Problem statement


### Understanding the Nature of the Product
Rimi is an online grocery store that offers a wide range of products, including fresh produce, meat, dairy, baked goods, and more. The store uses a product ranking system or recommendation algorithm.

When a user enters keywords such as "meat" or "fruits," this algorithm generates a list of products that could be relevant to that customer, based on factors like their profile, purchase history, and other data.

If we modify this ranking algorithm, the suggested products may become more relevant to customers, which in turn should **boost sales** for the online store.


### User Journey
![user_funnel.drawio.png](images/user_funnel.drawio.png)


### Syccess metrics
Our success metric is **Conversion Rate**, which we aim to increase. However, it's crucial that this improvement does not come at the expense of the **Average Revenue Per User (ARPU)**, which should remain stable or improve.



## Step 2 - Hypothesis testing
**Conversion Rate Hypotheses**:
- Null Hypothesis (H0): The сonversion rate between the old and new ranking algorithms is the same.
- Alternative Hypothesis (Ha): The conversion rate between the old and new ranking algorithms is different.

**ARPU Hypotheses**:
- Null Hypothesis (H0): The ARPU between the old and new ranking algorithms is the same.
- Alternative Hypothesis (Ha): The ARPU between the old and new ranking algorithms is different.

**Alpha** = 0.05

**Statistical Power** = 0.8 

**MDE** = 0.3% 



## Step 3 - Design the Experiment

**Randomization Unit**: User

**Target Population in the Experiment**: Users = Visitors who searches a product

**Duration of the Experiment**: 1 to 2 weeks

### Determine the Sample Size

We used this formula to estimate the sample size:

$$n = \left( \frac{Z_{\alpha/2} + Z_\beta}{\frac{\delta}{\sqrt{p(1-p)}}} \right) ^ 2 $$

Where:
- $n$ — This is the required sample size for each group (control and experimental).
- $Z_{\alpha/2}$ — This is the critical value of the normal distribution for the significance level ($\alpha$). It is set as $\alpha/2$ because we often use a two-tailed test. For example, for a significance level of 0.05, the value of $Z_{\alpha/2}$ is approximately 1.96.
- $Z_\beta$ — This is the critical value for the test power ($\beta$). For example, for a power of 0.8, the value of $Z_\beta$  is approximately 0.84.
- $p$ — This is the current base conversion rate (e.g. 4%).
- $\delta$ —  This is the minimum detectable effect (MDE). It is the difference between the means of the control and experimental groups that you want to detect. The smaller $\delta$, the larger the sample size needed to accurately detect this difference.


#### Assumptions
Since we don’t have real data about metrics, we’ll estimate what it could look like based on industry averages.

- **Conversion rate** = 4% (which corresponds to the conversion rate for a typical online grocery store).

- **ARPU** = 50 euros


## Step 4 - Data Generation

### Dataset Description

Since we do not have access to real-world data, we have generated a **synthetic dataset** that simulates user behavior based on realistic assumptions and probability distributions. This dataset allows us to mimic an online grocery store scenario for testing purposes.

The script used to generate this dataset can be found in the `data_generation.ipynb file`, available [here](https://github.com/S0la1re/Product-Ranking-AB-Testing/blob/Development/data_generation.ipynb).

### Key Columns
- **user_id**: A unique identifier for each user.
- **group**: Either 'control' or 'experiment', indicating whether the user belongs to the control group or the experiment group.
- **session_date**: The date and time of the user's session.
- **product_views**: The number of products viewed by the user during the session.
- **cart_adds**: The number of items added to the cart.
- **purchase_amount**: The total amount spent by the user in the session (if any purchase was made).
- **session_duration**: The duration of the session in minutes.
- **device_type**: The type of device used by the user (mobile, desktop, or tablet).
- **traffic_source**: The source of traffic that brought the user to the site (organic, paid ad, or direct).
- **region**: The region where the user is located (Estonia, Latvia, Lithuania).
- **visitor_type**: Whether the user is a "new" or "old" visitor (new or returning customer).


## Step 5 - Validity Checks

### Summary
- **Instrumentation Effect**: No issues were detected as the synthetic dataset was thoroughly validated.
- **External Factors**: Not applicable to our synthetic data, ensuring no impact from outside influences such as economic conditions or holidays.
- **Selection Bias**: Both control and experiment groups were found to be homogeneous, with no significant differences in key metrics before the experiment began.
- **Sample Ratio Mismatch**: The Chi-Square test confirmed a perfect 50/50 split between the control and experiment groups, eliminating any concerns about unequal sample sizes.
- **Novelty Effect**: There were no significant differences in behavior between new and returning visitors, indicating that the observed results are not due to temporary engagement spikes.

Overall, the experiment data has passed all validity checks, confirming its suitability for further statistical analysis and interpretation.


## Step 6 - Interpret Results

![results](images/summary1.jpg)

### Interpretation
We observed some improvement in the conversion rate for the experiment group compared to the control group, with an absolute increase of 0.36%, which is greater than the Minimum Detectable Effect (MDE) of 0.3%. However, there is **not enough evidence** at the 5% significance level to conclude that the conversion rate between the old and new ranking algorithms is different (p-value = 0.546). This result is likely due to high variability in our groups.

For ARPU, we observed an absolute increase of €13.32, which is statistically significant (p-value = 0.0348).


## Step 7 - Launch Decision

### Decision
If this were a real case, the best course of action would be to **rerun the experiment with increased statistical power** to ensure that the observed change is practically significant.

In addition, it would be beneficial to **analyze potential factors contributing to conversion variability**. Identifying and mitigating these factors could improve the accuracy of the test and reduce errors in subsequent iterations of the experiment.