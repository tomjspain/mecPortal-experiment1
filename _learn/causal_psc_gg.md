---
layout: post
title:  "How to use Model Estimated Controls"
date: 2025-03-12
categories: [methods]
description: How do Model Estimated Controls work?
---




<div class="box">
  <section id ="f" class=spotlights>


  <h2> MECs and other CI tools </h2>
  <p>
  Other CI tools have been developed to estimate causal effects
  from observational datasets.
  </p>
  
  
  <section>
    <a class="image">
      <img src="{% link assets/images/modelPlane.jpg %}" alt="" data-position="center center" />
    </a>
    <div class="content">
      <div class="inner">
        <header class="major">
          <h3> RCTs </h3>
        </header>
        <p>
        Randomised controlled trials (RCTs) are the gold-standard for CI, 
        and although they provide valuable evidence for predicting 
        treatment efficacy, they are costly and time-consuming. <br>
        </p>
      </div>
    </div>
  </section>
  
  <section>
  <a class="image">
      <img src="{% link assets/images/modelPlane.jpg %}" alt="" data-position="center center" />  
  </a>
  <div class="content">
    <div class="inner">
      <header class ="major">
        <h3> Other CI tools </h3>
      </header>
      <p>
      Multivariable modelling, G-estimation, Instrumental Variables,
      Propensity Score Analysis, Targeted Maximum Likelihood Estimations
      are other CI tools that have been developed. These tools 
      aim to estimate an average treatment effect. These methods 
      require patient level observational datasets from both the 
      control group and the experimental treatment group.
      </p>
    </div>
  </div>
  </section>
  
  <section>
  <a class="image">
    <img src="{% link assets/images/modelPlane.jpg %}" alt="" data-position="center center" />
  </a>

  <div class="content">
    <div class ="inner">
      <header class="major">
        <h3> How do MECs compare to other CI tools? </h3>
      </header>
      <p>
      MECs can act as a control group, and so an observational dataset
      for a control treatment group is not required. 
      MECs compare the observed response from an experimental group
      against the predicted response from the control.
      Other tools such as G-computation typically compare the expected 
      response from each treatment group
      </p>
    </div>
  </div>
  </section>
  
  </section>
</div>
