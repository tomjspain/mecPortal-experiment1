---
layout: model
title: Gemcitabine OS
image: assets/images/pancStock.png
area: PDAC
description:  A model to describe overall survival in patients with PDAC
---




<!------------------------>
<!------------------------>
<!-- Setting -->
<!------------------------>
<!------------------------>



<div>
    <ul class="actions">
      <li><a href="http://104.248.163.38/shiny/pdacShiny/" class="button special">Rshiny</a></li>
    </ul>
  </div>



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


<div class="box" style="background-color: #796878 ;">
<h2> Estimand </h2>
  <div class="row">
  	
  	<div class="7u 12u$(medium)">
  	  <div class="box">
    		<h4> Eligibility criteria </h4>
    		<p> Patients were eligible if they had undergone complete macroscopic (R0 
    		or R1) resection for ductal adenocarcinoma of the pancreas with 
    		histological confirmation and with no evidence of malignant ascites, 
    		peritoneal metastasis, or spread to the liver or other distant abdominal 
    		or extra-abdominal organs. Patients had to be fully recovered from the 
    		operation, with a World Health Organization performance score of 2 or 
    		lower and a life expectancy of more than 3 months.
    		</p>
    		<p>
    		<h4> Exclusion criteria </h4>
    		Patients with previous 
    		use of neoadjuvant chemotherapy or other concomitant chemotherapy and with 
    		pancreatic lymphoma, macroscopically remaining tumor (R2 resection), or 
    		TNM stage IVb disease were excluded. </p>
    	</div>	
  	</div>
  	
  	<div class="5u 12u$(medium)">
  		<div class="box">
  		<h3> Intervention </h3>
  		<p> Patients received gemcitabine as 1000 mg/m<sup>2</sup> intravenous infusion once a 
  		week for 3 of every 4 weeks for up to 6 months </p>
  		</div>	
  	</div>
  	
  	<div class="5u$ 12u$(medium)">
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

<div class="box" style="background-color: #856088;">
<h2 id="data">Data</h2>

<p> Data considered for inclusion in the model were observed from the baseline
case report forms of the ESPAC-3 study and included Resection
Margin Status, Lymph Nodes, Local Invasion, WHO status, Tumor Grade (Differentiation), Tumour
Size, Diabetes status and Post-operative CA19.9</p>


<p> The dataset included 339 patients of whom 267 (79%) observed an event (died). 
Median Overall Survival (95% CI) was 22.8 (21.2 - 27.2) months.
</p>

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
   <th style="text-align:left;"> Covariate </th>
   <th style="text-align:left;"> N = 339 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> <b>Resection Margin</b> </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  &nbsp;&nbsp;Negative </td>
   <td style="text-align:left;"> 206 (61%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &nbsp;&nbsp;&nbsp;Positive </td>
   <td style="text-align:left;"> 133 (39%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> <b>Tumour differentiation</b> </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &nbsp;&nbsp;&nbsp;&nbsp;Poor </td>
   <td style="text-align:left;"> 85 (25%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &nbsp;&nbsp;&nbsp;&nbsp;Moderate </td>
   <td style="text-align:left;"> 214 (63%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &nbsp;&nbsp;&nbsp;&nbsp;Well </td>
   <td style="text-align:left;"> 40 (12%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> <b>Lymph Nodes</b> </td>
   <td style="text-align:left;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  &nbsp;&nbsp;&nbsp;&nbsp;Negative </td>
   <td style="text-align:left;"> 97 (29%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &nbsp;&nbsp;&nbsp;&nbsp;Positive </td>
   <td style="text-align:left;"> 242 (71%) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> <b>log(PostOp CA19-9)</b> </td>
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
</div>





<!------------------------>
<!------------------------>
<!-- Model -->
<!------------------------>
<!------------------------>


<div class="box" style="background-color: #967bb6 ;">
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
   <td style="text-align:left;"> &gamma;<sub>0</sub> </td>
   <td style="text-align:left;"> -11.38 (1.56) </td>
   <td style="text-align:left;">  0 (0 - 0) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;<sub>1</sub> </td>
   <td style="text-align:left;"> 3.84 (0.79) </td>
   <td style="text-align:left;"> 46.34 (9.86 - 217.7) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;<sub>2</sub> </td>
   <td style="text-align:left;"> 1.29 (2.22) </td>
   <td style="text-align:left;"> 3.64 (0.05 - 284.34) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;<sub>3</sub> </td>
   <td style="text-align:left;"> -1.32 (4.0) </td>
   <td style="text-align:left;"> 0.27 (0 - 643.24) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;<sub>4</sub> </td>
   <td style="text-align:left;"> 1.12 (3.55) </td>
   <td style="text-align:left;"> 3.06 (0 - 3229.93) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;<sub>5</sub> </td>
   <td style="text-align:left;"> -0.89 (2.22) </td>
   <td style="text-align:left;"> 0.41 (0.01 - 31.87) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> &gamma;<sub>6</sub> </td>
   <td style="text-align:left;"> 0.34 (0.81) </td>
   <td style="text-align:left;"> 1.4 (0.28 - 6.89) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Lymph Nodes: Positive Vs Negative </td>
   <td style="text-align:left;"> 0.49 (0.15) </td>
   <td style="text-align:left;"> 1.63 (1.21 - 2.19) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Resection Margin: Positive Vs Negative </td>
   <td style="text-align:left;"> 0.18 (0.13) </td>
   <td style="text-align:left;"> 1.20 (0.94 - 1.53) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Tumour Differentiation Status: Moderate Vs Poor </td>
   <td style="text-align:left;"> -0.42 (0.14) </td>
   <td style="text-align:left;"> 0.66 (0.50 - 0.87) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Tumour Differentiation Status: Well Vs Poor </td>
   <td style="text-align:left;"> -0.59 (0.22) </td>
   <td style="text-align:left;"> 0.55 (0.36 - 0.86) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> log(Post-Operative CA19-9) </td>
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
      <li><a href="http://104.248.163.38/shiny/pdacShiny/" class="button special">Rshiny</a></li>
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

<div class="box" style="background-color: #563c5c;">

<h1 id="valid"> Validation </h1>

<p> Details on the validation of the model: </p>

<p>
Internal validation is performed by assessing how well the model performs on the 
training dataset.
<br>
The gemcitabine treated patients from the ESPAC-4 trial was used as an external
validation set.
</p>


<h3> Validation Details </h3>
<h4> Internal Validation </h4>
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
   <td style="text-align:left;"> 0.65 (0.016) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Slope </td>
   <td style="text-align:left;"> 0.999 (0.11) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Somers' D </td>
   <td style="text-align:left;"> 0.30 </td>
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

<br>
<h4> External Validation </h4>
<div class="box">
<p>
The model is validated on an external dataset of GEM treated patients
that took part in the ESPAC-4 study as well as the ESPAC-3 study that
was used to build the model.  <br>
The patients were categorised into 4 risk groups determined by the same
quantiles used for internal validation.
</p>
</div>
<h4> Calibration </h4>
<div class = "row">
  <div class= "6u 12u$(medium)">
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
       <td style="text-align:left;"> 0.59 (0.018) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Slope </td>
       <td style="text-align:left;">  0.290 (0.11) </td>
      </tr>
      <tr>
       <td style="text-align:left;"> Somers' D </td>
       <td style="text-align:left;"> 0.17 </td>
      </tr>
    </tbody>
    </table>
  </div>

<h4> Discrimination </h4>
<div class ="table-wrapper">
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
   <td style="text-align:left;"> Risk Group 2 </td>
   <td style="text-align:left;"> 0.26 (0.16)</td>
   <td style="text-align:left;"> 1.30 (0.95-1.78) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Risk Group 3 </td>
   <td style="text-align:left;"> 0.25 (0.18)</td>
   <td style="text-align:left;"> 1.29 (0.91-1.82) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Risk Group 4 </td>
   <td style="text-align:left;"> 0.83 (0.24)</td>
   <td style="text-align:left;"> 2.3 (1.45-3.65) </td>
  </tr>
</tbody>
</table>      
    
</div>

</div>
  
  	<div class="6u 12u$(medium)">
  	  <!-- Image -->

  Kaplan Meier plot to show survival estimates within each of the 4 risk groups

  <span class="image fit"><img src="{% link assets/images/e4_gem_discrim_ka.png %}" alt="" /></span>


   </div>

  </div>

  </div>




<!------------------------>
<!------------------------>

<div class="box" style="background-color:#614051;">

<h1 id="valid"> Use this model </h1>

<p> 
This model is available to download 
<a href = "https://github.com/richJJackson/pscRepository/tree/main/Models/PDAC/Gem_model"> here </a>
</p>

<p>
Find out more about how models are stored/shared and how you can use them 
<a href= "https://github.com/richJJackson/pscRepository/tree/main/Models"> here </a>
</p>


<p>
This model has been used to compare the combined therapy GemCap against Gem. 
Find out how 
<a href = "https://github.com/richJJackson/pscRepository/blob/main/Applications/Gem_vs_GemCap/gem_vs_gemcap.R"> here </a>
</p>

</div>




<!------------------------>
<!------------------------>

 <div class="box" style="background-color:#8d4e85; ">
<h1 id="valid"> References </h1>

<p> 
Details on the trial which provided the data for this model can be found at: <br>


<a href = "https://jamanetwork.com/journals/jama/fullarticle/186548" > Neoptolemos JP, Stocken DD, Bassi C, et al. Adjuvant Chemotherapy With 
Fluorouracil Plus Folinic Acid vs Gemcitabine Following Pancreatic Cancer 
Resection: A Randomized Controlled Trial. JAMA. 2010;304(10):1073–1081. 
doi:10.1001/jama.2010.1275 <br> </a>
</p>
</div>
