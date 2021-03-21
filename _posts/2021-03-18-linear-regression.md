---
layout: post
author: robw
title: Bayesian Inference
abstract: Here you will find the slides I presented at several
 reading groups designed to be a general intro to Bayesian
  Inference and linear regression. Much of the content is based on the
   Murpy and Bishop machine learning books which I thoroughly
    recommend if you want to find out more. If you have any
     questions or want to discuss anything please drop me an email.
image: /assets/images/bayesian.png
numbered: false
tags:
    - bayesian
    - reading group
    - machine learning
    - research
---


![Teaser](/assets/images/bayesian.png)

## Bayesian Statistics
These slides were presented at the Murphy reading
 group at the [Oxford Robotics Institute](https://ori.ox.ac.uk/) over a couple of weeks in
  March 2021 and were designed to cover the majority of the
   Bayesian statistics chapter from ["Probabilistic Machine Learning: An Introduction"](https://probml.github.io/pml-book/book1.html) by Kevin Murphy. 
   
   We begin by looking at what
    Bayesian inference
   _is_ and how it differs from a frequentist paradigm. Next the
    model is considered. Particular attention is given to the
     _prior_. We see how when using _conjugate priors_ inference is
      always
     tractible and investigate several options for defining priors
      when we have litte domain knowledge at our disposal. When
       inference is intractible several methods exist attempting to 
        _approximate_ the posterior; point estimates, the laplace
         method, variational inference
          and sampling methods are all explored to this end. 
          Finally we consider _Bayesian model selection_. We see
           how the bayesian paradigm provides us with a natural
            mechanism to compare the validity of different models
             and naturally favours the simpler explanation.

<a href="/assets/pdf/bayesian_statistics.pdf"><i class="fa fa-cloud
-download"> Download</i></a>

<div class="w3-container w3-center">
<object data="/assets/pdf/bayesian_statistics.pdf" width="100%" height="60%" type
="application/pdf">
        <embed src="https://drive.google.com/file/d/1Hw0lb7iycwc3n-v5REGz_6KTBdUiGwM9/preview" width="100%" height="60%">
</object>
</div>



## Linear Regression
These slides were presented at the Bishop reading group with the
 [Apllied Artificial Intelligence](https://ori.ox.ac.uk/labs/a2i/) lab covering most of the content
  from "Pattern Recognition and Machine Learning" by Chris Bishop. We
   begin by formulating the
  linear regression problem. We see that maximum likelihood is a
   good option for estimating the underlying function from noisy data
    when we have
    large datasets available to us but for smaller $N$ our
     solutions significantly overfit. We explore theoretically why
      this is the case using the bias-variance deomposition
      . Introducing a norm penalty on the weights is
       proposed as an attempt at
       overcoming the
       limitations of Maximum likelihood for small $N$. In doing so
        we are able to significantly reduce the
         variance in our estimator at the expense of increased bias
         . Finally we consider linear regression from the bayesian
          perspective: in this case the model is naturally
           regularised through the process of marginalising
           , and all parameters can be estimated without
            the need for a test set, allowing us to exploit all the
             observations we have available.
            
Code for the examples given in the slides can be found [here
](https://github.com/robw4/bayesain-regression/blob/master/bayesain_linear_regression.ipynb). 

<a href="/assets/pdf/linear_regression.pdf"><i class="fa fa-cloud
-download"> Download</i></a>

<div class="w3-container w3-center">
<object data="/assets/pdf/linear_regression.pdf" width="100%" height="60%" type
="application/pdf">
    <embed src="https://drive.google.com/file/d/1DnGq4ZEkiYcFloymOicLIF0Rb4fuolJU/preview" width="100%" height="60%">
</object>
</div>