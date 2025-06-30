# GHDP 7031 Final Project 

Author: Amber Ni

Date: 04/26/205

Course: Jobs, Workers and Development

## Introduction

The motherhood penalty refers to the economic disadvantages women face in the workplace as a result of becoming mothers. The motherhood penalty is a well-established concept with extensive literature documenting how working mothers often experience wage reductions, diminished perceived competence, and fewer career advancement opportunities compared to their childless counterparts.

Recent data from the U.S. Department of Labor presents an interesting development. Four years after the sharp decline in maternal employment during the COVID-19 pandemic, statistics show that overall maternal employment has largely recovered, with some groups even surpassing pre-pandemic levels. This seemingly positive shift raises important questions about whether traditional patterns associated with the motherhood penalty still persist in the post-pandemic labor market. Motivated by these changes, I aim to explore the current relationship between motherhood, employment status, and working hours using 2023 data to assess whether mothers, particularly those with younger children, continue to face employment disadvantages compared to women without children in the U.S.

## Research Question 

Do mothers, particularly those with younger children, work fewer hours or have lower employment rates compared to women without children in the U.S.?

## Data Source 

I identified key variables relevant to this research question from the 2023 survey data and downloaded a customized dataset from IPUMS USA: https://usa.ipums.org/usa/.

This dataset includes 27 variables and 146,133 observations.

Key variables include:

- `hourwage2`: hourly wage (rounded)
- `relate`: relationship to household head
- `age`: age
- `sex`: sex
- `race`: race
- `marst`: marital status
- `nchild`: number of own children in household
- `nchlt5`: number of own children under age 5 in household
- `yngch`: age of youngest own child in household
- `empstat`: employment status
- `labforce`: labor force status
- `uhrsworkt`: hours usually worked per week at all jobs
- `ahrsworkt`: hours worked last week
- `educ`: educational attainment recode
- `schlcoll`: school or college attendance

## Overview  

### Dependent Variable: Employment Status

I chose `empstat` - employment status (employed vs. unemployed) as my dependent variable, because it provides the most direct and fundamental measure of labor market participation. When analyzing the impact of young children on women's employment, the primary question is whether women remain in the workforce or exit due to caregiving responsibilities.

In contrast, variables like hours worked and wages only capture variations among those who are already employed. For example:

- Hours worked reflect work intensity but fail to account for women who are unemployed or have left the workforce altogether due to childcare demands. Also, hours don't usually have a lot of variations.
- Wages are influenced by multiple factors beyond childcare, such as industry, education, experience, and discrimination, making it a less precise indicator for isolating the effect of young children.

By focusing on employment status, this research captures the critical decision point: whether women with young children are able to be/stay employed. It allows for a clearer and more fundamental understanding of how childcare responsibilities correlate with women's participation in the labor market, regardless of job type, hours, or earnings.

![[Jobs] Figure 1](/Users/amberni/Desktop/[Jobs] Figure 1.png)
![[Jobs] Figure 2](/Users/amberni/Desktop/[Jobs] Figure 2.png)

**Both figures highlight that employment rates are consistently high for both genders, but males show a slightly higher unemployment count and proportion compared to females**. The absolute counts of employed and unemployed individuals by gender using a log scale show that while the majority of both males and females are employed, males have a higher number of both unemployed and employed individuals than females (Figure 1). The proportion of employment status by gender reinforces that although employment rates exceed 95% for both genders, the proportion of unemployment is marginally higher among males than females. This suggests that overall, women in this dataset are slightly more likely to be employed relative to men, without accounting for other factors (Figure 2).

### Main Variable of Interest: Number of Own Children under Age 5 in HH

I chose `nchlt5` as my main variable of interest because the number of own children under age 5 in the household serves as a strong indicator of potential exposure to the motherhood penalty. Young children typically require intensive care, and in the absence of sufficient societal or institutional childcare support, this responsibility disproportionately falls on mothers. This added burden can limit women's ability to participate fully in the labor market, leading to reduced employment opportunities or career interruptions. By focusing on the presence of young children, this variable captures a key mechanism through which caregiving demands impact women's employment outcomes.

![[Jobs] Figure 3](/Users/amberni/Desktop/[Jobs] Figure 3.png) 

**A clear gender difference emerges in the distribution of young children, with women having slightly fewer multiple children under age 5 in the household.** The majority of both males and females have no young children in the household under age 5, while the count sharply decreases as the number of young children increases. Notably, while the overall patterns for men and women are similar, females consistently show slightly lower counts across categories with different numbers of own children under age 5 (Figure 3).

However, this difference can be due to the existing smaller number of females present in the dataset. To avoid misinterpretation, I also checked the crosstab of sex and the number of children under age 5. Consistently, the vast majority of both males and females have no children under age 5, with proportions exceeding 86% for both genders. For those individuals with no children, the proportion of females is slightly higher. As the number of young children increases, the proportion decreases sharply, also aligning with Figure 3. Notably, women consistently exhibit slightly lower proportions in categories with multiple young children compared to men.

The observation that females in this dataset are less likely to have two or more young children, and more likely to have none, highlights a potential tendency for women to limit childbearing. This may be influenced by various job-related factors, such as employment pressures, career interruptions, and barriers like the glass ceiling, which can discourage women from having larger families while pursuing stable career development.

After descriptively examining both the overall employment status and the distribution of young children by gender, a seemingly contradictory pattern emerges — have women already gained a competitive edge in employment, or do they still face challenges balancing childbearing with labor market participation? These observations raise important questions about the true dynamics at play. To explore this further, I examined the relationship between the number of young children and employment rates by gender.

![[Jobs] Figure 4](/Users/amberni/Desktop/[Jobs] Figure 4.png)

**Increasing childcaring responsibilities appear to motivate both men and women to seek employment, but while men face limits when the burden becomes too large, women are consistently driven into the workforce.**

For males, employment proportions remain stable overall, but a nuanced trend emerges. As the number of young children increases from 0 to 1 or 2, unemployment slightly decreases, suggesting that additional childcare responsibilities may encourage men to seek more employment opportunities to support household needs. However, when the number of young children reaches 3 or more, the growing caregiving burden may begin to limit men’s ability to stay employed (Figure 4, right).

For females, unemployment consistently decreases as the number of young children rises, even when reaching 3 or more. This pattern indicates that, rather than deterring women from the workforce, the presence of young children may motivate them to pursue employment opportunities to contribute additional income to the household. Contrary to traditional assumptions about childcare limiting women's labor force participation, this suggests a potential economic necessity driving mothers into the job market. (Figure 4, left).

### Control Variables



I selected region (`region`), age (`age`), race (`race`), marital status (`marst`), and educational attainment (`educ`) as control variables, focusing on recoding and consolidating categories in this section for more effective analysis.

## Analysis

Based on Figure 4, it appears that the presence of young children may motivate women to pursue employment opportunities rather than limit their participation in the labor market. But is this truly the case for all women? Do females across different regions, age groups, and ethnicities exhibit the same pattern, or do these factors reveal variations in how young children impact women's employment?

In this section, I focus on the impact of young children on female employment across different ethnic groups, age groups, regions, marital statuses, and levels of educational attainment.

After subsetting my dataset with only females in the labor force, I begin by descriptively exploring how each of these factors may shape the influence of young children on women's employment through visualizations. Following this, I run a logistic regression model to examine the relationship between the number of young children and employment outcomes (measured by the probability of being employed), while controlling for region, age, race, marital status, and educational attainment.

### Race

![[Jobs] Figure 5](/Users/amberni/Desktop/[Jobs] Figure 5.png)

**Asian and white women generally exhibit high employment rates, but key differences emerge as the number of young children increases.** For example, Indigenous/Native and Black or African American women both experience a notable increase in employment at the two-child or 3+ child level. White women show a clear upward trend in employment as the number of young children increases. In contrast, Asian women experience a decrease in employment with one child but recover at higher child counts.

This pattern may suggest that structural barriers disproportionately affect Black and Indigenous/Native mothers, driving them to seek employment even with heavy childcaring burdens. White women’s steady increase could be due to broader access to flexible work arrangements or stronger institutional support.

### Marital Status

![[Jobs] Figure 6](/Users/amberni/Desktop/[Jobs] Figure 6.png)

**Married women maintain higher job stability than single women as caregiving demands for young children increase.** Overall, married women consistently show higher employment rates compared to single women across all categories of young children. For married females, employment proportions remain stable and high, even as the number of young children increases. There is only a slight decrease in employment rate when the number of young children reaches 3 or more. In contrast, single women exhibit a noticeable decline in employment proportion as the number of young children rises. However, there is an increase in employment rate when the number of young children reaches 3 or more (Figure 6).

This reverse trend highlights the critical role of marital status in shaping women’s employment amid childcare duties. Married women maintain high, stable employment rates, likely due to greater household and caregiving support. In contrast, single women face greater declines as childcare demands grow, reflecting the challenges of balancing work without spousal support. The slight rebound in employment for single mothers with 3+ young children suggests economic necessity drives workforce participation despite heavy caregiving burdens. It is also an indicator for gaps in social safety nets for single-parent households.

### Age

![[Jobs] Figure 7](/Users/amberni/Desktop/[Jobs] Figure 7.png)

**Middle-aged women (30-49) show greatest employment stability as caregiving demands for young children increase.** Overall, women aged 30-49 maintain the highest and most stable employment rates across all categories of young children, even as the number of children rises. In contrast, younger women (≤29) exhibit consistently lower employment proportions, with a slight decline when they have 3 or more young children. Women aged 50+ show more fluctuation, experiencing a noticeable drop in employment with two young children, but a sharp rebound when the number reaches 3+ (Figure 7).

This pattern highlights how different life stage affect women’s ability to balance work and childcare. Middle-aged women likely benefit from more established careers and resources, enabling them to sustain employment despite increased childcare responsibilities. Younger women may face early-career instability becasue of childcare demands.

### Region

![[Jobs] Figure 8](/Users/amberni/Desktop/[Jobs] Figure 8.png)

**Northeast and West regions showing greater resilience in employment rates as caregiving demands increase.** Overall, women in the Northeast and West maintain higher employment proportions, especially as the number of young children rises, even reaching 100% employment when they have 3 or more young children. Notably, the Northeast shows a steady increase in employment rates, while the West displays a much steeper rise. This sharp climb in the West may be attributed to its fast-growing high-tech industries and higher living costs, where having more than two young children likely compels both parents to participate in the workforce to sustain the household. Additionally, the prevalence of higher-paying jobs in the West may offer more incentives or opportunities for women to remain employed despite increasing childcare responsibilities (Figure 7).

This trend highlights the critical role of regional economic conditions, social policies, and childcare infrastructure in supporting working mothers. The higher employment in the Northeast and West may reflect better access to childcare services, more flexible labor markets, or cultural norms that encourage female workforce participation despite family burdens. Conversely, the declining trend in the North and South suggests that women in these regions face greater structural barriers, such as limited childcare support or fewer accommodating job opportunities, making it harder to balance employment with increasing caregiving demands.

### Educational Attainment

![[Jobs] Figure 9](/Users/amberni/Desktop/[Jobs] Figure 9.png)

**Higher education levels are correlated with more employment as caregiving demands for young children increase.** Overall, women with a bachelor’s degree or higher consistently show the highest employment rates across all categories of young children, maintaining stable and slightly rising employment proportions even as the number of young children increases. Women with some college education also demonstrate resilience, with employment rates improving notably when they have 3 or more young children. In contrast, women with a high school education or below experience a gradual decline in employment rates as the number of young children rises. (Figure 9).

This trend shows that higher education may help women get employed even as childcare responsibilities grow. Women with advanced education may have access to more stable jobs, better pay, and flexible work options, making it easier to balance work and family life. On the other hand, women with lower education levels might struggle with fewer job opportunities and less workplace support, which can make it difficult to keep working when childcare demands increase. But the slight rise in employment for those with 3 or more children suggests that financial pressure may push them all back into the workforce, even when balancing work and childcare is challenging.

### Regression Analysis

**Regression Results**

![[Jobs] Figure 10](/Users/amberni/Desktop/[Jobs] Figure 10.png)

The logistic regression analysis reveals several significant factors related to female employment probability:

- **Young Children (Number of own children under age 5 in HH)**: Having one child under age 5 is correlated with a 21% higher probability of being employed compared to having no young children, suggesting a potential link between childcare responsibilities and increased labor force participation for women with a single child. As the number of young children increases, the coefficients become statistically insignificant.

- **Educational Attainment**: Education is strongly associated with employment outcomes. Women with a high school diploma or below are linked to an 88% lower probability of being employed compared to college graduates, while those with some college education are associated with a 40% lower probability. This indicates that higher educational attainment is related to better employment prospects for women.

- **Race**: Clear racial disparities emerge. Being Black or African American is associated with a 43% lower probability of employment, and being Indigenous/Native is linked to a 30% lower probability compared to White women, reflecting ongoing racial inequalities in labor market participation.

  

- **Age**: Age is positively correlated with employment probability. Women aged 30-49 are associated with a 31% higher probability of being employed compared to those under 29, while women aged 50+ are linked to a 47% higher probability, suggesting greater workforce attachment in older age groups.

- **Region**: Women in the South are associated with a 12% higher probability of employment compared to those in the Northeast. This contrasts with earlier visual trends and may reflect regional labor market characteristics not fully captured in descriptive analysis.

- **Marital Status**: Being married is correlated with a 65% higher probability of employment compared to being single, consistent with visual patterns suggesting that marital status is linked to greater workforce participation, possibly due to household or financial dynamics.

## Conclusion & Policy Recommendation

While there are promising signs that having young children may encourage women to participate in the labor force, the effects vary significantly across different demographic groups. These disparities highlight the need for targeted policy interventions to ensure equitable support for women facing childcare especially for young children and employment challenges.

**Policy Recommendation**:

- **Expand affordable childcare support**:
Since having one young child is linked to higher employment probabilities, but the effect diminishes with multiple young children, expanding access to affordable childcare is essential. Public subsidies, employer-supported childcare, and extended early childhood education programs can help reduce caregiving burdens and sustain women's participation in the labor force.
- **Enhance educational opportunities for women**:
The strong negative correlation between low educational attainment and employment reinforces the importance of increasing access to education. Policies should focus on adult education, vocational training, and re-skilling programs, particularly for women with high school or some college education, to improve employment outcomes.
- **Address racial inequities in employment**:
Significant employment disparities across racial groups highlight the need for targeted equity programs. These may include inclusive hiring practices, anti-discrimination enforcement, job training focused on minority women, and mentorship or entrepreneurship support tailored to historically marginalized communities.
- **Support single mothers through financial and workplace Policies**:
  The observed employment gap between married and single women suggests single mothers face more barriers to workforce entry. Expanding child tax credits, paid family leave, and offering flexible or part-time job options could help single mothers maintain employment while managing caregiving duties.







- **Initiatives for young mothers with multiple young children**:
  While women with one young child show higher employment rates, this advantage fades with more children. Targeted programs that provide job placement support, transitional employment opportunities, and wraparound services for young mothers with multiple young children can help them re-enter or remain in the workforce.