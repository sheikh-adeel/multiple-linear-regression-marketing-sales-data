# **Finding the variables (marketing channels) that predict sales using multiple linear regression**

## **Overview**
In this project, we will be analyzing historical marketing promotion data.
Each row corresponds to an independent marketing promotion where TV, social media, radio, and influencer promotions are used to increase sales. We want to find the variables that predict sales, that can help target the marketing efforts.

We will conduct a multiple linear regression analysis to estimate sales from a combination of independent variables.

## **Data Dictionary**
This project uses a dataset called `marketing_data.csv` from [Kaggle](https://www.kaggle.com/datasets/harrimansaragih/dummy-advertising-and-sales-data/data). It represents the amount of money spent on TV, radio, and social media promotions, as well as the corresponding sales.

*Note: The data has been modified for this project.*

The dataset contains:

**572 rows** – each row represents a different promotion budget

**5 columns**

| Column name | Type | Description | 
|-------------|------|-------------|
| TV | str | Television promotion budget (Low, Medium, or High) | 
| Radio | float64 | Radio promotion budget (in millions) | 
| Social Media | float64 | Social media budget (in millions) |
| Influencer | str | What type of influencer the promotion collaborated with (Mega, Macro, Nano, or Micro) |
| Sales | float64 | Total of sales (in millions) |

## **Steps**
### **1. Imports**
- Import libraries and packages
- Load the dataset into a dataFrame

### **2. Data exploration, data cleaning, and model preparation**
- Explore the data
- Check for null values in the data
- Check the data types
- Change column names
- Review the distribution of the variables
- Create pairplot to visualize linear relationship between variables
- Check mean sales of categorical variables

### **3. Model building**
- Fit the model to the data
- Check model assumptions
  - Linearity
  - Independence
  - Normality
  - Constant variance
  - No multicollinearity

### **4. Results and evaluation**
- Analyze the OLS regression results
- Interpret model coefficients

## **Findings**
- There are total of 572 rows and 5 columns in this dataset, with each row representing a unique marketing promotion.
- Radio appears to have linear relationship with Sales.
- Social Media was not selected because it did not increase model performance and it is also correlated with another independent variable: Radio.
- The categories for Influencer have different average Sales, but the variation is not substantial.
- TV was selected, as the there is a strong relationship between the TV promotional budget and the average Sales.
- Model assumptions:
  - Linearity: The linearity assumption holds for Radio, as there is a clear linear relationship in the scatterplot between Radio and Sales. 
  - Independence: Each marketing promotion (i.e., row) is independent from one another, hence the independence assumption is not violated.
  - Normality: The histogram of the residuals are approximately normally distributed, supporting normality assumption is met. The residuals in the Q-Q plot form a straight line, further supporting that this assumption is met.
  - Constant variance: The variance of the fitted values is similarly distributed, validating that the assumption is met.
  - No multicollinearity: The model only has one continous independent variable, Radio, meaning there are no multicollinearity issues. The variance inflation factor when both Radio and Social_Media are included in the model is 4.93 for each variable, indicating high multicollinearity.
- Model coefficients:
  - $B_0$ = 217.6367
  - $B_{TV Low}$ = -152.0897
  - $B_{TV Medium}$ = -73.4835
  - $B_{Radio}$ = 2.8864
- The p-value for all coefficients is 0.000, meaning all coefficients are statistically significant at p = 5%.
- According to the model, high TV promotional budgets result in significantly more sales than medium and low TV promotional budgets.
- The coefficient for Radio is positive, confirming the positive linear relationship shown earlier during the exploratory data analysis.
- The model explains 90.4% ($R^2$ = 0.904) of the variation in Sales. This makes the model an excellent predictor of Sales.

## **Recommendations**
- High TV promotional budgets have a substantial positive influence on sales.
- The model estimates that switching from a high to medium TV promotional budget reduces sales by $73.4835 million (95% CI [-80.530, -66.437]), and switching from a high to low TV promotional budget reduces sales by $152.0897 million (95% CI [-162.225, -141.954]).
- The model also estimates that an increase of $1 million in the radio promotional budget will yield a $2.8864 million increase in sales (95% CI [2.460, 3.312]).
- Thus, it is recommended that to allot a high promotional budget to TV when possible and invest in radio promotions to increase sales.

## **Next steps**
- Providing the stakeholders with the estimated sales given different TV promotions and radio budgets.
- Additional plots to help convey the results, such as using the seaborn `regplot()` to plot the data with a best fit regression line.

## **Possible questions**
- What was the location of the marketing campaign?
- What time of the year was the marketing campaign?
- What was the purpose of the marketing campaign? Was it to gain new customers or retain the existing customers?
- What was the duration of the campaign?
