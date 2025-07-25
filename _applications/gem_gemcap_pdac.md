---
layout: app
title: Gemcitabine Vs Gemcitabine plus Capecitabine
area: PDAC
description:  A CFM model to predict and compare the response of gemcitabine capecitabine treated patients to treatment with monotherapy gemcitabine
---

## Executive Summary

<p>The observed survival outcome of patients treated with gemcitabine plus capecitabine (GEMCAP)
GEMCAP (experimental treatment) were compared against the predicted 
response of monotherapy gemcitabine (GEM) (control treatment). A counterfactual
model (CFM) is used to estimate the expected response of patients
had they been treated with GEM. </p>

<div class="box">

<h2 id="sett">Data</h2>

<h3 id="data">Data cohort for comparison against the CFM </h3>
<p>Observed patient data, to compare against the CFM, were taken from the European Study Group for PAncreatic Cancer
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
    		The ESPAC-4 dataset consisted of 732 patients in total.
    		Only patients that had been treated with GEMCAP were included 
    		as part of the data cohort for comparison, resulting in a total
    		of 362 patients. 
    		
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

<div class= "box">

<h2 id="desc"> Description of model </h2>
<h3 id="cfm"> Gemcitabine CFM </h3>
<p>
The GEM CFM model was used to generate counterfactual evidence had the ESPAC-4 data
cohort been treated with GEM. The actual observed response of patients treated
with GEMCAP were then compared against the model's expected response of the 
data cohort.
</p>


<p>
The GEM model and the details of the data used to build the model can be found here: 
<a href="https://richjjackson.github.io/mecPortal//models/pdac_gem.html">Visit GEM model</a>
</p>

## description of data

pscVis example
</div>

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



<div class = "box">
<h2 id="Sub-group"> Sub-group analysis </h2>
<body>
<p>
Sub-group effects are investigated by subsetting the observed 
data cohort into sub-groups.<br> </p>

  <div class="row">
    <div class = "8u 12u$(medium)">
      <div class ="box">
      <table>
      <thead>
        <tr>
         <th style="text-align:left;"> Characteristic </th>
         <th style="text-align:left;"> Level </th>
         <th style="text-align:left;"> &beta; (2.5%, 7.5%) </th>
         <th style="text-align:left;"> DIC (2.5%, 97.5%) </th>
        </tr>
      </thead>
      <tbody>
        <tr>
         <td style="text-align:left;"> Resection margin </td>
         <td style="text-align:left;"> Negative </td>
         <td style="text-align:left;"> -0.15 (-0.32, 0.02) </td>
         <td style="text-align:left;"> 848.69 (837, 866.55) </td>
        </tr>
        <tr>
         <td style="text-align:left;">  </td>
         <td style="text-align:left;"> Positive </td>
         <td style="text-align:left;"> -0.74 (-0.961, -0.507) </td>
         <td style="text-align:left;"> 445.8 (437.3, 459.7) </td>
        </tr>
        <tr>
         <td style="text-align:left;"> Lymph nodes </td>
         <td style="text-align:left;"> Negative </td>
         <td style="text-align:left;"> -0.80 (-1.182, -0.446) </td>
         <td style="text-align:left;"> 203.6 (198.3, 213.2) </td>
        </tr>
        <tr>
         <td style="text-align:left;"> </td>
         <td style="text-align:left;"> Positive </td>
         <td style="text-align:left;"> 0.086 (-0.090, 0.271) </td>
         <td style="text-align:left;"> 1106.7 (1088,1137)  </td>
        </tr>
        <tr>
         <td style="text-align:left;"> Tumour differentiation </td>
         <td style="text-align:left;"> Poor </td>
         <td style="text-align:left;"> -1.210 (-1.599, -0.848) </td>
         <td style="text-align:left;"> 149 (144.9, 157.6)</td>
        </tr>
        <tr>
         <td style="text-align:left;">  </td>
         <td style="text-align:left;"> Moderate </td>
         <td style="text-align:left;"> -0.88 (-1.087, -0.681) </td>
         <td style="text-align:left;"> 773 (760.8, 793.5)  </td>
        </tr>
        <tr>
         <td style="text-align:left;">  </td>
         <td style="text-align:left;"> Well </td>
         <td style="text-align:left;"> -0.54 (-0.80, -0.288) </td>
         <td style="text-align:left;"> 361 (355.3, 372.1)  </td>
        </tr>
      </tbody>
      </table>
      </div>
    </div>
    
  </div>
</body>
</div>

<div class = "box">
<h2 id="conclusion"> Conclusions </h2>
<p>
CFMs can be used to predict and compare patient level outcomes. <br>
In this example, the GEM CFM was compared against a data cohort that had been treated
with GEMCAP. The comparison showed that GEMCAP was the more effective treatment. <br>
</p>
<p>
Sub-group effects can be looked at by only including patients within a certain group
in the data cohort.
</p>
</div>


<div class="box">
<h1 id="valid"> References </h1> 
<p>
Details on the ESPAC-4 trial from which the data cohort were taken from can be found at: <br>
Neoptolemos, J.P. et al. (2017) ‘Comparison of adjuvant gemcitabine and capecitabine with gemcitabine monotherapy in patients with resected pancreatic cancer (ESPAC-4): a multicentre, open-label, randomised, phase 3 trial’, The Lancet (British edition), 389(10073), pp. 1011–1024. Available at: https://doi.org/10.1016/S0140-6736(16)32409-6.
</p>
<p>
Details on the gem model can be found
<a href="https://richjjackson.github.io/mecPortal//models/pdac_gem.html">here</a>
</p>
</div>



