# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)


1. A virtual environment is necessary when working with Python projects to ensure each project's dependencies are kept separate from each other. You need to create your virtual environment, also called a venv, and then ensure that it is activated any time you return to your workspace.
Click the gear icon in the lower left-hand corner of the screen to open the Manage menu and select **Command Palette** to open the VS Code command palette.

1. In the command palette, type: *create environment* and select **Python: Create Environment…**

1. Choose **Venv** from the dropdown list.

1. Choose the Python version you installed earlier. Currently, we recommend Python 3.12.8

1. **DO NOT** click the box next to `requirements.txt`, as you need to do more steps before you can install your dependencies. Click **OK**.

1. You will see a `.venv` folder appear in the file explorer pane to show that the virtual environment has been created.

1. **Important**: Note that the `.venv` folder is in the `.gitignore` file so that Git won't track it.

1. Return to the terminal by clicking on the TERMINAL tab, or click on the **Terminal** menu and choose **New Terminal** if no terminal is currently open.

1. In the terminal, use the command below to install your dependencies. This may take several minutes.

 ```console
 pip3 install -r requirements.txt
 ```

1. Open the `jupyter_notebooks` directory, and click on the notebook you want to open.

1. Click the **kernel** button and choose **Python Environments**.

Note that the kernel says `Python 3.12.8` as it inherits from the venv, so it will be Python-3.12.8 if that is what is installed on your PC. To confirm this, you can use the command below in a notebook code cell.

```console
! python --version
```

## Deployment Reminders

* Set the `.python-version` Python version to a [Heroku-22](https://devcenter.heroku.com/articles/python-support#supported-runtimes) stack currently supported version that closest matches what you used in this project.
* The project can be deployed to Heroku using the following steps.

1. Log in to Heroku and create an App
2. At the **Deploy** tab, select **GitHub** as the deployment method.
3. Select your repository name and click **Search**. Once it is found, click **Connect**.
4. Select the branch you want to deploy, then click **Deploy Branch**.
5. The deployment process should happen smoothly if all deployment files are fully functional. Click the button **Open App** at the top of the page to access your App.
6. If the slug size is too large, then add large files not required for the app to the `.slugignore` file.

# Capstone Project: OULAD Student Performance Analysis

# **Project Overview**

This project analyses the Open University Learning Analytics Dataset (OULAD) to understand how student demographics, engagement behaviour, and assessment performance relate to final outcomes. 

The goal is to produce clear, actionable insights supported by statistical analysis, reproducible Python workflows, and an executive-ready dashboard built in Power BI/Tableau.

This work was completed as part of a 5 day data analytics capstone, demonstrating end to end analytics capability: data cleaning, feature engineering, EDA, statistical testing, visualisation, and communication.

## ** Table of Contents**

# **Business Problem Statement / Requirements**

The Open University wishes to improve student retention and academic performance by understanding the drivers of success and what leads to students failing or withdrawing. This project analyses demographic,, engagement, and assessment data to identify early indicators of risk (i.e. students fail or withdraw) and provide actionable insights for early student intervention measures.

# **Key Business Question:**

1. What factors most strongly predict whether a student will succeed (pass or get a distinciton) or fail (fail or withdraw)
2. How can we identify at-risk students early?

# **Dataset:**

The Open University Analytics Dataset (OULAD) is a widely used , openly available dataset designed for research in learning analytics, student performance prediction and educational data mining. 

It was released by the Open University (UK) and contains anonymised data about students, courses and their interactions with the university's Virtual learning Environment (VLE). 

About 20 years ago I undertook two statistics courses with the Open University and so my familiarity with the learning environment led me to choose this dataset.

The dataset can be downloaded from here:
https://analyse.kmi.open.ac.uk/open-dataset

| **Feature**                     | **Description**                                                                                     |
|---------------------------------|-----------------------------------------------------------------------------------------------------|
| code_module                     | The module (course) code, e.g., “AAA”.                                                              |
| code_presentation               | The presentation (term) of the module, e.g., “2013B” (February) or “2013J” (October).               |
| module_presentation_length      | Length of the module in days.                                                                       |
| id_student                      | Unique anonymised student identifier.                                                               |
| gender                          | Student gender (“M”, “F”).                                                                           |
| region                          | Geographic region where the student lives (UK regions).                                             |
| highest_education               | Highest prior education level (e.g., “A Level”, “HE Qualification”).                                |
| imd_band                        | Index of Multiple Deprivation band for socioeconomic status (e.g., “0–10%”).                        |
| age_band                        | Age group (e.g., “0–35”, “35–55”, “55+”).                                                           |
| disability                      | Whether the student declared a disability (“Y”, “N”).                                               |
| num_of_prev_attempts            | Number of times the student previously attempted this module.                                       |
| studied_credits                 | Total credits the student has studied before this module.                                           |
| final_result                    | Final outcome: “Pass”, “Fail”, “Withdrawn”, “Distinction”.                                          |
| date_registration               | Day the student registered (relative to module start).                                              |
| date_unregistration             | Day the student withdrew (if applicable).                                                           |
| id_site                         | Identifier for a VLE activity/page (links to VLE table).                                            |
| date (click on VLE activity)    | Day student interacted with online content.                                                         |
| date (due date)                 | Date when assessment is due.                                                                        |
| sum_click                       | Number of clicks the student made on that VLE activity on that day.                                 |
| id_assessment                   | Unique assessment identifier.                                                                       |
| date_submitted                  | Submission date (relative to module start).                                                         |
| is_banked                       | Whether the score was carried over from a previous attempt.                                         |
| score                           | Student’s score (0–100) per assessment.                                                             |
| assessment_type                 | “TMA” (Tutor Marked), “CMA” (Computer Marked), “Exam”.                                              |
| weight                          | Percentage weight of the assessment toward final grade.                                             |
| activity_type                   | Type of VLE resource (e.g., “forum”, “quiz”, “resource”, “oucontent”).                              |
| week_from                       | First week the activity is available.                                                               |
| week_to                         | Last week the activity is available.                                                                |


## **Project Features**

1. **Data loading:** 

. 7 CSV datasets were downloaded and included in this project.

2. **Data cleaning:** 
•	Standardized categorical fields
•	Converted date offsets to numeric timelines
•	Removed invalid or impossible values
•	Handled missing values across tables

3. **Data Merged:**
7 dat files were merged into 2 files
•	StudentInfo
•	StudentVLE
•	VLE
-   Assessments
•	StudentAssessment
•	Courses
•	StudentRegistration

4. **Feature Engineering**

Created high impact features such as:
•	Total clicks
•	Clicks per week
•	Engagement before assessments
•	Submission lateness
•	Weighted average score
•	Engagement drop off rate

4. Exploratory Data Analysis
•	Demographic comparisons
-  Distribution analysis

5. **Statistical Analysis:** 

Statistical testing using Man Whitneyu test, linear regression, logistic regression

6. **Visualisation:**: 

Genearting bar charts and histograms in both Python and PowerBi/Tableau

7. **Export:** 

Save analysis results in various formats including CSV, PPT, SQL, Word, Text, Jupyter Source File

# **Installation**

## **Prerequisites**
- Python 3.7 or higher: pandas, numpy, seaborn, matplotlib, scikit learn, statsmodels
- pip
- Trello: Project Management
- VS Code for development
- Power BI / Tableau for dashboarding
- GitHub for version control and portfolio presentation
- Data set: 7 CSV files

## **Screenshots of finished Dashboard**

# **Clone and deploy**

## **Hypotheses to Test and how to validate them**

Engagement Hypothesis:
Ho: There is no difference in total VLE engagement between students who pass and those who fail/withdraw.
H1: Students who pass have significantly higher engagement than those who fail/withdraw.
Region Hypothesis (Anova):
Ho: Average assessment scores do not differ across regions
H1: Average assessment scores differ by region.
Gender Hypothesis (Chi-Square)??
Ho: Gender is independent of the final result
H1: Gender is associated with the final result.
Lateness Hypothesis
Ho: Submission lateness is independent of the final result
H1: Submission lateness is associated with the final result.
Registration Timing Hypothesis
Ho: Registration date does not impact the final result
H1: Late registration increased the likelihood of failing or withdrawing.
Your Final Hypothesis Framework (Portfolio Ready)
Cluster	Hypothesis	Test	Variables
Engagement Volume	Passers have higher total clicks	Mann–Whitney U	total_clicks × final_result
Engagement Consistency	Passers access VLE on more days	Mann–Whitney U	vle_days_accessed × final_result
Engagement Intensity	Passers have higher avg clicks/day	Mann–Whitney U	avg_clicks × final_result
Demographics	Final result differs by highest education	Chi square	highest_education × final_result
Prior Attempts	More previous attempts → lower pass rate	Mann–Whitney U	num_of_prev_attempts × final_result

## **Project Plan**

# **High level steps taken for analysis**
xxxxx

## How the data was managed throughout the collection, processing, nalaysis and interpretation steps


## ** Why the research emthodologies were chosen**


## Rationale to map the business requirements to the Data visualisations


## Analysis techniques used

# Data analysis methods used and their limitation/alternative approaches

# Did hte data limit and did I use an alternativ approach to meet these challenges

# The use of geneartive AI tools to help with ideation, design htinking and code optimisaiton

# **Ethical Considerations**

OULAD is an openly available and anonymised dataset. However, even here there may potentially be ethical considerations should as:

1. Privacy and aonymisation limits: there is a risk of re-identifation should external data sources be included or where subgroups are so small that re-identification is feasible   

2. Fairness and bias: Risk that the database might under or over-represent certain demogrphics leading to inequalities (e.g. socioeconomic status, disability, gender ) that are then amplified though analysis

3. Responsbile USe: Any analysis does not harm or disadvantage students

4. Interpretability: Complex models e.g. RandomForest can lack transparency and so any predictions may need to be verified using alternative algorithms

5. Data Context: OULAD is the dataset from the Open University and any conclusions and recommendations derived may not be transferable to other contexts/institutions

6. Respect for students: The OULAD dataset represents real students not simply data points. Hence any conclusions or recommendations derived from this dataset should actively seek to support students, treating them in an ethical manner, and not penalise them.  

# **Data privacy, bias or fairness issues with the data**

## Any legal or societal issues


## **Executive Summary**
The key findings from this research are:
xx
xx
xx
xx


## **Dashboards**
List all dashboard pages and their content, either blocks of information or widgets, like buttons, checkboxes, images, or any other item that your dashboard library supports.
Later, during the project development, you may revisit your dashboard plan to update a given feature (for example, at the beginning of the project you were confident you would use a given plot to display an insight but subsequently you used another plot type).
How were data insights communicated to technical and non-technical audiences?
Explain how the dashboard was designed to communicate complex data insights to different audiences.

## **Student Demographics**

**Overview: The OU student population shows a higher likelihood of students being male, residing in England, having a secondary level education, belonging to lower socio-economic bands, being younger in age and not reporting a disability.**

![alt text](image.png)

## Success can be measured via:

-  final result: (Pass, Distinction, Fail & Withdrawn)
-  ongoing assessments: Computer Marked Assessments (CMA), Tutor MArked Assessments (TMA) and Exam
-  engagement levels

## **Student Final Result (Pass = Success; At Risk = Fail/Withdrawn)**

**Overview: The OU student population shows success is most likely from those with post-graduate qualifications, higher socio economic groups and older or middle aged students.**

![alt text](image-5.png)

## ** Assessment Type**

## ** Overview: CMAs have the lowest weighting relative to the final result but produce the highest average scores, whereas TMAs and Exams have higher weights but lower average scores**

![alt text](image-3.png)

## ** Assessment Type Success**

## ** Overview: Assessment success (liek final result success) most likely from those with post-graduate qualifications, higher socio economic groups, older or middle aged students. and those in the South East**

![alt text](image-4.png)

## Unfixed Bugs and Development Roadmap

See Testing file.

# **Deployment**

Heroku
The App live link is: https://YOUR_APP_NAME.herokuapp.com/
Set the runtime.txt Python version to a Heroku-20 stack currently supported version.
The project was deployed to Heroku using the following steps.
Log in to Heroku and create an App
From the Deploy tab, select GitHub as the deployment method.
Select your repository name and click Search. Once it is found, click Connect.
Select the branch you want to deploy, then click Deploy Branch.
The deployment process should happen smoothly if all deployment files are fully functional. Click now the button Open App on the top of the page to access your App.
If the slug size is too large then add large files not required for the app to the .slugignore file.
Main Data Analysis Libraries
Here you should list the libraries you used in the project and provide an example(s) of how you used these libraries.
Credits
In this section, you need to reference where you got your content, media and extra help from. It is common practice to use code from other repositories and tutorials, however, it is important to be very specific about these sources to avoid plagiarism.
You can break the credits section up into Content and Media, depending on what you have included in your project.
Content
The text for the Home page was taken from Wikipedia Article A
Instructions on how to implement form validation on the Sign-Up page was taken from Specific YouTube Tutorial
The icons in the footer were taken from Font Awesome
Media
The photos used on the home and sign-up page are from This Open-Source site
The images used for the gallery page were taken from this other open-source site
Acknowledgements (optional)
Thank the people who provided support through this project.

## **How to Reproduce**

1.	Clone this repository

2.	Install dependencies:
-		Code
		pip install -r requirements.txt

3.	Place OULAD raw CSVs into /data_raw

4.	Run notebooks in numerical order

5.	Open the dashboard file in Power BI/Tableau

Dashboard
🟨 4. Dashboard Narrative (What your dashboard should answer)
This is the story your visuals will tell.
✅ Page 1 — Overview
•	What is the overall pass/withdrawal rate?
•	Which demographic groups show the highest risk?
•	What are the key KPIs (avg score, avg engagement, withdrawal rate)?
✅ Page 2 — Engagement
•	How does engagement change over time?
•	Do pass/fail/withdraw groups show different patterns?
•	Which activity types drive the most engagement?
✅ Page 3 — Assessment Performance
•	How do scores vary by assessment type?
•	How does lateness affect performance?
•	Are early assessments predictive of final outcomes?
✅ Page 4 — Risk Indicators (Optional)
•	Which features correlate most with withdrawal?
•	Can we identify at risk students by Week 2 or Week 4?
🟪 5. Modeling Question (Optional but impressive)
If you want to include a predictive model:
Can we predict whether a student will pass, fail, or withdraw using demographic, engagement, and assessment features?
This allows you to run:
•	Logistic regression
•	Random forest
•	Feature importance
•	ROC curve
Even a simple model adds huge value to your portfolio.
🟫 6. Executive Summary Structure (Use this in your final report)
Here’s a clean, professional structure:
✅ 1. Purpose
Why the analysis matters (retention, performance, early intervention).
✅ 2. Data
Brief description of OULAD and key tables.
✅ 3. Methods
Python cleaning, feature engineering, EDA, statistics, dashboard.
✅ 4. Key Findings
3–5 bullet points:
•	Engagement is the strongest predictor of success
•	Late submissions correlate with lower scores
•	Early disengagement predicts withdrawal
•	Certain demographic groups show higher risk
✅ 5. Recommendations
•	Early warning system based on engagement
•	Targeted support for high risk groups
•	Monitoring of assessment submission patterns
✅ 6. Dashboard
Screenshots + explanation.
✅ 7. Limitations
•	Observational data
•	No causal inference
•	Missing variables (motivation, external factors)
✅ 8. Next Steps
•	Predictive modeling
•	Intervention testing
•	Longitudinal tracking




## **Tools & Technologies**

The requirements for this project are:
- Trello for project management
- Python (pandas, numpy, seaborn, matplotlib, scikit learn, statsmodels)
- VS Code for development
- Power BI / Tableau for dashboarding
- GitHub for version control and portfolio presentation
- Data sets
- PostGres
Author
Teresa McGarry Analytics Professional Focused on reproducible workflows, executive dashboards, and portfolio ready data storytelling.
 


 