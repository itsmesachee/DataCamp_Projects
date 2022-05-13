# Excercise - Merging Tables With Different Join Types

![image](https://user-images.githubusercontent.com/29009536/157815467-26073b7d-a275-4c5c-850e-10d0c9c02226.png)

## Merge the movies table with the financials table with a left join

movies_financials = movies.merge(financials, on='id', how='left')

## Count the number of rows in the budget column that are missing

number_of_missing_fin = movies_financials['budget'].isnull().sum()

## Print the number of movies missing financials

print(number_of_missing_fin)

![image](https://user-images.githubusercontent.com/29009536/168136159-53379313-9da7-4bb6-8ca6-3abc907caef1.png)

# left join
# Merge sequels and financials on index id
sequels_fin = sequels.merge(financials, on='id', how='left')

# Self merge with suffixes as inner join with left on sequel and right on id
orig_seq = sequels_fin.merge(sequels_fin, how='inner', left_on='sequel', 
                             right_on='id', right_index=True,
                             suffixes=('_org','_seq'))

# Add calculation to subtract revenue_org from revenue_seq 
orig_seq['diff'] = orig_seq['revenue_seq'] - orig_seq['revenue_org']

# Select the title_org, title_seq, and diff 
titles_diff = orig_seq[['title_org','title_seq','diff']]

# Print the first rows of the sorted titles_diff
print(titles_diff.sort_values('diff', ascending=False).head())


## Filtering joins

## Mutating Join vs Filtering Joins
#MJ
Combines data from two tables based on matching observations in both tables
#FJ
Filter observations from table based on whether or not they match an observation in another table.


