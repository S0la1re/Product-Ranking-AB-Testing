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
