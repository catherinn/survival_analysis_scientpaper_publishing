# survival_analysis_scientpaper_publishing

## Installation (local)
* Activate a virtual environment 
* Install requirements


## Context
According to the World Health Organisation (WHO), stroke is the 2nd leading cause of death globally, responsible for approximately 11% of total deaths.


## Scope
The goal of the survival analysis is To examine the length of time between receiving funding and publishing the protocol and main paper for randomised controlled trials.
The source of the data: https://figshare.com/articles/dataset/Time_to_publication_data/4054878


## Dataset used
You can find the original dataset in the Publication.time.barnett.xlsx. The data contains information about:
1) nbMembers = number of investigators
2) fundingAwarded = funding awarded ($AUD); scrambled by -/+ $1000
3) fundingYears= length of funding in years
4) estimatedSampleSize = estimated sample size (some missing)
5) timeToProtocol = time in years from funding until protocol paper was published (or censored)
6) eventProtocol = protocol paper published (1=yes, 0=censored)
7) timeToMainPaper = time in years from funding until main paper was published (or censored)
8) eventPaper (1=yes, 0=censored)

Note: Main paper presents the results of a research study, a protocol paper outlines the plan for conducting the study.


## Proposed algorithms

Various algorithms and feature engineering and selection techniques were used in the notebook:

**Main techniques and algorithms used:**
  * Exploratory Data Analysis: The analysis includes several visualizations and summaries to understand the data and relationships between variables
  * Survival analysis: Computing and plotting the survival and hazard functions incl comparing multiple groups
  * Univariate and multivariate Cox Model


## Conclusion
After the analysis, we can get the following conclusions:
1)	The dataset contains information about various variables, including the number of investigators, funding awarded, funding years, estimated sample size, time to protocol paper publication, event of protocol paper publication, time to main paper publication, and event of main paper publication. The dataset consists of 74 observations.
2)	The data was relatively clean, but some steps were required to handle missing values and convert certain variables from character to numeric format (estimatedSampleSize).
3)	Exploratory Data Analysis: The analysis includes several visualizations and summaries to understand the data and relationships between variables. We can say that there is homogenous correlation between almost all variables.
4)	The publication of a protocol paper does not seem to have a significant impact to the main event.
5)	Survival analysis techniques were applied to understand the time to chance of main event (i.e. publication of the main paper) and the factors influencing it. We notice that:
   *	The survival function indicates that only 50% of the sample publishes a paper within the observed time. The hazard function provides the instantaneous probability of publishing a paper at any given time.
   *	The impact of individual covariates on the main event was assessed using univariate Cox models. Only fundingYears was shown to have a significant impact.
   *	A multivariate Cox model was built, including fundingYears, timeToProtocol and eventProtocol. These variables remained significant, indicating that longer fundingYears, longer timeToProtocol, and negative eventProtocol increase the risk of not publishing a main paper.
   * FundingYears, timeToProtocol, and eventProtocol have were shown to have significant impact on the main event.
   * Longer FundingYears, timeToProtocol are associated with a decreased likelihood of publishing a main paper.
   * The publication of a protocol paper seems to have a positive impact on the likelihood of publishing a main paper, although results are not statistically significant.
   * The number of investigators, the amount of the funding awarded, and the estimated sample size did not show a significant impact on the time to main event.


## References
The original paper on the topic: https://bmjopen.bmj.com/content/7/3/e012212x`
