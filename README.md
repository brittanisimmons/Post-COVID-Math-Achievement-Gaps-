# Post-COVID-Math-Achievement-Gaps-
The comparison of Pre &amp; Post COVID Achievement Gaps identifying how COVID affected achievement based on race and socioeconomic status. 
# Post-COVID Math Achievement Gaps: Race, Gender, and Socioeconomic Disparities

## Research Questions: 

How are post-COVID math achievement gaps associated with race, gender, and grade level?
To what extent are these gaps associated with socioeconomic status after controlling for grade and year?

## Dataset

Stanford Education Data Archive (SEDA) is a publicly available, district-level dataset of academic achievement and socioeconomic measures for U.S. public school districts.

Source: Stanford Education Data Archive — official download/documentation page https://edopportunity.org/opportunity/data/downloads/

Longitudinal and covariate data were merged to capture socioeconomic factors for the purposes of the study. 

Grades: 3–8

Subject: Mathematics

Full dataset: Over 1.7 million observations, 88 variables, years 2009–2024

Initial mathematics subset: 852,141 observations (before period filtering and paired-subgroup requirements)

Pre-COVID period: 2017–2019 (n = 185,558)

Post-COVID period: 2022–2024 (n = 162,591)

Standardization: Scores are reported in standard deviation units relative to a national reference. 

Note: The cleaned dataset is not included due to Stanford's Data Use Agreement, which restricts publishing SEDA data files without permission. Small aggregate CSV exports can support checking the displayed tables and recreating the charts; they cannot independently reproduce the regression estimates.

### Data Preparation

Filtering
Restricted to mathematics achievement, grades 3–8 (852,141 initial observations)

Excluded reading and other subjects

Created two comparison groups: Pre-COVID (2017–2019) and Post-COVID (2022–2024)

Filtered out years outside these two windows

Achievement Gap Construction:
Three achievement gap variables were constructed by subtracting the mean score of the reference group from the mean score of the focal group (at the district-grade-year level):
 
| Gap            | Focal Group | Reference Group | Reported Model 1 N |
| -------------- | ----------- | --------------- | ------------------ |
| Black–White    | Black       | White           | 26,207             |
| Hispanic–White | Hispanic    | White           | 43,666             |
| Female–Male    | Female      | Male            | 93,471             |
 
- Negative values indicate the focal group scored below the reference group

- Gap observations were retained only when both subgroups had non-missing scores

- The regression sample sizes above are smaller than the initial 852,141 because filtering to the two periods and requiring paired subgroup scores reduces the analysis sample

Socioeconomic Status (SES) Selection
- Variable used: SEDA sesavgall is a composite index capturing household income, parental education, poverty rate, unemployment, and single-parent household rate

- Selection rationale: Lowest missingness among available SES measures (4.7% missing)

### Modeling

Two complementary OLS regression models were used for Research Question 2, with district-clustered standard errors to account for repeated district observations across grades and years.

Model 1: Post-COVID Regression
Each achievement gap was regressed on district SES, controlling for grade and year using fixed effects:

Gap = β0 + β1(SES) + Grade Fixed Effects + Year Fixed Effects + ε

This estimates the within-grade, within-year association between district SES and gap size.

Model 2: Pre-to-Post COVID Change Model
District-grade averages were calculated for pre- and post-COVID periods, and the change was modeled as a function of pre-COVID SES and grade fixed effects:

Δ Gap = β0 + β1(Pre-COVID SES) + Grade Fixed Effects + ε

The outcome is the post-period gap minus the pre-period gap. A negative SES coefficient means higher baseline SES is associated with a more negative change in the signed gap; a positive coefficient means a more positive change. For gaps where the focal group scores below the reference group, these correspond respectively to greater widening and less widening or greater narrowing, conditional on the model. Do not apply "widening/narrowing" universally without checking the underlying gap's sign.

### Reported Findings

These are the table results reported in my capstone paper. The paper's tables and charts contain some discrepancies that need reconciliation against the original outputs before publication. These are descriptive comparisons and associations, not estimates of COVID's causal effect.

## Descriptive (Research Question 1)
Post-COVID mean math achievement by group (2022–2024):

| Group        | Mean Achievement (SD) | Reported Observation Count |
| ------------ | --------------------- | -------------------------- |
| All students | −0.120                | 162,591                    |
| White        | +0.084                | 122,066                    |
| Black        | −0.697                | 34,101                     |
| Hispanic     | −0.412                | 55,241                     |
| Asian        | +0.711                | 17,742                     |
| Female       | −0.133                | 104,123                    |
| Male         | −0.039                | 105,493                    |

Pre vs. Post COVID comparison (Table 3, as reported):

|                |           |            | Difference |
| Gap            | Pre-COVID | Post-COVID | In Years   |			               
| -------------- | --------- | ---------- | ---------- |
| Black–White    | −0.667    | −0.722     | −0.055     |
| Hispanic–White | −0.447    | −0.482     | −0.036     |
| Female–Male    | +0.007    | −0.095     | −0.102     |


Table 3 reports the Black–White gap widening by 0.055 SD post-COVID

Table 3 reports the Female–Male gap reversing from near parity (+0.007) to −0.095 SD post-COVID

Note: Graph 2 in the paper shows the Hispanic–White gap narrowing (−0.486 to −0.468), which conflicts with Table 3. This discrepancy needs reconciliation against the original outputs.

Regression (Research Question 2)
Model 1 — Post-COVID SES regression (as reported):

| Gap            | SES Coefficient | p-value | N      |
| -------------- | --------------- | ------- | ------ |
| Black–White    | −0.0677         | < .001  | 26,207 |
| Hispanic–White | −0.0811         | < .001  | 43,666 |
| Female–Male    | −0.0283         | < .001  | 93,471 |

The SES coefficients were reported as statistically significant in all three post-period models. Higher district SES is associated with wider achievement gaps in these models.

Model 2 — Pre-to-Post COVID change (as reported):

| Gap            | SES Coefficient | p-value | N      |
| -------------- | --------------- | ------- | ------ |
| Black–White    | −0.0092         | .010    | 9,458  |
| Hispanic–White | +0.0051         | .103    | 15,227 |
| Female–Male    | +0.0075         | < .001  | 34,806 |


## Limitations:

- Aggregate district-level data. SEDA aggregates to the district level. Conclusions describe systemic patterns across districts, not individual student outcomes.

- Causality. This is an observational study. OLS with fixed effects controls for observed confounders (grade, year, SES), but unobserved factors may still influence results. These are associations, not causal effects.

- Gap construction. Gaps are measured as differences in group means within districts. Districts with too few students in a subgroup to report a score are excluded, which may bias the sample toward larger or more diverse districts.

- Missing data and differing samples. Missing subgroup and SES values, and differing sample sizes across comparisons, may affect results.

- The pre-COVID/post-COVID windows (2017–2019, 2022–2024) exclude the disruption period (2020–2021). 

- SD interpretation. The conversion of SD units to "years of learning" is an approximation, not a direct measure of instructional time. 

- SES composite. The sesavgall index captures correlated socioeconomic dimensions but is not a direct measure of any single factor.



## Contact

- Website: edalyticsconsulting.com
- LinkedIn: www.linkedin.com/in/brittani-bolden
- Email: brittanisimmons01@gmail.com
