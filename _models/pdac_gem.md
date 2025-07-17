---
layout: model
title: Gemcitabine OS
image: assets/images/pancStock.png
area: PDAC
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
Data were taken from the European Study group for PAncreatic Cancer (ESPAC) 3 
Study - A randomised phase III study to investigate the role of chemotherapy in 
patients following surgery for Pancreatic Ductal Adenocarcinoma.  Patients were
randomised post surgery.  Patients were recruited from 159 pancreatic cancer 
centers in Europe, Australasia, Japan, and Canada
</p>

<h2> Estimand </h2>
<div class="box">
  <div class="row">
  	
  	<div class="6u 12u$(medium)">
  	  <div class="box">
    		<h3> Patients </h3>
    		<p> Patients were eligible if they had undergone complete macroscopic (R0 
    		or R1) resection for ductal adenocarcinoma of the pancreas with 
    		histological confirmation and with no evidence of malignant ascites, 
    		peritoneal metastasis, or spread to the liver or other distant abdominal 
    		or extra-abdominal organs. Patients had to be fully recovered from the 
    		operation, with a World Health Organization performance score of 2 or 
    		lower and a life expectancy of more than 3 months. Patients with previous 
    		use of neoadjuvant chemotherapy or other concomitant chemotherapy and with 
    		pancreatic lymphoma, macroscopically remaining tumor (R2 resection), or 
    		TNM stage IVb disease were excluded. </p>
    	</div>	
  	</div>
  	
  	<div class="3u 12u$(medium)">
  		<div class="box">
  		<h3> Intervention </h3>
  		<p> Patients received gemcitabine as 1000 mg/m<sup>2</sup> intravenous infusion once a 
  		week for 3 of every 4 weeks for up to 6 months </p>
  		</div>	
  	</div>
  	
  	<div class="3u$ 12u$(medium)">
  		<div class="box">
  		<h3> Outcome </h3>
  		<p> The outcome is Overall Survival measured as the point from randomisation 
  		until death by any cause </p>
  		</div>	
  	</div>

  		<h3> Inter-current Events </h3>
  		<p> The chosen estimand for analysis follows the Treatment Policy approach, ignoring 
      any intercurrent events or termination of therapies as is suitable for evaluating 
      patients at the point of treatment choice.   Lastly, as a key prognositc 
      indicator, only patients with a basleine measure of post-operative CA19-9 were retained in the 
      model.</p>

  </div>
</div>



<!------------------------>
<!------------------------>
<!-- Data -->
<!------------------------>
<!------------------------>


<h2 id="data">Data</h2>

<p> Data considered for inclusion in the model were observed from the baseline
case report forms of the ESPAC-3 study and included Resection
Margin Status, Lymph Nodes, Local Invasion, WHO status, Tumor Grade (Differentiation), Tumour
Size, Diabetes status and Post-operative CA19.9</p>


<p> The dataset included 339 patients of whom 267 (79%) observed an event (died). 
Median Overall Survival (95% CI) was 22.8 (21.2 - 27.2) months.

<div class="row 200%">
	
	<div class="6u 12u$(medium)">

  <!-- Table -->
		<h3>Model Covariates</h3>

    <p> The covariates selected for inclusion in the model were Resection Margin, Tumour 
    Grade, Lymph Nodes and (log) Post-operative CA19-9.
    </p>
    
    
      <div class="table-wrapper">
      <table>
 <thead>
  <tr>
   <th style="text-align:left;"> Characteristic </th>
   <th style="text-align:left;"> N = 339 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Resec </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Neg </td>
   <td style="text-align:left;"> 206 (61%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pos </td>
   <td style="text-align:left;"> 133 (39%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Diff status </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Poor </td>
   <td style="text-align:left;"> 85 (25%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Moderate </td>
   <td style="text-align:left;"> 214 (63%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Well </td>
   <td style="text-align:left;"> 40 (12%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> LymphN </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Neg </td>
   <td style="text-align:left;"> 97 (29%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Pos </td>
   <td style="text-align:left;"> 242 (71%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> log(PostOp CA19-9) </td>
   <td style="text-align:left;"> 3.04 (2.30, 4.14) </td>
  </tr>
</tbody>
</table>

      </div>
      
      
      
  </div>
  <!-- End Table -->
  

  
  <div class="6u 12u$(medium)">
    <!-- Image -->
    <span class="image fit"><img src="{% link assets/images/e3_gem_ka.png %}" alt="" /></span>
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

<p> The model consturcuted was a flexible parametric survival model using a 
spline function to model the underlying cumulative hazard function.  Five 
internal knots were chosen which gave sufficient flexibility. The number of 
knots was chosen based on the best log-likelihood.
</p>

<div class="row 200%">
	
	<div class="6u 12u$(medium)">
    <h3> Model Construction </h3>
    <div class="box">
    	<p> 
The model was constructed using a backwards stepwise procedure using
Akaikes Information Criterion (AIC) to evaluate model fit.  Initaily, a 'null' 
model constructed using all covaraites, irrespective of univariable significance, 
was constructed and single terms removed in an itterative fashion.  </p>
    </div>
    
    <!-- Image -->
    <div>
      <h3>Model Fit</h3>
      Overall fit of the model is demonstrated by plotting the unadjusted 
      survival estimates against the model obtained by applying the mean
      linear predictor.
      <span class="image fit"><img src="{% link assets/images/e3_gem_fpm.png %}" alt="" /></span>
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
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> Est (se) </th>
   <th style="text-align:left;"> HR (95% CI) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> &gamma;0 </td>
   <td style="text-align:left;"> -11.38 (1.56) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;1 </td>
   <td style="text-align:left;"> 3.84 (0.79) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;2 </td>
   <td style="text-align:left;"> 1.29 (2.22) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;3 </td>
   <td style="text-align:left;"> -1.32 (4.0) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;4 </td>
   <td style="text-align:left;"> 1.12 (3.55) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;5 </td>
   <td style="text-align:left;"> -0.89 (2.22) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;6 </td>
   <td style="text-align:left;"> 0.34 (0.81) </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> LymphN Pos </td>
   <td style="text-align:left;"> 0.49 (0.15) </td>
   <td style="text-align:left;"> 1.63 (1.21 - 2.19) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ResecM Pos </td>
   <td style="text-align:left;"> 0.18 (0.13) </td>
   <td style="text-align:left;"> 1.20 (0.94 - 1.53) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Diff status Moderate </td>
   <td style="text-align:left;"> -0.42 (0.14) </td>
   <td style="text-align:left;"> 0.66 (0.50 - 0.87) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Diff status Well </td>
   <td style="text-align:left;"> -0.59 (0.22) </td>
   <td style="text-align:left;"> 0.55 (0.36 - 0.86) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> log(PostOp CA19-9) </td>
   <td style="text-align:left;"> 0.27 (0.04) </td>
   <td style="text-align:left;"> 1.31 (1.21 - 1.41) </td>
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

<p>
Internal Validation is performed by assessing how well the model performs on the 
training dataset.
</p>


<h3> Validation Details </h3>
<div class="box">
	<p> Validation are reported in terms of Calibration, Discrimination and Somers' D.  
	Calibration is reported in terms of the Mallows C-Statistic and by regressing 
	the fitted linear predictor against the outcome (Slope). <br>
	
	Discrimination is evaluated by categorising patients into 4 risk groups.  
	Risk groups are determined by the 15th, 50th and 85th centiles of the linear predictor and 
	compared graphically and by evaluating the relative risk by fitting a 
	univariable Cox Proportional Hazards Model.
	</p>
</div>


<div class="row 200%">

	<div class="6u 12u$(medium)">

  <h4>Calibration </h4>
  
    <div class="table-wrapper">
  
  <table>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> est (se) </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> C-Statistic </td>
   <td style="text-align:left;"> 0.65 (0.018) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Slope </td>
   <td style="text-align:left;"> 0.999 (0.11) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Somers' D </td>
   <td style="text-align:left;"> 0.33 </td>
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
       <th style="text-align:left;"> est (se) </th>
       <th style="text-align:left;"> HR (95% CI) </th>
      </tr>
     </thead>
    <tbody>
      <tr>
       <td style="text-align:left;"> Risk Group 1 </td>
       <td style="text-align:left;">  </td>
       <td style="text-align:left;">  </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Risk Group 2 </td>
       <td style="text-align:left;"> 0.594 (0.231) </td>
       <td style="text-align:left;"> 1.810 (1.152, 2.846) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Risk Group 3 </td>
       <td style="text-align:left;"> 1.167 (0.227) </td>
       <td style="text-align:left;"> 3.213 (2.060, 5.012) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Risk Group 4 </td>
       <td style="text-align:left;"> 1.856 (0.185) </td>
       <td style="text-align:left;"> 6.395 (3.874, 10.558) </td>
      </tr>
    </tbody>
    </table>
   

  </div>

  </div>
  
  	<div class="6u 12u$(medium)">
  	  <!-- Image -->

  Kaplan Meier plot to show survival estimates within each of the 4 risk groups

  <span class="image fit"><img src="{% link assets/images/e3_gem_discrim_ka.png %}" alt="" /></span>


   </div>

  </div>

</div>



<!------------------------>
<!------------------------>

<div class="box">

<h1 id="valid"> Use this model </h1>

<p> 
This model is available to download [here](https://github.com/richJJackson/pscLibrary/tree/main/PDAC/Gem_model)
</p>

<p>
Find out more about how models are stored/shared and how you can use them [here](https://github.com/richJJackson/pscLibrary/tree/main/PDAC/Gem_model)
</p>


<p>
This model has been used to compare the combined therapy GemCap against Gem. 
Find out how [here](https://github.com/richJJackson/pscLibrary/tree/main/PDAC/Gem_Vs_GemCap)
</p>

</div>




<!------------------------>
<!------------------------>

 <div class="box">
<h1 id="valid"> References </h1>

Details on the trial which provided the data for this model can be found at:

Neoptolemos JP, Stocken DD, Bassi C, et al. Adjuvant Chemotherapy With 
Fluorouracil Plus Folinic Acid vs Gemcitabine Following Pancreatic Cancer 
Resection: A Randomized Controlled Trial. JAMA. 2010;304(10):1073–1081. 
doi:10.1001/jama.2010.1275
</div>
