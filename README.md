# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
    
# Aim:
TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:
### Step 1:
Import the required packages(pandas,numpy,scipy)

### Step 2:
Read the given csv file

### Step3:
Convert the file into a dataframe and get information of the data.

### Step 4:
Remove the non numerical data columns using drop() method.

### Step 5:
Detect the outliers in the data set using z scores method.

### Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7:
Check if the outliersare removed from data set using graphical methods.

### Step 8:
Save the final data set into the file.


# CODE

# bhp.csv
```
import numpy as np
import pandas as pd
from scipy import stats
a = pd.read_csv('bhp.csv')
df = pd.DataFrame(a['price_per_sqft'])
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
z = np.abs(stats.zscore(df))
df1 = df1[(z < 3)]
print(df1)
```


# height_weight.csv
```
import numpy as np
import pandas as pd
from scipy import stats
a = pd.read_csv('height_weight.csv')
df = pd.DataFrame(a['height'])
print(df)
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
df2 = pd.DataFrame(a['weight'])
print(df2)
q1 = df2.quantile(0.25)
q3 = df2.quantile(0.75)
IQR = q3 - q1
df2_new = df2[((df2 >= q1 - 1.5 * IQR) & (df2 <= q3 + 1.5 * IQR))]
print(df2_new)
```

# OUTPUT 

# bhp.csv
![dsoutbhp1](https://user-images.githubusercontent.com/120623583/229699069-6cb51f8b-79d9-451b-8376-6cd42b4301d6.png)

![dsoutbhp11](https://user-images.githubusercontent.com/120623583/229699119-897b360f-a87f-415c-9852-f26f7728577f.png)

![dsoutbhp111](https://user-images.githubusercontent.com/120623583/229699334-44131cd3-c671-4bc4-94b8-fa0d7ba2f780.png)


# height_weight.csv

![dsoutheight1](https://user-images.githubusercontent.com/120623583/229699445-d00f4b12-e4f3-4911-bad2-94f840d05213.png)

![dsheight11](https://user-images.githubusercontent.com/120623583/229699488-681e851d-cbb5-4bb8-8c53-bb54c9683d91.png)

![dsheighgt111](https://user-images.githubusercontent.com/120623583/229699660-c63a52f1-ae02-4e6b-a389-e9107d54c198.png)


# RESULT 

Thus the required output is displayed.

  








