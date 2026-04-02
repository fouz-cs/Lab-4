# Lab-4
Task 1 – Data Quality Issues
The dataset was loaded from the Excel file using pandas:

df = pd.read_csv("Chocolate_Sales(2).csv")
The first rows were inspected using df.head() to check the content.
Data types were checked using df.dtypes.
Observed issues:
Date column was stored as object instead of datetime.
Amount column contained $ and , symbols, making it non-numeric.
Corrections applied:

Converted Date column to datetime:

df['Date'] = pd.to_datetime(df['Date'], dayfirst=True)

Cleaned Amount column and converted it to numeric:

df['Amount'] = df['Amount'].replace(r'[\$,]', '', regex=True)
df['Amount'] = pd.to_numeric(df['Amount'])
After these changes, data types were checked again to confirm the corrections.
Images to include:
df.head() before and after cleaning
df.dtypes before and after cleaning



In Task 2, we applied a Missing Value strategy called Mean Imputation.

The code we used was:

df2 = df.copy()
df2.loc[0:5, 'Amount'] = np.nan

df_mean = df2.copy()
df_mean['Amount'].fillna(df_mean['Amount'].mean(), inplace=True)
First, we introduced artificial missing values (rows 0–5 in the Amount column) for demonstration purposes.
Then, we applied Mean Imputation, which replaces missing values with the average (mean) of the column.

This ensures that no data is lost while filling gaps, although it may reduce variability slightly and can be sensitive to outliers.

We could also apply this directly to any naturally missing values in the dataset without introducing artificial NaNs.
