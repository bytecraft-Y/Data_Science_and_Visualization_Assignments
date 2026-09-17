# Data_Science_and_Visualization_Assignments

This repository contains Python Pandas solutions for a set of 50 practical data operations questions based on the `students - students.csv` dataset. The dataset includes demographics, academic metrics, and skill levels of 200 students.

## Dataset Overview

The dataset (`students - students.csv`) contains 21 columns and 200 rows. Key columns include:
*   `student_id`, `student_name`, `gender`, `age`, `semester`
*   `attendance_percent`, `study_hours_per_day`, `previous_cgpa`
*   `python_skill_level`, `mathematics_skill`
*   `engagement_score`, `predicted_score`, `grade`, `risk_level`

## Sections and Code Cells

The operations are divided into five core sections. Below are the Pandas commands used to solve each cell/question.

### A. Loading and Exploring the Dataset
*   **Cell 1:** Load data -> `pd.read_csv('students - students.csv')`
*   **Cell 2:** First 5 rows -> `df.head(5)`
*   **Cell 3:** Last 10 rows -> `df.tail(10)`
*   **Cell 4:** Dataset dimensions -> `df.shape`
*   **Cell 5:** Column names -> `df.columns.tolist()`
*   **Cell 6:** Data types -> `df.dtypes`
*   **Cell 7:** Dataset summary -> `df.info()`
*   **Cell 8:** Descriptive statistics -> `df.describe()`
*   **Cell 9:** Count missing values -> `df.isnull().sum()`
*   **Cell 10:** Count unique values -> `df.nunique()`

### B. Selecting and Accessing Data
*   **Cell 11:** Select specific columns -> `df[['student_name', 'gender', 'semester']]`
*   **Cell 12:** Filter by semester -> `df[df['semester'] == 3]`
*   **Cell 13:** Filter by gender -> `df[df['gender'] == 'Female']`
*   **Cell 14:** Filter by high CGPA -> `df[df['previous_cgpa'] > 8.0]`
*   **Cell 15:** Filter by low attendance -> `df[df['attendance_percent'] < 75]`
*   **Cell 16:** Filter by study hours -> `df[df['study_hours_per_day'] > 4]`
*   **Cell 17:** Filter by skill level -> `df[df['python_skill_level'] == 'Advanced']`
*   **Cell 18:** Filter by grade -> `df[df['grade'] == 'A']`
*   **Cell 19:** Filter by risk -> `df[df['risk_level'] == 'High']`
*   **Cell 20:** Conditional select (Score > 80) -> `df.loc[df['predicted_score'] > 80, ['student_name', 'predicted_score']]`

### C. Filtering with Multiple Conditions
*   **Cell 21:** Sem 4 AND Attendance > 80% -> `df[(df['semester'] == 4) & (df['attendance_percent'] > 80)]`
*   **Cell 22:** CGPA > 8.0 AND Score > 75 -> `df[(df['previous_cgpa'] > 8.0) & (df['predicted_score'] > 75)]`
*   **Cell 23:** Sem 2 OR Sem 4 -> `df[df['semester'].isin([2, 4])]`
*   **Cell 24:** Female AND Advanced Python -> `df[(df['gender'] == 'Female') & (df['python_skill_level'] == 'Advanced')]`
*   **Cell 25:** Study hours between 2 and 5 -> `df[df['study_hours_per_day'].between(2, 5)]`
*   **Cell 26:** Grade A OR B -> `df[df['grade'].isin(['A', 'B'])]`
*   **Cell 27:** Risk Medium OR High -> `df[df['risk_level'].isin(['Medium', 'High'])]`
*   **Cell 28:** Math skill Good OR Excellent -> `df[df['mathematics_skill'].isin(['Good', 'Excellent'])]` *(Note: Dataset contains 'Low', 'Medium', 'High')*
*   **Cell 29:** Projects >= 2 AND Engagement > 70 -> `df[(df['projects_completed'] >= 2) & (df['engagement_score'] > 70)]`
*   **Cell 30:** Attendance > 85% AND Study > 3 AND Grade A -> `df[(df['attendance_percent'] > 85) & (df['study_hours_per_day'] > 3) & (df['grade'] == 'A')]`

### D. Sorting and Ranking
*   **Cell 31:** Sort by score (desc) -> `df.sort_values(by='predicted_score', ascending=False)`
*   **Cell 32:** Top 10 predicted scores -> `df.nlargest(10, 'predicted_score')`
*   **Cell 33:** Bottom 10 predicted scores -> `df.nsmallest(10, 'predicted_score')`
*   **Cell 34:** Student with max score -> `df.loc[df['predicted_score'].idxmax()]`
*   **Cell 35:** Student with min score -> `df.loc[df['predicted_score'].idxmin()]`
*   **Cell 36:** Sort by CGPA (desc) -> `df.sort_values(by='previous_cgpa', ascending=False)`
*   **Cell 37:** Sort by Sem (asc) then Score (desc) -> `df.sort_values(by=['semester', 'predicted_score'], ascending=[True, False])`
*   **Cell 38:** Rank by score -> `df['score_rank'] = df['predicted_score'].rank(ascending=False)`
*   **Cell 39:** Top 10 engagement scores -> `df.nlargest(10, 'engagement_score')`
*   **Cell 40:** Student with max online activity -> `df.loc[df['online_activity_count'].idxmax()]`

### E. GroupBy and Aggregation
*   **Cell 41:** Avg score by semester -> `df.groupby('semester')['predicted_score'].mean()`
*   **Cell 42:** Avg attendance by semester -> `df.groupby('semester')['attendance_percent'].mean()`
*   **Cell 43:** Avg study hours by gender -> `df.groupby('gender')['study_hours_per_day'].mean()`
*   **Cell 44:** Student count by grade -> `df['grade'].value_counts()`
*   **Cell 45:** Student count by risk level -> `df['risk_level'].value_counts()`
*   **Cell 46:** Avg score by Python skill -> `df.groupby('python_skill_level')['predicted_score'].mean()`
*   **Cell 47:** Avg CGPA by Math skill -> `df.groupby('mathematics_skill')['previous_cgpa'].mean()`
*   **Cell 48:** Avg engagement by semester -> `df.groupby('semester')['engagement_score'].mean()`
*   **Cell 49:** Max/Min score by grade -> `df.groupby('grade')['predicted_score'].agg(['max', 'min'])`
*   **Cell 50:** Multi-metric summary by semester -> 
    ```python
    df.groupby('semester').agg(
        avg_attendance=('attendance_percent', 'mean'),
        avg_study_hours=('study_hours_per_day', 'mean'),
        avg_predicted_score=('predicted_score', 'mean'),
        student_count=('student_id', 'count')
    )
    ```

## Requirements
*   Python 3.x
*   Pandas (`pip install pandas`)
