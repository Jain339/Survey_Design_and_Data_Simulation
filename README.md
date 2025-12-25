# Survey Design & Confidence Interval Analysis
---

## **Project Overview**

This project was completed in partnership with **STEMBuddies**, a nonprofit organization dedicated to providing accessible academic resources for underserved high school students.

The goal of this project is to design, test, and analyze a survey assessing students’ feedback on the **STEMBuddies High School Handbook**, focusing on identifying which sections require additional detail and how these needs differ across demographic groups.

Our work includes:

* designing a complete survey
* proposing a realistic sampling strategy
* simulating data to mimic real responses
* conducting exploratory analysis
* estimating a **two-proportion confidence interval** comparing Indigenous vs. non-Indigenous students’ needs
* presenting actionable recommendations for improving the handbook

This repository includes all code, simulated datasets, and final report files required to reproduce our analysis.

---

## **Research Question**

**Primary Research Question:**

> *Are Indigenous high school students more likely than non-Indigenous students to select “Scholarships” as one of the top three sections requiring more information in the STEMBuddies Handbook?*

This question was motivated by literature highlighting the unique financial and structural barriers faced by Indigenous youth, which often make scholarships a critical component of their postsecondary access.

---

## **Survey Design**

The survey was built using **Google Forms**, containing 9 total questions:

* **3 demographic questions** (including whether a respondent self-identifies as Indigenous)
* **4 needs-assessment questions** evaluating the handbook
* **2 open-ended feedback questions**

In the report, we highlighted and analyzed these two key questions:

1. **Indigenous identity:**
   *“Do you wish to self-identify as an Aboriginal person in Canada such as First Nation, Métis, or Inuit?”*

2. **Handbook improvement needs:**
   *“Which part of the Handbook do you think needs more detail / was not comprehensive enough?”* (choose up to 3)

These questions were selected because they directly contribute to our comparative analysis on scholarship needs and align with the handbook’s policy objectives.

---

## **Sampling Procedure**

We proposed a **non-probability purposive sampling strategy** to realistically reach high school students across Ontario—particularly in regions with higher Indigenous populations (e.g., Thunder Bay, Ottawa–Gatineau, Greater Sudbury).

Key elements:

* **Target population:** High school students (Grades 9–12) in Ontario
* **Sampling frame:** School boards in regions with large Indigenous communities
* **Sample unit:** Individual students
* **Strengths:** targeted outreach, higher relevance of responses
* **Limitations:** selection bias, non-response bias, reliance on school board cooperation

To perform our statistical analysis, all survey variables were **simulated in R**, following realistic probability weights and population proportions.

---

## **Data Overview**

The simulated dataset consists of **1,000 observations** and **14 variables**, including:

* grade
* is_indigenous
* handbook_length
* first-generation status
* postsecondary plans
* selected “most helpful” sections (3 variables)
* selected “needs more detail” sections (3 variables)
* extracted keywords from open-ended responses
* a derived binary variable **chose_scholarship**

### **Key Data Processing Steps**

* Merged multi-response questions into interpretable categorical variables
* Created `chose_scholarship = 1` if "Scholarships" appeared in any “needs more detail” field
* Computed group-wise proportions
* Generated exploratory plots, including:

  * **Proportion of Indigenous vs. non-Indigenous students selecting Scholarships** (Figure 4.1)

---

## **Modeling & Statistical Methods**

Our analysis uses a **Two-Proportion Confidence Interval** to estimate the difference in true proportions between two independent groups:

$$
(p_1 - p_2) \pm z_{\alpha/2} \sqrt{\frac{p_1(1-p_1)}{n_1} + \frac{p_2(1-p_2)}{n_2}}
$$

Where:

* $$(p_1)$$: proportion of Indigenous students selecting Scholarships
* $$(p_2)$$: proportion of non-Indigenous students selecting Scholarships
* $$(n_1, n_2)$$: corresponding sample sizes
* $$(z_{0.025} = 1.96)$$ for a 95% CI

This method is appropriate because:

* We compare **independent groups**
* Outcome is **binary**
* Sample size is sufficiently large
* Assumptions (independence, approximate normality of difference in proportions) are satisfied through simulation design

---

## **Results**

### **Key Findings**

* **36%** of Indigenous students selected “Scholarships” as needing more detail
* **24%** of non-Indigenous students selected it
* **Estimated difference:** **12 percentage points**
* **95% CI for the difference:** **(5.5%, 18.4%)**
* **Hypothesis test:**

  * (z = 3.62), *p* = 0.0003
  * Strong statistical evidence that Indigenous students have a higher likelihood of identifying scholarships as a priority

### **Interpretation**

Students who identify as Indigenous show a significantly higher need for additional scholarship information in the STEMBuddies Handbook.
This finding aligns with literature on financial barriers and postsecondary access for Indigenous youth.

---

## **Repository Structure**

```
Survey_Design_and_Data_Simulation/
├── Survey_Design.qmd          # Complete Quarto code for survey simulation and analysis
├── Survey_Desig.pdf           # Final rendered report
├── STEMBuddies Handbook.pdf   # Reference document for context
└── README.md                  # Project description and reproducibility guide
```

---

## **Reproducibility & Usage**

### **1. Clone the Repository**

```bash
git clone https://github.com/your-username/Survey_Design_and_Data_Simulation.git
cd Survey_Design_and_Data_Simulation
```

### **2. Install Required R Packages**

```r
install.packages(c("tidyverse", "dplyr", "ggplot2"))
```

### **3. Run the Analysis**

Open **Survey_Design.qmd** in RStudio:

* Click **Render** to reproduce the PDF
* All simulated data and plots will regenerate exactly

## **Generative AI Statement**

A detailed reflection is included in the report.
In summary:

* ChatGPT assisted with **multi-response simulation scaffolding** and **minor writing edits**
* All suggestions were verified using R documentation
* Final code, analysis, and interpretation were completed by the authors
* AI was used strictly within STA304 guidelines

# **References (APA 7th edition)**

### **Academic Sources**

1. Chenoweth, E., Cotter, P., Straley, J., & Lanphier, K. (2025). *Community-Based, Culturally Relevant STEM: Engaging Rural and Indigenous Students Through Partnerships, Institutional Flexibility, and One Health.* **Innovative Higher Education.** [https://doi.org/10.1007/s10755-025-09819-8](https://doi.org/10.1007/s10755-025-09819-8)
2. Deonandan, R., Janoudi, G., & Uzun, M. (2019). *Systematic Review of Indigenous Educational Experiences in Canada.* **Journal of Educational Leadership in Action, 6.**
   [https://digitalcommons.lindenwood.edu/cgi/viewcontent.cgi?article=1032&context=ela](https://digitalcommons.lindenwood.edu/cgi/viewcontent.cgi?article=1032&context=ela)
3. De Mars, A., Taken Alive, J., Burns Ortiz, M., Ma, Z., & Wang, M. (2022). *Educators’ Perspectives on Factors Impacting STEM Achievement in Rural Indigenous Student-Serving Schools.* **The Rural Educator, 43(1), 24–36.** [https://doi.org/10.35608/ruraled.v43i1.1207](https://doi.org/10.35608/ruraled.v43i1.1207)
4. Jin, Q. (2021). *Supporting Indigenous Students in Science and STEM Education: A Systematic Review.* **Education Sciences, 11(9), 555.** [https://doi.org/10.3390/educsci11090555](https://doi.org/10.3390/educsci11090555)
5. Layton, J. (2023). *First Nations youth: Experiences and outcomes in secondary and postsecondary learning.* Statistics Canada.
   [https://www150.statcan.gc.ca/n1/pub/81-599-x/81-599-x2023001-eng.htm](https://www150.statcan.gc.ca/n1/pub/81-599-x/81-599-x2023001-eng.htm)
6. Layton, J. (2025). *Using 2021 Census and the Index of Remoteness to examine barriers to education for First Nations, Métis, and Inuit learners.* Statistics Canada.
   [https://www150.statcan.gc.ca/n1/pub/75-006-x/2025002/article/00002-eng.htm](https://www150.statcan.gc.ca/n1/pub/75-006-x/2025002/article/00002-eng.htm)
7. Nelson, H. J., Cox-White, T. L.-A., & Ziefflie, B. A. (2018). *Indigenous students: Barriers and success strategies — A review of existing literature.* **Journal of Nursing Education and Practice, 9(3), 70.** [https://doi.org/10.5430/jnep.v9n3p70](https://doi.org/10.5430/jnep.v9n3p70)

---

### **Additional Sources**

8. *Aboriginal self-identification question.* Legal Aid Ontario (2025).
   [https://www.legalaid.on.ca/lawyers-legal-professionals/for-aboriginal-legal-issues/aboriginal-self-identification-question/](https://www.legalaid.on.ca/lawyers-legal-professionals/for-aboriginal-legal-issues/aboriginal-self-identification-question/)
9. Statistics Canada (2022). *Top 10 census metropolitan areas and census agglomerations by Indigenous population, Ontario, 2021.*
   [https://www12.statcan.gc.ca/census-recensement/2021/as-sa/fogs-spg/alternative.cfm?topic=8&lang=e&dguid=2021A000235&objectId=8_2](https://www12.statcan.gc.ca/census-recensement/2021/as-sa/fogs-spg/alternative.cfm?topic=8&lang=e&dguid=2021A000235&objectId=8_2)
10. CFS Ontario (2021). *Factsheet: Indigenous Education.*
    [https://cfsontario.ca/wp-content/uploads/2021/11/Indigenous-Education_Factsheets_2021_EN.pdf](https://cfsontario.ca/wp-content/uploads/2021/11/Indigenous-Education_Factsheets_2021_EN.pdf)
11. Datacamp. *ifelse function | R Documentation.*
    [https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/ifelse](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/ifelse)
12. Datacamp (2019). *list function – RDocumentation.*
    [https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/list](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/list)
13. DWR447 (2016). *Two Proportion Z-Test with R.* YouTube.
    [https://www.youtube.com/watch?v=xWwnVYO4Aus](https://www.youtube.com/watch?v=xWwnVYO4Aus)
14. Government of Canada (2024). *Affirmation of Indigenous Identity Form.*
    [https://www.canada.ca/en/public-service-commission/services/appointment-framework/guides-tools-appointment-framework/affirmation-indigenous-identity-form.html](https://www.canada.ca/en/public-service-commission/services/appointment-framework/guides-tools-appointment-framework/affirmation-indigenous-identity-form.html)
15. Greenfield, E. (2020). *Supporting Indigenous Student Success in Post-Secondary Education: Thriving from Application to Graduation.*
    [https://www.socialconnectedness.org/wp-content/uploads/2020/09/PDF-Supporting-Indigenous-Student-Success.pdf](https://www.socialconnectedness.org/wp-content/uploads/2020/09/PDF-Supporting-Indigenous-Student-Success.pdf)
16. STEMBuddies (2025). *STEMBuddies: Empowering Future Innovators.*
    [https://stembuddies.ca/](https://stembuddies.ca/)
17. The Conference Board of Canada (2020). *Indigenous STEM Access Programs.*
    [https://fsc-ccf.ca/wp-content/uploads/2020/12/10872_25005_issue-briefing_indigenous-stem-access-programs.pdf](https://fsc-ccf.ca/wp-content/uploads/2020/12/10872_25005_issue-briefing_indigenous-stem-access-programs.pdf)
18. Webb, R. (2021). *Two Proportion Z-Test and Confidence Interval.* Statistics LibreTexts.
    [https://stats.libretexts.org/Bookshelves/Introductory_Statistics/Mostly_Harmless_Statistics_(Webb)/09%3A_Hypothesis_Tests_and_Confidence_Intervals_for_Two_Populations/9.03%3A_Two_Proportion_Z-Test_and_Confidence_Interval](https://stats.libretexts.org/Bookshelves/Introductory_Statistics/Mostly_Harmless_Statistics_%28Webb%29/09%3A_Hypothesis_Tests_and_Confidence_Intervals_for_Two_Populations/9.03%3A_Two_Proportion_Z-Test_and_Confidence_Interval)
19. W3Schools. *R Functions.*
    [https://www.w3schools.com/r/r_functions.asp](https://www.w3schools.com/r/r_functions.asp)
20. W3Schools. *R If…Else.*
    [https://www.w3schools.com/r/r_if_else.asp](https://www.w3schools.com/r/r_if_else.asp)
