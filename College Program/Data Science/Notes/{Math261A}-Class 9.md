---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[Math261A_Lecture04.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Introduction
>	1. What is "Model Adequacy"? [[#Model Adequacy]]
>	2. **Know the theoretical assumptions on the residuals that should be satisfied in every regression model**
>	3. Know what happens if regression is carried out without the assumptions being satisfied
>2. [[#Scaling Residuals]]](What scaling residuals are usually used to do?)
>	1. [[#Standardized Residuals]]
>		- how standardized residuals defined? 
>		- how to use standardized residuals? 
>	3. [[#Studentized Residuals]]
>		- how studentized residuals defined?
>		- 
>	1. [[#PRESS Residuals]]
>		- how PRESS residuals defined
>		- what is $\hat{y}_{(i)}$, ${e}_{i}$ means?
>		- relationship between $e_{i}$ and $e(i)$
>3. Residual Plots
>	1. What is "qq-plot"
>	2. How to use qq-plot to [[#Check Normality]]

---
# In-Class Problems
## Model Adequacy
>[!tip] Assumptions on the regression models
>>- The relationship between each **regressor $x$** and the **response $y$** is approximately linear
>>- The **residuals $\epsilon$** are：
>>	- Uncorrelated
>>	- Normally distributed
>>	- Mean 0
>>	- constant variance $\sigma^2$

All T tests and F tests can only make sense when the RV is **normally distributed**
> ([[Math261A_Lecture04.pdf#page=1&selection=40,0,48,14&color=note|Math261A_Lecture04, p.1]])
> If the residuals are not normally distributed, for instance, then the test statistic for testing whether a slope is zero does not have a t-distribution.

> ([[Math261A_Lecture04.pdf#page=1&selection=72,17,73,12&color=note|Math261A_Lecture04, p.1]])
> Thus we need other numerical or graphical methods to check the assumptions.

## Residual Analysis
>[!question] Why all the residual actually don't have the same standard deviation?
### Scaling Residuals
> [!PDF|yellow] [[Math261A_Lecture04.pdf#page=2&selection=45,0,49,11&color=yellow|Math261A_Lecture04, p.2]]
>>[!tip] Scaling residuals can be helpful in identifying outlier observation
#### Standardized Residuals
![[Math261A_Lecture04.pdf#page=2&rect=68,461,505,565&color=yellow|Math261A_Lecture04, p.2]]
#### Studentized Residuals
![[Math261A_Lecture04.pdf#page=3&rect=66,557,499,656&color=yellow|Math261A_Lecture04, p.3]]
#### PRESS Residuals
> [!PDF|yellow] [[Math261A_Lecture04.pdf#page=2&selection=148,0,175,1&color=yellow|Math261A_Lecture04, p.2]]
> >[!faq] Fact: The “hat” matrix H is symmetric (H′ = H) and idempotent (HH = H)
##### The sum of PRESS
![[Math261A_Lecture04.pdf#page=5&rect=67,69,501,230|Math261A_Lecture04, p.5]]
> [!PDF|yellow] [[Math261A_Lecture04.pdf#page=6&selection=76,0,89,61&color=yellow|Math261A_Lecture04, p.6]]
> Since the value of R 2 prediction for the one-predictor model is quite a bit smaller than for the two-predictor model, this is an indication that the variable Distance should be included in the model to reliably model the delivery time.
## Residual Plots
### Check Normality
>[!tip]
>A good way to check whether data has any specific distribution is with so-called probability plots (pp-plots) or with quantile plots (qq-plots)
![[Math261A_Lecture04.pdf#page=4&rect=69,279,506,483&color=yellow|Math261A_Lecture04, p.4]]

> [!PDF|note] [[Math261A_Lecture04.pdf#page=4&selection=159,0,176,48&color=note|Math261A_Lecture04, p.4]]
>>[!tip] How to judge normality
>>If your data comes from the hypothesized distribution, then the points in the qq-plot should lie on (or close to) the line **y = x**. If the points do not lie on the **y = x** line, then the distribution of the data in not Normal.



`plot(fitted(fit.full),rstudent(fit),xlab="",ylab="",main="")`

`plot(fit.full)` will get 4 plots

`qqplot(residuals(fit.full))`





---

# Flash Cards
