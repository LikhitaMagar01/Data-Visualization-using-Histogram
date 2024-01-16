TASK 1:

Create a bar chart or histogram to visualize the distribution of a categorical or continuous variable, such as the distribution of ages or genders in a population.

Sample data set:
https://data.worldbank.org/indicator/SP.POP.TOTL

### steps:
1. First of all, import the necessary libraries like pandas for data manipulation, matplotlib.pyplot for basic plotting and seaborn for statistical data visualization

2. Then, pd.read_csv('file.csv') to read the .csv file.

3. skiprows = 3, use to skip the first three rows in the csv file.

4. header = 0, shows the column names that are in the first row of the data

5. df.columns[4:-1], this is to extract the year from the dataframe.

6. df_long = pd.melt(df, id_vars=['Country Name', 'Country Code'], value_vars=years, var_name='Year', value_name='Population')

pd.melt() to reshape the DataFrame from wide to long format. 

7. df_long['Year'] = pd.to_numeric(df_long['Year'], errors='coerce')
df_long = df_long.dropna(subset=['Population', 'Year'])

here, we are converting the 'Year' to numeric type, where we are handling errors by coercing any non-numeric values to NAN. Rows with NaN values in 'Population' or 'Year' are then dropped.

8. plt.figure(figsize=(12, 6))


9. sns.histplot(data=df_long, x='Year', y='Population', hue='Country Name', element='step', stat='density', common_norm=False)
here, we are creating histogram using seaborn histplot()
'Year' on x-axis
'Population' on y-axis
hue color coding with 'Country Name'
element = 'density' density is calculated for each country separated
state='density' density is calculated for each country separately

10. plt.title('Population Histogram by Year and Country')
this is title of the histogram

11. plt.xlabel('Year')
this is label of x axis

12. plt.ylabel('Population')
this is label of y label

13. plt.show()
this is to show the plot.