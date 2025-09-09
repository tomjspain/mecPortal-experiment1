---
layout: model
title: TACE OS in HCC
image: assets/images/hcc.jpg
area: tmpArea
description:  A template of the information to include
---



<!-- Setting -->
<div class="box">

<h1 id="sett">Setting and Data</h1>

<h2>Setting </h2>

A quick description of the model setting is provided:  E.G. This model
predicts the survival of patients with Hepatocellular Carcinoma (HCC) BCLC stage 
B and treated with Trans Arterial Chemoembolisation (TACE).  The model has been 
generated on the data from the TACE + Placebo arm from the TACE 2 trials.

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

		<h4>Covariates</h4>
		
		<p> A list of all available data in the construction of the description of 
		all the covariates that wew included in the dataset </p>
		
		<ul>
			<li> Covariate 1</li>
			  <p> Details of how it is maesured (eg. units) </p>
			<li> Covariate 2</li>
			  <p> Details of how it is maesured (eg. units) </p>
			<li> Covariate 3</li>
			  <p> Details of how it is maesured (eg. units) </p>
			<li> Covariate 4</li>
			  <p> Details of how it is maesured (eg. units) </p>
		</ul>

  <!-- Table -->
  
  <h4> Table of covariate summaries</h4>
  <div class="table-wrapper">
  	<table>
<caption>Covariates Summary</caption>
 <thead>
  <tr>
   <th style="text-align:center;"> Variable </th>
   <th style="text-align:center;"> Summary </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:center;"> Age </td>
   <td style="text-align:center;"> 68.19 (7.69) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> AFP </td>
   <td style="text-align:center;"> 4.22 (2.48) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Hepatitis B </td>
   <td style="text-align:center;"> 0.15 (0.36) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Hepatitis C </td>
   <td style="text-align:center;"> 0.25 (0.43) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Bilirubin </td>
   <td style="text-align:center;"> 18.8 (14.14) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Albumin </td>
   <td style="text-align:center;"> 38.89 (4.28) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Lesion1 </td>
   <td style="text-align:center;"> 5.7 (3.73) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Lesion2 </td>
   <td style="text-align:center;"> 3.26 (1.93) </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Gender </td>
   <td style="text-align:center;"> Female : 6, Male : 75 </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Cirrhosis </td>
   <td style="text-align:center;"> 0 : 4, 1 : 77 </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Focality </td>
   <td style="text-align:center;"> Multifocal : 75, Unifocal : 6 </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Vascular.invasion </td>
   <td style="text-align:center;"> 0 : 81 </td>
  </tr>
  <tr>
   <td style="text-align:center;"> Child.Pugh.grade </td>
   <td style="text-align:center;"> A : 81 </td>
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
    <span class="image fit"><img src="{% link assets/images/TACE_dataPlot.png %}" alt="" /></span>
    </div>
     <!-- End Image -->
  </div>


</div>
<!------>
<!------>
 
<!-- Model -->
<div class="box">
<h1 id="data"> Model </h1>

<p> A description of the data used to generate the model: </p>

<div class="row 200%">
	
	<div class="6u 12u$(medium)">
    <h3> Model Construction </h3>
    <div class="box">
    	<p> Include details here about the process of fitting the model.  E.G. 
    	backwards stepwise procedure based on model AIC </p>
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
      <th style="text-align:left;"> Parameter </th>
   <th style="text-align:right;"> Estimate </th>
   <th style="text-align:right;"> SE </th>
  </tr>
 </thead>
<tbody>
  <tr>
      <td style="text-align:left;"> gamma0 </td>
   <td style="text-align:right;"> -2.1373 </td>
   <td style="text-align:right;"> 1.9048 </td>
  </tr>
  <tr>
      <td style="text-align:left;"> gamma1 </td>
   <td style="text-align:right;"> 1.8352 </td>
   <td style="text-align:right;"> 0.4569 </td>
  </tr>
  <tr>
     <td style="text-align:left;"> gamma2 </td>
   <td style="text-align:right;"> 0.0614 </td>
   <td style="text-align:right;"> 0.0602 </td>
  </tr>
  <tr>
      <td style="text-align:left;"> AFP </td>
   <td style="text-align:right;"> 0.1801 </td>
   <td style="text-align:right;"> 0.0586 </td>
  </tr>
  <tr>
      <td style="text-align:left;"> Cirrhosis1 </td>
   <td style="text-align:right;"> -0.5538 </td>
   <td style="text-align:right;"> 1.0464 </td>
  </tr>
  <tr>
      <td style="text-align:left;"> Albumin </td>
   <td style="text-align:right;"> -0.0867 </td>
   <td style="text-align:right;"> 0.0371 </td>
  </tr>
  <tr>
      <td style="text-align:left;"> Lesion1 </td>
   <td style="text-align:right;"> 0.0221 </td>
   <td style="text-align:right;"> 0.0438 </td>
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
	<p> Provide some information on how the model is validated </p>
</div>


<div class="row 200%">

	<div class="6u 12u$(medium)">

  <h4>Calibration Details</h4>
  
  <div class="table-wrapper">
  	<table>
 <thead>
  <tr>
   <th style="text-align:left;"> Metric </th>
   <th style="text-align:right;"> Value </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> C-index </td>
   <td style="text-align:right;"> 0.2895377 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Calibration Slope </td>
   <td style="text-align:right;"> 0.9827559 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Calibration Slope SE </td>
   <td style="text-align:right;"> 0.2402236 </td>
  </tr>
</tbody>
</table>

<h4>Discrimination Details</h4>
  
  <div class="table-wrapper">
    <table>
 <thead>
  <tr>
   <th style="text-align:left;"> Risk Group </th>
   <th style="text-align:right;"> Coefficient </th>
   <th style="text-align:right;"> SE (Coef) </th>
   <th style="text-align:right;"> Z-value </th>
   <th style="text-align:right;"> P-value </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Medium-Low </td>
   <td style="text-align:right;"> 0.3462284 </td>
   <td style="text-align:right;"> 0.4426802 </td>
   <td style="text-align:right;"> 0.7821186 </td>
   <td style="text-align:right;"> 0.4341449 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Medium-High </td>
   <td style="text-align:right;"> 1.1493102 </td>
   <td style="text-align:right;"> 0.4519407 </td>
   <td style="text-align:right;"> 2.5430551 </td>
   <td style="text-align:right;"> 0.0109888 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> High </td>
   <td style="text-align:right;"> 1.3859891 </td>
   <td style="text-align:right;"> 0.4313030 </td>
   <td style="text-align:right;"> 3.2134929 </td>
   <td style="text-align:right;"> 0.0013113 </td>
  </tr>
</tbody>
</table>

      

  </div>

  </div>
  
  	<div class="6u 12u$(medium)">
  	  <!-- Image -->
  <h3>Validation</h3>

  Some text to describe the validation output

  <span class="image fit"><img src="{% link assets/images/Calibration.png %}" alt="" /></span>


   </div>

   git push origin master
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
