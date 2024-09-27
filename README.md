# Product Ranking Optimization | A/B Testing Project


## Project Overview

This project simulates an A/B testing scenario for an online grocery store, “Rimi,” to assess the impact of a new product ranking algorithm on user behavior. The primary focus is to evaluate changes in `conversion rates` and `Average Revenue Per User` (ARPU) between the control group (old ranking algorithm) and the experiment group (new ranking algorithm).

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



## Dataset Description

Since we do not have access to real-world data, we have generated a **synthetic dataset** that simulates user behavior based on realistic assumptions and probability distributions. This dataset allows us to mimic an online grocery store scenario for testing purposes.

The script used to generate this dataset can be found in the `data_generation.ipynb` file.

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


## Results

![results](images/summary1.jpg)

### Interpretation
We observed some improvement in the conversion rate for the experiment group compared to the control group, with an absolute increase of 0.36%, which is greater than the Minimum Detectable Effect (MDE) of 0.3%. However, there is **not enough evidence** at the 5% significance level to conclude that the conversion rate between the old and new ranking algorithms is different (p-value = 0.546). This result is likely due to high variability in our groups.

For ARPU, we observed an absolute increase of €13.32, which is statistically significant (p-value = 0.0348).


### Decision
If this were a real case, the best course of action would be to **rerun the experiment with increased statistical power** to ensure that the observed change is practically significant.

In addition, it would be beneficial to **analyze potential factors contributing to conversion variability**. Identifying and mitigating these factors could improve the accuracy of the test and reduce errors in subsequent iterations of the experiment.