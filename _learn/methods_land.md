---
layout: post
title:  "Model Estimated Controls - Methods"
date: 2025-03-12
categories: [methods]
description: How do Model Estimated Controls work?
image: assets/images/modelPlane.jpg
---











<!-- Two -->
<div class="box">
  <section id="concept" class="spotlights">
  
    <h2> Concept</h2> 
  
  	<section>
  		<a class="image">
  			<img src="{% link assets/images/methods_land_fig1.pdf %}" alt="" data-position="center center" />
  		</a>
  		<div class="content">
  			<div class="inner">
  				<header class="major">
  					<h3> Models as the base for counter-factual evidence </h3>
  				</header>
  				<p> The premis for Model Estimated Control is that a model can be used 
  				to estimate a patient's outcome and that this estimate can be compared 
  				against their observed outcome </p>
  			</div>
  		</div>
  	</section>
  	
  	<section>
  		<a class="image">
  			<img src="{% link assets/images/methods_land_fig2.pdf %}" alt="" data-position="top center" />
  		</a>
  		<div class="content">
  			<div class="inner">
  				<header class="major">
  					<h3> Average Treatment Effects obtained by averaging across individual effect </h3>
  				</header>
  				<p> To estimate the average treatment effect over a group of patients, we can average over all individual effects. </p>
  			</div>
  		</div>
  	</section>
  	
  </section>
</div>


<!-- Two -->

<div class="box">
  <section id="Estimation" class="spotlights">
  
    <h2> Estimation </h2> 
  
    <p> Two procedures exist for estimating treatment effects using MEC - a simulation and a likelihood approach </p>
    
  	<section>
  		<a class="image">
  			<img src="{% link assets/images/methods_land_fig3.pdf %}" alt="" data-position="center center" />
  		</a>
  		<div class="content">
  			<div class="inner">
  				<header class="major">
  					<h3> Simulation </h3>
  				</header>
  				<p> Use the model to directly simulate 'synthetic' patients.  For each 
  				observed patient we can then use basic analytical methods to compare the 
  				observed and the expected outcomes </p>
  			</div>
  		</div>
  	</section>
  	
  	<section>
  		<a class="image">
  			<img src="{% link assets/images/methods_land_fig4.pdf %}" alt="" data-position="top center" />
  		</a>
  		<div class="content">
  			<div class="inner">
  				<header class="major">
  					<h3> Likelihood based approach </h3>
  				</header>
  				<p> Define a likelihood where a term is added to measure the direct 
  				difference between the counter factual model and the new cohort of 
  				observations </p>
  			</div>
  		</div>
  	</section>
  	
  </section>
</div>



<!-- Two -->

  
<h2> Further Details </h2> 

<div class="box">
<!-- LINKS -->
<section id="links">
  <div class="inner">
      <header class="major">
  	    <h2>
        <a href="methods_glm.html"> MECs for Binary/Continuous Outcomes </a>
        </h2>
      </header>
	    <p>Understand how Model Estimated Controls work with MEC based on Generalised Linear Models </p>
  </div>
  
  <div class="inner">
      <header class="major">
  	    <h2>
        <a href="methods_surv.html"> MECs for Survival Outcomes </a>
        </h2>
      </header>
	    <p> Understand how Model Estimated Controls work with MEC based on Parametric Survival Models </p>
  </div>
  
  <div class="inner">
      <header class="major">
  	    <h2>
        <a href="methods_surv.html"> Bayesian Estimation of MECs </a>
        </h2>
      </header>
	    <p> Get more details on the Bayesian estimation procedures along with MCMC algorithms </p>
  </div>
    
</section>

</div>

