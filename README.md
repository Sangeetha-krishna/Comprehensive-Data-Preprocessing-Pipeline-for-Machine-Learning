# Comprehensive-Data-Preprocessing-Pipeline-for-Machine-Learning

Objective
This project aims to design and implement a robust data preprocessing system to address challenges such as missing values, outliers, inconsistent formatting, and noise. By enhancing the quality of the data, we enable its effective use in machine learning models.

---

1. Data Loading
The dataset is loaded from a CSV file using `pandas`. It includes 6 columns: `Company`, `Age`, `Salary`, `Place`, `Country`, and `Gender`. The column names are standardized to lowercase for consistency.

2. Data Exploration
- Unique Values: Extracted unique values and their counts for each column to understand data diversity.
- Statistical Analysis: Summary statistics (`count`, `mean`, `std`, `min`, `max`) were calculated for numerical columns to understand their distributions.

3. Data Cleaning
- Handling Missing Values:
  - Replaced missing categorical values (`company`, `place`) with their mode (most frequent value).
  - Replaced missing numerical values (`age`, `salary`) with their median.
- Invalid Values:
  - `age` values of `0` (invalid) were replaced with `NaN` and treated appropriately.
- Removing Duplicates:
  - Duplicate rows were dropped to ensure data integrity.
- Outlier Detection:
  - Outliers in `age` and `salary` were identified using the IQR (Interquartile Range) method.

4. Data Analysis
- Filtering Data:
  - Filtered rows with `age > 40` and `salary < 5000` for specific analysis.
- Visualization:
  - Scatter plot of `age` vs `salary` to observe relationships.
  - Bar chart showing the distribution of people across different `places`.

5. Data Encoding
- Applied one-hot encoding to categorical variables (`company`, `place`) to convert them into numerical representations, enabling machine learning algorithms to process them.

6. Feature Scaling
- Used two scaling techniques to normalize numerical data:
  - StandardScaler: Scales data to have a mean of 0 and a standard deviation of 1.
  - MinMaxScaler: Scales data to a specified range (default is 0 to 1).

---

Key Functions
1. detect_outliers_iqr:
   Identifies outliers using the IQR method:
   ```python
   def detect_outliers_iqr(column):
       Q1 = column.quantile(0.25)
       Q3 = column.quantile(0.75)
       IQR = Q3 - Q1
       lower_bound = Q1 - 1.5 * IQR
       upper_bound = Q3 + 1.5 * IQR
       return (column < lower_bound) | (column > upper_bound)
   ```

2. Scaling:
   Uses `StandardScaler` and `MinMaxScaler` for numerical data scaling.

---

Outputs
- Filtered Data: Subset of data matching specific criteria.
- Visualizations:
  - Scatter plot of `age` vs `salary`.
  - Bar chart of people distribution by `place`.
- Encoded and Scaled Data: Ready for machine learning applications.

---

Conclusion
This project demonstrates the complete data preprocessing pipeline, ensuring the dataset is clean, consistent, and ready for machine learning tasks. It addresses all challenges, such as missing values, outliers, and categorical data encoding, providing a scalable solution for diverse datasets.

--- 
