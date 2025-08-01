---
layout: model
title: Atezo Bev PFS
image: assets/images/hcc.jpg
area: HCC
description: A model to describe progression free survival in patients with HCC
---



<!-- Setting -->
<div class="box">

<h1 id="sett">Setting and Data</h1>

<h2>Setting </h2>

<p>
Data were taken from 
</p>

<div class="row">
	<div class="4u 12u$(medium)">
	  <div class="box">
  		<h3> Patients </h3>
  		<p> Details on the Patients (e.g. inclusion/exclusion criteria from the 
  		study) </p>
  	</div>	
	</div>
	<div class="4u 12u$(medium)">
		  <div class="box">
		<h3> Intervention </h3>
		<p> How was the intervention delivered? </p>
		  	</div>	
	</div>
	<div class="4u$ 12u$(medium)">
		  <div class="box">
		<h3> Outcome </h3>
		<p> How is the Outcome defined?  E.G. Overall Survival measured as the time 
		from randomisation until death by any cause </p>
		  	</div>	
	</div>
</div>



<!------>
<!------>


<!-- Data -->

<h2 id="data">Data</h2>

<p> A description of the data used to generate the model </p>

<div class="row 200%">
	
	<div class="6u 12u$(medium)">

		<h3>Model covariates</h3>
		
    <p> The covariates selected for inclusion in the model were Child-Pugh score
    Creatinine, Portal Vein ad Extrahepatic spread (EHS).
    </p>		
    

  <!-- Table -->
  
  <div class="table-wrapper">
  	<table>

 <thead>
  <tr>
   <th style="text-align:center;"> Characteristic </th>
   <th style="text-align:center;"> N = 480 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:center;"> Child-Pugh score 5 </td>
   <td style="text-align:center;"> 310 (65%) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Child-Pugh score 5+ </td>
   <td style="text-align:center;"> 79 (67,97) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Creatinine </td>
   <td style="text-align:center;"> 79 (0.36) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Portal vein none </td>
   <td style="text-align:center;"> 316 (66%) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Portal vein branch </td>
   <td style="text-align:center;"> 81 (17%) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Portal vein IVC/Main </td>
   <td style="text-align:center;"> 83 (17%) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Extrahepatic spread </td>
   <td style="text-align:center;"> 176 (37%)?? </td>
  </tr>
</tbody>
</table>
  </div>
  
  <!-- End Table -->
  
  </div>
  

  
  <div class="6u 12u$(medium)">
    <!-- Image -->
    <h3>Model covariates</h3>
    Details of the covariates used to generate the model are:
    <span class="image fit"><img src="{% link assets/images/at_bev_pfs.png %}" alt="" /></span>
    </div>
     <!-- End Image -->
  </div>


</div>
<!------>
<!------>
 
<!-- Model -->
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
    	<p> The model was contructed using a backward
    	stepwise procedure using Akaikes Information Criterion (AIC)
    	backwards stepwise procedure based on model AIC. </p>
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
	
   <h4>Model Estimates and Standard Errors</h4> 

  <div class="modelTable">
  	
  	<table>
<!-- <caption>Model Estimates and Standard Errors</caption> -->

 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> Est (se) </th>
   <th style="text-align:left;"> HR (95% CI) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> &gamma;0 </td>
   <td style="text-align:left;"> -3.75 (0.26) </td>
   <td style="text-align:left;"> 0.02 (0.014 - 0.039) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;1 </td>
   <td style="text-align:left;"> 2.71 (0.48) </td>
   <td style="text-align:left;"> 15.06 (5.888 - 38.541) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;2 </td>
   <td style="text-align:left;"> 0.21 (0.18) </td>
   <td style="text-align:left;"> 1.23 (0.864 - 1.747) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;3 </td>
   <td style="text-align:left;"> -0.18 (0.35) </td>
   <td style="text-align:left;"> 0.83 (0.418 - 1.665) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;4 </td>
   <td style="text-align:left;"> -0.16 (0.44) </td>
   <td style="text-align:left;"> 0.86 (0.358 - 2.046) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;5 </td>
   <td style="text-align:left;"> 0.65 (0.6) </td>
   <td style="text-align:left;"> 1.92 (0.591 - 6.272) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Aspartate aminotransferase </td>
   <td style="text-align:left;"> 0 (0) </td>
   <td style="text-align:left;"> 1 (1.002 - 1.003) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Child-Pugh 5+ </td>
   <td style="text-align:left;"> 0.55 (0.12) </td>
   <td style="text-align:left;"> 1.74 (1.377 - 2.195) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Creatinine </td>
   <td style="text-align:left;"> 0 (0) </td>
   <td style="text-align:left;"> 1 (1.001 - 1.007) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Portal Vein Branch </td>
   <td style="text-align:left;"> -0.26 (0.16) </td>
   <td style="text-align:left;"> 0.77 (0.563 - 1.056) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Portal Vein IVC/Main </td>
   <td style="text-align:left;"> 0.08 (0.15) </td>
   <td style="text-align:left;"> 1.08 (0.806 - 1.446) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Extrahepatic spread Pos</td>
   <td style="text-align:left;"> 0.2 (0.12) </td>
   <td style="text-align:left;"> 1.22 (0.967 - 1.535) </td>
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
 <!------>
 <!------>


<!-- Validation -->
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
   <td style="text-align:left;"> 0.61 (0.016) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Slope </td>
   <td style="text-align:left;"> 1.01 (0.14) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Somers' D </td>
   <td style="text-align:left;"> 0.22 </td>
  </tr>
</tbody>
</table>
  </div>

<h4>Discrimination</h4>
  
  <div class="table-wrapper">
    <table>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> Est (se) </th>
   <th style="text-align:left;"> HR (95% CI) </th>
  </tr>
 </thead>
 <tbody>
 <tr>
   <td style="text-align:left;"> Risk group 1 </td>
   <td style="text-align:left;"> </td>
   <td style="text-align:left;"> </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Risk group 2 </td>
   <td style="text-align:left;"> 0.43 (0.3) </td>
   <td style="text-align:left;"> 1.54 (0.85-2.79) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Risk group 3 </td>
   <td style="text-align:left;"> 0.84 (0.31) </td>
   <td style="text-align:left;"> 2.33 (1.28-4.24) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Risk group 4 </td>
   <td style="text-align:left;"> 1.46 (0.32)</td>
   <td style="text-align:left;"> 4.32 (1.91-4.15) </td>
  </tr>
</tbody>
</table>
  
  </div>

  </div>
  
  	<div class="6u 12u$(medium)">
  	  <!-- Image -->

  Kaplan Meier plot to show survival estimates within each of the 4 risk groups

  <span class="image fit"><img src="{% link assets/images/atBev_PFS_discrim.png %}" alt="" /></span>


   </div>

  </div>

</div>

<!------>
<!------>


<div class="box">

<h1 id="valid"> Use this model </h1>


Download this model and learn how to use it by visiting 
github/richJJackson/pscLibrary/test_model

</div>
<!------>
<!------>

 <div class="box">
<h1 id="valid"> References </h1>

Details on the trial which provided the data for this model can be found at:

Meyer T, Fox R, Ma YT, Ross PJ, James MW, Sturgess R, Stubbs C, Stocken DD, Wall 
L, Watkinson A, Hacking N. Sorafenib in combination with transarterial 
chemoembolisation in patients with unresectable hepatocellular carcinoma (TACE 
2): a randomised placebo-controlled, double-blind, phase 3 trial. The lancet 
Gastroenterology & hepatology. 2017 Aug 1;2(8):565-75.
</div>
