---
layout: post
title:  "How to use Model Estimated Controls"
date: 2025-03-12
categories: [methods]
description: How do Model Estimated Controls work?
---


<body class="fullcontent">
<div class="box">
<div id="quarto-content" class="page-columns page-rows-contents page-layout-article">

<main class="content" id="quarto-document-content">

<header id="title-block-header" class="quarto-title-block default">
<div class="quarto-title">
<h1 class="title">Model Estimated Controls for Survival Outcomes</h1>
</div>



<div class="quarto-title-meta">

    
  
    
  </div>
  


</header>


<section id="introduction" class="level2">
<h2 class="anchored" data-anchor-id="introduction">Introduction</h2>
<p>Model estimated controls (MECs) are statistical models that can be used to assess the efficacy of new therapies without needing to use clinical trials.</p>
<p>MECs can act as counterfactual evidence (a way to predict ‘what if?’- i.e., how would patients respond if they had received a different treatment?)</p>
<p>For survival outcomes, MECs can be used as a control to compare the effect of a control treatment against the effect of an observed experimental treatment on overall survival in patients.</p>
<p>We will implement MECs using the ‘psc’ package which specifically allows for the comparison of patient groups treated with an experimental treatment against a counterfactual model.</p>
<p>Let’s first install and load the ‘psc’ and other necessary packages:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="co"># install.package("psc")</span></span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(psc)</span>
<span id="cb1-3"><a href="#cb1-3" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(survival)</span>
<span id="cb1-4"><a href="#cb1-4" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(ggpubr)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stderr">
<pre><code>Loading required package: ggplot2</code></pre>
</div>
</div>
</section>
<section id="an-example" class="level2">
<h2 class="anchored" data-anchor-id="an-example">An example</h2>
<p>In this example, we will look at survival outcomes in patients with pancreatic cancer from the ESPAC (European Study for Pancreatic Cancer)-4 trial and compare how the survival of patients differs with two different treatments…</p>
<p>We are going to load the model that is going to act as the control treatment (the counterfactual evidence discussed above). This model is a flexible parametric model that was created using the ‘flexsurv’ package.</p>
<p>We can look at the model in more detail</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb3"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="fu">load</span>(<span class="st">"M:/Documents/Projects/Fellowship/modelDevelop/PDAC/Output/Models/flsm.R"</span>)</span>
<span id="cb3-2"><a href="#cb3-2" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb3-3"><a href="#cb3-3" aria-hidden="true" tabindex="-1"></a>flsm<span class="sc">$</span>call</span>
<span id="cb3-4"><a href="#cb3-4" aria-hidden="true" tabindex="-1"></a><span class="fu">class</span>(flsm)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>So now that we have our control treatment, monotherapy gemcitabine (GEM), we will load the ESPAC-4 dataset. ESPAC-4 consists of patients that have been treated with the experimental treatment, adjuvant gemcitabine and capecitabine, GEMCAP.</p>
<p>Our aim is to compare the ESPAC-4 dataset against the GEM model to determine which of the treatments is more effective.</p>
<p>It is important that the variables present in the model are also present in the comparison dataset. It is also important that the time variable in the model’s survival object and in the comparison dataset are encoded as ‘time’.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb4"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a><span class="fu">load</span>(<span class="st">"M:/Documents/Projects/Fellowship/modelDevelop/PDAC/Data/espac4gemcap.R"</span>)</span>
<span id="cb4-2"><a href="#cb4-2" aria-hidden="true" tabindex="-1"></a><span class="fu">head</span>(espac4_gemcap[<span class="dv">1</span><span class="sc">:</span><span class="dv">3</span>,])</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>  ResecM LymphN Diff_Status  treat      time cen PostOpCA199
2      0      1           2 GEMCAP  8.707019   1    1.383791
5      0      0           0 GEMCAP 49.277267   1    0.000000
8      0      1           1 GEMCAP  6.735929   1    1.824549</code></pre>
</div>
<div class="sourceCode cell-code" id="cb6"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb6-1"><a href="#cb6-1" aria-hidden="true" tabindex="-1"></a><span class="fu">head</span>(flsm<span class="sc">$</span>data<span class="sc">$</span>m[<span class="dv">1</span><span class="sc">:</span><span class="dv">3</span>,])</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>   Surv(time, cen) LymphN ResecM Diff_Status PostOpCA199 (weights)
18        11.30092      1      0           0    6.222576         1
19        14.81603      1      0           1    4.394449         1
28        17.18134      1      0           2    9.314430         1</code></pre>
</div>
<div class="sourceCode cell-code" id="cb8"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb8-1"><a href="#cb8-1" aria-hidden="true" tabindex="-1"></a><span class="fu">names</span>(flsm<span class="sc">$</span>data<span class="sc">$</span>m[,<span class="dv">2</span><span class="sc">:</span><span class="dv">5</span>])<span class="sc">%in%</span><span class="fu">names</span>(espac4_gemcap)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] TRUE TRUE TRUE TRUE</code></pre>
</div>
</div>
<p>We should also check the the variables are the correct class…</p>
<p>Categorical variables should be class factor and continuous variables should be numeric.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb10"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb10-1"><a href="#cb10-1" aria-hidden="true" tabindex="-1"></a><span class="fu">str</span>(espac4_gemcap)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>'data.frame':   362 obs. of  7 variables:
 $ ResecM     : Factor w/ 2 levels "0","1": 1 1 1 2 2 2 2 1 2 2 ...
 $ LymphN     : Factor w/ 2 levels "0","1": 2 1 2 1 2 1 2 1 1 1 ...
 $ Diff_Status: Factor w/ 3 levels "0","1","2": 3 1 2 2 1 1 1 2 3 2 ...
 $ treat      : chr  "GEMCAP" "GEMCAP" "GEMCAP" "GEMCAP" ...
 $ time       : num  8.71 49.28 6.74 21.91 23.55 ...
 $ cen        : int  1 1 1 1 1 0 0 1 0 0 ...
 $ PostOpCA199: num  1.38 0 1.82 1.13 5.86 ...</code></pre>
</div>
</div>
</section>
<section id="fit-counterfactual-model" class="level2">
<h2 class="anchored" data-anchor-id="fit-counterfactual-model">Fit counterfactual model :)</h2>
<p>Now that we have checked the correct variables are in our dataset and that they are encoded correctly, we can turn the flexible parametric model into a counterfactual model. We will use the pscfit() function:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb12"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb12-1"><a href="#cb12-1" aria-hidden="true" tabindex="-1"></a>cfm <span class="ot">&lt;-</span> <span class="fu">pscCFM</span>(flsm)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>It is possible to visualise and summarise the data that was used to fit this model with the built in functions within pscCFM():</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb13"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb13-1"><a href="#cb13-1" aria-hidden="true" tabindex="-1"></a>cfm<span class="sc">$</span>datasumm<span class="sc">$</span>summ_Table</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output-display">
<div id="gkvnmhfeaj" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#gkvnmhfeaj table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#gkvnmhfeaj thead, #gkvnmhfeaj tbody, #gkvnmhfeaj tfoot, #gkvnmhfeaj tr, #gkvnmhfeaj td, #gkvnmhfeaj th {
  border-style: none;
}

#gkvnmhfeaj p {
  margin: 0;
  padding: 0;
}

#gkvnmhfeaj .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#gkvnmhfeaj .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#gkvnmhfeaj .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gkvnmhfeaj .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#gkvnmhfeaj .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gkvnmhfeaj .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gkvnmhfeaj .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gkvnmhfeaj .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#gkvnmhfeaj .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#gkvnmhfeaj .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gkvnmhfeaj .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gkvnmhfeaj .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#gkvnmhfeaj .gt_spanner_row {
  border-bottom-style: hidden;
}

#gkvnmhfeaj .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#gkvnmhfeaj .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#gkvnmhfeaj .gt_from_md > :first-child {
  margin-top: 0;
}

#gkvnmhfeaj .gt_from_md > :last-child {
  margin-bottom: 0;
}

#gkvnmhfeaj .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#gkvnmhfeaj .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#gkvnmhfeaj .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#gkvnmhfeaj .gt_row_group_first td {
  border-top-width: 2px;
}

#gkvnmhfeaj .gt_row_group_first th {
  border-top-width: 2px;
}

#gkvnmhfeaj .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gkvnmhfeaj .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#gkvnmhfeaj .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#gkvnmhfeaj .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gkvnmhfeaj .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gkvnmhfeaj .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#gkvnmhfeaj .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#gkvnmhfeaj .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#gkvnmhfeaj .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gkvnmhfeaj .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gkvnmhfeaj .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#gkvnmhfeaj .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gkvnmhfeaj .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#gkvnmhfeaj .gt_left {
  text-align: left;
}

#gkvnmhfeaj .gt_center {
  text-align: center;
}

#gkvnmhfeaj .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#gkvnmhfeaj .gt_font_normal {
  font-weight: normal;
}

#gkvnmhfeaj .gt_font_bold {
  font-weight: bold;
}

#gkvnmhfeaj .gt_font_italic {
  font-style: italic;
}

#gkvnmhfeaj .gt_super {
  font-size: 65%;
}

#gkvnmhfeaj .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#gkvnmhfeaj .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#gkvnmhfeaj .gt_indent_1 {
  text-indent: 5px;
}

#gkvnmhfeaj .gt_indent_2 {
  text-indent: 10px;
}

#gkvnmhfeaj .gt_indent_3 {
  text-indent: 15px;
}

#gkvnmhfeaj .gt_indent_4 {
  text-indent: 20px;
}

#gkvnmhfeaj .gt_indent_5 {
  text-indent: 25px;
}

#gkvnmhfeaj .katex-display {
  display: inline-flex !important;
  margin-bottom: 0.75em !important;
}

#gkvnmhfeaj div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
  height: 0px !important;
}
</style>

<table class="gt_table caption-top table table-sm table-striped small" data-quarto-postprocess="true" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
<colgroup>
<col style="width: 50%">
<col style="width: 50%">
</colgroup>
<thead>
<tr class="gt_col_headings header">
<th id="label" class="gt_col_heading gt_columns_bottom_border gt_left" data-quarto-table-cell-role="th" scope="col"><strong>Characteristic</strong></th>
<th id="stat_0" class="gt_col_heading gt_columns_bottom_border gt_center" data-quarto-table-cell-role="th" scope="col"><strong>N = 339</strong><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height:0;"><sup>1</sup></span></th>
</tr>
</thead>
<tbody class="gt_table_body">
<tr class="odd">
<td class="gt_row gt_left" headers="label">LymphN</td>
<td class="gt_row gt_center" headers="stat_0"><br>
</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;0</td>
<td class="gt_row gt_center" headers="stat_0">97 (29%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;1</td>
<td class="gt_row gt_center" headers="stat_0">242 (71%)</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">ResecM</td>
<td class="gt_row gt_center" headers="stat_0"><br>
</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;0</td>
<td class="gt_row gt_center" headers="stat_0">206 (61%)</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;1</td>
<td class="gt_row gt_center" headers="stat_0">133 (39%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">Diff_Status</td>
<td class="gt_row gt_center" headers="stat_0"><br>
</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;0</td>
<td class="gt_row gt_center" headers="stat_0">85 (25%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;1</td>
<td class="gt_row gt_center" headers="stat_0">214 (63%)</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">&nbsp;&nbsp;&nbsp;&nbsp;2</td>
<td class="gt_row gt_center" headers="stat_0">40 (12%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">PostOpCA199</td>
<td class="gt_row gt_center" headers="stat_0">3.04 (2.30, 4.14)</td>
</tr>
</tbody><tfoot class="gt_footnotes">
<tr class="odd">
<td colspan="2" class="gt_footnote"><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;line-height:0;"><sup>1</sup></span> n (%); Median (Q1, Q3)</td>
</tr>
</tfoot>

</table>

</div>
</div>
<div class="sourceCode cell-code" id="cb14"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb14-1"><a href="#cb14-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggarrange</span>(<span class="at">plotlist =</span> cfm<span class="sc">$</span>datavis, <span class="at">ncol =</span> <span class="dv">2</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$`1`</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="../assets/images/fig_dataSumm_gem-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
<div class="cell-output cell-output-stdout">
<pre><code>
$`2`</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="../assets/images/fig_dataSumm_gem-2.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
<div class="cell-output cell-output-stdout">
<pre><code>
attr(,"class")
[1] "list"      "ggarrange"</code></pre>
</div>
</div>
</section>
<section id="make-comparison" class="level2">
<h2 class="anchored" data-anchor-id="make-comparison">Make comparison!</h2>
<p>We have now created a counterfactual model which can be compared against the ESPAC-4 data cohort. The comparison can be carried out using the pscfcit() function.</p>
<p>Don’t forget that the pscfit() function requires the ‘time’ variables in the data cohort and in the counterfactual model to be encoded as ‘time’ and the event variable to be encoded as ‘cen’. The variable names need to be the exact same.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb18"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb18-1"><a href="#cb18-1" aria-hidden="true" tabindex="-1"></a>psc <span class="ot">&lt;-</span> <span class="fu">pscfit</span>(cfm, espac4_gemcap)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>The output of the comparison can be visualised. The plot below visualises the effect of each treatment on ESPAC-4 patients. The pink line represents the model’s predicted survival estimates (if the ESPAC-4 patients had been treated with GEM) and the orange line represents the data cohort’s observed survival estimates.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb19"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb19-1"><a href="#cb19-1" aria-hidden="true" tabindex="-1"></a><span class="fu">plot</span>(psc)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="../assets/images/plot_psc_surv_espac-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>The summary of the model can be obtained using the generic summary() function to show the posterior density. The posterior estimates of the deviance information criterion (DIC) and the efficacy parameter, <span class="math inline">\(\beta\)</span>, are calculated and shown.</p>
<p><span class="math inline">\(\beta\)</span> is a measurement of the distance between the observed data and the model estimate. The 2.5 and 97.5% quantiles are also given. The odds ratio comparing the experimental treatment to the control can be calculated as exp(<span class="math inline">\(\beta\)</span>), in this case exp(-0.466452).</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb20"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb20-1"><a href="#cb20-1" aria-hidden="true" tabindex="-1"></a><span class="fu">summary</span>(psc)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>Summary: 
 
362 observations selected from the data cohort for comparison 
CFM of type flexsurvreg identified  
linear predictor succesfully obtained with median: 
 trt: 0.812
Average expected response: 
 trt: 28.337
Average observed response: 31.67 

Counterfactual Model (CFM): 
A model of class 'flexsurvreg' 
 Fit with 5 internal knots

Formula: 
Surv(time, cen) ~ LymphN + ResecM + Diff_Status + PostOpCA199
&lt;environment: 0x000002bd2cc745b0&gt;

Call:
 CFM model + beta

Coefficients:
      median     2.5%       97.5%      Pr(x&lt;0)    Pr(x&gt;0)  
beta    -0.4654    -0.5980    -0.3374     1.0000     0.0000
DIC   1321.9110  1298.1965  1356.4793         NA         NA</code></pre>
</div>
</div>
<p>We can extract the posterior distribution of the ‘psc’ and can view its autocorrelation and trace</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb22"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb22-1"><a href="#cb22-1" aria-hidden="true" tabindex="-1"></a>posterior <span class="ot">&lt;-</span> psc<span class="sc">$</span>posterior</span>
<span id="cb22-2"><a href="#cb22-2" aria-hidden="true" tabindex="-1"></a><span class="fu">head</span>(posterior[<span class="dv">1</span><span class="sc">:</span><span class="dv">3</span>,])</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>     gamma0   gamma1    gamma2     gamma3     gamma4     gamma5     gamma6
1 -11.38080 3.835982 1.2911623 -1.3176560  1.1190182 -0.8876277  0.3372484
2 -12.67794 4.229261 0.7241809  1.9009958 -4.7052873  3.8123302 -1.1898916
3 -10.31870 3.250702 0.5695342 -0.6962649  0.7173846 -0.3868049  0.1740992
    LymphN1    ResecM1 Diff_Status1 Diff_Status2 PostOpCA199       beta
1 0.4876152 0.18053219   -0.4160534   -0.5897823   0.2671471 -0.4552224
2 0.9674277 0.07947108   -0.3650303   -0.4154747   0.2506839 -0.4552224
3 0.6713722 0.24288970   -0.5539652   -0.6549099   0.2414302 -0.5074574
       DIC
1       NA
2 1306.578
3 1313.935</code></pre>
</div>
<div class="sourceCode cell-code" id="cb24"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb24-1"><a href="#cb24-1" aria-hidden="true" tabindex="-1"></a><span class="co"># autocorrelation</span></span>
<span id="cb24-2"><a href="#cb24-2" aria-hidden="true" tabindex="-1"></a><span class="fu">acf</span>(posterior<span class="sc">$</span>beta)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="../assets/images/posterior_psc_gem-1.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
<div class="sourceCode cell-code" id="cb25"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb25-1"><a href="#cb25-1" aria-hidden="true" tabindex="-1"></a><span class="co"># trace</span></span>
<span id="cb25-2"><a href="#cb25-2" aria-hidden="true" tabindex="-1"></a><span class="fu">plot</span>(posterior<span class="sc">$</span>beta, <span class="at">type =</span> <span class="st">'s'</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img src="../assets/images/posterior_psc_gem-2.png" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
<section id="take-homes" class="level2">
<h2 class="anchored" data-anchor-id="take-homes">Take homes</h2>
<ul>
<li><p>Check your data is formatted correctly (variable names should exactly match that of the model’s)</p></li>
<li></li>
</ul>
</section>

</main>
<!-- /main column -->
<script id="quarto-html-after-body" type="application/javascript">
window.document.addEventListener("DOMContentLoaded", function (event) {
  const toggleBodyColorMode = (bsSheetEl) => {
    const mode = bsSheetEl.getAttribute("data-mode");
    const bodyEl = window.document.querySelector("body");
    if (mode === "dark") {
      bodyEl.classList.add("quarto-dark");
      bodyEl.classList.remove("quarto-light");
    } else {
      bodyEl.classList.add("quarto-light");
      bodyEl.classList.remove("quarto-dark");
    }
  }
  const toggleBodyColorPrimary = () => {
    const bsSheetEl = window.document.querySelector("link#quarto-bootstrap");
    if (bsSheetEl) {
      toggleBodyColorMode(bsSheetEl);
    }
  }
  toggleBodyColorPrimary();  
  const icon = "";
  const anchorJS = new window.AnchorJS();
  anchorJS.options = {
    placement: 'right',
    icon: icon
  };
  anchorJS.add('.anchored');
  const isCodeAnnotation = (el) => {
    for (const clz of el.classList) {
      if (clz.startsWith('code-annotation-')) {                     
        return true;
      }
    }
    return false;
  }
  const onCopySuccess = function(e) {
    // button target
    const button = e.trigger;
    // don't keep focus
    button.blur();
    // flash "checked"
    button.classList.add('code-copy-button-checked');
    var currentTitle = button.getAttribute("title");
    button.setAttribute("title", "Copied!");
    let tooltip;
    if (window.bootstrap) {
      button.setAttribute("data-bs-toggle", "tooltip");
      button.setAttribute("data-bs-placement", "left");
      button.setAttribute("data-bs-title", "Copied!");
      tooltip = new bootstrap.Tooltip(button, 
        { trigger: "manual", 
          customClass: "code-copy-button-tooltip",
          offset: [0, -8]});
      tooltip.show();    
    }
    setTimeout(function() {
      if (tooltip) {
        tooltip.hide();
        button.removeAttribute("data-bs-title");
        button.removeAttribute("data-bs-toggle");
        button.removeAttribute("data-bs-placement");
      }
      button.setAttribute("title", currentTitle);
      button.classList.remove('code-copy-button-checked');
    }, 1000);
    // clear code selection
    e.clearSelection();
  }
  const getTextToCopy = function(trigger) {
      const codeEl = trigger.previousElementSibling.cloneNode(true);
      for (const childEl of codeEl.children) {
        if (isCodeAnnotation(childEl)) {
          childEl.remove();
        }
      }
      return codeEl.innerText;
  }
  const clipboard = new window.ClipboardJS('.code-copy-button:not([data-in-quarto-modal])', {
    text: getTextToCopy
  });
  clipboard.on('success', onCopySuccess);
  if (window.document.getElementById('quarto-embedded-source-code-modal')) {
    const clipboardModal = new window.ClipboardJS('.code-copy-button[data-in-quarto-modal]', {
      text: getTextToCopy,
      container: window.document.getElementById('quarto-embedded-source-code-modal')
    });
    clipboardModal.on('success', onCopySuccess);
  }
    var localhostRegex = new RegExp(/^(?:http|https):\/\/localhost\:?[0-9]*\//);
    var mailtoRegex = new RegExp(/^mailto:/);
      var filterRegex = new RegExp('/' + window.location.host + '/');
    var isInternal = (href) => {
        return filterRegex.test(href) || localhostRegex.test(href) || mailtoRegex.test(href);
    }
    // Inspect non-navigation links and adorn them if external
 	var links = window.document.querySelectorAll('a[href]:not(.nav-link):not(.navbar-brand):not(.toc-action):not(.sidebar-link):not(.sidebar-item-toggle):not(.pagination-link):not(.no-external):not([aria-hidden]):not(.dropdown-item):not(.quarto-navigation-tool):not(.about-link)');
    for (var i=0; i<links.length; i++) {
      const link = links[i];
      if (!isInternal(link.href)) {
        // undo the damage that might have been done by quarto-nav.js in the case of
        // links that we want to consider external
        if (link.dataset.originalHref !== undefined) {
          link.href = link.dataset.originalHref;
        }
      }
    }
  function tippyHover(el, contentFn, onTriggerFn, onUntriggerFn) {
    const config = {
      allowHTML: true,
      maxWidth: 500,
      delay: 100,
      arrow: false,
      appendTo: function(el) {
          return el.parentElement;
      },
      interactive: true,
      interactiveBorder: 10,
      theme: 'quarto',
      placement: 'bottom-start',
    };
    if (contentFn) {
      config.content = contentFn;
    }
    if (onTriggerFn) {
      config.onTrigger = onTriggerFn;
    }
    if (onUntriggerFn) {
      config.onUntrigger = onUntriggerFn;
    }
    window.tippy(el, config); 
  }
  const noterefs = window.document.querySelectorAll('a[role="doc-noteref"]');
  for (var i=0; i<noterefs.length; i++) {
    const ref = noterefs[i];
    tippyHover(ref, function() {
      // use id or data attribute instead here
      let href = ref.getAttribute('data-footnote-href') || ref.getAttribute('href');
      try { href = new URL(href).hash; } catch {}
      const id = href.replace(/^#\/?/, "");
      const note = window.document.getElementById(id);
      if (note) {
        return note.innerHTML;
      } else {
        return "";
      }
    });
  }
  const xrefs = window.document.querySelectorAll('a.quarto-xref');
  const processXRef = (id, note) => {
    // Strip column container classes
    const stripColumnClz = (el) => {
      el.classList.remove("page-full", "page-columns");
      if (el.children) {
        for (const child of el.children) {
          stripColumnClz(child);
        }
      }
    }
    stripColumnClz(note)
    if (id === null || id.startsWith('sec-')) {
      // Special case sections, only their first couple elements
      const container = document.createElement("div");
      if (note.children && note.children.length > 2) {
        container.appendChild(note.children[0].cloneNode(true));
        for (let i = 1; i < note.children.length; i++) {
          const child = note.children[i];
          if (child.tagName === "P" && child.innerText === "") {
            continue;
          } else {
            container.appendChild(child.cloneNode(true));
            break;
          }
        }
        if (window.Quarto?.typesetMath) {
          window.Quarto.typesetMath(container);
        }
        return container.innerHTML
      } else {
        if (window.Quarto?.typesetMath) {
          window.Quarto.typesetMath(note);
        }
        return note.innerHTML;
      }
    } else {
      // Remove any anchor links if they are present
      const anchorLink = note.querySelector('a.anchorjs-link');
      if (anchorLink) {
        anchorLink.remove();
      }
      if (window.Quarto?.typesetMath) {
        window.Quarto.typesetMath(note);
      }
      if (note.classList.contains("callout")) {
        return note.outerHTML;
      } else {
        return note.innerHTML;
      }
    }
  }
  for (var i=0; i<xrefs.length; i++) {
    const xref = xrefs[i];
    tippyHover(xref, undefined, function(instance) {
      instance.disable();
      let url = xref.getAttribute('href');
      let hash = undefined; 
      if (url.startsWith('#')) {
        hash = url;
      } else {
        try { hash = new URL(url).hash; } catch {}
      }
      if (hash) {
        const id = hash.replace(/^#\/?/, "");
        const note = window.document.getElementById(id);
        if (note !== null) {
          try {
            const html = processXRef(id, note.cloneNode(true));
            instance.setContent(html);
          } finally {
            instance.enable();
            instance.show();
          }
        } else {
          // See if we can fetch this
          fetch(url.split('#')[0])
          .then(res => res.text())
          .then(html => {
            const parser = new DOMParser();
            const htmlDoc = parser.parseFromString(html, "text/html");
            const note = htmlDoc.getElementById(id);
            if (note !== null) {
              const html = processXRef(id, note);
              instance.setContent(html);
            } 
          }).finally(() => {
            instance.enable();
            instance.show();
          });
        }
      } else {
        // See if we can fetch a full url (with no hash to target)
        // This is a special case and we should probably do some content thinning / targeting
        fetch(url)
        .then(res => res.text())
        .then(html => {
          const parser = new DOMParser();
          const htmlDoc = parser.parseFromString(html, "text/html");
          const note = htmlDoc.querySelector('main.content');
          if (note !== null) {
            // This should only happen for chapter cross references
            // (since there is no id in the URL)
            // remove the first header
            if (note.children.length > 0 && note.children[0].tagName === "HEADER") {
              note.children[0].remove();
            }
            const html = processXRef(null, note);
            instance.setContent(html);
          } 
        }).finally(() => {
          instance.enable();
          instance.show();
        });
      }
    }, function(instance) {
    });
  }
      let selectedAnnoteEl;
      const selectorForAnnotation = ( cell, annotation) => {
        let cellAttr = 'data-code-cell="' + cell + '"';
        let lineAttr = 'data-code-annotation="' +  annotation + '"';
        const selector = 'span[' + cellAttr + '][' + lineAttr + ']';
        return selector;
      }
      const selectCodeLines = (annoteEl) => {
        const doc = window.document;
        const targetCell = annoteEl.getAttribute("data-target-cell");
        const targetAnnotation = annoteEl.getAttribute("data-target-annotation");
        const annoteSpan = window.document.querySelector(selectorForAnnotation(targetCell, targetAnnotation));
        const lines = annoteSpan.getAttribute("data-code-lines").split(",");
        const lineIds = lines.map((line) => {
          return targetCell + "-" + line;
        })
        let top = null;
        let height = null;
        let parent = null;
        if (lineIds.length > 0) {
            //compute the position of the single el (top and bottom and make a div)
            const el = window.document.getElementById(lineIds[0]);
            top = el.offsetTop;
            height = el.offsetHeight;
            parent = el.parentElement.parentElement;
          if (lineIds.length > 1) {
            const lastEl = window.document.getElementById(lineIds[lineIds.length - 1]);
            const bottom = lastEl.offsetTop + lastEl.offsetHeight;
            height = bottom - top;
          }
          if (top !== null && height !== null && parent !== null) {
            // cook up a div (if necessary) and position it 
            let div = window.document.getElementById("code-annotation-line-highlight");
            if (div === null) {
              div = window.document.createElement("div");
              div.setAttribute("id", "code-annotation-line-highlight");
              div.style.position = 'absolute';
              parent.appendChild(div);
            }
            div.style.top = top - 2 + "px";
            div.style.height = height + 4 + "px";
            div.style.left = 0;
            let gutterDiv = window.document.getElementById("code-annotation-line-highlight-gutter");
            if (gutterDiv === null) {
              gutterDiv = window.document.createElement("div");
              gutterDiv.setAttribute("id", "code-annotation-line-highlight-gutter");
              gutterDiv.style.position = 'absolute';
              const codeCell = window.document.getElementById(targetCell);
              const gutter = codeCell.querySelector('.code-annotation-gutter');
              gutter.appendChild(gutterDiv);
            }
            gutterDiv.style.top = top - 2 + "px";
            gutterDiv.style.height = height + 4 + "px";
          }
          selectedAnnoteEl = annoteEl;
        }
      };
      const unselectCodeLines = () => {
        const elementsIds = ["code-annotation-line-highlight", "code-annotation-line-highlight-gutter"];
        elementsIds.forEach((elId) => {
          const div = window.document.getElementById(elId);
          if (div) {
            div.remove();
          }
        });
        selectedAnnoteEl = undefined;
      };
        // Handle positioning of the toggle
    window.addEventListener(
      "resize",
      throttle(() => {
        elRect = undefined;
        if (selectedAnnoteEl) {
          selectCodeLines(selectedAnnoteEl);
        }
      }, 10)
    );
    function throttle(fn, ms) {
    let throttle = false;
    let timer;
      return (...args) => {
        if(!throttle) { // first call gets through
            fn.apply(this, args);
            throttle = true;
        } else { // all the others get throttled
            if(timer) clearTimeout(timer); // cancel #2
            timer = setTimeout(() => {
              fn.apply(this, args);
              timer = throttle = false;
            }, ms);
        }
      };
    }
      // Attach click handler to the DT
      const annoteDls = window.document.querySelectorAll('dt[data-target-cell]');
      for (const annoteDlNode of annoteDls) {
        annoteDlNode.addEventListener('click', (event) => {
          const clickedEl = event.target;
          if (clickedEl !== selectedAnnoteEl) {
            unselectCodeLines();
            const activeEl = window.document.querySelector('dt[data-target-cell].code-annotation-active');
            if (activeEl) {
              activeEl.classList.remove('code-annotation-active');
            }
            selectCodeLines(clickedEl);
            clickedEl.classList.add('code-annotation-active');
          } else {
            // Unselect the line
            unselectCodeLines();
            clickedEl.classList.remove('code-annotation-active');
          }
        });
      }
  const findCites = (el) => {
    const parentEl = el.parentElement;
    if (parentEl) {
      const cites = parentEl.dataset.cites;
      if (cites) {
        return {
          el,
          cites: cites.split(' ')
        };
      } else {
        return findCites(el.parentElement)
      }
    } else {
      return undefined;
    }
  };
  var bibliorefs = window.document.querySelectorAll('a[role="doc-biblioref"]');
  for (var i=0; i<bibliorefs.length; i++) {
    const ref = bibliorefs[i];
    const citeInfo = findCites(ref);
    if (citeInfo) {
      tippyHover(citeInfo.el, function() {
        var popup = window.document.createElement('div');
        citeInfo.cites.forEach(function(cite) {
          var citeDiv = window.document.createElement('div');
          citeDiv.classList.add('hanging-indent');
          citeDiv.classList.add('csl-entry');
          var biblioDiv = window.document.getElementById('ref-' + cite);
          if (biblioDiv) {
            citeDiv.innerHTML = biblioDiv.innerHTML;
          }
          popup.appendChild(citeDiv);
        });
        return popup.innerHTML;
      });
    }
  }
});
</script>
</div> <!-- /content -->
</div>



</body>
