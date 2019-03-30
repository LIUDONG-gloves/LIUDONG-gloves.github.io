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

## This document will provide some descriptions and expansions about the variance inflation factor( VIF ).


A simple way to detect collinearity is to llok at the correlation matrix of the predictors. The most popular way is to examine the correlation matrix of explanatory variables.
However, there can still be multicollinearity even when all correlations are low, as correlation does not always match collinearity. Hence, to find out the more accurate diagnostic, people starts to establish the determinant of the matrix **R**( det**R**).

> But it still suffers from the similar problem. Say, even if determinant is close to one, there still might be multicollinearity among the columns of X. Futher more, both correlations and det**R** do ont reveal the nnumber of coexisting relations and their structure.


