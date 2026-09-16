## Labor Market Data Sources and Measurement


### Overview of Measurement Challenges

Labor market outcomes — employment, unemployment, wages, hours — are not observed directly as unambiguous physical quantities; they are constructed via survey questionnaires and administrative definitions that embed specific conceptual choices. Understanding labor economics empirically requires understanding *how* these constructs are measured, since definitional choices (e.g., who counts as "unemployed") materially affect headline statistics and cross-country comparability.

### Household Survey Data

**Current Population Survey (CPS), United States.** The CPS is a monthly survey of approximately 60,000 households conducted by the U.S. Census Bureau for the Bureau of Labor Statistics (BLS). It is the source of the official U.S. unemployment rate and labor force participation rate.

- Respondents are classified via a labor force status algorithm based on activity in the reference week: **employed** (did any work for pay, or unpaid work in a family business, or were temporarily absent from a job), **unemployed** (did not work but were available for work and actively searched in the prior four weeks, or were on temporary layoff), or **not in the labor force** (neither employed nor unemployed by these criteria).
- The CPS has a rotating panel design (households are interviewed for four consecutive months, out for eight, then interviewed for four more), enabling short-run longitudinal linkage without a full panel structure.
- The CPS **Outgoing Rotation Groups (ORG)** supplement collects detailed wage and hours data, widely used in wage inequality research.
- The **Annual Social and Economic Supplement (ASEC/March CPS)** collects detailed annual income data.

**Panel Study of Income Dynamics (PSID).** A long-running U.S. household panel (since 1968) following the same families and their descendants over decades, enabling analysis of intergenerational mobility, life-cycle earnings dynamics, and within-family transitions that repeated cross-sections cannot support.

**Survey of Income and Program Participation (SIPP).** A U.S. panel survey with shorter but more frequent (originally interview-based, later annual) waves, focused on income dynamics and program participation, useful for studying transitions into and out of poverty and benefit receipt.

**International analogs.** The Labour Force Survey (LFS) framework, harmonized across countries under International Labour Organization (ILO) guidelines, underlies most national labor force surveys (e.g., the UK LFS, EU-LFS), facilitating cross-country comparability of unemployment definitions.

### Administrative Data

**Unemployment Insurance (UI) wage records.** Employers report quarterly earnings per employee to state UI systems for benefit administration purposes. These records, when linked into state or national databases, provide near-universal coverage of formal-sector wage earnings with minimal measurement error (no recall bias), though they exclude informal work, self-employment in some states, and earnings above/below certain thresholds in some designs.

**Matched employer-employee data.** Datasets that link worker-level records to the specific establishment or firm employing them (e.g., the U.S. Longitudinal Employer-Household Dynamics, LEHD, program; Germany's IAB establishment and employee data; France's DADS). These enable decomposition of wage variation into worker fixed effects, firm fixed effects, and worker-firm sorting components — foundational to the Abowd-Kramarz-Margolis (AKM) methodology for measuring firm wage premia.

**Social Security earnings records.** Longitudinal administrative earnings histories (e.g., U.S. Social Security Administration data) used in life-cycle earnings and retirement research, offering long panels but limited demographic detail relative to survey data.

### Establishment/Firm-Side Data

**Job Openings and Labor Turnover Survey (JOLTS).** A U.S. BLS survey of establishments providing monthly data on job openings, hires, and separations (quits, layoffs, and other separations), the primary source for vacancy data used in Beveridge curve and matching-function analysis.

**Current Employment Statistics (CES) / "payroll survey."** A U.S. BLS establishment survey estimating nonfarm payroll employment, hours, and earnings — methodologically distinct from the CPS (a household survey), which is why the two produce headline "payroll jobs" and "household employment" figures that can diverge month to month.

### Key Measurement Concepts and Pitfalls

- **Labor force participation rate**: $\frac{\text{Employed} + \text{Unemployed}}{\text{Civilian Noninstitutional Population}}$ — sensitive to discouraged-worker effects, since workers who stop searching exit the numerator's unemployed category and the denominator's active labor force.
- **U-3 vs. broader unemployment measures (U-1 through U-6)**: the official U.S. unemployment rate (U-3) excludes discouraged workers, marginally attached workers, and involuntary part-time workers ("underemployed"), all of which are captured in the broader U-6 measure — a common source of confusion when comparing headline rates across sources or time.
- **Recall bias** in survey-based earnings and hours data, versus the near-absence of recall bias in administrative wage records.
- **Top-coding** in public-use survey data (e.g., historically in the CPS), which truncates high earners' reported income and complicates inequality measurement at the top of the distribution unless corrected via Pareto imputation or restricted-access data.
- **Informal sector and self-employment measurement**, particularly acute in developing-country labor market measurement, where formal administrative records substantially undercount total employment.

### Data Source Comparison

| Source | Unit of Observation | Frequency | Strength | Limitation |
| --- | --- | --- | --- | --- |
| CPS | Household/Individual | Monthly | Timely, rich demographics | Recall/reporting error |
| PSID | Household (panel) | Annual/biennial | Long panel, intergenerational | Small sample, attrition |
| UI Wage Records | Employer-employee | Quarterly | Low measurement error | Excludes informal sector |
| LEHD/AKM-style data | Matched employer-employee | Quarterly/annual | Firm-worker decomposition | Access restrictions |
| JOLTS | Establishment | Monthly | Vacancy/turnover data | No worker-level detail |
| CES | Establishment | Monthly | Large sample, low noise | No demographic detail |

### Key Points

- Employment and unemployment are constructed statuses defined by specific survey algorithms, not self-evident categories, and differ meaningfully across surveys (household vs. establishment) and across broader/narrower unemployment definitions (U-3 vs. U-6).
- Administrative wage records offer superior measurement accuracy for earnings but lack coverage of informal work and rich demographic detail relative to household surveys.
- Matched employer-employee datasets underpin the modern literature decomposing wage inequality into worker and firm components.
- Divergences between household-survey and establishment-survey employment figures reflect genuine methodological differences, not measurement error in either alone.

**Related Topics**

- The AKM Framework for Decomposing Firm and Worker Wage Effects
- Discouraged Worker and Added Worker Effects
- Measuring Informal Employment in Developing Economies
- Beveridge Curve Construction from JOLTS Data
- Top-Coding and Inequality Measurement in Survey Data