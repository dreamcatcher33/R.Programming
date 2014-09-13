# Note: practical machine learning [Week1]

标签（空格分隔）： MOOC stat cs

---

# 1. Motivation of machine learning.
- A very exciting website:\[kaggle](https://www.kaggle.com/account/confirmation).
- and an R package name **caret**.
- More advanced material: *The elements of statistical learning*;
- And a more advanced course on MOOC: *Machine Learning* by Andrew NG@Stanford;
- workflow of a predictor:
```flow
st0=>start: Question
st=>start: Collect Data
st1=>start: Features
st2=>start: Algorithm
st3=>start: Parameters
st4=>start: Prediction
st5=>end: Evaluation
st0->st->st1->st2->st3->st4->st5->end
```

---

Remarks:
> a) Relative importance: Quesion > data > feature > algorithm;
> b) Feature abstraction requirements:
    >> i)  compress data;
    >> ii) retain important information;
    >> iii)expert application knowledge.
    >> iv) automatic feature selection with care!!!


# 2. The "best" Machine Learning method:
- Interpretable (very important! sensiblility)
- Simple
- Accurate
- Scalable(可扩展的)
- Fast


# 3. **In sample error** and **out of sample error**:
We care about the out of sample errror;
in sample error < out of sample error;
forbid overfitting!! ( distinguish signal and noise)

----

#4. Type of errors

- dicholomous data: TP,TN,FP,FN and other quantities.
![TypeOfError](http://photo.weibo.com/1651659553/wbphotos/large/mid/3754383134707562/pid/62725321jw1ekay21zkjaj20wf0g7n0v)

- continuous data: MSE(or RMSE),MAD,ROC curve.concordance(eg:kappa)

---

#5. Prediction Study designs:
- partition data into training data,test data (and validation data);
- generally: 60% training data, test+validation = 40%.
- protocol:  Cross Validation in the training data to pick features, pick best prediction function, estimate the test set accuracy,and then:
    - if having validation data: apply the prediction function to test data and refine it a little bit; then apply the refined prediction function to the validation data for just **ONCE**!
    - if NO validation data: directly apply the prediction function to test data, still **ONCE**.


#6. Cross validation: (sample withOUT replacement)
- random subsampling;
- K-fold CV;
- Leave one out.





