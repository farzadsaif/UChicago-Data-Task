# UChicago-Data-Task
A data analysis task I did for the University of Chicago in 2020.

Below are the instructions they gave me.

## 1 Overview
The data consists of partially cleaned temperature and rainfall readings from the Indian Meteorological Department. The datasets in the “Rainfall” and “Temperature” subdirectories consist of daily rainfall and temperature grid point data from 2009-2013. Rainfall is recorded in millimeters and temperature is recorded in degrees Celsius. Each grid point comes from a 1°(latitude) x 1°(longitude) grid covering the Indian subcontinent.
When you are done with Sections 2-4 below, please send in the following items:
• Well-commented code files in the language of your choice (.do files for Stata, .R or .Rmd for R, .py or Jupyter Notebook for Python, etc.)
• Final dataset produced from Section 2
• Final graphs and table produced from Section 3
• A short document answering the questions raised in Sections 2-4
If you find any of these instructions to be confusing, please proceed in a way that you find relevant and reasonable, and list your assumptions in your writeup.

## 2 Data Cleaning
The central task of this section is to collapse the grid-level dataset into a district-level dataset. The algorithm to match each grid point to a district is as follows: take a weighted average of daily mean temperature, daily mean rainfall, and daily total rainfall for all grid points within 100 KM of each district’s geographic center. The weights are the inverse of the squared distance from the district center.
“district crosswalk small.dta” in the “Geo” subdirectory consists of district centroids for five Indian states: Gujarat, Kerala, Pondicherry, Punjab, and Rajasthan. For the purposes of this task, only use these districts when matching with the grid points. Note: the state and district names in this file correspond with 1961 definitions. They will not always match modern names.
To determine which grid points lie within 100 KM of each district center, you will have to calculate the distance between every grid point and every centroid. The *geodist* or *vincenty* commands may be useful.
The final product from this section is a district-level daily dataset from 2009-2013 with temperature, rainfall, and total rainfall variables.
The actual EPIC project used 339 districts in India, 112 years of data and a 0.25°(latitude) x 0.25°(longitude) grid for rainfall. How would your code scale up with this larger dataset? Would you need any additional computing resources? Be as specific as possible.

## 3 Data Exploration
This section uses the district-level daily dataset created in Section 2. We are interested in documenting the monsoon season in various districts.
### 1. For the Jaipur district in Rajasthan, create a time series dataset of daily rainfall, averaged over the five years.
### 2. Using this time series, create a scatterplot of rainfall by day. On what day does the monsoon season start in Jaipur? When does it end? Indicate your answer on the graph.
### 3. Format your graphs so that they are publication-quality and save them as .pdf files.
### 4. Create a publication-quality table of annual average temperature by state and year.

## 4 Estimation and Causal Inference
We are interested in using this dataset to estimate the impact of temperature on yearly district-level mortality in India.
### 1. Write out a simple econometric model regressing mortality on temperature.
### 2. Suppose you estimate the model using OLS and obtain a coefficient of 0.05 with a standard error of 0.02. Interpret this result.
### 3. The effect of temperature on mortality is very likely nonlinear. How would you modify your model above to estimate any potential nonlinearities?
### 4. Is your parameter of interest identified? How could you use a) fixed effects and b) other control variables to remove potentially confounding factors?
### 5. Write out a full econometric model addressing the concerns raised in 3 and 4. How should the standard errors from this specification be estimated?
