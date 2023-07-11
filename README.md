# The Standard Normal Distribution - Lab

## Introduction

In the previous lesson, you learned about the formula of the $z$-score, and looked at a few toy examples to explain an observation's standard score for normally distributed data. In this lab, you'll practice by standardizing and visualize some normal distributions.

## Objectives

You will be able to:

* Calculate and interpret the z-score (standard score) for an observation from normally distributed data
* Visualize data before and after standardization to visually inspect the results

## Let's get started

> A $z$-score can help identify how many standard deviations above or below the mean a certain observation is. Every time you obtain a $z$-score, use “above” or “below” in your phrasing.

The yields of apple trees in an orchard have been recorded in the file `yield.csv`. Each observation is recorded by weighing apples from trees (in pounds) and adding their weights. There are 5000 observations in total for this data. 

## Load, visualize and give general comments about the dataset

Use pandas for loading and inspecting the data.


```python
# Import libraries

# Read the yield data as a dataframe

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>39.741234</td>
    </tr>
    <tr>
      <th>1</th>
      <td>39.872055</td>
    </tr>
    <tr>
      <th>2</th>
      <td>44.331164</td>
    </tr>
    <tr>
      <th>3</th>
      <td>46.600623</td>
    </tr>
    <tr>
      <th>4</th>
      <td>40.694984</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a plot
```


    
![png](index_files/index_2_0.png)
    



```python
# Your comments about the data here

```


```python
# __SOLUTION__ 
# Import libraries
import numpy as np
import seaborn as sns
import pandas as pd

# Read the yield data as a dataframe
df = pd.read_csv('yield.csv')
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>39.741234</td>
    </tr>
    <tr>
      <th>1</th>
      <td>39.872055</td>
    </tr>
    <tr>
      <th>2</th>
      <td>44.331164</td>
    </tr>
    <tr>
      <th>3</th>
      <td>46.600623</td>
    </tr>
    <tr>
      <th>4</th>
      <td>40.694984</td>
    </tr>
  </tbody>
</table>
</div>




```python
# __SOLUTION__ 
sns.displot(df);
```


    
![png](index_files/index_5_0.png)
    



```python
# __SOLUTION__ 
# Your comments about the data here

# The data is normally distributed as shown by the density curve
```

## Briefly explain what each value represents in this data set


```python
# Your answer here

```


```python
# __SOLUTION__ 
# Your answer here

# Each value represents the yield from a single tree in terms of total weight of apples
# that were obtained from this tree
```

## Define the interval bounds which contain 99% of the observations   

> **Hint**: Recall the empirical rule related to $3\sigma$.


```python
# Perform any calculations necessary here

```


```python
# Write your answer here 

```


```python
# __SOLUTION__ 
# Perform any calculations necessary here
mean = df.mean()
sd = df.std()
mean,sd
```




    (0    42.407624
     dtype: float64, 0    6.003697
     dtype: float64)




```python
# __SOLUTION__ 
# Write your answer here 

# the mean value is 42.4 and the standard deviation is around 6
# 68% of tree yields have weight between (42.4 - 6) 36.4 and (42.4 - 6) 48.4 pounds; 
# 95% between 30.4 and 54.4; 
# Almost all between 24.4 and 60.4 pounds
```

## Compute and interpret the z-score for a tree yielding 35 pounds of apples


```python
# Calculate z

```


```python
# Interpret the result

```


```python
# __SOLUTION__ 
# Calculate z
z = (35 - mean)/sd
z
```




    0   -1.233844
    dtype: float64




```python
# __SOLUTION__ 
# Interpret the result

# This tree’s yield is 1.23 standard deviations below the mean yield.
```

## Suppose a tree has a z-score of 1.85. Interpret this z-score. What is the yield of this tree?


```python
# Interpret the z score

```


```python
# Calculate yield

```


```python
# What is the yield ?

```


```python
# __SOLUTION__ 
# Interpret the z score

# This tree’s yield is 1.85 standard deviations above the mean
```


```python
# __SOLUTION__ 
X = mean + 1.85*sd
X
```




    0    53.514462
    dtype: float64




```python
# __SOLUTION__ 
# What is the yield ?

# Yield of this tree is 53.5 pounds. 
```

##  Convert each tree’s yield to a z-score so the new variable is the “z-score for weight”

The units are still the apple trees. For the data set of all z-scores:

* What is the shape? 
* The mean? 
* The standard deviation?


```python
# Give your solution here 

```

    Mean: 0.0
    SD: 1.0



    
![png](index_files/index_28_1.png)
    



```python
# Your observations

```


```python
# __SOLUTION__ 
z_data = [(x - df['0'].mean())/df['0'].std() for x in df['0']]
sns.displot(z_data)
mean = np.mean(np.array(z_data))
sd = np.std((np.array(z_data)))
print ('Mean:', round(mean,2))
print ('SD:', round(sd,2))
```

    Mean: 0.0
    SD: 1.0



    
![png](index_files/index_30_1.png)
    



```python
# __SOLUTION__ 
# Your observations

# It is a standard normal distribution
# Mean is 0 (it is a very small figure that rounds off to 0)
# SD is 1
# This is obvious because we standardised the whole distribution
```

## Summary

In this lab, you practiced your knowledge of the standard normal distribution!
