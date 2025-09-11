---
layout: post
title:  "Package for Model Estimated Controls"
date: 2025-03-12
categories: [methods]
description: Learn more about the package for MECs
---

<div class="box">
<body class="fullcontent">

<div id="quarto-content" class="page-columns page-rows-contents page-layout-article">

<main class="content" id="quarto-document-content">




<!-- README.md is generated from README.Rmd. Please edit that file -->
<section id="psc" class="level1">
<h1>psc</h1>
<!-- badges: start -->
<p><a href="https://github.com/richJJackson/psc/actions/workflows/R-CMD-check.yaml"><img role="img" aria-label="R-CMD-check" src="data:image/svg+xml; charset=utf-8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNzUiIGhlaWdodD0iMjAiPgogIDx0aXRsZT5SLUNNRC1jaGVjay55YW1sIC0gZmFpbGluZzwvdGl0bGU+CiAgPGRlZnM+CiAgICA8bGluZWFyR3JhZGllbnQgaWQ9IndvcmtmbG93LWZpbGwiIHgxPSI1MCUiIHkxPSIwJSIgeDI9IjUwJSIgeTI9IjEwMCUiPgogICAgICA8c3RvcCBzdG9wLWNvbG9yPSIjNDQ0RDU2IiBvZmZzZXQ9IjAlIj48L3N0b3A+CiAgICAgIDxzdG9wIHN0b3AtY29sb3I9IiMyNDI5MkUiIG9mZnNldD0iMTAwJSI+PC9zdG9wPgogICAgPC9saW5lYXJHcmFkaWVudD4KICAgIDxsaW5lYXJHcmFkaWVudCBpZD0ic3RhdGUtZmlsbCIgeDE9IjUwJSIgeTE9IjAlIiB4Mj0iNTAlIiB5Mj0iMTAwJSI+CiAgICAgIDxzdG9wIHN0b3AtY29sb3I9IiNENzNBNDkiIG9mZnNldD0iMCUiPjwvc3RvcD4KICAgICAgPHN0b3Agc3RvcC1jb2xvcj0iI0NCMjQzMSIgb2Zmc2V0PSIxMDAlIj48L3N0b3A+CiAgICA8L2xpbmVhckdyYWRpZW50PgogIDwvZGVmcz4KICA8ZyBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPgogICAgPGcgZm9udC1mYW1pbHk9IiYjMzk7RGVqYVZ1IFNhbnMmIzM5OyxWZXJkYW5hLEdlbmV2YSxzYW5zLXNlcmlmIiBmb250LXNpemU9IjExIj4KICAgICAgPHBhdGggaWQ9IndvcmtmbG93LWJnIiBkPSJNMCwzIEMwLDEuMzQzMSAxLjM1NTIsMCAzLjAyNzAyNzAzLDAgTDEzMiwwIEwxMzIsMjAgTDMuMDI3MDI3MDMsMjAgQzEuMzU1MiwyMCAwLDE4LjY1NjkgMCwxNyBMMCwzIFoiIGZpbGw9InVybCgjd29ya2Zsb3ctZmlsbCkiIGZpbGwtcnVsZT0ibm9uemVybyI+PC9wYXRoPgogICAgICA8dGV4dCBmaWxsPSIjMDEwMTAxIiBmaWxsLW9wYWNpdHk9Ii4zIj4KICAgICAgICA8dHNwYW4geD0iMjIuMTk4MTk4MiIgeT0iMTUiIGFyaWEtaGlkZGVuPSJ0cnVlIj5SLUNNRC1jaGVjay55YW1sPC90c3Bhbj4KICAgICAgPC90ZXh0PgogICAgICA8dGV4dCBmaWxsPSIjRkZGRkZGIj4KICAgICAgICA8dHNwYW4geD0iMjIuMTk4MTk4MiIgeT0iMTQiPlItQ01ELWNoZWNrLnlhbWw8L3RzcGFuPgogICAgICA8L3RleHQ+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMzIpIiBmb250LWZhbWlseT0iJiMzOTtEZWphVnUgU2FucyYjMzk7LFZlcmRhbmEsR2VuZXZhLHNhbnMtc2VyaWYiIGZvbnQtc2l6ZT0iMTEiPgogICAgICA8cGF0aCBkPSJNMCAwaDQwLjQ3QzQxLjg2OSAwIDQzIDEuMzQzIDQzIDN2MTRjMCAxLjY1Ny0xLjEzMiAzLTIuNTMgM0gwVjB6IiBpZD0ic3RhdGUtYmciIGZpbGw9InVybCgjc3RhdGUtZmlsbCkiIGZpbGwtcnVsZT0ibm9uemVybyI+PC9wYXRoPgogICAgICA8dGV4dCBmaWxsPSIjMDEwMTAxIiBmaWxsLW9wYWNpdHk9Ii4zIiBhcmlhLWhpZGRlbj0idHJ1ZSI+CiAgICAgICAgPHRzcGFuIHg9IjUiIHk9IjE1Ij5mYWlsaW5nPC90c3Bhbj4KICAgICAgPC90ZXh0PgogICAgICA8dGV4dCBmaWxsPSIjRkZGRkZGIj4KICAgICAgICA8dHNwYW4geD0iNSIgeT0iMTQiPmZhaWxpbmc8L3RzcGFuPgogICAgICA8L3RleHQ+CiAgICA8L2c+CiAgICA8cGF0aCBmaWxsPSIjOTU5REE1IiBkPSJNMTEgM2MtMy44NjggMC03IDMuMTMyLTcgN2E2Ljk5NiA2Ljk5NiAwIDAgMCA0Ljc4NiA2LjY0MWMuMzUuMDYyLjQ4Mi0uMTQ4LjQ4Mi0uMzMyIDAtLjE2Ni0uMDEtLjcxOC0uMDEtMS4zMDQtMS43NTguMzI0LTIuMjEzLS40MjktMi4zNTMtLjgyMi0uMDc5LS4yMDItLjQyLS44MjMtLjcxNy0uOTktLjI0NS0uMTMtLjU5NS0uNDU0LS4wMS0uNDYzLjU1Mi0uMDA5Ljk0Ni41MDggMS4wNzcuNzE4LjYzIDEuMDU4IDEuNjM2Ljc2IDIuMDM5LjU3Ny4wNjEtLjQ1NS4yNDUtLjc2MS40NDYtLjkzNi0xLjU1Ny0uMTc1LTMuMTg1LS43NzktMy4xODUtMy40NTYgMC0uNzYyLjI3MS0xLjM5Mi43MTgtMS44ODItLjA3LS4xNzUtLjMxNS0uODkyLjA3LTEuODU1IDAgMCAuNTg2LS4xODMgMS45MjUuNzE4YTYuNSA2LjUgMCAwIDEgMS43NS0uMjM2IDYuNSA2LjUgMCAwIDEgMS43NS4yMzZjMS4zMzgtLjkxIDEuOTI1LS43MTggMS45MjUtLjcxOC4zODUuOTYzLjE0IDEuNjguMDcgMS44NTUuNDQ2LjQ5LjcxNyAxLjExMi43MTcgMS44ODIgMCAyLjY4Ni0xLjYzNiAzLjI4LTMuMTk0IDMuNDU2LjI1NC4yMTkuNDczLjYzOS40NzMgMS4yOTUgMCAuOTM2LS4wMDkgMS42ODktLjAwOSAxLjkyNSAwIC4xODQuMTMxLjQwMi40ODEuMzMyQTcuMDExIDcuMDExIDAgMCAwIDE4IDEwYzAtMy44NjctMy4xMzMtNy03LTd6Ij48L3BhdGg+CiAgPC9nPgo8L3N2Zz4KCg==" class="img-fluid" alt="R-CMD-check"></a> <a href="https://github.com/richJJackson/psc/actions/workflows/R-CMD-check.yaml"><img role="img" aria-label="R-CMD-check" src="data:image/svg+xml; charset=utf-8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNzUiIGhlaWdodD0iMjAiPgogIDx0aXRsZT5SLUNNRC1jaGVjay55YW1sIC0gZmFpbGluZzwvdGl0bGU+CiAgPGRlZnM+CiAgICA8bGluZWFyR3JhZGllbnQgaWQ9IndvcmtmbG93LWZpbGwiIHgxPSI1MCUiIHkxPSIwJSIgeDI9IjUwJSIgeTI9IjEwMCUiPgogICAgICA8c3RvcCBzdG9wLWNvbG9yPSIjNDQ0RDU2IiBvZmZzZXQ9IjAlIj48L3N0b3A+CiAgICAgIDxzdG9wIHN0b3AtY29sb3I9IiMyNDI5MkUiIG9mZnNldD0iMTAwJSI+PC9zdG9wPgogICAgPC9saW5lYXJHcmFkaWVudD4KICAgIDxsaW5lYXJHcmFkaWVudCBpZD0ic3RhdGUtZmlsbCIgeDE9IjUwJSIgeTE9IjAlIiB4Mj0iNTAlIiB5Mj0iMTAwJSI+CiAgICAgIDxzdG9wIHN0b3AtY29sb3I9IiNENzNBNDkiIG9mZnNldD0iMCUiPjwvc3RvcD4KICAgICAgPHN0b3Agc3RvcC1jb2xvcj0iI0NCMjQzMSIgb2Zmc2V0PSIxMDAlIj48L3N0b3A+CiAgICA8L2xpbmVhckdyYWRpZW50PgogIDwvZGVmcz4KICA8ZyBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPgogICAgPGcgZm9udC1mYW1pbHk9IiYjMzk7RGVqYVZ1IFNhbnMmIzM5OyxWZXJkYW5hLEdlbmV2YSxzYW5zLXNlcmlmIiBmb250LXNpemU9IjExIj4KICAgICAgPHBhdGggaWQ9IndvcmtmbG93LWJnIiBkPSJNMCwzIEMwLDEuMzQzMSAxLjM1NTIsMCAzLjAyNzAyNzAzLDAgTDEzMiwwIEwxMzIsMjAgTDMuMDI3MDI3MDMsMjAgQzEuMzU1MiwyMCAwLDE4LjY1NjkgMCwxNyBMMCwzIFoiIGZpbGw9InVybCgjd29ya2Zsb3ctZmlsbCkiIGZpbGwtcnVsZT0ibm9uemVybyI+PC9wYXRoPgogICAgICA8dGV4dCBmaWxsPSIjMDEwMTAxIiBmaWxsLW9wYWNpdHk9Ii4zIj4KICAgICAgICA8dHNwYW4geD0iMjIuMTk4MTk4MiIgeT0iMTUiIGFyaWEtaGlkZGVuPSJ0cnVlIj5SLUNNRC1jaGVjay55YW1sPC90c3Bhbj4KICAgICAgPC90ZXh0PgogICAgICA8dGV4dCBmaWxsPSIjRkZGRkZGIj4KICAgICAgICA8dHNwYW4geD0iMjIuMTk4MTk4MiIgeT0iMTQiPlItQ01ELWNoZWNrLnlhbWw8L3RzcGFuPgogICAgICA8L3RleHQ+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMzIpIiBmb250LWZhbWlseT0iJiMzOTtEZWphVnUgU2FucyYjMzk7LFZlcmRhbmEsR2VuZXZhLHNhbnMtc2VyaWYiIGZvbnQtc2l6ZT0iMTEiPgogICAgICA8cGF0aCBkPSJNMCAwaDQwLjQ3QzQxLjg2OSAwIDQzIDEuMzQzIDQzIDN2MTRjMCAxLjY1Ny0xLjEzMiAzLTIuNTMgM0gwVjB6IiBpZD0ic3RhdGUtYmciIGZpbGw9InVybCgjc3RhdGUtZmlsbCkiIGZpbGwtcnVsZT0ibm9uemVybyI+PC9wYXRoPgogICAgICA8dGV4dCBmaWxsPSIjMDEwMTAxIiBmaWxsLW9wYWNpdHk9Ii4zIiBhcmlhLWhpZGRlbj0idHJ1ZSI+CiAgICAgICAgPHRzcGFuIHg9IjUiIHk9IjE1Ij5mYWlsaW5nPC90c3Bhbj4KICAgICAgPC90ZXh0PgogICAgICA8dGV4dCBmaWxsPSIjRkZGRkZGIj4KICAgICAgICA8dHNwYW4geD0iNSIgeT0iMTQiPmZhaWxpbmc8L3RzcGFuPgogICAgICA8L3RleHQ+CiAgICA8L2c+CiAgICA8cGF0aCBmaWxsPSIjOTU5REE1IiBkPSJNMTEgM2MtMy44NjggMC03IDMuMTMyLTcgN2E2Ljk5NiA2Ljk5NiAwIDAgMCA0Ljc4NiA2LjY0MWMuMzUuMDYyLjQ4Mi0uMTQ4LjQ4Mi0uMzMyIDAtLjE2Ni0uMDEtLjcxOC0uMDEtMS4zMDQtMS43NTguMzI0LTIuMjEzLS40MjktMi4zNTMtLjgyMi0uMDc5LS4yMDItLjQyLS44MjMtLjcxNy0uOTktLjI0NS0uMTMtLjU5NS0uNDU0LS4wMS0uNDYzLjU1Mi0uMDA5Ljk0Ni41MDggMS4wNzcuNzE4LjYzIDEuMDU4IDEuNjM2Ljc2IDIuMDM5LjU3Ny4wNjEtLjQ1NS4yNDUtLjc2MS40NDYtLjkzNi0xLjU1Ny0uMTc1LTMuMTg1LS43NzktMy4xODUtMy40NTYgMC0uNzYyLjI3MS0xLjM5Mi43MTgtMS44ODItLjA3LS4xNzUtLjMxNS0uODkyLjA3LTEuODU1IDAgMCAuNTg2LS4xODMgMS45MjUuNzE4YTYuNSA2LjUgMCAwIDEgMS43NS0uMjM2IDYuNSA2LjUgMCAwIDEgMS43NS4yMzZjMS4zMzgtLjkxIDEuOTI1LS43MTggMS45MjUtLjcxOC4zODUuOTYzLjE0IDEuNjguMDcgMS44NTUuNDQ2LjQ5LjcxNyAxLjExMi43MTcgMS44ODIgMCAyLjY4Ni0xLjYzNiAzLjI4LTMuMTk0IDMuNDU2LjI1NC4yMTkuNDczLjYzOS40NzMgMS4yOTUgMCAuOTM2LS4wMDkgMS42ODktLjAwOSAxLjkyNSAwIC4xODQuMTMxLjQwMi40ODEuMzMyQTcuMDExIDcuMDExIDAgMCAwIDE4IDEwYzAtMy44NjctMy4xMzMtNy03LTd6Ij48L3BhdGg+CiAgPC9nPgo8L3N2Zz4KCg==" class="img-fluid" alt="R-CMD-check"></a> <!-- badges: end --></p>
<p>The goal of psc is to compare a dataset of observations against a parametric model.</p>
<p>Visit the mecPortal website <a href="https://richjjackson.github.io/mecPortal/"> here!</a></p>
<div class="box" style= "background-color:#666699;">
<section id="installation" class="level2">
<h2 class="anchored" data-anchor-id="installation">Installation</h2>
<p>You can install the development version of psc from <a href="https://github.com/">GitHub</a> with:</p>
<div class="sourceCode" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="co"># install.packages(&quot;devtools&quot;)</span></span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a>devtools<span class="sc">::</span><span class="fu">install_github</span>(<span class="st">&quot;richJJackson/psc&quot;</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</section>
</div>
<div class="box" style="background-color:#777696 ;">
<section id="example" class="level2">
<h2 class="anchored" data-anchor-id="example">Example</h2>
<p>This is a basic example which shows you how to solve a common problem:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb2"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb2-1"><a href="#cb2-1" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(psc)</span>
<span id="cb2-2"><a href="#cb2-2" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Warning: package &#39;psc&#39; was built under R version 4.5.1</span></span>
<span id="cb2-3"><a href="#cb2-3" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(survival)</span>
<span id="cb2-4"><a href="#cb2-4" aria-hidden="true" tabindex="-1"></a><span class="do">## basic example code</span></span>
<span id="cb2-5"><a href="#cb2-5" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb2-6"><a href="#cb2-6" aria-hidden="true" tabindex="-1"></a><span class="do">### Load model</span></span>
<span id="cb2-7"><a href="#cb2-7" aria-hidden="true" tabindex="-1"></a><span class="fu">data</span>(<span class="st">&quot;surv.mod&quot;</span>)</span>
<span id="cb2-8"><a href="#cb2-8" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb2-9"><a href="#cb2-9" aria-hidden="true" tabindex="-1"></a><span class="do">### Load Data</span></span>
<span id="cb2-10"><a href="#cb2-10" aria-hidden="true" tabindex="-1"></a><span class="fu">data</span>(<span class="st">&quot;data&quot;</span>)</span>
<span id="cb2-11"><a href="#cb2-11" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb2-12"><a href="#cb2-12" aria-hidden="true" tabindex="-1"></a><span class="do">### Use &#39;pscfit&#39; to compare</span></span>
<span id="cb2-13"><a href="#cb2-13" aria-hidden="true" tabindex="-1"></a>surv.psc <span class="ot">&lt;-</span> <span class="fu">pscfit</span>(surv.mod,data)</span>
<span id="cb2-14"><a href="#cb2-14" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Warning in data_match(cls, lev, DC): vi specified as a character in the model, consider respecifying</span></span>
<span id="cb2-15"><a href="#cb2-15" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;                 as a factor to ensure categories match between CFM and DC</span></span>
<span id="cb2-16"><a href="#cb2-16" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Warning in data_match(cls, lev, DC): allmets specified as a character in the model, consider respecifying</span></span>
<span id="cb2-17"><a href="#cb2-17" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;                 as a factor to ensure categories match between CFM and DC</span></span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>You can use standard commands for getting a summary of your analysis…</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb3"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="fu">summary</span>(surv.psc)</span>
<span id="cb3-2"><a href="#cb3-2" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Summary: </span></span>
<span id="cb3-3"><a href="#cb3-3" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;  </span></span>
<span id="cb3-4"><a href="#cb3-4" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; 100 observations selected from the data cohort for comparison </span></span>
<span id="cb3-5"><a href="#cb3-5" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; CFM of type flexsurvreg identified  </span></span>
<span id="cb3-6"><a href="#cb3-6" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; linear predictor succesfully obtained with median: </span></span>
<span id="cb3-7"><a href="#cb3-7" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;  trt: 3.15</span></span>
<span id="cb3-8"><a href="#cb3-8" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Average expected response: </span></span>
<span id="cb3-9"><a href="#cb3-9" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;  trt: 9.1</span></span>
<span id="cb3-10"><a href="#cb3-10" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Average observed response: 6.366 </span></span>
<span id="cb3-11"><a href="#cb3-11" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; </span></span>
<span id="cb3-12"><a href="#cb3-12" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Counterfactual Model (CFM): </span></span>
<span id="cb3-13"><a href="#cb3-13" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; A model of class &#39;flexsurvreg&#39; </span></span>
<span id="cb3-14"><a href="#cb3-14" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;  Fit with 3 internal knots</span></span>
<span id="cb3-15"><a href="#cb3-15" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; </span></span>
<span id="cb3-16"><a href="#cb3-16" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Formula: </span></span>
<span id="cb3-17"><a href="#cb3-17" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Surv(time, cen) ~ vi/age60 + ecog + allmets + logafp + alb + </span></span>
<span id="cb3-18"><a href="#cb3-18" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;     logcreat + logast + aet</span></span>
<span id="cb3-19"><a href="#cb3-19" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; &lt;environment: 0x0000021a2ea6e770&gt;</span></span>
<span id="cb3-20"><a href="#cb3-20" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; </span></span>
<span id="cb3-21"><a href="#cb3-21" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Call:</span></span>
<span id="cb3-22"><a href="#cb3-22" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;  CFM model + beta</span></span>
<span id="cb3-23"><a href="#cb3-23" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; </span></span>
<span id="cb3-24"><a href="#cb3-24" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; Coefficients:</span></span>
<span id="cb3-25"><a href="#cb3-25" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt;       median    2.5%      97.5%     Pr(x&lt;0)   Pr(x&gt;0) </span></span>
<span id="cb3-26"><a href="#cb3-26" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; beta    0.3681    0.1667    0.5554    0.0004    0.9996</span></span>
<span id="cb3-27"><a href="#cb3-27" aria-hidden="true" tabindex="-1"></a><span class="co">#&gt; DIC   280.6119  273.5065  291.7572        NA        NA</span></span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>… and to see a plot of what you have done</p>
<div class="cell">
<div class="cell-output-display">
<div>
<figure class="figure">
<p><img role="img" src="data:image/png;base64,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" class="img-fluid figure-img" style="width:100.0%"></p>
</figure>
</div>
</div>
</div>
<p>In that case, don’t forget to commit and push the resulting figure files, so they display on GitHub and CRAN.</p>
<p><a href="https://richjjackson.github.io/mecPortal/">Visit the mecPortal website!</a></p>
</section>
</div>
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




</body></div>