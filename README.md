# 2016 Elections

*For my third project, I decided to use a dataset from Kaggle. This dataset is entitled "us elections". The dataset
is made of eight columns, and 24612 rows. The dataset is comprised of the number of votes garnered by 16 candidates, both
democrats and republicans, in the 2016 primaries. The data provided covers all the 50 states.*

*With this dataset as you will observe, I tried to visualize different aspects of the primary elections,
that I personally found to be interesting. Nonetheless, a lot more can be done with this dataset for someone
with more expertise in the python programming language.*

## The Code

*In this section I will showcase the code that used to visualize my data, in as musch detail as possible. Futhermore,
I will demonstrate my inputs and outputs.*

```
# As previously done in other projects, we always start by importing pandas,numpy, and matplotlib
# It is with them that we are able to do visualizations
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
```
```
# Before we read in our csv, we first have to download it from kaggle
# We then save it as a csv file, and upload it to our jupyter notebook
#The function pd.read_csv reads in the csv file, which was saved on the computer as "primary_results.csv"
#We save the csv file in the variable results
results=pd.read_csv("primary_results.csv")
results.head()
```
```
# We ran the dtypes function quickly to better understand our data
# We observe that with have both integers and ojects
results.dtypes
```
```
#Next we create a variable vot_results
#In this variable we create a smaller table made up of the columns 'party' and 'votes'
vot_results = results[['party','votes']]
vot_results.head
```
```
#This step is not necessary
#It was just done to understand more and play around with the data
vot_results.describe()
```
```
#Next we use our table/variable to group our data by party and sum up all the votes
#This is because we want to see how many votes democratic and republican candidates garnered respectively
#For this we use functions: groupby and sum
#Lastly we save everything in the variable parties
parties=vot_results.groupby(by='party').sum()
parties.reset_index()
```
```
#Now we call in the function plot to visualize our averages
#We set kind to "pie" , because we want a pie graph
parties.plot(kind='pie',y='votes')
```
```
#Now because we want to see how many votes each candidate gathered, we group candidate
# And sum up the votes
# we save it all in the dataframe candidate_votes
# We use reset_index, so that candidate is not an index but a column
candidate_votes=results.groupby(by='candidate')['votes'].sum()
candidate_votes=pd.DataFrame(candidate_votes)
candidate_votes.reset_index()
```
```
##We set kind to "bar" , because we want a bar graph
candidate_votes.plot(kind='bar')
```
```
candidate_votes1=pd.DataFrame(candidate_votes1)
candidate_votes1.reset_index()
```
```




