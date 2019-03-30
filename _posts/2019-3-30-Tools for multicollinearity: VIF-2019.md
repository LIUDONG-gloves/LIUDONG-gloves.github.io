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

#  the Variance Inflation Factor( VIF ).

## What's the mutlicollinearity?

The multicollinearity arises when there is any departure from orthogonality in the set of regressors and get worse as the correlation among explanatory variables increase.      

As far as I know there are two effects, I mean, harms that multicollinearity has. On the one hand, the strong correlation among explanatory variables induces numerical instability in the estimates of both regression and statistical tests. The /hat{$\beta$} is very likely to be overestimated and the confidence interval is too loose to br of any practical use. On the other hand, it's not surprising to observe an increased R-square despite the reduced number of individual significant coefficients, also the t-statistic just fail to present the real pic.  

---
## How to assess it?
A simple way to detect collinearity is to llok at the correlation matrix of the predictors. The most popular way is to examine the correlation matrix of explanatory variables.
However, there can still be multicollinearity even when all correlations are low, as correlation does not always match collinearity. Hence, to find out the more accurate diagnostic, people starts to establish the determinant of the matrix **R**( det**R**).

> But it still suffers from the similar problem. Say, even if determinant is close to one, there still might be multicollinearity among the columns of X. Futher more, both correlations and det**R** do ont reveal the nnumber of coexisting relations and their structure.    




