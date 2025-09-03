---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - "#flashcards"
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[Math261A_Lecture03.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Testing for Significance of Regression
>2. Assessing Model Adequacy
>	1. $R^2$ and adjusted $R^2$
>3. Testing Individual Regression Coefficients
>4. Test For a Group of Predictiors

---
# In-Class Problems
## Testing for Significance of Regression
#flashcards/Math 
The test for significance of regression in *multiple linear regression model* is to test {{**whether any of the k predictor variables have any relationship with the response**}} .

> ([[Math261A_Lecture03.pdf#page=11&selection=24,0,65,1&color=note|Math261A_Lecture03, p.11]])
> This very pessimistic test asks whether any of the k predictor variables in the model have any relationship with the response. H 0 : β1 = · · · = βk = 0 vs. Ha : βj 6 = 0 for at least one j
### The F distribution and f-Table
![[Math261A_Lecture03.pdf#page=11&rect=70,232,405,287&color=red|Math261A_Lecture03, p.11]]
> [!PDF|red] Example [[Math261A_Lecture03.pdf#page=11&selection=231,0,236,34&color=red|Math261A_Lecture03, p.11]]
> >[!faq] Read off and interpret the result of the F -test for significance of regression in the Delivery Time Example.
> > [[《Probability and Statistics for Engineering》.pdf#page=723&selection=0,4,10,13&color=note|《Probability and Statistics for Engineering》, p.A-14]]
> 
> 
## Assessing Model Adequacy
[[Math261A_Lecture03.pdf#page=12&selection=6,0,54,1&color=note|Math261A_Lecture03, p.12]]
### $R^2$ and Adjusted $R^2$
![[Math261A_Lecture03.pdf#page=12&rect=192,482,371,528&color=red|Math261A_Lecture03, p.12]]
> [!PDF|red] Example [[Math261A_Lecture03.pdf#page=12&selection=130,1,142,46&color=red|Math261A_Lecture03, p.12]]
> >[!faq] For the Delivery Time data, find R 2 and the adjusted R 2 for the model with both predictor variables in the R-output.
> 
> 
## Testing Individual Regression Coefficients
The test for Individual Regression Coefficients in *multiple linear regression model* is to test {{**whether the slop associated with the j-th predictor is significantly different from zero where k predictors are included}} .
![[Math261A_Lecture03.pdf#page=12&rect=63,120,506,282&color=red|Math261A_Lecture03, p.12]]

>[!tip] If this test’s null hypothesis is rejected, we can conclude that the jth predictor has a significant influence on the response, given the other regressors in the model at the same time.


> [!PDF|red] [[Math261A_Lecture03.pdf#page=13&selection=13,0,25,11&color=red|Math261A_Lecture03, p.13]]
> >[!faq] Read off test statistic values and p-values for the two regressors Cases and Distance in the Delivery Time data example. Formulate conclusions for both predictors.
> 
> 
## Test For a Group of Predictiors
[[Math261A_Lecture03.pdf#page=13&selection=40,0,69,58&color=note|Math261A_Lecture03, p.13]]
> [!PDF|red] Example [[Math261A_Lecture03.pdf#page=14&selection=18,1,29,13&color=red|Math261A_Lecture03, p.14]]
> >[!faq] For the Delivery Time data, test whether there is a significant contribution from including the Distance variable, if the Cases variable is already included in the model.
> 
> 
---

# Flash Cards
