---
create date: 2024-09-03
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
>1. The definition of simple linear regression model with its 3 important parameters
>	1. Assumptions
>	2. [[#Mean and Variance of Y]]
>2. The least-squares estimation of the parameters
>	1. What is  $SS_{Res}$

---
# In-Class Problems
## Simple Linear Regression Model

>[!important] Definition
>A **single response variable Y** is related to a **single predictor variable X** via the linear equation:
>> $Y=\beta_0+\beta_1X+\epsilon$
>>>[!warning] Important Assumptions 
>>> ![[Pasted image 20240904182329.png]]
>>> >1. **$\beta_{0}$** and **$\beta_{1}$** are assumed to be **Unknown constant**
>>>>2. **residual $\epsilon$** are assumed to be **independent, normally distributed RV** with mean 0 and unknown (but constant) variance $\sigma^2$
>>>>3. The variable x is usually assumed to be controllable (measured without error)
>>>>4. The response y is a random variable whose distribution depends on x

#flashcards/Math
In simple linear regression model $Y=\beta_0+\beta_1X+\epsilon$, What is the properties of  $\beta_{0}$  $\beta_{1}$ and residual $\epsilon$ ？
???
1. **$\beta_{0}$** and **$\beta_{1}$** are assumed to be **Unknown constant**
2. **residual $\epsilon$** are assumed to be **independent, normally distributed RV** with mean 0 and unknown (but constant) variance $\sigma^2$
<!--SR:!2024-10-10,8,250-->

### Mean and Variance of Y
-  $E(Y|X)=\beta_0+\beta_1X$ (Because $\epsilon$ has mean 0)
- $Var(Y|X)=Var(\beta_0+\beta_1X+\epsilon)=Var(\epsilon)=\sigma^2$
![[Pasted image 20240904183025.png]]
>[!question] What is Regression modeling?
>>A: Regression modeling is about using the estimates obtained from the data to make statistical statements about the true model parameters
## Least-Squares Estimation of Parameters
In simple linear regression model, SSres = ---> **the sum of squared residuals**: $\sum\limits_{i=1}^{n} \epsilon_{i}^2=\sum\limits_{i=1}^{n}(y_{i-\beta_{0}-\beta_{1}x_{1}})^2$
<!--SR:!2024-10-04,2,230-->
>[!important] Definition
>>Find parameter $\hat{\beta_0}$, $\hat{\beta_1}$ which make the line fit to minimize the sum of squared residuals.
### The derivation process of SSres (sum of squared residual)
> [!PDF|red] $SS_{RES}$ [[Math261A_Lecture02.pdf#page=2&selection=87,0,104,0&color=red|Math261A_Lecture02, p.2]]
> >[!faq] Minimize the quantity $S(\hat{\beta_0}$, $\hat{\beta_1})$ with respect to $\beta_0$ and $\beta_1$
> 

### $S_{x x}$ 和 $S_xy$
$$
\begin{equation}
S_{xx}=\sum \limits_{ i=1 }^n x_{i}^2 - \frac{(\sum \limits_{ i=1 }^n x_{i})^2}{n}
\end{equation}
$$
$$
\begin{equation}
S_{xy}=\sum \limits_{ i=1 }^n y_{i} x_{i} - \frac{(\sum \limits_{ i=1 }^n y_{i})(\sum \limits_{ i=1 }^n x_{i})}{n} = \sum \limits_{ i=1 }^n y_{i}(x_{i}-\bar{x})
\end{equation}
$$

$$
\hat{\beta_{1}}=\frac{s_{xy}}{s_{x x}} \text{ and } \hat{\beta_{0}}=\bar{y}-\hat{\beta_{1}}\bar{x}
$$
![[Pasted image 20240910181817.png]]

### Example “The Rocket Propellant Data”
#### Read the Output from R
![[R output for SLR model.excalidraw#^area=OlSWLPgWjNI-JnH3YtOh9|R-output]]
- The blue circle is the value of $\hat{\beta_{0}}=2627.822$ and $\hat{\beta_{1}}=-37.154$
- The green circle is the value of result of t-test for $\hat{\beta_{0}}$ and $\hat{\beta_{1}}$
- The Residual standard error is $\hat{\sigma} = \sqrt{ MS_{RES} }=96.11$

> [!PDF|yellow] [[Math261A_Lecture02.pdf#page=3&selection=93,0,94,10&color=yellow|Math261A_Lecture02, p.3]]
> > Twenty observations on **shear strength (the response y)** and **age of propellant (the predictor x)**


> [!PDF|red] [[Math261A_Lecture02.pdf#page=4&selection=32,0,33,21&color=red|Math261A_Lecture02, p.4]] Question:
> > Compute the estimates of the regression intercept and slope “by hand” using the method outlined above
$$
\sum \limits_{i=1}^n x_{i}=267.25,\sum \limits_{i=1}^ny_{i}=42627.15, \sum \limits_{i=1}^n x_{i} y_{i}=528492.64, \sum \limits_{i=1}^n x_{i}^2=4677.688, \sum \limits_{i=1}^n y_{i} ^2=92547433.46
$$
$S_{xx} = \sum\limits_{i=1}^{n} x_{i}^2 - \frac{\left( \sum\limits_{}^{}x_{i} \right)^2}{n}$
$S_{xy}=\sum\limits_{}^{}x_{i}y_{i}-\frac{\sum\limits_{}^{}y_{i}\sum\limits_{}^{}x_{i}}{n}$


---

# Flash Cards
