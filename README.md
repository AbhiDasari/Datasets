# Datasets
Sample Datasets for Machine Learning and deeplearning
https://www.tutorialspoint.com/python_pandas/python_pandas_groupby.htm
# -*- coding: utf-8 -*-
"""
Created on Wed Aug 28 22:29:39 2019

@author: Abhi
"""

import pandas as pd
import numpy as np
data=pd.read_csv("indianwin.csv")
print(data.columns)
#print(data[['state','turnout']])
import matplotlib.pyplot as plt
#plt.plot(data['county'],data['turnout'])
#plt.show()
print(data.info())
print(data.head(100))
states=data.groupby('State')['Constituency','Votes']
print(states)
plt.scatter(data['State'],data['Votes'])
plt.xticks(data['State'],rotation=90)
plt.show()
