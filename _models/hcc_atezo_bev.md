---
layout: model
title: Atezo Bev OS
image: assets/images/hcc.jpg
area: HCC
description:  A model to describe overall survival in patients with aHCC
---




<!------------------------>
<!------------------------>
<!-- Setting -->
<!------------------------>
<!------------------------>

<div class="box">

<h1 id="sett">Setting and Data</h1>

<h2>Setting </h2>
<p>
Data were taken from the BRISK-FL study- a randomised phase III study to 
compare the overall survival of brivanib versus sorafenib in patients
with advanced HCC (aHCC).
</p>

<h2> Estimand </h2>
<div class="box">
  <div class="row">
  
	  <div class="6u 12u$(medium)">
	    <div class="box">
  		  <h3> Patients </h3>
  		<p> Patients were eligible if they had not received any prior
  		systemic therapy for aHCC. </p>
  	  </div>	
	  </div>
	  
	  <div class="3u 12u$(medium)">
		  <div class="box">
		  <h3> Intervention </h3>
		  <p> Patients received brivanib as 800mg orally every day. </p>
		  </div>	
	   </div>
	  
	  <div class="3u$ 12u$(medium)">
		  <div class="box">
		  <h3> Outcome </h3>
		  <p> Outcome details </p>
		  </div>	
  </div>
</div>



<!------------------------>
<!------------------------>
<!-- Data -->
<!------------------------>
<!------------------------>


<h2 id="data">Data</h2>

<p> The dataset consisted of 454 patients of whom 204 (45%) observed an 
event and 250 (55%) did not. The median overall survival (95% CI) was 
16.2 (14.3, 17.6) months. </p>

<div class="row 200%">
	
	<div class="6u 12u$(medium)">

  <!-- Table -->
		<h3>Model Covariates</h3>
		
		<p> The covariates selected for inclusion in the model were<br>
		Eastern Cooperative Oncology Group (ECOG) score, extra-hepatic spread (EHS), 
		bilirubin (BIL), tumour size, age, albumin (ALB) and alpha-fetoprotein (AFP) </p>
		
      <div class="table-wrapper">
      <table>
 <thead>
  <tr>
   <th style="text-align:left;"> Characteristic </th>
   <th style="text-align:left;"> N = 454 </th>
  </tr>
 </thead>
<tbody>
      <tr>
       <td style="text-align:left;"> ECOG0 </td>
       <td style="text-align:left;"> 199 (44%) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> ECOG1 </td>
       <td style="text-align:left;"> 230 (51%) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> ECOG2 </td>
       <td style="text-align:left;"> 25 (5.5%) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> EHS Pos </td>
       <td style="text-align:left;"> 164 (36%) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> EHS Neg </td>
       <td style="text-align:left;"> 290 (64%) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Bilirubin </td>
       <td style="text-align:left;"> 1.13 (0.95, 1.34) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Tumour size </td>
       <td style="text-align:left;"> 7.35 (5.57, 9.64) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Age </td>
       <td style="text-align:left;"> 68 (62,74) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Albumin </td>
       <td style="text-align:left;"> 3.80 (3.40,4.20) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> AFP </td>
       <td style="text-align:left;"> 2.70 (1.79,3.76) </td>
      </tr>
</tbody>
</table>
      </div>
  
  </div>
  <!-- End Table -->
  

  <div class="6u 12u$(medium)">
    <!-- Image -->
    <span class="image fit"><img src="{% link assets/images/at_bev_ka.png %}" alt="" /></span>
  </div>
     <!-- End Image -->
  </div>






<!------------------------>
<!------------------------>
<!-- Model -->
<!------------------------>
<!------------------------>


<div class="box">
<h1 id="data"> Model </h1>

<p> The model constructed was a flexible parametric survival model using
a spline function to model the underlying cumulative hazard function. Four internal
knots were chosen and were placed at the timepoints 3, 6 12, and 24 months. 
</p>

<div class="row 200%">
	
	<div class="6u 12u$(medium)">
    <h3> Model Construction </h3>
    <div class="box">
    	<p> Include details here about the process of fitting the model.  E.G. 
    	backwards stepwise procedure based on model AIC. 
    	</p>
    </div>
    
    <!-- Image -->
    <div>
      <h3>Model Fit</h3>
      Some text to describe what is provided
      <span class="image fit"><img src="{% link assets/images/TACE_km1.png %}" alt="" /></span>
    </div>
  
  </div>
    <!-- End Image -->
    
    
    
  <div class="6u 12u$(medium)">

<!-- Table -->
	
   <h4>Model Estimates</h4> 

  <div class="modelTable">
  	
  	<table>

 <thead>
  <tr>
   <th style="text-align:left;">  </th>
   <th style="text-align:right;"> Estimate (se) </th>
   <th style="text-align:right;"> HR (95% CI) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> &gamma;0 </td>
   <td style="text-align:right;"> -5.65 (1.02) </td>
   <td style="text-align:right;"> 0.00 (0 - 0.026) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;1 </td>
   <td style="text-align:right;"> 1.98 (0.47) </td>
   <td style="text-align:right;"> 7.27 (2.906 - 18.173) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;2 </td>
   <td style="text-align:right;"> 0.06 (0.25) </td>
   <td style="text-align:right;"> 1.07 (0.655 - 1.738) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;3 </td>
   <td style="text-align:right;"> 0.42 (0.5) </td>
   <td style="text-align:right;"> 1.52 (0.57 - 4.049) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;4 </td>
   <td style="text-align:right;"> -1.62 (0.67) </td>
   <td style="text-align:right;">  0.2 (0.053 - 0.728) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;5 </td>
   <td style="text-align:right;"> 3.58  (1.18) </td>
   <td style="text-align:right;"> 36.04 (3.578 - 363.04) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ECOG1 </td>
   <td style="text-align:right;"> 0.28 (0.15) </td>
   <td style="text-align:right;"> 1.32 (0.981 - 1.78) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ECOG2 </td>
   <td style="text-align:right;"> 0.59 (0.31) </td>
   <td style="text-align:right;"> 1.81 (0.981 - 3.333) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> EHS Pos </td>
   <td style="text-align:right;"> 0.52 (0.15) </td>
   <td style="text-align:right;"> 1.68 (1.248 - 2.251) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bilirubin </td>
   <td style="text-align:right;"> 1.41 (0.29) </td>
   <td style="text-align:right;"> 4.09 4.09 (2.326 - 7.208) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Tumour size </td>
   <td style="text-align:right;"> 0.08 (0.03) </td>
   <td style="text-align:right;"> 1.08 (1.03 - 1.141) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age </td>
   <td style="text-align:right;"> 0.02 (0.01) </td>
   <td style="text-align:right;"> 1.02 (1.002 - 1.03) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Albumin </td>
   <td style="text-align:right;"> -0.61 (0.14) </td>
   <td style="text-align:right;"> 0.54 (0.408 - 0.72) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Alpha-fetoprotein </td>
   <td style="text-align:right;"> 0.07 (0.06) </td>
   <td style="text-align:right;"> 1.08 ((0.959 - 1.209)) </td>
  </tr>
</tbody>
</table>

  </div>
  <!-- End Table -->
  <div>
    <h3> Model Prediction</h3>
    See how this model can be used to predict survival!
    <ul class="actions">
      <li><a href="#" class="button special">Rshiny</a></li>
    </ul>
  </div>
 
 </div>
  
</div>


</div>

<!------------------------>
<!------------------------>
<!-- Validation -->
<!------------------------>
<!------------------------>

<div class="box">

<h1 id="valid"> Validation </h1>

<p> Details on the validation of the model: </p>


<h3> Validation Details </h3>
<div class="box">
	<p> Validation are reported in term of Calibration, Discrimination and Somers' D.  
	Calibration is reported in terms of the Mallows C-Statistic and by regressing 
	the fitted linear predictor against the outcome (Slope). The linear predictor is 
	derived using the model's coefficients. <br>
	
	Discrimination is evaluated by categorising patients into 4 risk groups.  
	Risk groups are generated by using the 5th, 50th and 85th centiles of the 
	linear predictor. The risk groups are	compared graphically 
	and the relative risk is evaluated by fitting a 
	univariable Cox Proportional Hazards Model.
	</p>
</div>


<div class="row 200%">

	<div class="6u 12u$(medium)">

  <h4>Calibration</h4>
  
    <div class="table-wrapper">
  <table>
 <thead>
  <tr>
   <th style="text-align:left;">  </th>
   <th style="text-align:left;"> est (se) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> C-Statistic </td>
   <td style="text-align:left;"> 0.70 (0.017) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Slope </td>
   <td style="text-align:left;"> 1.00 (0.101) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Somers' D </td>
   <td style="text-align:left;"> 0.41 </td>
  </tr>
</tbody>
</table>
  </div>

<h4>Discrimination</h4>
  
  <div class="table-wrapper">
    <table>
     <thead>
      <tr>
       <th style="text-align:left;"> </th>
       <th style="text-align:right;"> est (se) </th>
       <th style="text-align:right;"> HR (95% CI) </th>
      </tr>
     </thead>
    <tbody>
      <tr>
       <td style="text-align:left;"> Risk Group 1 </td>
       <td style="text-align:left;"> </td>
       <td style="text-align:left;"> </td>
      </tr>
      <tr>
       <td style="text-align:left;">  Risk Group 2 </td>
       <td style="text-align:left;">  0.06 (0.26) </td>
       <td style="text-align:left;"> 1.06 (0.63, 1.77) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Risk Group 3 </td>
       <td style="text-align:left;">  1.06 (0.24) </td>
       <td style="text-align:left;">  2.89 (1.81, 4.61) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Risk Group 4 </td>
       <td style="text-align:left;"> 1.82 (0.26) </td>
       <td style="text-align:left;"> 6.20 (3.70, 10.37) </td>
      </tr>
    </tbody>
    </table>
  
  </div>

  </div>
  
  	<div class="6u 12u$(medium)">
  	  <!-- Image -->

  Kaplan Meier plot to show survival estimates within each of the 4 risk groups

  <span class="image fit"><img src="{% link assets/images/atBev_discrim.png %}" alt="" /></span>


   </div>

  </div>

</div>



<!------------------------>
<!------------------------>

<div class="box">

<h1 id="valid"> Use this model </h1>


Download this model and learn how to use it by visiting 
github/richJJackson/pscLibrary/test_model

</div>

<!------------------------>
<!------------------------>

 <div class="box">
<h1 id="valid"> References </h1>

Details on the trial which provided the data for this model can be found at:

Meyer T, Fox R, Ma YT, Ross PJ, James MW, Sturgess R, Stubbs C, Stocken DD, Wall 
L, Watkinson A, Hacking N. Sorafenib in combination with transarterial 
chemoembolisation in patients with unresectable hepatocellular carcinoma (TACE 
2): a randomised placebo-controlled, double-blind, phase 3 trial. The lancet 
Gastroenterology & hepatology. 2017 Aug 1;2(8):565-75.
</div>
