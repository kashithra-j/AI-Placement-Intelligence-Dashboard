# Data Transformation and Data Preparation

## 1. Introduction

Data transformation is an important stage in developing the AI Placement Intelligence Dashboard. Raw student placement data must be organized, cleaned, and structured before creating meaningful visualizations.

Microsoft Power BI's Power Query Editor is used to prepare the dataset for analysis.

## 2. Dataset Structure

The original dataset contains the following categories of information:

| Category | Attributes |
|---|---|
| Student Information | Student_ID, Branch |
| Academic Information | CGPA |
| Placement Information | Company, Package_LPA, Placement_Percentage |
| Prediction Information | Probability, Prediction |
| Skill Information | Eight individual skill columns |

The skill attributes include Python, SQL, Java, DSA, Communication, Aptitude, and two additional skill columns.

## 3. Data Import

The dataset is imported into Microsoft Power BI using the following steps:

1. Open Power BI Desktop.
2. Select **Home → Get Data**.
3. Choose Text/CSV.
4. Browse and select the student placement dataset.
5. Preview the dataset.
6. Select Transform Data to open Power Query Editor.

## 4. Data Cleaning

The dataset is reviewed to improve consistency and reliability.

The following data preparation activities are considered:

- Inspecting column names.
- Checking missing or null values.
- Identifying duplicate student records.
- Verifying numerical data types.
- Checking categorical values for inconsistencies.
- Reviewing the CGPA and salary package columns.
- Checking probability values and prediction categories.

### Data Type Configuration

| Column | Expected Data Type |
|---|---|
| Student_ID | Text or Whole Number |
| Branch | Text |
| CGPA | Decimal Number |
| Company | Text |
| Package_LPA | Decimal Number |
| Placement_Percentage | Decimal Number |
| Probability | Decimal Number |
| Prediction | Text or appropriate category |
| Skill Columns | Numeric |

The actual data types should be verified against the original dataset.

## 5. Skill Data Transformation Using Unpivot Columns

The dataset initially contains eight separate skill columns.

For easier comparison and visualization, these columns can be transformed into a normalized structure using Power Query's **Unpivot Columns** feature.

### Original Structure

| Student_ID | Python | SQL | Java | DSA |
|---|---:|---:|---:|---:|
| S001 | 85 | 90 | 75 | 80 |
| S002 | 70 | 80 | 85 | 75 |
| S003 | 90 | 85 | 80 | 90 |

*Illustrative sample values.*

### Transformation Process

1. Open Power Query Editor.
2. Select the eight skill columns.
3. Right-click the selected columns.
4. Choose **Unpivot Columns**.
5. Power Query converts the selected columns into attribute-value pairs.
6. Rename the resulting columns:
   - Attribute → Skill
   - Value → Skill Score

### Transformed Structure

| Student_ID | Skill | Skill Score |
|---|---|---:|
| S001 | Python | 85 |
| S001 | SQL | 90 |
| S001 | Java | 75 |
| S001 | DSA | 80 |
| S002 | Python | 70 |
| S002 | SQL | 80 |

*Illustrative sample values.*

This structure makes it easier to compare skill proficiency across different categories using Power BI charts.

## 6. Handling Transformation Errors

During data transformation, column reference errors may occur if a previous step refers to an incorrect or renamed column.

For example, an error involving the `Attribute` column can occur if the column has been renamed or removed in an earlier transformation step.

To resolve such issues:

1. Open Power Query Editor.
2. Locate the Applied Steps panel.
3. Review the steps following Unpivot Columns.
4. Check the column names used in each step.
5. Correct or remove the problematic transformation step.
6. Verify that the final columns are named Skill and Skill Score.

## 7. Data Loading

After completing the required transformations:

1. Review the final table.
2. Verify column names and data types.
3. Select **Home → Close & Apply**.
4. Load the transformed data into Power BI.
5. Verify that the fields are available for dashboard development.

## 8. Data Preparation Considerations

The following considerations are important:

- Maintain the original student identifiers for accurate student-level analysis.
- Avoid unnecessary removal of valid records.
- Handle missing values appropriately.
- Ensure that skill scores use a consistent scale.
- Verify that probability values are represented consistently.
- Avoid treating AI predictions as actual placement outcomes unless independently validated.

## 9. Conclusion

Data transformation prepares the student placement dataset for effective analysis and visualization.

The use of Power Query cleaning operations and Unpivot Columns helps organize the dataset into a structure suitable for interactive skill analysis, placement comparisons, and prediction-related visualizations.
