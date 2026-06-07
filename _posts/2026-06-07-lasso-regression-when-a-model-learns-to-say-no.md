---
layout: post
title: "Lasso Regression: When a Model Learns to Say \"No\""
---

In data science, people often say that more data is better. More columns, more variables, more information. At first, this sounds correct. If a model knows more about the data, maybe it should make better predictions. But after last quarter learning, either in deep learning or statistics survey method, I started to feel that this idea is not true. More variables can also make a model be more noisy and harder to explain. This time Lasso regression "saves" the statistics.

Lasso stands for **Least Absolute Shrinkage and Selection Operator**. It is a regression method that can do both regularization and variable selection. In simple words, Lasso does not just fit a model. It also decides which variables are worth keeping. Some coefficients can be pushed all the way to zero, which means those variables are removed from the model. For readers who want a more technical explanation, the original idea comes from Robert Tibshirani's paper on regression shrinkage and selection, and many machine learning guides also explain how Lasso is used for feature selection today.

What I like about Lasso is the ability of feature selections. In many real projects, the goal is not only to get a prediction. We also want to understand what the model is using, and more important, which features actually work in the prediction. For example, in medical data, business analytics, or radiology report analysis, interpretability matters. A model that uses fewer but more useful variables may perform better than a model that uses everything but is hard to explain.

Some funny graphs shows the training process of penalty (lambda) and validation loss (score):

I always treated Lasso as a model with a "budget." If regular regression is to keep almost every feature, then Lasso is more selective. It is like you are packing for a trip with only one luggage. You cannot bring every possible item you like, so you keep the things that are most useful. This is not only a mathematical trick. It is also a good reminder for me: not every variable deserves attention.

However, Lasso should not be treated like a perfect truth machine. One issue is that when variables are highly correlated, Lasso may keep one and drop all the others. This can make the model look clean, but it may hide several variables that are actually related to the outcome. Another issue is the choice of lambda, the tuning hyperparameter, also known as the penalty factor. If the penalty is too big, useful variables may also disappear. If it is too small, then the model may still keep too many useless variables. This is why validation is still important. Even scikit-learn's documentation treats Lasso feature selection as a modeling choice, not as solid proof that certain variables are truly unimportant.

My opinion is that Lasso is valuable because it gives us a new vision to make predictions. I recently started to do research on predicting grouped data in Lasso based on LassoNet and Pretraining Lasso. Feature selections are also important and extensible in neural networks, especially in real datasets, where there are always more than 50 or even 10000 features, such as in DNA sequences. In this case, we can combine Lasso into a more complex scenario.

That is why I still think Lasso is worth discussing. It may not be the newest or most fashionable method, but its idea is still important. Legends never die!

## Original Blog Pages

![Lasso blog page 1](/asset/blogs/lasso-pages/page-01.png)

![Lasso blog page 2](/asset/blogs/lasso-pages/page-02.png)

![Lasso blog page 3](/asset/blogs/lasso-pages/page-03.png)
