# Data Science in Production

# Introduction

This is a project that shows my progress in Data Science training in production. 

Data Science in Prodution is a course taught by data scientist **Meigarom Lopes**. It teaches how to build a data science project using an easy-to-understand methodology. And in the end, he teaches how to deploy the model in production.

The challange of this project is to make a sales prevision of **Rossmann's Store**. Therefore, it's used the datasets from *Kaggle*.

This project is divided into 10 modules where the necessary steps to make a complete data science project are presented. They are:

- Understanding the Bussiness Problem

- Data Description

- Featuring Engineering

- Exploratory Data Analysis (EDA)

- Data Preparation

- Feature Selection

- Machine Learning Modeling

- Hyperparameter Fine Tuning

- Error Translation and Interpretation 

- Deploy Model to Production

# Module 01 - Understanding the business problem

In this module, I learn how important it is to understand the business problem before starting a data science project.

In the case of Rossmann's Stores the business problem was to make **a sales prevision of all the stores in the next six weeks**.

So, there are four importants points to consider:

- Understand the motivation of the problem - What is the motivation for making this a sales prevision ?

- Understand the root cause of the problem - Why do it ?

- Identify the project sponsor - Who's the stalkerholder ?

- Understand the solution format - Granulality, for example.

Using these points above, it was answered

- The CFO requested this solution during a monthly results meeting.

- The CFO wants to know the bugdet of each store to make reforms.

- The project sponsor is the CFO.

- The format solution is to make the predict of daily sales of each store in the next six weeks using predict methods.

# Module 02 - Data Description

In this module, I start getting familiar with the dataset to understand how complex is the problem that I have to solve.

With this, I analyse some features of the data set as:

- Dataset size

 Do I have the correct resources to work with ? Does the infrastrutucture support the amount of data ?
  
- Variable types

What variables types does the dataset have?
  
- Missing Data

How much missing data from the dataset ? Why are there missing data ?

- Summary Statistics


# Module 03 - Feature Engineering 

In this module, we learn how to create a mindmap. It helps in creating the list of hypotheses to validating the data in the phase Exploratory Data Analyses.

There are three importants points to consider:

- Phenomenal: What the phenomenal are we modeling ? In the case, we are modeling the daily store sales.

- Agents: who are the agents acting on the phenomenon of interest ? Customers, stores, assortments.

- Attributes of Agents: What's the description of the agents ? 

![alt text](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/daily_store.png)

Based on the hypothesis map, we create our hypothesis about the various stores, products and time.

## Creating Hypothesis

*Hypotheses about Stores*

1. Store with more employees should sell more.

2. Store with greater inventory capacity should sell more.

3. Larger stores should sell more.

4. Store with larger assortments should sell more.

5. Store with closer competitors should sell less.

6. Stores with longer competitors can sell more.

*Hyphoteses about Products*

1. Stores that invest more in marketing should sell more.

2. Store with greater product exposure should sell more.

3. Store with low-priced products are expected to sell more.

4. Store with more aggressive promotions (bigger discounts) should sell more.

5. Stores with active promotions for longer should sell more.

6. Stores with more promotion days can sell more.

7. Stores with more consecutive promotions should sell more.

*Hyphoteses about Time*

1. Stores that open on Christmas should sell more.

2. Stores should sell more over the years.

3. Stores should sell more in the second half of the year.

4. Stores should sell more after the 10th of each month.

5. Stores should sell less on weekends.

6. Stores should sell less during school holidays.

And we created a final list of hypotheses by choosing the most important hypotheses.

## Hypothesis Final List

1. Store with larger assortments should sell more.

2. Store with closer competitors should sell less.

3. Stores with longer competitors can sell more.

4. Stores with active promotions for longer should sell more.

5. Stores with more promotion days can sell more.

6. Stores with more consecutive promotions should sell more.

7. Stores that open on Christmas should sell more.

8. Stores should sell more over the years.

9. Stores should sell more in the second half of the year.

10. Stores should sell more after the 10th of each month.

11. Stores should sell less on weekends.

12. Stores should sell less during school holidays.

With the proposed mindmap of hypotheses, we create some variables in the data set to facilitate the exploration of the data set in the EDA phase as can be seen in the notebook.

Also, we make the variable filtering because is necessary for business restrics.

- **Variable Filtering** : it is constrained to the Business. There are variables which values you will only be able to have when a business rule is triggered in the system. So, your model will not always be able to use them at hand to make predictions.

- **Variable Selection**:picking the most relevant variables for the model. Considers the correlations between variables. It does not take into account business rules.

# Module 04 - Exploratory Data Analysis

In this module, we get to learn a lot of awesome stuff about EDA. In summary, the importance of exploratory data analysis is to understand how the variables impact the phenomenon. And from there, measure the strength of that impact.

Therefore, the three objectives of the EDA are:

- Gain business experience.

- Validate business hypotheses.

- Understand which variables are important to the business.

There are three types of Exploratory Data Analysis:

- **Univariate Analysis**

-- How is this variable ?

Get summary statistics (min, max, distribution, range, etc)

- **Bivariate Analysis**

How the explanatory variable impacts the target variable?

Get correlation between them.

Validate / Invalidate hypotheses.

- **Multivariate Analysis**

How is the relation between the explanatory variables ?

Get correlation between them


## 4.1. Univariate Analysis

### 4.1.1. Target Variable (Sales)

![01](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/01.png)

How we can analyse, the sales distribution is an asymmetric curve, that is,it's a curve that not follow a normal distribution.

The Machine Learning algorithms require that data follow a normal distribution because their constructions are based on a continuous probability distribution. When the data not follow a normal distribution, we can apply techniques. 

### 4.1.2. Numerical Variables

![03](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/03.png)

Analyzing the histograms, we have:

**Competition Distance:** We can see that competitiors meet in a range of 0 to 50000.

**Competition Open Since Month:** We can see that there is an increase in competition in the first months. Then in the months of May to August there is a drop / stability. And finally, in the months of September to December there is an increase and a decrease. This generates seasonality.

**Competition Open Since Year**: we can see that the competitions of open stores had an increasing increase since the 2000s. But in 2015 the number of competitions was very high.

**Customers**: We can see that the number of customers per day for the first 1000 days is higher. But then, the number of customers drops considerably.

**Day of Week**: We can see that the histogram have a uniform distribution, is that, the stores open every day of the week. 

**Is Promo**: We can see that many stores are not in promotion (promo=0) than in promotion (promo=1).

**Open**: We can see that there many stores open (open=1) than closed (open=0). This result may be influenced by stores that open on holidays.

**Promo**: we can see that there are many more stores that weren't in regular promotion (promo=0) than those who were (promo=1).

**Promo2**: we can see that there is a tie between stores that participated in promo2 and stores that did not participate in promo2.

**Promo2 Since Week**: we can observe that the graph does not present an immediate conclusion. We have that analise more.

**Promo2 Since Year**: We can observe that many stores participed of the promotion in the years 2013 and 2014.

**Sales**: we can see that there were many more sales ranging from 0 to nearly 10,000.

**School Holiday**: we can see that there many more stores that were not affected by the closure of publics schools.

**Stores**: The stores variable describe a unique Id for each store. Therefore, in this graph there is nothing to extract. 

### 4.1.3. Categorical Variable

![04](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/04.png)

Analyzing the plots, we can see that:


## 4.2. Bivariate Analysys

We make the bivariate analysis of the hyphoteses final list. Therefore, follow that

### **H1. Stores with higher assortment should have higher sales.**

*FALSE Store larger assortment sells less*.

![05](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/05.png)

Assuming that largest assortments are of the extra type and analyzing the barplot, we find that sales of extra assortments are small compared to the basic and extended types. Therefore, we can conclude that **stores with larger assortments sell less**.

However, we can ask ourselves if there has been any change in sales behavior over time. For this, we will check the **sales** for each assortment during the **weeks of the years**.

![06](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/06.png)

Looking at the graph above, we can conclude that the sales of the basic and extended assortment types are practically the same over time. But, we need verify the line that describe teh sales behavior of the extra type assortment. Therefore,

![07](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/07.png)

Looking at the line graphs, we can see if the stores with the largest (extra) assortment have the least sales.

Therefore, the hyphotesis is **FALSE**

### **H2. Store with closer competitors should sell less**

*FALSE Store with closer competitors sell more*

![08](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/08.png)

Observing the results, stores with closer competitors sell more. Therefore, the hyphotese is **FALSE**.

We can also plot a scatter plot to verify this result. 

![09](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/09.png)

On the scatter plot, the concentration of the points of sale occurs in stores with closer competitors. This also confirms the hypothesis is **FALSE**.

![10](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/10.png)

Reggarding Pearson's correlation, we can see that the result of **-0,23** is a **weak negative correlation**. This explains that the further away the competitions are, the lower the store sales will be.

### **H3. Stores with longer competitions can sell more**

*FALSE Stores with longer competitions sell less*

![11](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/11.png)

Analyzing the barplot, we can see that the more negative values approach 0, the sales are higher. What does that mean ?
Means that stores with recent competitions sell more. On the other hand, stores with longer competitions sell less.
Therefore, the hypothesis is **FALSE**.

Let's plots the Pearson's correlation according to the code.

![12](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/12.png)

The Pearson's correlation is weak negative because your result is **-0,10**. But, this result is important because it influences the variable response which is sales. On the other hand, is necessary to use another type of correlation to measure the dispersion of the points and error. 

### **H4. Stores with active promotions for longer should sell more**

*FALSE Stores with active promotions for longer sell less*

### Reading of the table above

1) promo_time_week > 0: sales made inside the **extended** promotion time.

2) promo_time_week < 0: sales made inside the **regular** promotion time.

![13](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/13.png)

As we can see in the total sales x weeks in extended promotion, there is a period when the extended promotion results in more sales. After a period of time, total sales begin to decline.

From the total sales x weeks in regular promotion, we can see that, as compensation gets closer to zero, sales start to increase.

Therefore, stores with a longer promotion period do not have higher sales. The hypothesis is **FALSE**.

In relation the correlation heat map, we obtained a coeficient of **-0,029** which is very close to zero. Therefore, we have a super weak correlation. This is result makes sense because it has sales that are often constant over time.

So, maybe we won't include promo_time_week in the model. Of course, this variable might work if we combine it with another variable, but we'll leave it for the time being.

### <s>**H5. Stores with more promotion days can sell more**</s>

As this hypothesis similar to H4. We will leave to validate it in the next CRISP cycle.

###  **H6. Stores with more consecutive promotions should sell more**

*FALSE Stores with more consecutive promotions sell less*

![14](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/14.png)

Looking at the results it seems that stores with more consecutive promotions sell less. Therefore, the hypothesis is **FALSE**.

Regarding the relevance of the promo2 variable to the ML model, we can say that its relevance is low.

### **H7. Stores that open on Christmas should sell more**

*FALSE Stores that open on Christmas sell less*

![15](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/15.png)

![16](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/16.png)

As noted in the previous results, stores that open on Cristmas sell less. Therefore, the hypothesis is **FALSE**.

One observation we need to make here is that, in 2015, we still don't have Christmas sales data, because the data ends on July 31, 2015.

Maybe we can consider this relevant variables for the Machine Learning model beause we have changes in sales depending on the type of holiday state and in what year.

### **H8. Stores should sell more over the years**

*FALSE Stores sell less over the years.*

![17](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/17.png)

As noted in the previous results, stores sell less over the years. In addition, looking at the Pearson correlation coefficient of -0.92, we can see that there is a strong negative correlation between year and sales. So, the hypothesis is FALSE.

### H9. Stores should sell more in the second half of the year

*FALSE Stores sell less in the second half of the year.*

![18](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/18.png)

As noted in the previous results, stores sell less in the second half of the year. In addition, by looking at Pearson's correlation coefficient of -0.75, we can see if there is a strong negative correlation between month and sales, which means that the sales fall over time.

### H10. Stores should sell more after the 10th of each month

*TRUE Stores sell more after the 10th of each month*

![19](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/19.png)

As observed in the previous results, stores sell more after the 10th day of the month. Therefore, the hypothesis is **TRUE**.

In addition, checking the Pearson's correlation coefficient, we got a value of -0.35 which tells us that is a no so strong correlation between day and sales. However, as we have different values for total sales before and after the 10th day of the month, this variable can be relevant for our ML Model.

### H11. Stores should sell less on weekends

*TRUE Stores sell less on weekends.*

![20](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/20.png)

As noted in previous results, stores sell less on weekends. In addition, looking at Pearson's correlation coefficient of -0.76, we can see that there is a strong negative correlation between day of the week and sales.

There, the hypothesis is **TRUE**

### H12. Stores should sell less during school holidays

*TRUE Stores sell less during school holidays*

![21](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/21.png)

As noted in the previous results, stores sell less during school holidays, except in July (7) and August (8). Therefore, this hypothesis is **TRUE**.


## 4.3. Multivariate Analysis

In this section we'll check the correlations between the explanatory variables, separating the analysis for numerical attributes and categorical attributes.

### 4.3.1. Numerical Attributes

![22](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/22.png)

### 4.3.2. Categorical Attributes

To make the correlation between two categorical variables, we'll use the Cramér V method.

Please, refer to the notebook to check the calculations.

![23](https://github.com/nickolasdias/DataScienceEmProducao/blob/master/image/23.png)

According to the heat map, we can conclude that the larger correlation occurs between *assortment* and *store type*. The result of 0.54 is a medium correlation. This means that the bigger the store, the higher is assortment of its products. With respect to the correlations of the other variables close to zero, we can conclude that they are weak and independent.

# Module 05 - Data Preparation

