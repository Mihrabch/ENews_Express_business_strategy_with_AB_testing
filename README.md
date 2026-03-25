# ENews Express — A/B Testing for Landing Page Optimisation

## Business Context
The advent of e-news, or electronic news, portals has offered us a great opportunity to quickly get updates on the day-to-day events occurring globally. The information on these portals is retrieved electronically from online databases, processed using a variety of software, and then transmitted to the users. There are multiple advantages of transmitting news electronically, like faster access to the content and the ability to utilize different technologies such as audio, graphics, video, and other interactive elements that are either not being used or aren’t common yet in traditional newspapers.

E-news Express, an online news portal, aims to expand its business by acquiring new subscribers. With every visitor to the website taking certain actions based on their interest, the company plans to analyze these actions to understand user interests and determine how to drive better engagement. The executives at E-news Express are of the opinion that there has been a decline in new monthly subscribers compared to the past year because the current webpage is not designed well enough in terms of the outline & recommended content to keep customers engaged long enough to make a decision to subscribe.

[Companies often analyze user responses to two variants of a product to decide which of the two variants is more effective. This experimental technique, known as A/B testing, is used to determine whether a new feature attracts users based on a chosen metric.]

## Objective
The design team of the company has researched and created a new landing page that has a new outline & more relevant content shown compared to the old page. 
In order to test the effectiveness of the new landing page in gathering new subscribers, the Data Science team conducted an experiment by randomly selecting 100 users and dividing them equally into two groups. 
The existing landing page was served to the first group (control group) and the new landing page to the second group (treatment group). Data regarding the interaction of users in both groups with the two versions of the landing page was collected. 
Being a data scientist in E-news Express, you have been asked to explore the data and perform a statistical analysis (at a significance level of 5%) to determine the effectiveness of the new landing page in gathering new subscribers for the news portal by answering the following questions:

**Do the users spend more time on the new landing page than on the existing landing page?**

**Is the conversion rate (the proportion of users who visit the landing page and get converted) for the new page greater than the conversion rate for the old page?**

**Does the converted status depend on the preferred language? [Hint: Create a contingency table using the pandas.crosstab() function]**

**Is the time spent on the new page the same for the different language users?**

## Data Dictionary
The data contains information regarding the interaction of users in both groups with the two versions of the landing page.

1. **user_id** - Unique user ID of the person visiting the website

2. **group** - Whether the user belongs to the first group (control) or the second group (treatment)

3. **landing_page** - Whether the landing page is new or old

4. **time_spent_on_the_page** - Time (in minutes) spent by the user on the landing page

5. **converted** - Whether the user gets converted to a subscriber of the news portal or not

6. **language_preferred** - Language chosen by the user to view the landing page

## Approach

| Step | What Was Done |
|------|---------------|
| **1. EDA** | Univariate and bivariate analysis of all 6 features |
| **2. Test 1** | Welch's t-test — time spent on new vs old page |
| **3. Test 2** | Proportions z-test — conversion rate new vs old page |
| **4. Test 3** | Chi-squared test — conversion status vs preferred language |
| **5. Test 4** | One-way ANOVA — time spent on new page across 3 language groups |

---

## Results

| # | Question | Test | p-value | Decision |
|---|----------|------|---------|----------|
| 1 | Do users spend more time on the new page? | Welch's t-test | **0.000139** | Reject H₀ ✅ |
| 2 | Is the conversion rate higher for the new page? | Proportions z-test | **0.008026** | Reject H₀ ✅ |
| 3 | Does conversion depend on preferred language? | Chi-squared | 0.212989 | Fail to reject H₀ ❌ |
| 4 | Is time on new page equal across languages? | One-way ANOVA | 0.432041 | Fail to reject H₀ ❌ |

### Key Numbers

| Metric | Old Page | New Page |
|--------|----------|----------|
| Mean time on page | 4.53 min | 6.22 min (+37%) |
| Conversion rate | 40% (20/50) | 68% (34/50) |

---

## Key Findings

1. **New page drives 37% more time on site** — mean time increased from 4.53 to 6.22 minutes, statistically significant at p=0.000139
2. **New page nearly doubles conversion rate** — 68% vs 40%, statistically significant at p=0.008026
3. **Language has no effect on conversion** — English, French, and Spanish users convert at equivalent rates (p=0.213)
4. **Language has no effect on time spent** — engagement on the new page is consistent across all three language groups (p=0.432)

---

## Conclusions

1. The new landing page is significantly more effective on both key metrics — time on page and conversion rate
2. The improvements hold regardless of language, making the new page suitable for all user segments without localisation changes
3. With language ruled out as a variable, future experiments should focus on demographic factors (age, device, referral source) to find the next optimisation lever

---

## Recommendations

1. **Deploy the new page** — statistical evidence is strong across both engagement and conversion metrics
2. **Deprioritise language-based personalisation** — no measurable impact on either metric; redirect resources to higher-value experiments
3. **Run demographic follow-up experiments** — age, device type, and traffic source may reveal further optimisation opportunities
4. **Monitor post-deployment metrics** — validate that experiment results hold at full traffic scale

---

## Repository Structure

```
├── ENews_AB_Testing_Clean.ipynb   # Full analysis notebook with results and figures
├── abtest.csv                     # Experiment dataset (100 users x 6 features)
└── README.md
```

---

## Stack

`Python` `Pandas` `NumPy` `SciPy` `Statsmodels` `Matplotlib` `Seaborn`

