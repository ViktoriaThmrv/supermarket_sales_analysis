### Project Title: Supermarket Sales Analysis

#### Description:
This guided project created by Bassim Eledath can be found in Coursera as [Exploratory Data Analysis With Python and Pandas](https://www.coursera.org/projects/exploratory-data-analysis-python-pandas). It analyzes the sales data of a supermarket company recorded across three branches over three months. The aim is to explore the dataset, uncover patterns, and derive insights using various data analysis and visualization techniques.

#### Files Included:
- `README.md`
- `supermarket_sales_analysis.md`

## Description

This project analyzes the sales data of a supermarket company recorded across three branches over three months. The aim is to explore the dataset, uncover patterns, and derive insights using various data analysis and visualization techniques.

## Dataset

The dataset is available on Kaggle: [Supermarket Sales Dataset](https://www.kaggle.com/aungpyaeap/supermarket-sales)

### Data Dictionary

- **Invoice id**: Computer generated sales slip invoice identification number
- **Branch**: Branch of supercenter (3 branches are available identified by A, B, and C)
- **City**: Location of supercenters
- **Customer type**: Type of customers, recorded by Members for customers using member card and Normal for without member card
- **Gender**: Gender type of customer
- **Product line**: General item categorization groups - Electronic accessories, Fashion accessories, Food and beverages, Health and beauty, Home and lifestyle, Sports and travel
- **Unit price**: Price of each product in USD
- **Quantity**: Number of products purchased by customer
- **Tax**: 5% tax fee for customer buying
- **Total**: Total price including tax
- **Date**: Date of purchase (Record available from January 2019 to March 2019)
- **Time**: Purchase time (10 am to 9 pm)
- **Payment**: Payment method used by customer for purchase (3 methods are available – Cash, Credit card, and Ewallet)
- **COGS**: Cost of goods sold
- **Gross margin percentage**: Gross margin percentage
- **Gross income**: Gross income
- **Rating**: Customer stratification rating on their overall shopping experience (On a scale of 1 to 10)

## Project Structure

- `supermarket_sales_analysis.md`: containing the analysis and visualizations
- `README.md`: Project documentation

## Analysis Overview

**Task 1: Initial data exploration**

**Task 2: Data cleaning and preparation**

**Task 3: Univariate analysis**

**Task 4: Dealing with duplicate rows and missing values**

**Task 5: Correlation analysis**


### Task 1: Initial data exploration

**1. Load the dataset:**
```python
df = pd.read_csv('supermarket_sales.csv')
```
- We begin by loading the dataset from a CSV file into a DataFrame called `df`.

**2. Display the first few rows:**
```python
df.head()
```
- This command shows the first five rows of the DataFrame, giving us an initial look at the data.

### Output

| Invoice ID  | Branch | City      | Customer type | Gender | Product line         | Unit price | Quantity | Tax 5%  | Total     | Date    | Time  | Payment    | cogs    | gross margin percentage | gross income | Rating |
|-------------|--------|-----------|---------------|--------|----------------------|------------|----------|---------|-----------|---------|-------|------------|---------|------------------------|--------------|--------|
| 750-67-8428 | A      | Yangon    | Member        | Female | Health and beauty    | 74.69      | 7.0      | 26.1415 | 548.9715  | 1/5/19  | 13:08 | Ewallet    | 522.83  | 4.761905               | 26.1415      | 9.1    |
| 226-31-3081 | C      | Naypyitaw | Normal        | Female | Electronic accessories | 15.28    | 5.0      | 3.8200  | 80.2200   | 3/8/19  | 10:29 | Cash       | 76.40   | 4.761905               | 3.8200       | 9.6    |
| 631-41-3108 | A      | Yangon    | Normal        | Male   | Home and lifestyle   | 46.33      | 7.0      | 16.2155 | 340.5255  | 3/3/19  | 13:23 | Credit card| 324.31  | 4.761905               | 16.2155      | 7.4    |
| 123-19-1176 | A      | Yangon    | Member        | Male   | Health and beauty    | 58.22      | 8.0      | 23.2880 | 489.0480  | 1/27/19 | 20:33 | Ewallet    | 465.76  | 4.761905               | 23.2880      | 8.4    |
| 373-73-7910 | A      | Yangon    | Normal        | Male   | Sports and travel    | 86.31      | 7.0      | 30.2085 | 634.3785  | 2/8/19  | 10:37 | Ewallet    | 604.17  | 4.761905               | 30.2085      | 5.3    |


**3. Display the last few rows:**
```python
df.tail()
```
- This command shows the last five rows of the DataFrame to help us understand how the data ends.
###  Output

| Invoice ID  | Branch | City     | Customer type | Gender | Product line          | Unit price | Quantity | Tax 5%  | Total    | Date     | Time  | Payment   | cogs   | gross margin percentage | gross income | Rating |
|-------------|--------|----------|---------------|--------|-----------------------|------------|----------|---------|----------|----------|-------|-----------|--------|------------------------|--------------|--------|
| 347-56-2442 | A      | Yangon   | Normal        | Male   | Home and lifestyle    | 65.82      | 1.0      | 3.291   | 69.111   | 2/22/19  | 15:33 | Cash      | 65.82  | 4.761905               | 3.291        | 4.1    |
| 849-09-3807 | A      | Yangon   | Member        | Female | Fashion accessories   | 88.34      | 7.0      | 30.919  | 649.299  | 2/18/19  | 13:28 | Cash      | 618.38 | 4.761905               | 30.919       | 6.6    |
| 849-09-3807 | A      | Yangon   | Member        | Female | Fashion accessories   | 88.34      | 7.0      | 30.919  | 649.299  | 2/18/19  | 13:28 | Cash      | 618.38 | 4.761905               | 30.919       | 6.6    |
| 745-74-0715 | A      | Yangon   | Normal        | Male   | Electronic accessories| NaN        | 2.0      | 5.803   | 121.863  | 3/10/19  | 20:46 | Ewallet   | 116.06 | 4.761905               | 5.803        | 8.8    |
| 452-04-8808 | B      | Mandalay | Normal        | Male   | Electronic accessories| 87.08      | NaN      | 30.478  | 640.038  | 1/26/19  | 15:17 | Cash      | 609.56 | 4.761905               | 30.478       | 5.5    |


**4. Display the column names:**
```python
df.columns
```
- This displays the names of all the columns in the DataFrame, helping us understand the structure of the dataset.

### Output

| Invoice ID | Branch | City | Customer type | Gender | Product line | Unit price | Quantity | Tax 5% | Total | Date | Time | Payment | cogs | gross margin percentage | gross income | Rating |

**5. Display the data types of each column:**
```python
df.dtypes
```
- This command shows the data type of each column. Here, we notice that the `Date` column is of type `object` (string) when it should be a `datetime` type.

## Output

| Invoice ID              | Branch | City    | Customer type | Gender | Product line         | Unit price | Quantity | Tax 5%  | Total   | Date       | Time  | Payment   | cogs     | gross margin percentage | gross income | Rating |
|-------------------------|--------|---------|---------------|--------|----------------------|------------|----------|---------|---------|------------|-------|-----------|----------|-------------------------|---------------|--------|
| object                  | object | object  | object        | object | object               | float64    | float64  | float64 | float64 | object     | object| object    | float64  | float64                 | float64       | float64|

### Task 2: Data Cleaning and Preparation

**1. Convert `Date` column to datetime:**
```python
df['Date'] = pd.to_datetime(df['Date'])
```
- Converts the `Date` column from a string to a `datetime` object for easier manipulation and analysis of date-related data. And to check the result:
```python
df['Date']
```

### Output

| Date       |
|------------|
| 2019-01-05 |
| 2019-03-08 |
| 2019-03-03 |
| 2019-01-27 |
| 2019-02-08 |
| ...        |
| 2019-02-22 |
| 2019-02-18 |
| 2019-02-18 |
| 2019-03-10 |
| 2019-01-26 |


**3. Display updated data types:**
```python
df.dtypes
```
- Confirms that the `Date` column is now of type `datetime64[ns]`.

### Output

| Invoice ID | Branch | City | Customer type | Gender | Product line | Unit price | Quantity | Tax 5% | Total | Date       | Time | Payment | cogs | gross margin percentage | gross income | Rating |
|------------|--------|------|---------------|--------|--------------|------------|----------|--------|-------|------------|------|---------|------|-------------------------|--------------|--------|

**4. Set `Date` as the index:**
```python
df.set_index('Date', inplace=True)
```
- Sets the `Date` column as the index of the DataFrame for time series analysis. `inplace=True` ensures the change is permanent. To verify it's working:
```python
df.head()
```
| Date       | Invoice ID | Branch     | City       | Customer type | Gender | Product line          | Unit price | Quantity | Tax 5% | Total   | Time  | Payment    | cogs   | gross margin percentage | gross income | Rating |
|------------|------------|------------|------------|---------------|--------|-----------------------|------------|----------|--------|---------|-------|------------|--------|-------------------------|--------------|--------|
| 2019-01-05 | 750-67-8428| A          | Yangon     | Member        | Female | Health and beauty     | 74.69      | 7.0      | 26.1415| 548.9715| 13:08 | Ewallet    | 522.83 | 4.761905                | 26.1415      | 9.1    |
| 2019-03-08 | 226-31-3081| C          | Naypyitaw  | Normal        | Female | Electronic accessories| 15.28      | 5.0      | 3.8200 | 80.2200 | 10:29 | Cash       | 76.40  | 4.761905                | 3.8200       | 9.6    |
| 2019-03-03 | 631-41-3108| A          | Yangon     | Normal        | Male   | Home and lifestyle    | 46.33      | 7.0      | 16.2155| 340.5255| 13:23 | Credit card| 324.31 | 4.761905                | 16.2155      | 7.4    |
| 2019-01-27 | 123-19-1176| A          | Yangon     | Member        | Male   | Health and beauty     | 58.22      | 8.0      | 23.2880| 489.0480| 20:33 | Ewallet    | 465.76 | 4.761905                | 23.2880      | 8.4    |
| 2019-02-08 | 373-73-7910| A          | Yangon     | Normal        | Male   | Sports and travel     | 86.31      | 7.0      | 30.2085|         | 10:37 | Ewallet    | 604.17 | 4.761905                | 30.2085      | 5.3    |


### Task 3: Univariate Analysis

**1. Summary statistics:**
```python
df.describe()
```
- Generates summary statistics for all numeric columns, including count, mean, standard deviation, min, and max values.

### Output

|              | Unit price | Quantity |  Tax 5%  |   Total  |   cogs   | gross margin percentage | gross income |  Rating  |
|--------------|------------|----------|----------|----------|----------|-------------------------|--------------|----------|
| count        | 996.000    | 983.000  | 1003.000 | 1003.000 | 1003.000 | 1003.000                | 1003.000     | 1003.000 |
| mean         | 55.765     | 5.502    | 15.400   | 323.408  | 308.007  | 4.762                   | 15.400       | 6.973    |
| std          | 26.510     | 2.925    | 11.715   | 246.019  | 234.304  | 0.000                   | 11.715       | 1.718    |
| min          | 10.080     | 1.000    | 0.509    | 10.679   | 10.170   | 4.762                   | 0.509        | 4.000    |
| 25%          | 33.125     | 3.000    | 5.895    | 123.790  | 117.895  | 4.762                   | 5.895        | 5.500    |
| 50%          | 55.420     | 5.000    | 12.096   | 254.016  | 241.920  | 4.762                   | 12.096       | 7.000    |
| 75%          | 78.085     | 8.000    | 22.540   | 473.330  | 450.790  | 4.762                   | 22.540       | 8.500    |
| max          | 99.960     | 10.000   | 49.650   | 1042.650 | 993.000  | 4.762                   | 49.650       |          |


**2. Distribution of customer ratings:**
```python
sns.distplot(df['Rating'])
```
- Plots the distribution of the `Rating` column to see how customer ratings are spread across the dataset.

### Output

![image](https://github.com/user-attachments/assets/736b0543-ae43-4558-9a2d-dd466730a7e3)

**3. Adding a mean line to the plot:**
```python
plt.axvline(x=np.mean(df['Rating']), c='red', ls='--')
```
- Adds a vertical line at the mean rating to the distribution plot for better visualization and formats the line red.

### Output

![image](https://github.com/user-attachments/assets/57ad91f2-9877-4fa6-b0e6-ef2778888e14)


**4. Adding percentile lines to the plot:**
```python
plt.axvline(x=np.percentile(df['Rating'], 25), c='green', ls='--', label='25th percentile')
plt.axvline(x=np.percentile(df['Rating'], 75), c='green', ls='--', label='75th percentile')
plt.legend()
```
- Adds lines for the 25th and 75th percentiles to the plot to show the spread of most ratings along with formatting of each line in differen colors.

### Output

![image](https://github.com/user-attachments/assets/1702f1da-fa61-4660-8f85-da208f0743c7)

**5. Histogram for all numeric variables:**
```python
df.hist(figsize=(10, 10))
```
- Creates histograms for all numeric variables to visualize their distributions. In the tax view we can see that the data is skewed on the right, which means that most of the tax collected is between 0 and 20, but there are a few cases where its over 40. The gross rating, cogs and gross income are highly correlated variables, so its normal to see they follow identical distributions. The user rating has a uniform distribution. 

### Output

![image](https://github.com/user-attachments/assets/b6190daf-1ea4-4d3d-a470-cb3eb3b5c61f)
![image](https://github.com/user-attachments/assets/9318f815-fb45-4af2-8c89-02c8108945ab)

### Task 4: Bivariate Analysis

**1. Branch sales distribution:**
```python
sns.countplot(df['Branch'])
```
- Plots the number of sales per branch to see if sales numbers differ significantly.

### Output



**2. Exact branch sales counts:**
```python
df['Branch'].value_counts()
```
- Provides the exact count of sales for each branch to see if aggregate sales numbers differ by much between branches.

### Output

![image](https://github.com/user-attachments/assets/67fbc891-1308-4cdd-ab16-0af87b317b99)

And to check the exact numeric values:

```python
df['Branch'].value_counts()
```
### Output

| A | 342 |
| B | 333 |
| C | 328 |

**3. Payment method distribution:**
```python
sns.countplot(df['Payment'])
```
- Plots the distribution of different payment methods used. Here, we can see that Ewallet seems to be the most popular form of payment

### Output

![image](https://github.com/user-attachments/assets/148d8038-8ee6-4672-92b1-a4b638effa3a)


**4. Relationship between rating and gross income:**
```python
sns.scatterplot(df['Rating'], df['gross income'])
```
- Creates a scatter plot to visualize any relationship between customer ratings and gross income. Here, we're looking at how ratings are influenced by gross income and there doesn't seem to be a relationship between customer rating and gross income.

### Output

![image](https://github.com/user-attachments/assets/dc63884f-be35-414e-a140-fec69aff4742)

**5. Regression plot for rating and gross income:**
```python
sns.regplot(df['Rating'], df['gross income'])
```
- Adds a regression line to the scatter plot to better visualize any trends.

### Output

![image](https://github.com/user-attachments/assets/80308485-534e-44e4-887f-55df41314a7a)

**6. Branch-wise gross income comparison:**
```python
sns.boxplot(x=df['Branch'], y=df['gross income'])
```
- Uses a box plot to compare gross income distributions across different branches. There doesn’t seem to be a variation in the gross income between the branches.

### Output

![image](https://github.com/user-attachments/assets/dca2d32f-b8f9-40ea-8799-9861b0edad7c)

**7. Gender-wise gross income comparison:**
```python
sns.boxplot(x=df['Gender'], y=df['gross income'])
```
- Uses a box plot to compare gross income distributions between genders. On average, they seem to be similar, the men and women in this data set spend about the same.

### Output

![image](https://github.com/user-attachments/assets/e6e1f755-89a9-4feb-b3f8-2edc702b395e)


**8. Time trend in gross income:**
```python
df.groupby(df.index).mean()
sns.lineplot(x=df.groupby(df.index).mean().index, y=df.groupby(df.index).mean()['gross income'])
```
- Groups data by date and plots the mean gross income over time to identify any trends. This is done by using Seaborn’s line plot. In this plot, we cannot use the data frame as is in this plot, because dates are repeated, and there can be multiple customers at any given date, in this case, we would have to aggregate the data. Instead, we can use group by, a function in pandas. In the table below, each date row is unique and it represents the average variable value for that particular day.

**9. Pair plot for all relationships:**
```python
sns.pairplot(df)
```
- Creates pair plots for all variables to visualize their relationships, but can be overwhelming for large datasets.

### Output

| Date       | Unit price | Quantity | Tax 5%    | Total     | cogs      | gross margin percentage | gross income | Rating   |
|------------|------------|----------|-----------|-----------|-----------|-------------------------|--------------|----------|
| 2019-01-01 | 54.995833  | 6.454545 | 18.830083 | 395.431750| 376.601667| 4.761905                | 18.830083    | 6.583333 |
| 2019-01-02 | 44.635000  | 6.000000 | 11.580375 | 243.187875| 231.607500| 4.761905                | 11.580375    | 6.050000 |
| 2019-01-03 | 59.457500  | 4.625000 | 12.369813 | 259.766062| 247.396250| 4.761905                | 12.369813    | 8.112500 |
| 2019-01-04 | 51.743333  | 5.333333 | 12.886417 | 270.614750| 257.728333| 4.761905                | 12.886417    | 6.516667 |
| 2019-01-05 | 61.636667  | 4.583333 | 14.034458 | 294.723625| 280.689167| 4.761905                | 14.034458    | 7.433333 |
| ...        | ...        | ...      | ...       | ...       | ...       | ...                     | ...          | ...      |
| 2019-03-26 | 42.972308  | 4.000000 | 7.188692  | 150.962538| 143.773846| 4.761905                | 7.188692     | 6.623077 |
| 2019-03-27 | 56.841000  | 4.500000 | 13.822950 | 290.281950| 276.459000| 4.761905                | 13.822950    | 6.760000 |
| 2019-03-28 | 45.525000  | 4.800000 | 10.616200 | 222.940200| 212.324000| 4.761905                | 10.616200    | 7.050000 |
| 2019-03-29 | 66.346250  | 6.750000 | 23.947875 | 502.905375| 478.957500| 4.761905                | 23.947875    | 6.925000 |
| 2019-03-30 | 67.408182  | 5.888889 | 19.424500 | 407.914500| 388.490000| 4.761905                | 19.424500    |          |

**10. Generating the graph**

First, we would need the index.

```python
df.groupby(df.index).mean().index
```
### Output

| Date       |
|------------|
| 2019-01-01 |
| 2019-01-02 |
| 2019-01-03 |
| 2019-01-04 |
| 2019-01-05 |
| 2019-01-06 |
| 2019-01-07 |
| 2019-01-08 |
| 2019-01-09 |
| 2019-01-10 |
| 2019-01-11 |
| 2019-01-12 |
| 2019-01-13 |
| 2019-01-14 |
| 2019-01-15 |
| 2019-01-16 |
| 2019-01-17 |
| 2019-01-18 |
| 2019-01-19 |
| 2019-01-20 |
| 2019-01-21 |
| 2019-01-22 |
| 2019-01-23 |
| 2019-01-24 |
| 2019-01-25 |
| 2019-01-26 |
| 2019-01-27 |
| 2019-01-28 |
| 2019-01-29 |
| 2019-01-30 |
| 2019-01-31 |
| 2019-02-01 |
| 2019-02-02 |
| 2019-02-03 |
| 2019-02-04 |
| 2019-02-05 |
| 2019-02-06 |
| 2019-02-07 |
| 2019-02-08 |
| 2019-02-09 |
| 2019-02-10 |
| 2019-02-11 |
| 2019-02-12 |
| 2019-02-13 |
| 2019-02-14 |
| 2019-02-15 |
| 2019-02-16 |
| 2019-02-17 |
| 2019-02-18 |
| 2019-02-19 |
| 2019-02-20 |
| 2019-02-21 |
| 2019-02-22 |
| 2019-02-23 |
| 2019-02-24 |
| 2019-02-25 |
| 2019-02-26 |
| 2019-02-27 |
| 2019-02-28 |
| 2019-03-01 |
| 2019-03-02 |
| 2019-03-03 |
| 2019-03-04 |
| 2019-03-05 |
| 2019-03-06 |
| 2019-03-07 |
| 2019-03-08 |
| 2019-03-09 |
| 2019-03-10 |
| 2019-03-11 |
| 2019-03-12 |
| 2019-03-13 |
| 2019-03-14 |
| 2019-03-15 |
| 2019-03-16 |
| 2019-03-17 |
| 2019-03-18 |
| 2019-03-19 |
| 2019-03-20 |
| 2019-03-21 |
| 2019-03-22 |
| 2019-03-23 |
| 2019-03-24 |
| 2019-03-25 |
| 2019-03-26 |
| 2019-03-27 |
| 2019-03-28 |
| 2019-03-29 |
| 2019-03-30 |

Now, we can go ahead and pass the following to generate the graph:

```python
sns.lineplot(x=df.groupby(df.index).mean().index, y=df.groupby(df.index).mean()['gross income'])
```
- Here, the X variable is the index, which is the individual unique days and the Y variable is the gross income or the mean gross income associated with those days.
No time trend can be noticed, it varies around the same mean, but there are days where there are high number of gross incomes and other days with lower gross incomes.

### Output

![image](https://github.com/user-attachments/assets/9d08b9d3-158c-4cee-831a-fd90e2e01f71)

### Task 4: Dealing with duplicate rows and missing values

**1. Identify duplicates:**
```python
df.duplicated()
```
- Checks for duplicate rows in the DataFrame.

### Output

| Date       | Value  |
|------------|--------|
| 2019-01-05 | False  |
| 2019-03-08 | False  |
| 2019-03-03 | False  |
| 2019-01-27 | False  |
| 2019-02-08 | False  |
| ...        | ...    |
| 2019-02-22 | False  |
| 2019-02-18 | False  |
| 2019-02-18 | True   |
| 2019-03-10 | True   |
| 2019-01-26 | True   |

**2. Count duplicate rows:**
```python
df.duplicated().sum()
```
- Counts the number of duplicate rows.

### Output
```plaintext
3
```

**3. Display duplicate rows:**
```python
df[df.duplicated() == True]
```
- Displays the duplicate rows for inspection.

### Output

| Date       | Invoice ID | Branch | City     | Customer type | Gender | Product line           | Unit price | Quantity | Tax 5%  | Total   | Time  | Payment | cogs    | gross margin percentage | gross income | Rating |
|------------|------------|--------|----------|---------------|--------|------------------------|------------|----------|---------|---------|-------|---------|---------|-------------------------|--------------|--------|
| 2019-02-18 | 849-09-3807| A      | Yangon   | Member        | Female | Fashion accessories    | 88.34      | 7.0      | 30.919  | 649.299 | 13:28 | Cash    | 618.38  | 4.761905                | 30.919       | 6.6    |
| 2019-03-10 | 745-74-0715| A      | Yangon   | Normal        | Male   | Electronic accessories | NaN        | 2.0      | 5.803   | 121.863 | 20:46 | Ewallet | 116.06  | 4.761905                | 5.803        | 8.8    |
| 2019-01-26 | 452-04-8808| B      | Mandalay | Normal        | Male   | Electronic accessories | 87.08      | NaN      | 30.478  | 640.038 | 15:17 | Cash    | 609.56  | 4.761905                | 30.478       | 5.5    |


**4. Remove duplicate rows:**
```python
df.drop_duplicates(inplace=True)
```
- Removes duplicate rows from the DataFrame.

**5. Identify missing values:**
```python
df.isna().sum()
```
- Counts the number of missing values in each column.

## Output

| Field                   | Missing Values |
|-------------------------|-----------------|
| Invoice ID              | 0               |
| Branch                  | 0               |
| City                    | 0               |
| Customer type           | 79              |
| Gender                  | 0               |
| Product line            | 43              |
| Unit price              | 6               |
| Quantity                | 19              |
| Tax 5%                  | 0               |
| Total                   | 0               |
| Time                    | 0               |
| Payment                 | 0               |
| cogs                    | 0               |
| gross margin percentage | 0               |
| gross income            | 0               |

**If we wanted to see the ratio, we would divide by the lenght:**
```python
df.isna().sum()/len(df)
```
### Output

| Field                   | Missing Values (%) |
|-------------------------|---------------------|
| Invoice ID              | 0.000               |
| Branch                  | 0.000               |
| City                    | 0.000               |
| Customer type           | 0.079               |
| Gender                  | 0.000               |
| Product line            | 0.043               |
| Unit price              | 0.006               |
| Quantity                | 0.019               |
| Tax 5%                  | 0.000               |
| Total                   | 0.000               |
| Time                    | 0.000               |
| Payment                 | 0.000               |
| cogs                    | 0.000               |
| gross margin percentage | 0.000               |
| gross income            | 0.000               |
| Rating                  | 0.000               |

**6. Visualisation using Seaborn's heatmap**
```python
sns.heatmap(df.isnull())
```
- Uses Seaborn's heatmap to visually highlight missing values in a DataFrame, where missing values are indicated by one color and non-missing values by another.

### Output

![image](https://github.com/user-attachments/assets/bb66074f-9953-4517-84c5-7eedbf9e4e5f)

# Task 5: Correlation Analysis

**1. Correlation Coefficient between 'gross income' and 'Rating'**

```python
import numpy as np

correlation_matrix = np.corrcoef(df['gross income'], df['Rating'])
print(correlation_matrix)
```

### Output:
```plaintext
array([[ 1.       , -0.0364417],
       [-0.0364417,  1.       ]])
```

**To get a specific number:**
```python
specific_correlation = np.corrcoef(df['gross income'], df['Rating'])[1][0]
print(specific_correlation)
```

### Output:
```plaintext
-0.03644170499701835
```

**To round it up:**
```python
rounded_correlation = round(np.corrcoef(df['gross income'], df['Rating'])[1][0], 2)
print(rounded_correlation)
```

### Output:
```plaintext
-0.04
```

**2. Correlation Matrix**

Instead of calculating the correlation for every pair of columns individually, we can look at a correlation matrix and round the values:

```python
correlation_matrix_rounded = np.round(df.corr(), 2)
print(correlation_matrix_rounded)
```

### Output
|                           | Unit price | Quantity | Tax 5% | Total | cogs | gross margin percentage | gross income | Rating |
|---------------------------|------------|----------|--------|-------|------|-------------------------|--------------|--------|
| Unit price                | 1.00       | 0.01     | 0.62   | 0.62  | 0.62 | -0.00                   | 0.62         | -0.01  |
| Quantity                  | 0.01       | 1.00     | 0.69   | 0.69  | 0.69 | 0.00                    | 0.69         | -0.01  |
| Tax 5%                    | 0.62       | 0.69     | 1.00   | 1.00  | 1.00 | 0.00                    | 1.00         | -0.04  |
| Total                     | 0.62       | 0.69     | 1.00   | 1.00  | 1.00 | 0.00                    | 1.00         | -0.04  |
| cogs                      | 0.62       | 0.69     | 1.00   | 1.00  | 1.00 | 0.00                    | 1.00         | -0.04  |
| gross margin percentage   | -0.00      | 0.00     | 0.00   | 0.00  | 0.00 | 1.00                    | 0.00         | 0.00   |
| gross income              | 0.62       | 0.69     | 1.00   | 1.00  | 1.00 | 0.00                    | 1.00         | -0.04  |
| Rating                    | -0.01      | -0.01    | -0.04  | -0.04 | -0.04| 0.00                    | -0.04        | 1.00   |

### Visualizing Correlation Matrix

We can use Seaborn's heatmap to visualize the correlation matrix:

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(np.round(df.corr(), 2))
plt.show()
```
### Output

![image](https://github.com/user-attachments/assets/8fc5b73d-e35c-4d1d-bbf5-891604ce2dc9)

For even more detailed information:

```python
sns.heatmap(np.round(df.corr(), 2), annot=True)
plt.show()
```

### Output

![image](https://github.com/user-attachments/assets/0fcba32e-d241-44db-a0c7-9dbdb4251a9e)

### Conclusion

The user rating seems to have very low correlation with every other variable. It doesn't seem like the amount which a customer spends on an item is in any way correlated with their overall shopping experience rating.
