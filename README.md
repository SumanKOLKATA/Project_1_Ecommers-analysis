# Project_1_Ecommers-analysis
Analysis and visualization of different insights  
## Import dat from github respiratory 
## E-commers project for analysis and finding insights 


import pandas as pd

url = 'https://raw.githubusercontent.com/DataThinkers/Datasets/main/DS/Ecommerce%20Purchases'
def read_data_git():
    ex1 = pd.read_csv(url)
    return ex1

ecommerce=read_data_git()
ecommerce.head(1)

## Copy the main data 
data=ecommerce.copy()

data.head(2)

## Findings of null value 
data.isnull().sum()

## Check datatype of each columns 
data.dtypes

## Number of rows and columns
data.shape

 ## highest and lowest purchase price 

data.columns

## Highest purchase price 

print('Highest purchase price',data['Purchase Price'].max())

print('Lowest purchase price',data['Purchase Price'].min())

## Average purchase price 
print('Average purchase price -',data['Purchase Price'].mean())

## How many people have French language 
len(data[data['Language']=='fr'])

## job title contain 'Enginers'

len(data[data['Job'].str.contains('engineer',case=False)])

## Find Email of the person with the fllowing IP adress: 132.207.160.22

data.columns


data[data['IP Address']== '132.207.160.22'][['Email','Company']]

## How many people have master card and purchase above 50
len(data[(data['CC Provider'] == 'Mastercard') & (data['Purchase Price']>=50)])


## Find Email of person with the following card number:4664825258997302

data[data['Credit Card']== 4664825258997302]['Email']

## How many people purchase in AM and PM

## AM 
len(data[data['AM or PM']=='AM'])

## PM

len(data[data['AM or PM']=='PM'])


data['AM or PM'].value_counts()

## How many people have credit card expire on 2020
data2=ecommerce.copy()

def fun():
    count=0
    for date in data2['CC Exp Date']:
        if date.split('/')[1]=='20':
            count=count+1
    print(count)

fun()

## another processure

data2['Ex_Year'] = data2['CC Exp Date'].str[3:5]

data2.head(2)

## How many people have credit card expire on 2020

len(data2[data2['Ex_Year'] == '20'])

## another processure using Lamda function

len(data2[data2['CC Exp Date'].apply(lambda x:x[3:]=='20')])

## Top 5 Email provider 
data2['Email_last'] = data2['Email'].apply(lambda x:x.split('@')[1])
data2.head(2)

Top_5 = data2['Email_last'].value_counts()
Top_5.head(5)

