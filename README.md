# Lab-4
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
