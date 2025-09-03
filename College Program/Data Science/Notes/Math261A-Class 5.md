---
create date: 2024-09-05
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
- [[Math261A_Lecture02.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. What is ANOVA
>2. What is "the degree of freedom"
>3. What is $R^2$

---
# In-Class Problems
## The degree of freedom
![[Math261A_Lecture02.pdf#page=9&rect=68,75,500,333&color=note|Math261A_Lecture02, p.9]]
### ANOVA Table Output of R
![[Excalidraw/R output for SLR model.excalidraw.md#^area=hBvnTb-lU6b2So6M281C4|ANOVA_R]]
- $SS_{R}$ = 1527483
- $SS_{RES}$ =166255
- $MS_{R}$ =1527483= $\frac{SS_{R}}{df=1}$
- $MS_{RES}$ =9236= $\frac{SS_{RES}}{df=18}$
## The CI for the $\sigma^2$ 
[[Math261A_Lecture02.pdf#page=10&selection=45,60,51,1&color=yellow|Math261A_Lecture02, p.10]]
![[Math261A_Lecture02.pdf#page=10&rect=66,213,501,364&color=red|Math261A_Lecture02, p.10]]

> [!PDF|red] [[Math261A_Lecture02.pdf#page=10&selection=165,0,171,19&color=red|Math261A_Lecture02, p.10]]
> >[!faq] Find a 95% confidence interval for the residual variance σ2 in the Rocket Propellant Example.

## The CI for the mean response
![[Math261A_Lecture02.pdf#page=11&rect=68,443,410,526&color=red|Math261A_Lecture02, p.11]]
> [!PDF|red] Example [[Math261A_Lecture02.pdf#page=11&selection=239,0,240,45&color=red|Math261A_Lecture02, p.11]]
> >[!faq] For the Rocket Propellant data, we can create a 95% confidence interval for the mean response with the following code


## The PI(Prediction Interval) 

## $R^2$
> [!PDF|note] $R^2$ [[Math261A_Lecture02.pdf#page=13&selection=4,0,4,26&color=note|Math261A_Lecture02, p.13]]
> >[!faq] Coefficient of Determination
>> $R^2=\frac{SS_{R}}{SS_{T}}= 1-\frac{SS_{Res}}{SS_{T}}$ 
> 

---

# Flash Cards
#flashcards/Math 
"ANOVA" is: ---> **Analysis of Variance**
<!--SR:!2024-10-05,3,250-->