# Excercise - Merging Tables With Different Join Types

![image](https://user-images.githubusercontent.com/29009536/157815467-26073b7d-a275-4c5c-850e-10d0c9c02226.png)

## Merge the movies table with the financials table with a left join
movies_financials = movies.merge(financials, on='id', how='left')

## Count the number of rows in the budget column that are missing
number_of_missing_fin = movies_financials['budget'].isnull().sum()

## Print the number of movies missing financials
print(number_of_missing_fin)
