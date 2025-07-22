---
layout: app
title: Gemcitabine Vs Gemcitabine plus Capecitabine
area: PDAC
description:  A CFM model to predict and compare the response of gemcitabine capecitabine patients to treatment with monotherapy gemcitabine
---

## Executive Summary

<p>The survival outcome of patients that received gemcitabine plus capecitabine (GEMCAP)
GEMCAP (experimental treatment) were compared against a 
counterfactual model (CFM). The CFM predicts the survival outcome
of patients if they had been treated with monotherapy gemcitabine (GEM). </p>

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

<p>
The GEM CFM model was used as a control to compare the predicted performance of GEM treatment
with the actual observed performance of GEMCAP treatments on ESPAC-4 patients.
</p>


<p>
The GEM model and the details of the ESPAC-3 study used to build the model can be found here: 
<a href="https://richjjackson.github.io/mecPortal//models/pdac_gem.html">Visit GEM model</a>
</p>

## description of data

pscVis example

<div class = "box">
<h2 id="Analysis"> Analysis </h2>
<body>
<div class="row">
  <div class="5u 12u$(medium)">
    <!-- Image -->
    <h4> Comparison </h4>
    <p> 
    The average expected survival estimate of the CFM (control treatment -GEM) and the
    average observed survival estimate of the GEMCAP patients is shown below to 
    visualise the comparison of the GEM CFM (pink) vs GEMCAP treatment (orange) <br>
    </p>
    <span class="image fit">
      <img src="{% link assets/images/e3gem_vs_e4gemcap.png %}" alt="" />
    </span>
    <!-- End Image -->
  </div>
  
  <div class="5u 12u$(medium)">
    <div class="box">

      <div class="table-wrapper">
        <table>
          <thead>
          <tr>
            <th style="text-align:left;"> </th>
            <th style="text-align:left;"> Median </th>
            <th style="text-align:left;"> 2.5% </th>
            <th style="text-align:left;"> 97.5% </th>
            
          </tr>
          </thead>
        <tbody>
          <tr>
            <td style="text-align:left;"> &beta; </td>
            <td style="text-align:left;"> -0.47 </td>
            <td style="text-align:left;"> -0.60 </td>
            <td style="text-align:left;"> -0.34 </td>
          </tr>
          <tr>
            <td style="text-align:left;"> DIC </td>
            <td style="text-align:left;"> 1321.34 </td>
            <td style="text-align:left;"> 1297.85 </td>
            <td style="text-align:left;"> 1356.92 </td>
          </tr>
        </tbody>
      </table>
      </div>
    <p>
    DIC, deviance information criterion.
    </p>
    </div>
  </div>
  <div class="5u 12u$(medium)">
    <div class="box">
    <p>
    The predicted survival probability for ESPAC-4 patients treated with GEM 
    is less than the observed survival probability of ESPAC-4 patients treated
    with GEMCAP, demonstrating that combination therapy GEMCAP has greater 
    efficacy than monotherapy GEM.
    </p> <br>
    &beta; is the efficacy parameter which measures the distance between the actual 
    observed data and the model's estimates.
    </div>
  </div>
</div>
</body>
</div>


## Sub-group analysis


## Conclusions


## Reference

Give details of the models




