---
layout:     post                    # 使用的布局（不需要改）
title:      TOOLS FOR MULTICOLLINEARITY--VIF               # 标题 
subtitle:   Microeconometrics #副标题
date:       2019-03-30              # 时间
author:     ELVIS                      # 作者
header-img: img/post-bg-2015.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - Microeconometrics
---
<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>

#  the Variance Inflation Factor( VIF ).

## What's the mutlicollinearity?

The multicollinearity arises when there is any departure from orthogonality in the set of regressors and get worse as the correlation among explanatory variables increase.      

As far as I know there are two effects, I mean, harms that multicollinearity has. On the one hand, the strong correlation among explanatory variables induces numerical instability in the estimates of both regression and statistical tests. The /hat{$\beta$} is very likely to be overestimated and the confidence interval is too loose to br of any practical use. On the other hand, it's not surprising to observe an increased R-square despite the reduced number of individual significant coefficients, also the t-statistic just fail to present the real pic.  

---
## How to assess it?
A simple way to detect collinearity is to llok at the correlation matrix of the predictors. The most popular way is to examine the correlation matrix of explanatory variables.
However, there can still be multicollinearity even when all correlations are low, as correlation does not always match collinearity. Hence, to find out the more accurate diagnostic, people starts to establish the determinant of the matrix **R**( det**R**).

> But it still suffers from the similar problem. Say, even if determinant is close to one, there still might be multicollinearity among the columns of X. Futher more, both correlations and det**R** do ont reveal the number of coexisting relations and their structure.    

## VIF
Variance inflation factor( VIF ) is another multicollinearity diagnostic, given in the equation below.   

$$VIF_j=\frac{Var\left ( \widehat{\beta_j}\right )}{ Var\left ( \widehat{\beta _j_0}\right ) }=\frac{1}{1-R_j^2}$$    

Where R-square is the coefficient of multiple determination of x_i on the remaining explanatory variables. VIF values caould vary from unity to infinity. Out of the perspect of simplicity, people get used to interpret $$\sqrt{VIF_j}$$. The following R example will also construct the square root.   

### Explanations
Now I offer one example to illstrute the VIF value. If $$VIF_j=10$$, then $$\sqrt{VIF_j}=3.1623$$, which means that the standard error of $$\widehat{\beta_j}$$ would be 3.1623 times larger than it was when all predictors are independent. As the VIF becomes larger, the relationship will become stronger and vice versa. To look futher, let's take a look at the origin of VIF.   

$$Var\left ( b_j* \right )=VIF_j\times \frac{1-R^2}{n-p-1}$$    

Hence VIF shows the degree to which $$V\left ( b_j* \right )$$ increases due to multicollinearity between $$X_j$$ and other preditors. It's clear that any interdependence between predictos causes a precision for the slopes.  

### Futhermore
As stated by Wooldridge[2] and Johnston[3], $$VIF_j$$ is a function of $$R_j^2$$ and obviously it's highly nonlinear. Though many researchers say higher value of VIF leads to more troublesome results, its not that properly to make our conclusion about whether to drop variables based on VIFs.   

> If we think certain explanatory variables need to be included in a regression to infer causality of $$x_j$$, then we are hesitant to drop them, and whether we think $$VIF_j$$ is "too high" cannot really affect that desicion.        

Besides the concern above, we still need to a rule for evaluating VIF. The interesting thing is that many researchers set the cutoff value as 10, or equivalently, $$R_j^2>0.9$$, while others take $$\sqrt{ VIF_j }>2$$ as harmful, maybe its not the level of cutoff value but the logic behind this that matters. a VIF above 10 or 4 does not mean that the variance of $$\widehat{\beta_j}$$ is useless since it's jointly determined by $$\sigma^2$$ and $$SST_j$$.   


### Example
Next I'll use the "lonely" package to show how to calculate VIF with R and how does the mmutlicollinearity looks like:  
```
> lm1 <- lm(GNP.deflator ~ ., data = longley)
> summary(lm1)
> library(car)
> vif(lm1, digits = 3)
> plot(longley[, 2:7])   

```
![R process.png](https://i.loli.net/2019/03/31/5ca07124bf591.png)
![IMG_1493.png](https://i.loli.net/2019/03/31/5ca072528c1ee.png)     

Vary large VIF values are indicators of multicollinearity, here is the figure proof:  

![IMG_1494.png](https://i.loli.net/2019/03/31/5ca072ad524d7.png)     

Actually from the VIF values we could still not get the straightforward access to the structure of the coexisting replations. And that is one big restriction of VIF. 




