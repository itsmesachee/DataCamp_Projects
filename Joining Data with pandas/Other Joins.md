# Excercises - Other Joins

![image](https://user-images.githubusercontent.com/29009536/157827956-45bedc31-e3f7-4aba-9e30-83af46960ad8.png)

## Merge action_movies to the scifi_movies with right join
action_scifi = action_movies.merge(scifi_movies, on='movie_id', how='right',
                                   suffixes=('_act','_sci'))

## From action_scifi, select only the rows where the genre_act column is null
scifi_only = action_scifi[action_scifi['genre_act'].isnull()]

## Merge the movies and scifi_only tables with an inner join
movies_and_scifi_only = movies.merge(scifi_only, how='inner', left_on='id', right_on='movie_id')

## Print the first few rows and shape of movies_and_scifi_only
print(movies_and_scifi_only.head())
print(movies_and_scifi_only.shape)

============================================================================================
# Popular genres with right join

![image](https://user-images.githubusercontent.com/29009536/157828617-c83d6eae-8e14-4306-9c42-34b4dd7fc52d.png)

## Use right join to merge the movie_to_genres and pop_movies tables
genres_movies = movie_to_genres.merge(pop_movies, how='right', 
                                        left_on = 'movie_id',
                                        right_on = 'id' 
                                        )

## Count the number of genres
genre_count = genres_movies.groupby('genre').agg({'id':'count'})

## Plot a bar chart of the genre_count
genre_count.plot(kind='bar')
plt.show()

============================================================================================

# Excercises - Using outer join to select actors

![image](https://user-images.githubusercontent.com/29009536/157829284-9b463dd4-0de5-4bd5-a2ac-b1734fd7f818.png)

## Merge iron_1_actors to iron_2_actors on id with outer join using suffixes
iron_1_and_2 = iron_1_actors.merge(iron_2_actors,
                                     how = 'outer',
                                     on = 'id',
                                     suffixes=('_1','_2'))

## Create an index that returns true if name_1 or name_2 are null
m = ( (iron_1_and_2['name_1'].isnull() ) | 
     (iron_1_and_2['name_2'].isnull())
)

## Print the first few rows of iron_1_and_2
print(iron_1_and_2[m].head())
