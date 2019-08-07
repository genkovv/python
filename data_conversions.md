Useful data conversions

list = [i+randrange(10) for i in range(1,100)] - creates a list which has the value of i from the for loop 
series = pd.Series(list) - converts above list to series and you can also do:
series = pd.Series(i+randrange(10) for i in range(1,100)) 
df=series.to_frame() - Convert the series to dataframe
