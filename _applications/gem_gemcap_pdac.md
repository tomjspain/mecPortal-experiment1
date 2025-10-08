---
layout: app
title: Gemcitabine Vs Gemcitabine plus Capecitabine
area: PDAC
description:  A CFM model to predict and compare the response of gemcitabine capecitabine treated patients to treatment with monotherapy gemcitabine
---



<p>The observed survival outcome of patients treated with gemcitabine plus capecitabine (GEMCAP)
(experimental treatment) were compared against the predicted 
response of monotherapy gemcitabine (GEM) (control treatment). A counterfactual
model (CFM) is used to estimate the expected response of patients
had they been treated with GEM. </p>

<div>
  <ul class="actions">
      <li><a href="../models/pdac_gem.html" class="button special">GEM model</a></li>
  </ul>
</div>

<div class="box" style="background-color:#8878c3;">

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

<div class= "box" style="background-color:#b284be;">

<h2 id="desc"> Description of model </h2>
<h3 id="cfm"> Gemcitabine CFM </h3>
<p>
The GEM CFM model (developed on the ESPAC-3 data) was used to generate counterfactual evidence had the ESPAC-4 data
cohort been treated with GEM. The actual observed response of patients treated
with GEMCAP were then compared against the model's expected response of the 
data cohort.
</p>


<p>
The GEM model and the details of the data used to build the model can be found 
<a href="../models/pdac_gem.html">here</a>
</p>


</div>

<div class = "box" style="background-color:#796878;">
<h2 id="Analysis"> Analysis </h2>
<p> 
A counterfactual model and a data cohort were used to make a comparison of treatment
efficacy.
</p>
<body>

<div class="row">

  <div class="6u 12u$(medium)">
  <div class="box">
  <h4> GEM Vs GEMCAP </h4>
  <p>
    The average expected survival estimate of the CFM (control treatment- GEM) and the
    average observed survival estimate of the GEMCAP patients is shown below to 
    visualise the comparison of GEM treatment (pink) vs GEMCAP treatment (orange).
  </p>    
  <!-- Image -->
    <span class="image fit"><img src="{% link assets/images/e3gem_vs_e4gemcap.png %}" alt="" /></span>
  <!-- End Image -->
  
  
    
  </div>
  </div>
  
  <div class="6u 12u$(medium)">
    <div class="box">
    <h4> Estimates of the efficacy parameter for the overall comparison of GEM Vs GEMCAP </h4>
    <p>
    The efficacy parameter (&beta;) measures the distance between the observed data and the 
    model's estimate. 
    Here, a median value (2.5%, 97.5% quantiles) of -0.47 (-0.60,-0.34) is obtained for &beta;
    </p>
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
  <h4></h4>
  <p>
    The predicted survival probability for ESPAC-4 patients treated with GEM 
    is less than the observed survival probability of ESPAC-4 patients treated
    with GEMCAP, demonstrating that combination therapy GEMCAP has greater 
    efficacy than monotherapy GEM.
    The survival estimates are obtained by multiplying the cumulative baseline
    hazard function by the mean of the linear predictor.
  </p>
  </div>
</div>
</body>
</div>



<div class = "box" style="background-color:#b784a7;">
<h2 id="Sub-group"> Sub-group analysis </h2>
<body>

<div class="box">
The comparison of treatment efficacy can also be estimated within individual sub-groups.
Sub-group analyses is carried out by filtering for a specific sub-group of patients from
the population (e.g., only patients that have poor tumour differentiation). A comparison
is then made on the sub-group of patients.
<a href="https://github.com/kusqaum/PDAC/blob/main/gem_vs_gemcap.R"> Code for the sub-group analysis is available here! </a>

</div>

<div class="row">
  <div class="8u 12u$(medium)">
    
      <!--Image-->
      <span class="image fit"><img src="{% link assets/images/sub-group_forest.png %}" alt="" /></span>
      <!--End image-->

  </div>
  <div class="4u 12u$(medium)">
    <div class="box">
      <p>
      Treatment efficacy can be compared within individual sub-groups.
      The estimated efficacy parameters (&beta;) (95% CI) are visualised using
      forest plots. 
      The results of the sub-group analyses show that survival estimates
      differ between sub-groups. For example the negative resection margin 
      group has a higher observed &beta; than the positive resection margin group.
      </p>
    </div>  
  </div>
</div>
 
</body>
</div>

<div class = "box" style="background-color:#856088;">
<h2 id="conclusion"> Conclusions </h2>
<p>
CFMs can be used to predict and compare patient level outcomes. <br>
In this example, we used a data-cohort of patients that
were treated with an experimental treatment and a CFM that was used
to predict the survival of the same data-cohort when treatead with 
GEM (a control). The GEM CFM survival predictions were compared with
the actual outcome of the GEM treatment. 
The comparison showed that GEMCAP was the more effective treatment. <br>
</p>
<p>
Sub-group effects can be looked at by only including patients within a certain group
in the data cohort.
</p>
</div>


<div class="box" style="background-color:#5d3954;">
<h1 id="valid"> References </h1> 
<p>
Details on the ESPAC-4 trial from which the data cohort were taken from can be found at: <br>
<a href="https://www.sciencedirect.com/science/article/pii/S0140673616324096?via%3Dihub">
Neoptolemos, J.P. et al. (2017) ‘Comparison of adjuvant gemcitabine and
capecitabine with gemcitabine monotherapy in patients with resected 
pancreatic cancer (ESPAC-4): a multicentre, open-label,
randomised, phase 3 trial’, The Lancet (British edition), 
389(10073), pp. 1011–1024. </a>
</p>
<p>
Details on the gem model can be found
<a href="../models/pdac_gem.html">here</a>
</p>
</div>



