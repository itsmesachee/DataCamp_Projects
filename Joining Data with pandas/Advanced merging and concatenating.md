# filtering Joins

# Semi join

# Anti Join

# concatenating dataframes vertically
## pd.concat()

-> basically, the join is outer in this, if wanted we can change this to other type.

eg:   pd.concat([df1, df2]), join='<type of join>')

### ->Concatenate tracks_master, tracks_ride, and tracks_st, in that order, setting sort to True.
  
tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                               sort=True)
print(tracks_from_albums) 

### ->Concatenate tracks_master, tracks_ride, and tracks_st, where the index goes from 0 to n-1.
 Concatenate the tracks so the index goes from 0 to n-1 </br>
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
 
 df1.append([df2, df3], ignore_index=True, sort=True)
 appending tables
 
 ![image](https://user-images.githubusercontent.com/29009536/168926624-140185da-4cde-4cd4-98b6-76ac32e306cc.png)
 
 ## Concatenating with keys
 
 ### Concatenate the tables and add keys
inv_jul_thr_sep = pd.concat([inv_jul, inv_aug, inv_sep], 
                            keys=['7Jul', '8Aug', '9Sep'])

### Group the invoices by the index keys and find avg of the total column
avg_inv_by_month = inv_jul_thr_sep.groupby(level=0).agg({'total':'mean'})

### Bar plot of avg_inv_by_month
avg_inv_by_month.plot(kind='bar')
plt.show()

## Using the append method

![image](https://user-images.githubusercontent.com/29009536/168926995-894387bf-9590-4d42-8e28-c3917676350d.png)

### Use the .append() method to combine the tracks tables
metallica_tracks = tracks_ride.append([tracks_master, tracks_st], sort=False)

### Merge metallica_tracks and invoice_items
tracks_invoices = metallica_tracks.merge(invoice_items, on='tid')

### For each tid and name sum the quantity sold
tracks_sold = tracks_invoices.groupby(['tid','name']).agg({'quantity':'sum'})

### Sort in decending order by quantity and print the results
print(tracks_sold.sort_values(ascending = False, by='quantity'))

# Verifying integrity


 
 
