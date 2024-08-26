x#Pandas 

**Series** : 1-dimensional indexed array of single data-type
**DataFrame** : 2-dimensional collection of series objects

![[Pasted image 20240815123756.png]]

DATA_URL = "`url`"
read_csv : method to read csv file using a DATA_URL
	`df = pd.read_csv(DATA_URL)`

head() to read first 5 lines
	`df.head()`

 each row corresponds to one client, an **instance**, and columns are **features** of this instance.

shape() to see number of rows and columns
	`df.shape()`

columns() to print column names
	`df.columns()`

info() to print general info about the db
	`df.info()`

astype() to change columns data 
	`df[`feature`] = df[`feature`].astype(`datatype`)`

sorting with sort_values()
	`df.sort_values(by=["Churn", "Total day charge"], ascending=[True, False]).head()`
	this is multi-column sorting, and the head function shows the first 5 columns

to get a single column, use `df.[`column_name`]`

**Boolean Indexing In Pandas**
`df [ P ( df ['Name'] ) ]` 

P is any logical condition checked for each element of Name column
	example : `df.select_dtypes(include=np.number)[df["Churn"] == 1].mean()`	
	- **`df.select_dtypes(include=np.number)`**:
    - This part of the code selects all columns in the DataFrame `df` that have a numerical data type (like integers or floats).
	    - `np.number` is used to specify that you're interested in selecting numerical columns. `np` refers to the NumPy library, which is commonly used in data science for numerical operations.
	
- **`df["Churn"] == 1`**:
        - This part is creating a boolean mask where it checks which rows in the `Churn` column have a value equal to `1`.
	    - The `Churn` column presumably indicates whether a customer has churned (left the service). So, this mask will be `True` for rows where the customer has churned.
	
	- **Combining the two**:
        - When you combine these two parts, `df.select_dtypes(include=np.number)[df["Churn"] == 1]`, you are selecting only the rows where `Churn` equals `1` (i.e., customers who churned) from the subset of columns that are numerical.
	
	- **`.mean()`**:
        - Finally, `.mean()` calculates the mean (average) of each numerical column for the rows where the `Churn` value is `1`.


`df[df["Churn"] == 1]["Total day minutes"].mean()`

Indexing by name : 
	`loc()` 

	df.loc[0:5, "State":"Area Code"]
selects rows from 0 to 5 and columns from "State" to "Area Code"

Indexing by number :
	`iloc()`

	df.iloc[0:5, 0:3]
selects rows from 0 to 5 and columns from 0 to 3


df[1:] or df[:-1] for selecting the last line of the data frame

**APPLYING FUNCTIONS TO CELLS, COLUMNS, ROWS**

use apply()
	`df.apply(np.max)` : numpy maximum function

we can use apply() to apply a function to each row by setting axis = 1
	`df.apply(np.max, axis=1)`

To select all states starting with W
	`df[df["State"].apply(lambda state: state[0] == "W")].head()`

**MAP FUNCTION**
The `map` method can be used to **replace values in a column** by passing a dictionary of the form `{old_value: new_value}` as its argument:

`d = {"No": False, "Yes": True}` dictionary to change all 'No's and 'Yes'es to False' and 'True'
`df["International plan"] = df["International plan"].map(d)

Almost the same thing can be done with the `replace` method.

	`df = df.replace({"Voice mail plan": d})
	`df.head()`

There's a slight difference. Еру `replace` method will not do anything with values not found in the mapping dictionary, while `map` will change them to NaNs).

`a_series = pd.Series(['a', 'b', 'c'])

`a_series.replace({'a': 1, 'b': 1})     # 1, 2, c
`a_series.map({'a': 1, 'b': 2})     # 1, 2, NaN

0    1.0
1    2.0
2    NaN
dtype: float64

**GROUPING**
`df.groupby(by=grouping_columns)[columns_to_show].function()`
1. First, the `groupby` method divides the `grouping_columns` by their values. They become a new index in the resulting dataframe.
    
2. Then, columns of interest are selected (`columns_to_show`). If `columns_to_show` is not included, all non groupby clauses will be included.
    
3. Finally, one or several functions are applied to the obtained groups per selected columns.


