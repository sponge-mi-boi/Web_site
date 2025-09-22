```
# Pandas is a module which contains mainly Pandas.series and  Pandas.Dataframe, both of which are very reliable and efficient to use for time series analysis.

## imports the module pandas to be used
	
import pandas as pd

# creates an example series based on a list to describe an index and a list to describe a data set

## in this example, the index is a list of stocks and the data is the corresponding closing prices on some given day

ex_index = ['BRO', 'DIS', 'ICE', 'CSX', 'AAPL', 'KR', 'CBRE', 'CCL', 'BRO', 'INCY', 'HON', 'DD', 'CNP', 'AOS', 'CL', 'CTRA', 'FRT', 'KEYS', 'BR', 'JCI']

ex_data = [15.312822341918945, 112.20580291748047, 40.59511184692383, 8.820080757141113, 25.675556182861328, 31.671602249145508, 37.630001068115234, 44.74552917480469, 15.312822341918945, 109.73999786376953, 81.06645202636719, 52.7418212890625, 13.334376335144043, 30.626880645751953, 54.17769241333008, 18.849369049072266, 95.1009750366211, 30.40999984741211, 45.62876892089844, 28.291528701782227]

example_series = pd.Series(index = ex_index,data = ex_data)
print(example_series)

->

	Ticker
	BRO      15.312822
	DIS     112.205803
	ICE      40.595112
	CSX       8.820081
	AAPL     25.675556
	KR       31.671602
	CBRE     37.630001
	CCL      44.745529
	BRO      15.312822
	INCY    109.739998
	HON      81.066452
	DD       52.741821
	CNP      13.334376
	AOS      30.626881
	CL       54.177692
	CTRA     18.849369
	FRT      95.100975
	KEYS     30.410000
	BR       45.628769
	JCI      28.291529
	dtype: float64

## note that the following are identical ways to instantiate a pd.Series obj

example_series = pd.Series(ex_data,ex_index)
example_series = pd.Series(data = ex_data, index = ex_index)

## data is the only required parameter, called a non-named parameter

## the values to be passed are called named parameters in python compared to non-named parameters which need explict values to be passed, index is a named parameter and the default index value is just the list of integers starting from 0, in the syntax of python functions, named parameters always go first in the order given in the function documentation, or can be expliclty defined like unnamed parameters which is usually prefered if there are many parameters involved, and both types are being used repeatedly 
 

# The easiest way to index a series is the same as a list or a key-value pair
 
 val_1 = example_series['BRO']
 print(val_1)

->
 2 

# But these concepts of indexing are better understood in terms of label based indexing and position based

## label based indexing uses the keyword, or property, `loc`

val_1=example_series.loc['BRO']
print(val_1)

## position based indexing uses the keyword, or property 'iloc'

val_1=example_series.iloc[1]
print(val_1)

## note that for pd.Series, label based indexing is exactly the same as direct indexing, meaning that it is not usually used, however, position based indexing is still useful if the index labels are not exactly known, or if the code being done fits position based indexing better, note however that in any situation

i = 1
val_1=example_series.iloc[i]
val_1=example_series.loc[example_series.index[i]]

## both print the exact same value since an index can be accessed as a list

## direct indexing always supports labels remember and direct indexing based on positioning if the labels are different will always throw a warning, if not an error since position based direct indexing will be removed soon from pandas

print(examples_series[1])

-> 
	Deappreciation Error

# the best method that is commonly used is the rolling method `.rolling(roll_size)` which returns a rolling object upon which rolling operations can be performed

# for example say that a series of close prices is given with date time indices extracted from yahoo finance or any financial time series api

print(series_close)

-> 
	Date
	2015-07-31    110.647507
	2015-08-03    111.680229
	2015-08-04    112.205803
	2015-08-05    101.915573
	2015-08-06    100.089890
	2015-08-07    100.827530
	2015-08-10    102.348946
	2015-08-11     99.582756
	2015-08-12     98.651482
	2015-08-13     99.140152
	2015-08-14     98.808228
	2015-08-17    100.550911
	2015-08-18     98.605385
	2015-08-19     98.153557
	2015-08-20     92.224693
	2015-08-21     91.136650
	2015-08-24     87.927887
	2015-08-25     88.416573
	2015-08-26     91.496277
	2015-08-27     94.207130
	2015-08-28     94.492973
	2015-08-31     93.939735
	2015-09-01     91.754448
	2015-09-02     93.948952
	2015-09-03     94.041168
	2015-09-04     93.100655
	2015-09-08     95.903725
	2015-09-09     93.967392
	2015-09-10     94.603615
	2015-09-11     96.337105
	2015-09-14     95.728539
	2015-09-15     95.368935
	2015-09-16     95.857628
	2015-09-17     96.078918

##
a rolling object can be created with a roll size of siey 20

roll = series_close.rolling(window = 20)

## rolling operations can be performed on this rolling object such as obtaining the rolling mean, std, correlation, and other statistical quantiti

mean_series = roll.mean()
std_series = roll.std()

print(mean_series)
print(std_series)

->	  

	Date
	2015-07-31           NaN
	2015-08-03           NaN
	2015-08-04           NaN
	2015-08-05           NaN
	2015-08-06           NaN
	2015-08-07           NaN
	2015-08-10           NaN
	2015-08-11           NaN
	2015-08-12           NaN
	2015-08-13           NaN
	2015-08-14           NaN
	2015-08-17           NaN
	2015-08-18           NaN
	2015-08-19           NaN
	2015-08-20           NaN
	2015-08-21           NaN
	2015-08-24           NaN
	2015-08-25           NaN
	2015-08-26           NaN
	2015-08-27     98.930858
	2015-08-28     98.123131
	2015-08-31     97.236106
	2015-09-01     96.213539
	2015-09-02     95.815208
	2015-09-03     95.512772
	2015-09-04     95.126428
	2015-09-08     94.804167
	2015-09-09     94.523399
	2015-09-10     94.321005
	2015-09-11     94.180853
	2015-09-14     94.026868
	2015-09-15     93.767770
	2015-09-16     93.630382
	2015-09-17     93.526650
	dtype: float64
	
	Date
	2015-07-31         NaN
	2015-08-03         NaN
	2015-08-04         NaN
	2015-08-05         NaN
	2015-08-06         NaN
	2015-08-07         NaN
	2015-08-10         NaN
	2015-08-11         NaN
	2015-08-12         NaN
	2015-08-13    5.515884
	2015-08-14    5.117316
	2015-08-17    3.991327
	2015-08-18    1.343852
	2015-08-19    1.289702
	2015-08-20    2.669429
	2015-08-21    3.513299
	2015-08-24    4.352872
	2015-08-25    4.869520
	2015-08-26    4.858063
	2015-08-27    4.594309
	2015-08-28    4.301796
	2015-08-31    3.583622
	2015-09-01    3.015551
	2015-09-02    2.337130
	2015-09-03    2.429236
	2015-09-04    2.418818
	2015-09-08    2.098849
	2015-09-09    1.293073
	2015-09-10    1.061163
	2015-09-11    1.296029
	2015-09-14    1.382147
	2015-09-15    1.410616
	2015-09-16    1.091964
	2015-09-17    1.096649
	dtype: float64


## note there are NaN values given where the operation cannot be performed because the roll is not big enough at those points,'NaN' translates to literally not a number
they are advised to be removed from a series n

## example of a series dropping the na values with the 'dropna' metho

std_values_final = std_values.dropna()
print(std_values_final)

## the dropna method has a key,ord inplace,

std_values.dropna(inplace=True)
print(std_values)

## the values can also be filled with some

std_values_final_two = std_values.fillna(0)
print(std_values_final_two)


->

	Date
	2015-08-13    5.515884
	2015-08-14    5.117316
	2015-08-17    3.991327
	2015-08-18    1.343852
	2015-08-19    1.289702
	2015-08-20    2.669429
	2015-08-21    3.513299
	2015-08-24    4.352872
	2015-08-25    4.869520
	2015-08-26    4.858063
	2015-08-27    4.594309
	2015-08-28    4.301796
	2015-08-31    3.583622
	2015-09-01    3.015551
	2015-09-02    2.337130
	2015-09-03    2.429236
	2015-09-04    2.418818
	2015-09-08    2.098849
	2015-09-09    1.293073
	2015-09-10    1.061163
	2015-09-11    1.296029
	2015-09-14    1.382147
	2015-09-15    1.410616
	2015-09-16    1.091964
	2015-09-17    1.096649
	
	Date
	2015-08-13    5.515884
	2015-08-14    5.117316
	2015-08-17    3.991327
	2015-08-18    1.343852
	2015-08-19    1.289702
	2015-08-20    2.669429
	2015-08-21    3.513299
	2015-08-24    4.352872
	2015-08-25    4.869520
	2015-08-26    4.858063
	2015-08-27    4.594309
	2015-08-28    4.301796
	2015-08-31    3.583622
	2015-09-01    3.015551
	2015-09-02    2.337130
	2015-09-03    2.429236
	2015-09-04    2.418818
	2015-09-08    2.098849
	2015-09-09    1.293073
	2015-09-10    1.061163
	2015-09-11    1.296029
	2015-09-14    1.382147
	2015-09-15    1.410616
	2015-09-16    1.091964
	2015-09-17    1.096649
	
	Date
	2015-07-31    0.000000
	2015-08-03    0.000000
	2015-08-04    0.000000
	2015-08-05    0.000000
	2015-08-06    0.000000
	2015-08-07    0.000000
	2015-08-10    0.000000
	2015-08-11    0.000000
	2015-08-12    0.000000
	2015-08-13    5.515884
	2015-08-14    5.117316
	2015-08-17    3.991327
	2015-08-18    1.343852
	2015-08-19    1.289702
	2015-08-20    2.669429
	2015-08-21    3.513299
	2015-08-24    4.352872
	2015-08-25    4.869520
	2015-08-26    4.858063
	2015-08-27    4.594309
	2015-08-28    4.301796
	2015-08-31    3.583622
	2015-09-01    3.015551
	2015-09-02    2.337130
	2015-09-03    2.429236
	2015-09-04    2.418818
	2015-09-08    2.098849
	2015-09-09    1.293073
	2015-09-10    1.061163
	2015-09-11    1.296029
	2015-09-14    1.382147
	2015-09-15    1.410616
	2015-09-16    1.091964
	2015-09-17    1.096649


## This leads to an important point about series in that they are immutable in terms of size. The dropna() function returns a new series which is smaller in size in this example and the inplace=true keyword just does the same, but 'underneath' 

## Values can of course be replaced with little issue 


# This leads to another important concept, which is boolean masking,  essentially a dynamic index vise boolean comparision. 

boolean_mask = [False]*len(series_example)
for i in range(len(boolean_mask)): if i mod 2 == 0 boolean_mask[i] = True 
series_mask = series_close[boolean_mask]
print(series_mask)	
	
# there can also be dynamic comparing in the following qty

series_mask = series_close > 200
print(series_mask)
	
# A series can be indexed like a list with a boolean list of equal length

This leads to the idea of chaining these operations 

print(series_close[series_close > 10000])
	
# a series can have its length obtained in the same way as a list

length = len(series_mask)
print(length)

# this is the same as 

length = len(series_mask.index)

# there is also the shape property can 

length_tuple = series_mask.shape
print(length_tuple)

# there is also a method to shift a series

series_shifted = series_example.shift(periods=amount_of_shift)
print(series_shifted)
 
## there are na values of course from the shift which can be removed by either dropping or filling 
 
# there is also a way to sort a series

series.sort_values(inplace=boolean_inplace,by=function_to_sort,ascending=boolean_ascending) 

# where the keywords are used to define the sorting

# a good example of all these is the creation of z score based entry, exit signals

## Example with z-score based mean reversion where there is a z score 
 
 
 series_mean = series_example.rolling(20).mean().fillna(0)
 series_std = series_example.rolling(20).st().fillna(0)
 series_z_score = (mean - series_clos
 z_score = 
 z_threshold = 1.5
 series_close_indicator = (series_close > z_threshold) &(series_close.shift(1) < z_threshold)
 
# A signal indicator event driven series
This is in contrast to state based signals which are usually not as good.	

series_indicator_example = series_indicator > k

	
```
