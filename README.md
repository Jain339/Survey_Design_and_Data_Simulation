# Survey Design & Confidence Interval Analysis

**Authors:** Narae Lee, Nikita Jain, Radia Salam

## **Table of Contents**

* [Project Overview](#project-overview)
* [Research Question](#research-question)
* [Survey Design](#survey-design)
* [Sampling Procedure](#sampling-procedure)
* [Data Overview](#data-overview)
* [Modeling & Statistical Methods](#modeling--statistical-methods)
* [Results](#results)
* [Repository Structure](#repository-structure)
* [Reproducibility & Usage](#reproducibility--usage)
* [Generative AI Statement](#generative-ai-statement)
* [Citations](#citations)

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
Assignment1/
├── Survey_Design.qmd          # Complete Quarto code for survey simulation and analysis
├── Survey_Desig.pdf           # Final rendered report
├── STEMBuddies Handbook.pdf   # Reference document for context
└── README.md                  # Project description and reproducibility guide
```

---

## **Reproducibility & Usage**

### **1. Clone the Repository**

```bash
git clone https://github.com/your-username/STA304-Assignment1.git
cd STA304-Assignment1
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

## **Citations**

Academic sources used in the report are included in the full bibliography (see PDF).
They cover Indigenous education barriers, culturally relevant programming, and structural inequities in postsecondary access.
