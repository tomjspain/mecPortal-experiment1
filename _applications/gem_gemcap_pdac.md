---
layout: app
title: Gemcitabine Vs Gemcitabine plus Capecitabine
area: PDAC
description:  A CFM model to predict and compare the response of gemcitabine capecitabine patients to treatment with monotherapy gemcitabine
---

# Layout


## Executive Summary

<p>Patients that received GEMCAP (experimental treatment) were 
compared against a counterfactual model (CFM) developed 
using patients treated with GEM (control treatment) 
in the ESPAC-3 study. </p>

<div class="box">

<h2 id="sett">Model setting and Data</h2>

<h3 id="data">Data </h3>
<p>Data were taken from the European Study Group for PAncreatic Cancer
(ESPAC-4) Study- A randomised  controlled phase III trial that compared
the effect of adjuvant combination chemotherapy of gemcitabine and 
capecitabine (GEMCAP) versus monotherapy gemcitabine (GEM) in patients 
with resected pancreatic ductal adenocarcinoma. </p>
<div class="box">
  <div class="row">
  	
  	<div class="6u 12u$(medium)">
  	  <div class="box">
    		<h4> Patients </h4>
    		<p> 
    		Eligible patients had undergone complete macroscopic resection
    		for ductal adenocarcinoma of the pancreas (R0 or R1)
    		</p>
    	</div>	
  	</div>
  	
  	<div class="3u 12u$(medium)">
  		<div class="box">
  		<h4> Intervention </h4>
  		<p>
  		GEMCAP patients received GEM 1000mg/m<sup>2</sup> and oral CAP
    	1660 mg/m<sup>2</sup>/day 
  		</p>
  		</div>	
  	</div>
  	
  	<div class="3u$ 12u$(medium)">
  		<div class="box">
  		<h4> Comparison </h4>
  		<p> 
  		Patients were treated with either 
  		GEM or adjuvant GEMCAP combination therapy
  		</p>
  		</div>	
  	</div>
  </div>
</div>
</div>
## Description of model

<p>The GEM CFM model was used as a control to predict the performance
of GEM treatment on GEMCAP patients and to compare the predictions
against the actual performance of GEMCAP treatment.</p>


The GEM model and the data used to build the model can be found here: <br>
<p><a href="https://richjjackson.github.io/mecPortal//models/pdac_gem.html">Visit GEM model</a></p>

## description of data

pscVis example

## Analysis
<p>pscfit and images</p>
<body>
  <div class="5u 12u$(medium)">
    <!-- Image -->
    <span class="image fit"><img src="{% link assets/images/e3gem_vs_e4gemcap.png %}" alt="" /></span>
  </div>
     <!-- End Image -->
</body>


## Sub-group analysis


## Conclusions


## Reference

Give details of the models




