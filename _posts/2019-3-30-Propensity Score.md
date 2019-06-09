---
layout:     post                    # 使用的布局（不需要改）
title:      KL DIVERGENCE EXPALNATIONS               # 标题 
subtitle:   Microeconometrics #副标题
date:       2019-03-29              # 时间
author:     ELVIS                      # 作者
header-img: img/post-bg-2015.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - Microeconometrics
---

## Propensity score was first propsed by Rosenbaum and Rubin(1983)



# Propensity score   

The concept of Propensity system was first proposed by Rosenbaum and Rubin. They define the propensity score as the conditional probability that an individual is affected by an independent variable after controlling the observable "confused" variable. The causal relationship between the phenomena obtained by controlling the propensity score can eliminate the influence of the "confusing" variable and pbtain the "net effect" between the two, thus ensuring the reliability of the conclusion. From a philosophical point of view, PSM is a clever use of "control" ideas in sociological research. From a statistical point of view, it is based on the counterfactual framework and technologically controls many confusing variables.   

Now, we examine this method based on two perspectives of philosophy and satistics.    

### The philosophical perspective of propensity score matching  

All sociological studies emphasize that only by controlling other variables can we really get the causal relationship between the two varibales of interest. When there is only one confusing variable, such as only the ability variable may bias the causal relationship between education and income, the general practice of controlling ability is to subdivide the ability variable into different levels and guarantee each level. The ability levels of the middle samples are the same or similar. In this way, we can examine the relationship between education and income at each level. Which is a common practice for controlling confusing variables. However, as the number of confusing variables that need to be controlled increases, this method of directly controlling confusing variables becomes more and more difficult. When we have two confusing variables, we can divide the variables into $$2\times 2$$ interactive groups, and only need to observe the relationship between education and income within the group, and then ask for the overall effect.   

However, when the number of variables to be controlled is increased to 5 or 6, then equal amount of interactive groups will be generated, which will make the grouping into no longer easy, and there may also be some other problems, such that a group without individual may be created due to the limitation of sample size. At this point, PSM subtly reduces the dimension of the confusion variable by means of the tendency to score. Instead of focusing on the specific value of the confusion variable, it focus on these confounding variables are placed on the predicted propensity score after the logistic regression equation. Under this situation, you can control all of the obfuscated variables simply by ensuring that the propensity scores match. Therefore, no matter how many confusing variables thare are, we can still control them through PSM to get the ideal causal relationship. From the perspective of "control", PSM solves the problem of controlling multiple confounding variables well, so that a moew "pure" causal relationship can be obtained.    

### The statistical basis of the propensity score matching method   

From a statistical point of view, let $$Y_{if}Y$$ represent the dependent variables of experimental variables and the control group. W is a binary variable, $$w=1$$ means the individual is in the experimental group, $$w=0$$ means the individual is in the control group. Therefore, when an individual belongs to the experimental group, $$E\left ( Y_{t}|w=1 \right )$$ is observableand counterfactual. We cannot observe that for a person who has been educated, we cannot observe that if he is not under university. The situation at the time of education. Similarly, for the control group, $$E\left ( Y_{0}|w=0 \right )$$ is observable, and $$E\left ( Y!|w=0 \right )$$ is counterfactual and unobservable. The causal relationship we hope to obtain is a weighted average of the differences between the "facts" and "reverse facts" of individuals in the experimental group.    

$$T = n\left [ E\left ( Y_{j}|w=0 \right )-E\left ( Y_{0}|w=1 \right ) \right ] + （1-n)\left [ E\left ( Y_{1}|w=0 \right )-E\left ( Y_{0}|w=0 \right ) \right ]$$
