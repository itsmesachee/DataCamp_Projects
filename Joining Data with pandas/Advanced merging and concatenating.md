# filtering Joins

# Semi join

# Anti Join

# concatenating dataframes vertically
## pd.concat()

-> basically, the join is outer in this, if wanted we can change this to other type.

eg:   pd.concat([df1, df2]), join='<type of join>')

 ->Concatenate tracks_master, tracks_ride, and tracks_st, in that order, setting sort to True.
 ### Concatenate the tracks
tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                               sort=True)
print(tracks_from_albums) 

 ->Concatenate tracks_master, tracks_ride, and tracks_st, where the index goes from 0 to n-1.
 ### Concatenate the tracks so the index goes from 0 to n-1
tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                               ignore_index = True,
                               sort=True)
print(tracks_from_albums)
  

 ### -> Concatenate the tracks, show only columns names that are in all tables
tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                               join='inner',
                               sort=True)
print(tracks_from_albums)
  
## .append()
  
 appending tables
 
 
