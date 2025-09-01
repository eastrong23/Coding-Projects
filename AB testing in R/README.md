# A/B Testing in R

## Task Description
You are a team of senior analysts working for the Analytics Department of a consumer lending company. The company receives loan applications from consumers, mostly in the range of $20,000–$35,000, and needs to decide whether to approve or reject each of them. The overall goal of the company is to minimize their losses from bad loans (loans that default) and maximize their profit from good loans (loans paid back on time). The company has been facing challenges related to loan approval review effectiveness, as loan officers have been producing high error rates.

## Approach
- Processed and cleaned loan application data.  
- Designed an A/B test comparing the **existing approval model** with a **new proposed model**.  
- Calculated **recall** and **precision** to evaluate performance, since no explicit business objective was specified.  
- Applied statistical testing in R to verify whether differences between models were significant.  
- Visualized results with **ggplot2** for clearer comparison.  

## Results
- Statistical testing showed a significant difference in **precision** between the two models.  
- The treatment model achieved a higher average precision (0.075) compared to the control model (-0.060), with a moderate effect size (~0.37).  
- This indicates that the new model reduces false positives and makes more accurate approvals, suggesting it may be a more reliable option for loan evaluation.

## Challenges & Learnings
- **Data imbalance**: The control group contained only 10 samples, while the treatment group had 28 samples. This uneven distribution limited the robustness of statistical comparisons.  
- **Test selection**: Precision and recall data did not always follow a normal distribution across groups. As a result, the Mann-Whitney U test was used instead of the more common t-test.  
- **Power analysis**: When estimating the sample size required for 80% power, the effect size for recall was too small. Under the fixed treatment group size, the required control group sample size could not be determined.

## Tech Stack
- R  
- dplyr, ggplot2  
- Statistical testing (power.t2n.test, Mann-Whitney U test)  
