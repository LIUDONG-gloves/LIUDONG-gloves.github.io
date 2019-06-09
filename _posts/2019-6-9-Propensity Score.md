---
layout:     post                    # 使用的布局（不需要改）
title:      PROPENSITY SCORE               # 标题 
subtitle:   Microeconometrics           #副标题
date:       2019-06-09              # 时间
author:     ELVIS                      # 作者
header-img: img/post-bg-2015.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - Microeconometrics
---
<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script> 
## Propensity score was first propsed by Rosenbaum and Rubin(1983)



# Propensity score   

The concept of Propensity score system was first proposed by Rosenbaum and Rubin. They define the propensity score as the conditional probability that an individual is affected by an independent variable after controlling the observable "confused" variable. The causal relationship between the phenomena obtained by controlling the propensity score can eliminate the influence of the "confusing" variable and pbtain the "net effect" between the two, thus ensuring the reliability of the conclusion. From a philosophical point of view, PSM is a clever use of "control" ideas in sociological research. From a statistical point of view, it is based on the counterfactual framework and technologically controls many confusing variables.   

Now, we examine this method based on two perspectives of philosophy and satistics.    

## The philosophical perspective of propensity score matching  

All sociological studies emphasize that only by controlling other variables can we really derive the causal relationship between the two varibales of interest. When there is only one confusing variable, such as only the "ability" variable may bias the causal relationship between education and income, the general practice of controlling ability is to subdivide the ability variable into different levels and guarantee that during each level, the ability of samples are the same or close. In this way, we can examine the relationship between education and income at each level. Which is a common practice for controlling confusing variables. However, as the number of confusing variables that need to be controlled increases, this method of directly controlling confusing variables becomes more and more difficult. When we have two confusing variables, we can divide the variables into $$2\times 2$$ interactive groups, and only need to observe the relationship between education and income within the group, then figure out the overall effect.   

However, when the number of variables to be controlled is increased to 5 or 6, then equal amount of interactive groups will be generated, which will make the grouping no longer easy, and there may also be some other problems, such that a group without individual may be created due to the limitation of sample size. At this point, PSM is able to subtly reduce the dimension of the confusion variable by means of tendency scoring. Instead of focusing on the specific value of the confusion variable, it focuses on the propensity score obtained by substituting these confounding variables into the logistic regression equation. Under this situation, you can control all of the obfuscated variables simply by ensuring that the propensity scores match. Therefore, no matter how many confusing variables thare are, we can still control them through PSM to get the ideal causal relationship. From the perspective of "control", PSM solves the problem of controlling multiple confounding variables well, so that a  "purer" causal relationship can be obtained.    


## The statistical basis of the propensity score matching method    

From a statistical point of view, let $$Y_{if},Y$$ represent the dependent variables of experimental group and the control group. W is a binary variable, $$w=1$$ means the individual is in the experimental group, $$w=0$$ means the individual is in the control group. When an individual belongs to the experimental group,       $$E\left ( Y_{t}|w=1 \right )$$    is observable and counterfactual. We cannot observe what if a well educated person without being educated at the time. Similarly, for the control group,    $$E\left ( Y_{0}|w=0 \right )$$     is observable, and    $$E\left ( Yj|w=0 \right )$$    is counterfactual and unobservable. The causal relationship we hope to obtain is a weighted average of the differences between the "facts" and "reverse facts" of individuals in the experimental group.    

$$T = n\left [ E\left ( Y_{j}|w=0 \right )-E\left ( Y_{0}|w=1 \right ) \right ] + （1-n)\left [ E\left ( Y_{1}|w=0 \right )-E\left ( Y_{0}|w=0 \right ) \right ]$$    

Where n is the proportion of all subjects in the experimental group. Since counterfactuality cannot be observed, a specific group of people can only be in the experimental group or in the control group, the following non-confusion assumptions must still be met when making causal inferences:     

$$E\left ( Y_{1}|w=0 \right )=E\left ( Y_{1}|w=1 \right )$$       


$$E\left ( Y_{0}|w=0 \right )=E\left ( Y_{0}|w=1 \right )$$      

That is, another group in the control group can represent the "counterfactual" status of the individual in the experimental group. Thus, equation(1) can be simplified as:     

$$T=E\left ( Y_{j}|w=1 \right )-E\left ( Y_{0}|w=0 \right )$$     

Under randomized experimental conditions, since the experimental individuals were assigned to the experimental and control groups in a random manner,   

$$E\left ( Y_{1}|w=0 \right )=E\left ( Y_{i}|w=1 \right )$$     

$$E\left ( Y_{0}|w=0 \right )=E\left ( Y_{0}|w=1 \right )$$ 
assumptions hold. Based on the fact that the observed test cannot guarantee randomization, it is necessary to control the confusion variable as much as  possible so that $$w$$ is independent from $$Y_{0}$$ and $$Y_{1}$$.    

$$ E\left ( Y_{1}|w=0,x \right )=E\left ( Y_{1}|w=1,x \right )$$      

$$E\left ( Y_{0}|w=0,x \right )=E\left ( Y_{0}|w=1,x \right ) $$     

Among them, it is a confusion variable. As long as the aliasing variables can be found and controlled, it is approximated that $$w$$ is independent of $$Y_{0},Y_{1}$$(Rosenbaum and Rubin, 1983), i.e. $$\left ( Y_{0}, Y_{1} \right )\perp w\mid x$$  

At this point, the confounding variable obtains a specific propensity value p by logistic regression, which results in:   

$$E\left ( Y_{1}|w=0,p \right )=E\left ( Y_{1}|w=1,p \right )$$   

$$E\left ( Y_{0}|w=0,p \right )=E\left ( Y_{0}|w=1,p \right )$$    

In summary, the non-confused assumptions can be satisfied "approximate" to obtain the desired causality inference.
