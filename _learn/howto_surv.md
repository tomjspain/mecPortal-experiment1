---
layout: post
title:  "How to use Model Estimated Controls"
date: 2025-03-12
categories: [methods]
description: How do Model Estimated Controls work?
---



<body class="fullcontent">

<div id="quarto-content" class="page-columns page-rows-contents page-layout-article">

<main class="content" id="quarto-document-content">

<header id="title-block-header" class="quarto-title-block default">
<div class="quarto-title">
<h1 class="title">Model Estimated Controls for Survival Outcomes</h1>
</div>



<div class="quarto-title-meta">

    
  
    
  </div>
  


</header>

<div class="box" style = "background-color:#86608e;">
<section id="introduction" class="level2">
<h2 class="anchored" data-anchor-id="introduction">Introduction</h2>
<p>For survival outcomes, MECs can be used as a control to compare the effect of a control treatment against the effect of an observed experimental treatment on overall survival in patients.</p>
<p>We will implement MECs using the ‘psc’ package which specifically allows for the comparison of patient groups treated with an experimental treatment against a counterfactual model (CFM).</p>
<p>Load necessary packages:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(psc)</span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(survival)</span>
<span id="cb1-3"><a href="#cb1-3" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(ggpubr)</span></code></pre></div>
</div>
</section>
</div>

<div class="box" style="background-color:#8a496b;">
<section id="an-example" class="level2">
<h2 class="anchored" data-anchor-id="an-example">An example</h2>
<p>In this example, we will look at survival outcomes in patients with pancreatic cancer from the ESPAC (European Study for Pancreatic Cancer)-4 trial and compare how the survival of patients differs with two different treatments:<a href="../applications/gem_gemcap_pdac.html" > GEM Vs. GEMCAP… </a></p>
<p>Load the model that will act as the control treatment (CFM). This model is a flexible parametric model.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb2"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb2-1"><a href="#cb2-1" aria-hidden="true" tabindex="-1"></a><span class="fu">load</span>(<span class="st">&quot;flsm.R&quot;</span>)</span></code></pre></div>
</div>
<p>Now that we have our control treatment, monotherapy gemcitabine (GEM), we will load the ESPAC-4 dataset. ESPAC-4 consists of patients that have been treated with the experimental treatment, adjuvant gemcitabine and capecitabine, GEMCAP.</p>
<p>Our aim is to compare the patients treated with GEMCAP in the ESPAC-4 dataset against the GEM model to determine which of the treatments is more effective.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb3"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="fu">load</span>(<span class="st">&quot;espac4gemcap.R&quot;</span>)</span></code></pre></div>
</div>
</section>
</div>
<div class="box" style="background-color:#5d3954;">
<section id="fit-counterfactual-model" class="level2">
<h2 class="anchored" data-anchor-id="fit-counterfactual-model">Fit counterfactual model :)</h2>
<p>We can turn the flexible parametric model into a CFM using the pscCFM() function:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb4"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a>cfm <span class="ot">&lt;-</span> <span class="fu">pscCFM</span>(flsm)</span></code></pre></div>
</div>
<p>It is possible to visualise and summarise the data that was used to fit this model with the built in functions within pscCFM():</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb5"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb5-1"><a href="#cb5-1" aria-hidden="true" tabindex="-1"></a>cfm<span class="sc">$</span>datasumm<span class="sc">$</span>summ_Table</span></code></pre></div>
<div class="cell-output-display">
<div id="xlusyojlhm" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#xlusyojlhm table {
font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
}
#xlusyojlhm thead, #xlusyojlhm tbody, #xlusyojlhm tfoot, #xlusyojlhm tr, #xlusyojlhm td, #xlusyojlhm th {
border-style: none;
}
#xlusyojlhm p {
margin: 0;
padding: 0;
}
#xlusyojlhm .gt_table {
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
#xlusyojlhm .gt_caption {
padding-top: 4px;
padding-bottom: 4px;
}
#xlusyojlhm .gt_title {
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
#xlusyojlhm .gt_subtitle {
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
#xlusyojlhm .gt_heading {
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
#xlusyojlhm .gt_bottom_border {
border-bottom-style: solid;
border-bottom-width: 2px;
border-bottom-color: #D3D3D3;
}
#xlusyojlhm .gt_col_headings {
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
#xlusyojlhm .gt_col_heading {
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
#xlusyojlhm .gt_column_spanner_outer {
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
#xlusyojlhm .gt_column_spanner_outer:first-child {
padding-left: 0;
}
#xlusyojlhm .gt_column_spanner_outer:last-child {
padding-right: 0;
}
#xlusyojlhm .gt_column_spanner {
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
#xlusyojlhm .gt_spanner_row {
border-bottom-style: hidden;
}
#xlusyojlhm .gt_group_heading {
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
#xlusyojlhm .gt_empty_group_heading {
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
#xlusyojlhm .gt_from_md > :first-child {
margin-top: 0;
}
#xlusyojlhm .gt_from_md > :last-child {
margin-bottom: 0;
}
#xlusyojlhm .gt_row {
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
#xlusyojlhm .gt_stub {
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
#xlusyojlhm .gt_stub_row_group {
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
#xlusyojlhm .gt_row_group_first td {
border-top-width: 2px;
}
#xlusyojlhm .gt_row_group_first th {
border-top-width: 2px;
}
#xlusyojlhm .gt_summary_row {
color: #333333;
background-color: #FFFFFF;
text-transform: inherit;
padding-top: 8px;
padding-bottom: 8px;
padding-left: 5px;
padding-right: 5px;
}
#xlusyojlhm .gt_first_summary_row {
border-top-style: solid;
border-top-color: #D3D3D3;
}
#xlusyojlhm .gt_first_summary_row.thick {
border-top-width: 2px;
}
#xlusyojlhm .gt_last_summary_row {
padding-top: 8px;
padding-bottom: 8px;
padding-left: 5px;
padding-right: 5px;
border-bottom-style: solid;
border-bottom-width: 2px;
border-bottom-color: #D3D3D3;
}
#xlusyojlhm .gt_grand_summary_row {
color: #333333;
background-color: #FFFFFF;
text-transform: inherit;
padding-top: 8px;
padding-bottom: 8px;
padding-left: 5px;
padding-right: 5px;
}
#xlusyojlhm .gt_first_grand_summary_row {
padding-top: 8px;
padding-bottom: 8px;
padding-left: 5px;
padding-right: 5px;
border-top-style: double;
border-top-width: 6px;
border-top-color: #D3D3D3;
}
#xlusyojlhm .gt_last_grand_summary_row_top {
padding-top: 8px;
padding-bottom: 8px;
padding-left: 5px;
padding-right: 5px;
border-bottom-style: double;
border-bottom-width: 6px;
border-bottom-color: #D3D3D3;
}
#xlusyojlhm .gt_striped {
background-color: rgba(128, 128, 128, 0.05);
}
#xlusyojlhm .gt_table_body {
border-top-style: solid;
border-top-width: 2px;
border-top-color: #D3D3D3;
border-bottom-style: solid;
border-bottom-width: 2px;
border-bottom-color: #D3D3D3;
}
#xlusyojlhm .gt_footnotes {
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
#xlusyojlhm .gt_footnote {
margin: 0px;
font-size: 90%;
padding-top: 4px;
padding-bottom: 4px;
padding-left: 5px;
padding-right: 5px;
}
#xlusyojlhm .gt_sourcenotes {
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
#xlusyojlhm .gt_sourcenote {
font-size: 90%;
padding-top: 4px;
padding-bottom: 4px;
padding-left: 5px;
padding-right: 5px;
}
#xlusyojlhm .gt_left {
text-align: left;
}
#xlusyojlhm .gt_center {
text-align: center;
}
#xlusyojlhm .gt_right {
text-align: right;
font-variant-numeric: tabular-nums;
}
#xlusyojlhm .gt_font_normal {
font-weight: normal;
}
#xlusyojlhm .gt_font_bold {
font-weight: bold;
}
#xlusyojlhm .gt_font_italic {
font-style: italic;
}
#xlusyojlhm .gt_super {
font-size: 65%;
}
#xlusyojlhm .gt_footnote_marks {
font-size: 75%;
vertical-align: 0.4em;
position: initial;
}
#xlusyojlhm .gt_asterisk {
font-size: 100%;
vertical-align: 0;
}
#xlusyojlhm .gt_indent_1 {
text-indent: 5px;
}
#xlusyojlhm .gt_indent_2 {
text-indent: 10px;
}
#xlusyojlhm .gt_indent_3 {
text-indent: 15px;
}
#xlusyojlhm .gt_indent_4 {
text-indent: 20px;
}
#xlusyojlhm .gt_indent_5 {
text-indent: 25px;
}
#xlusyojlhm .katex-display {
display: inline-flex !important;
margin-bottom: 0.75em !important;
}
#xlusyojlhm div.Reactable > div.rt-table > div.rt-thead > div.rt-tr.rt-tr-group-header > div.rt-th-group:after {
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
<td class="gt_row gt_left" headers="label">    0</td>
<td class="gt_row gt_center" headers="stat_0">97 (29%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">    1</td>
<td class="gt_row gt_center" headers="stat_0">242 (71%)</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">ResecM</td>
<td class="gt_row gt_center" headers="stat_0"><br>
</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">    0</td>
<td class="gt_row gt_center" headers="stat_0">206 (61%)</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">    1</td>
<td class="gt_row gt_center" headers="stat_0">133 (39%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">Diff_Status</td>
<td class="gt_row gt_center" headers="stat_0"><br>
</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">    0</td>
<td class="gt_row gt_center" headers="stat_0">85 (25%)</td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="label">    1</td>
<td class="gt_row gt_center" headers="stat_0">214 (63%)</td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="label">    2</td>
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
<div class="sourceCode cell-code" id="cb6"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb6-1"><a href="#cb6-1" aria-hidden="true" tabindex="-1"></a><span class="fu">ggarrange</span>(<span class="at">plotlist =</span> cfm<span class="sc">$</span>datavis, <span class="at">ncol =</span> <span class="dv">2</span>)</span></code></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$`1`</code></pre>
</div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img role="img" src="data:image/png;base64,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OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1KfTbZkUbs2AA5o2IZ+OhtSn022ZFG7NgAOaNiGfjobUp9NtmRRuzYADmjYhn46G1Kf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" class="img-fluid figure-img" width="672"></p>
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
<p><img role="img" src="data:image/png;base64,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" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
<div class="cell-output cell-output-stdout">
<pre><code>
attr(,&quot;class&quot;)
[1] &quot;list&quot;      &quot;ggarrange&quot;</code></pre>
</div>
</div>
</section>
</div>
<div class="box" style="background-color:#915c83;">
<section id="make-comparison" class="level2">
<h2 class="anchored" data-anchor-id="make-comparison">Make comparison!</h2>
<p>The CFM can be compared against the ESPAC-4 data cohort. The comparison will be carried out using the pscfcit() function.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb10"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb10-1"><a href="#cb10-1" aria-hidden="true" tabindex="-1"></a>psc <span class="ot">&lt;-</span> <span class="fu">pscfit</span>(cfm, espac4_gemcap)</span></code></pre></div>
</div>
<p>The plot below visualises the effect of each treatment on ESPAC-4 patients. The pink line represents the model’s predicted survival estimates (if the ESPAC-4 patients had been treated with GEM) and the orange line represents the data cohort’s observed survival estimates.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb11"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb11-1"><a href="#cb11-1" aria-hidden="true" tabindex="-1"></a><span class="fu">plot</span>(psc)</span></code></pre></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img role="img" src="data:image/png;base64,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" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
<p>The summary of the model can be obtained using the generic summary() function to show the posterior density. The posterior estimates of the deviance information criterion (DIC) and the efficacy parameter, <span class="math inline">&beta;</span>, are calculated and shown.</p>
<p><span class="math inline">&beta;</span> is a measurement of the distance between the observed data and the model estimate. The 2.5 and 97.5% quantiles are also given. The odds ratio comparing the experimental treatment to the control can be calculated as exp(<span class="math inline">&beta;</span>), in this case exp(-0.466452).</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb12"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb12-1"><a href="#cb12-1" aria-hidden="true" tabindex="-1"></a><span class="fu">summary</span>(psc)</span></code></pre></div>
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
A model of class &#39;flexsurvreg&#39; 
 Fit with 5 internal knots

Formula: 
Surv(time, cen) ~ LymphN + ResecM + Diff_Status + PostOpCA199
&lt;environment: 0x0000016a1fa155b0&gt;

Call:
 CFM model + beta

Coefficients:
      median     2.5%       97.5%      Pr(x&lt;0)    Pr(x&gt;0)  
beta    -0.4627    -0.5988    -0.3378     1.0000     0.0000
DIC   1320.7933  1297.5917  1355.0851         NA         NA</code></pre>
</div>
</div>
<p>We can extract the posterior distribution of the ‘psc’ and can view its autocorrelation and trace</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb14"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb14-1"><a href="#cb14-1" aria-hidden="true" tabindex="-1"></a>posterior <span class="ot">&lt;-</span> psc<span class="sc">$</span>posterior</span>
<span id="cb14-2"><a href="#cb14-2" aria-hidden="true" tabindex="-1"></a><span class="fu">head</span>(posterior[<span class="dv">1</span><span class="sc">:</span><span class="dv">3</span>,])</span></code></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>     gamma0   gamma1   gamma2    gamma3    gamma4     gamma5     gamma6
1 -11.38080 3.835982 1.291162 -1.317656 1.1190182 -0.8876277  0.3372484
2 -13.30464 4.898178 4.394070 -5.271692 1.6488526  0.7120773 -0.6273199
3 -10.92023 3.903896 2.945046 -2.635881 0.5773368 -0.8796604  0.8259487
    LymphN1     ResecM1 Diff_Status1 Diff_Status2 PostOpCA199       beta
1 0.4876152  0.18053219   -0.4160534   -0.5897823   0.2671471 -0.4552224
2 0.6315325 -0.08449907   -0.5292838   -0.2732867   0.2633989 -0.4552224
3 0.7238781  0.08044458   -0.3553484   -0.5314689   0.2202701 -0.4552224
       DIC
1       NA
2 1310.674
3 1314.744</code></pre>
</div>
<div class="sourceCode cell-code" id="cb16"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb16-1"><a href="#cb16-1" aria-hidden="true" tabindex="-1"></a><span class="co"># autocorrelation</span></span>
<span id="cb16-2"><a href="#cb16-2" aria-hidden="true" tabindex="-1"></a><span class="fu">acf</span>(posterior<span class="sc">$</span>beta)</span></code></pre></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img role="img" src="data:image/png;base64,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" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
<div class="sourceCode cell-code" id="cb17"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb17-1"><a href="#cb17-1" aria-hidden="true" tabindex="-1"></a><span class="co"># trace</span></span>
<span id="cb17-2"><a href="#cb17-2" aria-hidden="true" tabindex="-1"></a><span class="fu">plot</span>(posterior<span class="sc">$</span>beta, <span class="at">type =</span> <span class="st">&#39;s&#39;</span>)</span></code></pre></div>
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img role="img" src="data:image/png;base64,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" class="img-fluid figure-img" width="672"></p>
</figure>
</div>
</div>
</div>
</section>
</div>

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

<div class="box" style= "background-color: #58427c ;">
<section id="more-details" class="level2">
<h2 class="anchored" data-anchor-id="more-details">More details!</h2>
<li>More details on GEM model vs GEMCAP patients can be found <a href="../applications/gem_gemcap_pdac.html"> here. </a></li>
<li> <a href="https://github.com/kusqaum/PDAC/blob/main/howto_surv_k.qmd" >Code for tutorial is available </a></li>

</section>
</div>

</body>