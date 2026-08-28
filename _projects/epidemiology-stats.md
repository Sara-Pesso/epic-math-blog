---
layout: page
title: Counting Processes, Regression, and Bayesian Methods for Epidemiology
description: An application of Bayesian statistical methods on the spread of epidemics, with a focus on the COVID-19 pandemic and 2014 to present Ebola epidemics in Africa. 
img: /assets/img/epidemics_projects/thumbnail-epidemic.png
category: work
---

Project completed for graduate level statistics class (MAT 721) at the Johns Hopkins University as part of the Applied & Computational Mathematics Graduate Certificate.

All Python scripts referenced in this project can be found on this [Github Repo](https://github.com/Sara-Pesso/Research-Project-Pessognelli).

Below is a downloadable PDF version of this project, rendered in LaTeX. There is also a complete bibliography at the end of this document!

<div class="embed-responsive" style="height: 80vh;">
  <iframe src="{{ '/assets/pdf/Research_Project_721_Pessognelli_FINAL.pdf' | relative_url }}" width="100%" height="100%" style="border: none;">
  </iframe>
</div>

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <meta name="author" content="Sara Pessognelli" />
  <title>Counting Processes, Regression, and Bayesian Methods for Epidemiology</title>
  <style>
    /* Default styles provided by pandoc.
    ** See https://pandoc.org/MANUAL.html#variables-for-html for config info.
    */
    html {
      color: #1a1a1a;
      background-color: #fdfdfd;
    }
    body {
      margin: 0 auto;
      max-width: 100%;
      padding-left: 50px;
      padding-right: 50px;
      padding-top: 50px;
      padding-bottom: 50px;
      hyphens: auto;
      overflow-wrap: break-word;
      text-rendering: optimizeLegibility;
      font-kerning: normal;
    }
    @media (max-width: 600px) {
      body {
        font-size: 0.9em;
        padding: 12px;
      }
      h1 {
        font-size: 1.8em;
      }
    }
    @media print {
      html {
        background-color: white;
      }
      body {
        background-color: transparent;
        color: black;
        font-size: 12pt;
      }
      p, h2, h3 {
        orphans: 3;
        widows: 3;
      }
      h2, h3, h4 {
        page-break-after: avoid;
      }
    }
    p {
      margin: 1em 0;
    }
    a {
      color: #1a1a1a;
    }
    a:visited {
      color: #1a1a1a;
    }
    img {
      max-width: 100%;
    }
    svg {
      height: auto;
      max-width: 100%;
    }
    h1, h2, h3, h4, h5, h6 {
      margin-top: 1.4em;
    }
    h5, h6 {
      font-size: 1em;
      font-style: italic;
    }
    h6 {
      font-weight: normal;
    }
    ol, ul {
      padding-left: 1.7em;
      margin-top: 1em;
    }
    li > ol, li > ul {
      margin-top: 0;
    }
    blockquote {
      margin: 1em 0 1em 1.7em;
      padding-left: 1em;
      border-left: 2px solid #e6e6e6;
      color: #606060;
    }
    div.abstract {
      margin: 2em 2em 2em 2em;
      text-align: left;
      font-size: 85%;
    }
    div.abstract-title {
      font-weight: bold;
      text-align: center;
      padding: 0;
      margin-bottom: 0.5em;
    }
    code {
      font-family: Menlo, Monaco, Consolas, 'Lucida Console', monospace;
      font-size: 85%;
      margin: 0;
      hyphens: manual;
    }
    pre {
      margin: 1em 0;
      overflow: auto;
    }
    pre code {
      padding: 0;
      overflow: visible;
      overflow-wrap: normal;
    }
    .sourceCode {
     background-color: transparent;
     overflow: visible;
    }
    hr {
      border: none;
      border-top: 1px solid #1a1a1a;
      height: 1px;
      margin: 1em 0;
    }
    table {
      margin: 1em 0;
      border-collapse: collapse;
      width: 100%;
      overflow-x: auto;
      display: block;
      font-variant-numeric: lining-nums tabular-nums;
    }
    table caption {
      margin-bottom: 0.75em;
    }
    tbody {
      margin-top: 0.5em;
      border-top: 1px solid #1a1a1a;
      border-bottom: 1px solid #1a1a1a;
    }
    th {
      border-top: 1px solid #1a1a1a;
      padding: 0.25em 0.5em 0.25em 0.5em;
    }
    td {
      padding: 0.125em 0.5em 0.25em 0.5em;
    }
    header {
      margin-bottom: 4em;
      text-align: center;
    }
    #TOC li {
      list-style: none;
    }
    #TOC ul {
      padding-left: 1.3em;
    }
    #TOC > ul {
      padding-left: 0;
    }
    #TOC a:not(:hover) {
      text-decoration: none;
    }
    code{white-space: pre-wrap;}
    span.smallcaps{font-variant: small-caps;}
    div.columns{display: flex; gap: min(4vw, 1.5em);}
    div.column{flex: auto; overflow-x: auto;}
    div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
    /* The extra [class] is a hack that increases specificity enough to
       override a similar rule in reveal.js */
    ul.task-list[class]{list-style: none;}
    ul.task-list li input[type="checkbox"] {
      font-size: inherit;
      width: 0.8em;
      margin: 0 0.8em 0.2em -1.6em;
      vertical-align: middle;
    }
  </style>
</head>
<body>
<header id="title-block-header">
<h1 class="title">Counting Processes, Regression, and Bayesian Methods
for Epidemiology</h1>
<p class="author">Sara Pessognelli</p>
<div class="abstract">
<div class="abstract-title">Abstract</div>
<p>We will first explore how to model the spread of disease through a
population, focusing on the Galton-Watson branching process for the
early stages of an outbreak and the SIR model for later stages. Turning
this section, the idea of treating infectious periods as a random
variable from a Poisson process is also explored, and the modelling
implications discussed. Once the branching process has been modelled,
with discuss several techniques for estimating the parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
from data collected from various pandemics and epidemics. These
techniques include objective Bayesian parameter estimation, linear
regression (best linear predictor), and Bayesian linear regression.
Then, how
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
changes overtime due to mitigation efforts is explored using Bayesian
A/B testing. Finally, we will look at the efficacy of Gaussian naive
Bayes’ classifiers and Bayesian logistic regression for prediction of
disease.</p>
</div>
</header>
<p><br />
<br />
</p>
<h1 id="modelling-the-spread-of-disease.">Modelling the Spread of
Disease.</h1>
<h2 id="early-stages-the-galton-watson-process.">Early Stages: The
Galton-Watson Process.</h2>
<p>The spread of disease, especially the early stages of epidemics, is
easily modeled using branching processes—namely, the Galton-Watson
process. A branching process is a stochastic process, and the
Galton-Watson has two distinct features: a) all individuals give birth
according to the same probability law independently of each other, and
b) the number of offspring produced by an individual is independent of
the number of individuals in that generation <span class="citation"
data-cites="GIP"></span>.<br />
<br />
With respect to epidemiology, the number of individuals in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>X</mi><mi>n</mi></msub><annotation encoding="application/x-tex">X_n</annotation></semantics></math>,
is equivalent to the number of <strong>new cases</strong> during a given
infectious period, and offspring refers to the number of new people,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>Y</mi><mo stretchy="false" form="prefix">(</mo></msup><mi>j</mi><msub><mo stretchy="false" form="postfix">)</mo><mi>k</mi></msub></mrow><annotation encoding="application/x-tex">Y^(j)_k</annotation></semantics></math>
each individual in a generation infects, where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>
refers to the generation and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
to the individual of that generation. So, clearly
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>X</mi><mrow><mi>n</mi><mo>+</mo><mn>1</mn></mrow></msub><mo>:=</mo><msubsup><mi>Y</mi><mn>1</mn><mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>+</mo><msubsup><mi>Y</mi><mn>2</mn><mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msubsup><mi>Y</mi><msub><mi>X</mi><mi>n</mi></msub><mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></mrow><annotation encoding="application/x-tex">X_{n+1} := Y^{(n)}_1 + Y_2^{(n)} + ... + Y^{(n)}_{X_n}</annotation></semantics></math>
<span class="citation" data-cites="sir3"></span>.<br />
<br />
It is not unreasonable to model the number of offspring using a Poisson
distribution <span class="citation" data-cites="bp_covid"></span>:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>K</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_K \in Po(\lambda)</annotation></semantics></math>
And in fact, this simplifies some of the math. When discussing the
spread of disease, one of the relevant variables of interest is called
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
This value,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>,
is the <strong>basic reproductive number</strong>, and is a metric used
to describe the transmissibility of a disease <span class="citation"
data-cites="Re_R0"></span>. Referring back to Ahlberg’s paper
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mi>E</mi><mi>Y</mi></mrow><annotation encoding="application/x-tex">R_0 = EY</annotation></semantics></math>
which, in the case of the Poisson distribution, is simply the Poisson
parameter,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>.
In other words,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mi>E</mi><mi>Y</mi><mo>=</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">R_0 = EY = \lambda</annotation></semantics></math>
Intuitively, this makes sense. The offspring,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y^{(j)}_k</annotation></semantics></math>,
really just represents the number of infectious contacts of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>k</mi><mrow><mi>t</mi><mi>h</mi></mrow></msup><annotation encoding="application/x-tex">k^{th}</annotation></semantics></math>
individual in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>.
So, if we think about the number of infectious contacts as being Poisson
distributed, then we already know that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
is the mean number of infectious contacts, by definition of the Poisson
parameter.</p>
<h2 id="late-stages-the-sir-model.">Late Stages: The SIR Model.</h2>
<p>Interestingly, it is well documented that probabilistic models, like
the Galton-Watson branching process, are really only necessary in the
<strong>beginning</strong> stages of an outbreak. As time progresses,
the simpler SIR model–which is a deterministic ODE model– is used
instead as it fits data just as well and is less computationally dense
<span class="citation" data-cites="sir3"></span><span class="citation"
data-cites="BP_Epidemiology"></span>. In the SIR model, "S" stands for
<strong>susceptible</strong>, "I" for <strong>infected</strong>, and "R"
for <strong>recovered</strong>. From Smith and Moore of the Mathematical
Association of America <span class="citation" data-cites="sir1"></span>,
we therefore know we can model an outbreak of disease over time as the
following:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mtext mathvariant="normal">proportion of population that is susceptible at time t.</mtext></mrow><annotation encoding="application/x-tex">s(t) = \text{proportion of population that is susceptible at time t.}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>i</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mtext mathvariant="normal">proportion of population that is infected at time t.</mtext></mrow><annotation encoding="application/x-tex">i(t) = \text{proportion of population that is infected at time t.}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>r</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mtext mathvariant="normal">proportion of population that is recovered at time t.</mtext></mrow><annotation encoding="application/x-tex">r(t) = \text{proportion of population that is recovered at time t.}</annotation></semantics></math>
And the differential equations related to the SIR model are as follows:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mfrac><mrow><mi>d</mi><mi>s</mi></mrow><mrow><mi>d</mi><mi>t</mi></mrow></mfrac><mo>=</mo><mi>−</mi><mi>b</mi><mo>⋅</mo><mi>s</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mi>i</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\frac{ds}{dt} = -b\cdot s(t) i(t)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mfrac><mrow><mi>d</mi><mi>r</mi></mrow><mrow><mi>d</mi><mi>t</mi></mrow></mfrac><mo>=</mo><mi>k</mi><mo>⋅</mo><mi>i</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\frac{dr}{dt} = k\cdot i(t)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mfrac><mrow><mi>d</mi><mi>i</mi></mrow><mrow><mi>d</mi><mi>t</mi></mrow></mfrac><mo>=</mo><mi>b</mi><mo>⋅</mo><mi>s</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mi>i</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mi>k</mi><mo>⋅</mo><mi>i</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\frac{di}{dt} = b\cdot s(t)i(t)-k\cdot i(t)</annotation></semantics></math>
Where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>b</mi><annotation encoding="application/x-tex">b</annotation></semantics></math>
is the proportion of infected-susceptible interactions per day, that
result in infection (i.e., that are sufficient to spread the disease)
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
is the fraction of the infected group that will recover during a given
generation. For the purposes of example,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
will equal one. Again, intuitively, these equations make sense. Of
course the number of individuals leaving susceptible status is
proportional to
-<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>b</mi><annotation encoding="application/x-tex">b</annotation></semantics></math>,
the number of susceptible people and the number of infected people, at
time
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>t</mi><annotation encoding="application/x-tex">t</annotation></semantics></math>.
And then, of course, the number of infected increases by the same, and
decreases by the number of infected at time
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>t</mi><annotation encoding="application/x-tex">t</annotation></semantics></math>,
when
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">k=1</annotation></semantics></math>.
Then, the number of recovered is just the number of people leaving
infected status at time
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>t</mi><annotation encoding="application/x-tex">t</annotation></semantics></math>.<br />
<br />
A natural question is how the parameters
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>b</mi><annotation encoding="application/x-tex">b</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
relate to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
or
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
We can define
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
as follows
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>=</mo><mfrac><mrow><mi>b</mi><mo>⋅</mo><mi>s</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><mi>k</mi></mfrac></mrow><annotation encoding="application/x-tex">R_e = \frac{b\cdot s(t)}{k}</annotation></semantics></math>
So,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
is <strong>decreasing</strong> overtime, and when once
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">R_e &lt; 1</annotation></semantics></math>,
the infected population will decrease to 0<span class="citation"
data-cites="sir4"></span>. We also see this in Allan Gut’s <em>An
Intermediate Course in Probability</em><span class="citation"
data-cites="GIP"></span>, which states
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>η</mi><annotation encoding="application/x-tex">\eta</annotation></semantics></math>,
the probability of (eventual) extinction is 1 when
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">EY_k^{(j)} &lt; 1</annotation></semantics></math>.
Something interesting to note about this model is that the parameters
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>b</mi><mo>,</mo><mi>k</mi></mrow><annotation encoding="application/x-tex">b,k</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>i</mi><mo stretchy="false" form="prefix">(</mo><mn>0</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">i(0)</annotation></semantics></math>
are frequently determined by a trial and error method <span
class="citation" data-cites="sir4"></span>.</p>
<figure data-latex-placement="h">
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/SIR_example.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption aria-hidden="true"></figcaption>
</figure>
<p>Looking ahead to the section where we work out
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
for various counties in the US, we can see the orange line in Figure 1,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>I</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">I(t)</annotation></semantics></math>,
shares a similar shape to what we see in the "New Cases by day" charts,
as we would expect. Figure 1 also provides some insight into the
relationship between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>S</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>,</mo><mi>I</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">S(t), I(t)</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">R(t)</annotation></semantics></math>.</p>
<h2 id="covid-19-data-by-county.">COVID-19 Data By County.</h2>
<p>The data from the CDC and CSSE at Johns Hopkins <span
class="citation" data-cites="jhu_covid"></span> gives us the total
number of confirmed cases of COVID-19 and deaths by COVID-19 as a
function of date <span class="citation" data-cites="jhu_covid"></span>.
The data starts on January 22, 2020 and ends on July 27, 2020. During
this timespan, the CDC tracked these numbers by county for every county
in the United States. It is also important to note that thought the CDC
begins tracking cases on January 22, 2020, the first case in each county
varies. This becomes important when accounting for generation,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>.<br />
<br />
For the purposes of this analysis we’ll choose several counties from
throughout the country to work with individually. Those counties will be
Berks County, Pennsylvania, Manhattan County New York, Los Angeles
County California, and Philadelphia County, Pennsylvania. Figure 2 shows
the cumulative cases for each of these specified counties:</p>
<figure data-latex-placement="h">

<figcaption>Total Confirmed Cases, by county</figcaption>
</figure>
<p>Really, what the above graphs are showing is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>T</mi><mi>i</mi></msub><annotation encoding="application/x-tex">T_i</annotation></semantics></math>–
that is, the total number of cases each day, cumulatively. What we are
really interested in is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(i)</annotation></semantics></math>–
or the number of new cases each generation. Because the data is taken
each day, we simply find
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>X</mi><mi>i</mi></msub><annotation encoding="application/x-tex">X_i</annotation></semantics></math>
to be
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msub><mi>T</mi><mi>i</mi></msub><mo>−</mo><msub><mi>T</mi><mrow><mi>i</mi><mo>−</mo><mn>1</mn></mrow></msub></mrow><annotation encoding="application/x-tex">X(i) = T_i - T_{i-1}</annotation></semantics></math>
The CDC data was transformed this way and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(i)</annotation></semantics></math>
for the various US counties of interest are plotted below:</p>
<figure data-latex-placement="h">
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/all_newcases.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>New Cases Major US Counties, by day</figcaption>
</figure>
<p>What’s interesting about each graph, is that even though three of
them have very similar shapes the scales are drastically different. Not
to mention one county, that being Los Angeles, actually has a very
different shape than the other three counties in terms of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>
versus N. This was a little surprising to see, since we would have
expected similar
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
values for each county considering we’re dealing with the same disease
in each. But there are some rational reasons why this could have
occurred. For one, access to testing resources could have artificially
deflated the number of detected cases in certain areas. Of the four
counties that we’ve chosen, Berks County is by far the smallest and
least densely populated. So in densely populated counties like Los
Angeles or Manhattan, you would expect to see more interactions per day
therefore driving up the effective
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>,
or
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>.
This could explain why those two counties have many more cases in pure
numbers than places like Berks county.</p>
<h1 id="data-sets.">Data Sets.</h1>
<h2 id="covid-19-data-worldwide.">COVID-19 Data Worldwide.</h2>
<p>The CDC and the CSSE at Johns Hopkins <span class="citation"
data-cites="jhu_covid"></span> also tracked the number of cumulative
cases and cumulative deaths by day world wide similarly to what was done
by county in the United States <span class="citation"
data-cites="jhu_covid"></span>. From this data, using a similar method
as before, we will again determine
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>–
but this time, for the entire world. Again, the data is visualized
below:</p>
<figure data-latex-placement="h">

<figcaption>Total Cases &amp; New Cases of COVID-19 World
Wide.</figcaption>
</figure>
<h2 id="ebola-data-set.">Ebola Data Set.</h2>
<p>Similar to our previous work examining the COVID-19 pandemic, we have
our
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>T</mi><mi>i</mi></msub><annotation encoding="application/x-tex">T_i</annotation></semantics></math>
data (i.e., the total rolling reported number of cases) for the
2014-2016 West Africa Ebola Outbreak <span class="citation"
data-cites="ebola_total2"></span>. Looking at the below graphs, we can
see a few peculiarities:</p>
<ul>
<li><p>Though the data comes from the CDC, unlike COVID-19 in the US,
the number of newly infected Ebola patients was not recorded daily, so
there are some several day gaps in the data.</p></li>
<li><p>At times, the total case count decreases by a few patients
day-to-day. It is unclear how this is possible, and is not discussed on
the CDC’s site. Most likely, some previously suspected cases are ruled
out as being Ebola.</p></li>
<li><p>Given the date and location of this outbreak, if anything the
number of reported cases is well under the true number of
cases.</p></li>
<li><p>Unlike the COVID-19 data that was granular to the scale of
individual counties, the Ebola data is totalled across all three
countries: Guinea, Sierra Leone, and Liberia.</p></li>
</ul>
<figure data-latex-placement="h">
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/ebola_total_cases.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<!-- <img src="./ebola_total_cases.png" style="width:73.0%" /> -->
<figcaption>Total Confirmed Ebola Cases in West Africa (2014-16), using
the raw CDC data set.</figcaption>
</figure>
<figure data-latex-placement="h">
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/ebola_xn_raw.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<!-- <img src="./ebola_xn_raw.png" style="width:73.0%" /> -->
<figcaption>Newly Confirmed Ebola Cases in West Africa (2014-16), using
the raw CDC data set.</figcaption>
</figure>
<h1 id="parameter-estimation-using-bayes-theorem.">Parameter Estimation
Using Baye’s Theorem.</h1>
<h2 id="what-is-r_0">What is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>?</h2>
<p>If you are at all familiar with epidemiology or the study of disease
in general, then you’ve probably heard of the value
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
Simply stated
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
is the average number of people an infected person will infect during
their infectious period. The value varies by disease, and it depends on
many factors, but in general the higher the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
value the more likely the disease is to spread through a
population.<br />
<br />
In the context of this paper, we can think of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
as the expected number of children in the Galton-Watson process we will
use to describe the spread of an epidemic. It is widely accepted that
the number of infectious interactions a carrier will have is Poisson
distributed. So, if we let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y_k^{(j)}</annotation></semantics></math>
be the infected cases ("offspring") caused by individual
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>,
then
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y_k^{(j)} \in Po(\lambda)</annotation></semantics></math></p>
<p>This relationship allows us to estimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">R_0 = \lambda</annotation></semantics></math>.
Below are some of the currently (as of December 2023) accepted
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
values for various strains of SARS-CoV-2 <span class="citation"
data-cites="transmissibility"></span>.</p>
<div class="center">
<table>
<thead>
<tr>
<th style="text-align: center;">COVID-19 Strain</th>
<th
style="text-align: center;"><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;">Alpha</td>
<td style="text-align: center;">1.22</td>
</tr>
<tr>
<td style="text-align: center;">Beta</td>
<td style="text-align: center;">1.19</td>
</tr>
<tr>
<td style="text-align: center;">Gamma</td>
<td style="text-align: center;">1.21</td>
</tr>
<tr>
<td style="text-align: center;">Delta</td>
<td style="text-align: center;">1.38</td>
</tr>
<tr>
<td style="text-align: center;">Omnicron</td>
<td style="text-align: center;">1.90</td>
</tr>
</tbody>
</table>
</div>
<p>At the beginning of the pandemic, the literature has initial
calculations for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
much higher and were much more varied. One Chinese study<span
class="citation" data-cites="ebola_r0_liu"></span> compared 12 studies
published in the first few months of 2020 and found
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>’s
ranging from 1.5 to 6.68. Especially in the early stages, under
reporting due to lack of awareness could account for artificially low
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>s,
then over reporting due to hysteria could account for artificially high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>s.
The great variation in early reports can be explained somewhat by the
behaviors and mitigation method certain populations take.
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
is the average number of infectious <strong>interactions</strong>, so
societies that reduce their interactions via lockdown or other means
will skew their local
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
while societies that make no changes will see high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>s.
For example, an Italian model estimated
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
from 2.76 to 3.25 initially but after mitigation measures saw a decrease
in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
<span class="citation" data-cites="Re_R0"></span>.<br />
<br />
</p>
<h3
id="r_0-vs.-r_e."><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
vs.
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>.</h3>
<p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
is the basic reproductive number and is the reproductive ratio that most
people are familiar with, but there is also the
<strong>effective</strong> reproductive number,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>,
that changes as the immunity of the population changes. Where you might
consider
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
to be the “true” reproductive ratio,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
can be thought of as describing how human behavior, herd immunity, and
other outside factors influence the spread of disease. For example,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
is affected purely by the infectiousness of the organism and the rate of
recovery and death during an outbreak. While,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
is affected by herd immunity, either through natural immunity of
significant proportions of the population contracting the disease or
through immunization efforts. Obviously, such efforts will affect the
rate at which the disease spreads, but we don’t describe this using
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>,
we described this using
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
<span class="citation" data-cites="Re_R0"></span>. In essence,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
remains, regardless of human intervention.<br />
<br />
Within the confines of this paper, we will be attempting to estimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
values of diseases in various counties and locations. We will also be
seeing how certain efforts, namely lockdown efforts, affect the spread
of disease. In these cases, we will be estimating
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
and the effect that mitigation efforts have on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>.</p>
<h2
id="lambda-as-a-random-parameter"><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
as a Random Parameter</h2>
<p>In this section we will explore what happens when we consider the
infectious period of a disease as a random variable.<br />
Looking at the expression for infected offspring gleaned from the
branching process discussed previously, recall:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Po(\lambda)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mi>E</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></mrow><annotation encoding="application/x-tex">\lambda = R_0 = EY_k^{(j)}</annotation></semantics></math>
is the expected number of new infectious caused from the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>k</mi><mrow><mi>t</mi><mi>h</mi></mrow></msup><annotation encoding="application/x-tex">k^{th}</annotation></semantics></math>
individual in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>.
While using the average number of infections caused by an infectious
individual is useful and convenient, in reality some people’s immune
systems will respond better than others. In the case of COVID-19, some
people are completely asymptomatic, and unwittingly spread the infection
to more people, while some people’s immune systems will handle whatever
disease more readily, decreasing their infectious period.<br />
<br />
Therefore, our branching process becomes: the infectious periods,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>T</mi><annotation encoding="application/x-tex">T</annotation></semantics></math>,
are independent, identically distributed random variables; the
reproduction rate means that infectious individuals infect others at a
constant rate of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo stretchy="false" form="prefix">(</mo><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda (=R_0)</annotation></semantics></math>
throughout their lifetime <span class="citation"
data-cites="GIP"></span>. Therefore, our Poisson parameter becomes:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mi>T</mi></mrow><annotation encoding="application/x-tex">\lambda T</annotation></semantics></math>
and the number of offspring of each infected individual becomes
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo stretchy="false" form="prefix">|</mo><mi>T</mi><mo>=</mo><mi>τ</mi><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>τ</mi><mo stretchy="false" form="postfix">)</mo><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> where, </mtext><mspace width="0.333em"></mspace></mrow><mi>T</mi><mo>∈</mo><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mi>/</mi><mi>μ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k| T = \tau \in Po(\lambda\tau)\text{     where,    }T \in Exp(1/\mu)</annotation></semantics></math></p>
<h3 id="infections-as-a-poisson-process.">Infections as a Poisson
Process.</h3>
<p>Rather than simply describing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>T</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y_k^{(j)}\in Po(\lambda T)</annotation></semantics></math>,
we can also think of this situation as a Poisson process <span
class="citation" data-cites="GIP"></span>.<br />
<br />
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">{</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>,</mo><mi>t</mi><mo>≥</mo><mn>0</mn><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">\{Y_k^{(j)}(t), t\geq 0\}</annotation></semantics></math>
be the number offspring the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>k</mi><mrow><mi>t</mi><mi>h</mi></mrow></msup><annotation encoding="application/x-tex">k^{th}</annotation></semantics></math>
individual in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>
has at time
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>t</mi><annotation encoding="application/x-tex">t</annotation></semantics></math>.
The rate of infection for this process is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>,
and the times between each newly infected offspring are
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>T</mi><mo>∈</mo><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mi>/</mi><mi>μ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">T\in Exp(1/\mu)</annotation></semantics></math>.
This representation is equivalent to the branching process we previously
described, and the number of offspring of each infected individual again
becomes
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo stretchy="false" form="prefix">|</mo><mi>T</mi><mo>=</mo><mi>τ</mi><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>τ</mi><mo stretchy="false" form="postfix">)</mo><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> where, </mtext><mspace width="0.333em"></mspace></mrow><mi>T</mi><mo>∈</mo><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mi>/</mi><mi>μ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k| T = \tau \in Po(\lambda\tau)\text{     where,    }T \in Exp(1/\mu)</annotation></semantics></math>
and thus, the following derived distributions for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y^{(j)}_k</annotation></semantics></math>
are applicable for either interpretation.</p>
<h3 id="exponentially-distributed-infectious-periods.">Exponentially
Distributed Infectious Periods.</h3>
<p>Using the aforementioned distribution of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">y_k^{(j)}</annotation></semantics></math>,
by the Law of Total Probability, where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>i</mi><annotation encoding="application/x-tex">i</annotation></semantics></math>
is the number of infectees of the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>k</mi><mrow><mi>t</mi><mi>h</mi></mrow></msup><annotation encoding="application/x-tex">k^{th}</annotation></semantics></math>
individual of generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>i</mi><mo stretchy="false" form="prefix">|</mo><mi>T</mi><mo>=</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><msub><mi>f</mi><mi>τ</mi></msub><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">P(Y^{(j)}_k = i) = \int_0^\infty P(Y^{(j)}_k = i|T = t) \cdot f_{\tau}(t) \cdot dt</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><msup><mi>e</mi><mrow><mi>−</mi><mi>λ</mi><mi>t</mi></mrow></msup><mo>⋅</mo><mfrac><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>t</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>i</mi></msup></mrow><mrow><mi>i</mi><mi>!</mi></mrow></mfrac><mi>μ</mi><msup><mi>e</mi><mrow><mi>−</mi><mi>μ</mi><mi>t</mi></mrow></msup><mo>⋅</mo><mi>d</mi><mi>t</mi><mo>=</mo><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><mfrac><mrow><mi>μ</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>t</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>i</mi></msup></mrow><mrow><mi>i</mi><mi>!</mi></mrow></mfrac><mo>⋅</mo><mrow><mi mathvariant="normal">exp</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mo stretchy="false" form="prefix">[</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">]</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>d</mi><mi>x</mi></mrow><annotation encoding="application/x-tex">= \int_0^\infty e^{-\lambda  t}\cdot\frac{(\lambda t)^i}{i!}\mu e^{-\mu t}\cdot dt = \int_0^\infty\frac{\mu (\lambda t)^i}{i!}\cdot \exp(-[\lambda + \mu]t)\cdot dx</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mi>μ</mi><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><mfrac><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>t</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>i</mi></msup></mrow><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mo>⋅</mo><mrow><mi mathvariant="normal">exp</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mo stretchy="false" form="prefix">[</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">]</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">= \mu\int_0^\infty\frac{ (\lambda t)^i}{\Gamma(i+1)}\cdot \exp(-[\lambda + \mu]t)\cdot dt</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mfrac><mrow><mi>μ</mi><msup><mi>λ</mi><mi>i</mi></msup></mrow><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></msup></mrow></mfrac><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><mfrac><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></msup><msup><mi>t</mi><mi>i</mi></msup></mrow><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mo>⋅</mo><mrow><mi mathvariant="normal">exp</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mo stretchy="false" form="prefix">[</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">]</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">= \frac{\mu \lambda^i}{(\lambda + \mu)^{i+1}}\int_0^\infty \frac{(\lambda + \mu)^{i+1}t^i}{\Gamma(i+1)}\cdot\exp(-[\lambda + \mu]t)\cdot dt</annotation></semantics></math>
We recognize the integral as the PDF for a
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo>+</mo><mn>1</mn><mo>,</mo><mn>1</mn><mi>/</mi><mo stretchy="false" form="prefix">[</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\Gamma(t+1, 1/[\lambda+\mu])</annotation></semantics></math>,
being integrated over its support. Therefore, by the Law of Total
Probability this integral reduces to 1, leaving us with
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mrow><mi>μ</mi><msup><mi>λ</mi><mi>i</mi></msup></mrow><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></msup></mrow></mfrac><mo>=</mo><mfrac><mi>μ</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mo>⋅</mo><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mfrac><mi>λ</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><msup><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo><mi>i</mi></msup></mrow><annotation encoding="application/x-tex">P(Y^{(j)}_k = i) =\frac{\mu \lambda^i}{(\lambda + \mu)^{i+1}} = \frac{\mu}{(\lambda + \mu)} \cdot \Biggl(\frac{\lambda}{(\lambda + \mu)} \Biggr)^i</annotation></semantics></math>
Which we recognize mean that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y^{(j)}_k</annotation></semantics></math>
is a geometric random variable, specifically it is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mi>e</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mfrac><mi>μ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Ge\Biggl(\frac{\mu}{\lambda + \mu} \Biggr)</annotation></semantics></math>-distributed.<br />
<br />
In fact, we can take this one step further and look at the probability
of non-extinction,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>−</mo><mi>η</mi></mrow><annotation encoding="application/x-tex">1-\eta</annotation></semantics></math>
<span class="citation" data-cites="GIP"></span>. By Theorem 3.7.3(c) in
Allan Gut’s <em>An Intermediate Course in Probability</em>, we know that
if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>≤</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m \leq 1</annotation></semantics></math>,
them
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\eta = 1</annotation></semantics></math>
and if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>&gt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m &gt;  1</annotation></semantics></math>,
then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\eta &lt; 1</annotation></semantics></math>.
We also know that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mi>E</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></mrow><annotation encoding="application/x-tex">m = EY^{(j)}_k</annotation></semantics></math>
<span class="citation" data-cites="GIP"></span>, and because we have
already established
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>G</mi><mi>e</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mfrac><mi>μ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Ge\Biggl(\frac{\mu}{\lambda + \mu}\Biggr)</annotation></semantics></math>,
then</p>
<p><math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mi>E</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mfrac><mi>q</mi><mi>p</mi></mfrac><mo>=</mo><mfrac><mfrac><mi>λ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac><mfrac><mi>μ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac></mfrac><mo>=</mo><mfrac><mi>λ</mi><mi>μ</mi></mfrac></mrow><annotation encoding="application/x-tex">m = EY^{(j)}_k = \frac{q}{p} = \frac{\frac{\lambda}{\lambda+\mu}}{\frac{\mu}{\lambda+\mu}} = \frac{\lambda}{\mu}</annotation></semantics></math>
So, we can see that we have two cases:<br />
If
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>&gt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m &gt; 1</annotation></semantics></math>,
then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mfrac><mi>λ</mi><mi>μ</mi></mfrac><mo>&gt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m = \frac{\lambda}{\mu} &gt; 1</annotation></semantics></math>,
that is, if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>μ</mi><mo>&gt;</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">\mu &gt; \lambda</annotation></semantics></math>,
then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\eta = 1</annotation></semantics></math>,
and therefore the probability of non-extinction is
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>−</mo><mi>η</mi><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">1 - \eta = 0</annotation></semantics></math>
Or, if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>≤</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m \leq 1</annotation></semantics></math>,
then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mfrac><mi>λ</mi><mi>μ</mi></mfrac><mo>≤</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m = \frac{\lambda}{\mu} \leq 1</annotation></semantics></math>,
that is, if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>μ</mi><mo>≤</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">\mu \leq \lambda</annotation></semantics></math>,
then we know by Theorem 3.7.3 (b) that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>η</mi><annotation encoding="application/x-tex">\eta</annotation></semantics></math>
is the smallest non-negative root of
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>=</mo><msub><mi>g</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></msub><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">x = g_{Y^{(j)}_k}(x)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></msub><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">g_{Y^{(j)}_k}(x)</annotation></semantics></math>
is the probability generating function of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y^{(j)}_k</annotation></semantics></math>.<br />
Because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>G</mi><mi>e</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mfrac><mi>μ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Ge\Biggl(\frac{\mu}{\lambda + \mu} \Biggr)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></msub><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>x</mi><mo>=</mo><mfrac><mi>p</mi><mrow><mn>1</mn><mo>−</mo><mi>q</mi><mi>t</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">g_{Y^{(j)}_k}(x) = x =  \frac{p}{1-qt}</annotation></semantics></math>
and therefore to solve this equation, recalling that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>,</mo><mi>μ</mi><mo>&gt;</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">\lambda, \mu &gt; 0</annotation></semantics></math>:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>−</mo><mi>q</mi><mi>x</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>p</mi></mrow><annotation encoding="application/x-tex">x(1-qx) = p</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mn>1</mn><mo>−</mo><mfrac><mi>λ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac><mi>x</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo><mo>=</mo><mfrac><mi>μ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">x \Biggl(1-\frac{\lambda}{\lambda+\mu}x \Biggr) = \frac{\mu}{\lambda+\mu}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">)</mo><mi>x</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mn>1</mn><mo>−</mo><mfrac><mi>λ</mi><mrow><mi>λ</mi><mo>+</mo><mi>μ</mi></mrow></mfrac><mi>x</mi><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo><mo>=</mo><mi>μ</mi></mrow><annotation encoding="application/x-tex">(\lambda+\mu)x \Biggl(1-\frac{\lambda}{\lambda+\mu}x \Biggr) = \mu</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>+</mo><mi>μ</mi><mo stretchy="false" form="postfix">)</mo><mi>x</mi><mo>−</mo><mi>λ</mi><msup><mi>x</mi><mn>2</mn></msup><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo><mo>=</mo><mi>μ</mi></mrow><annotation encoding="application/x-tex">\Biggl((\lambda+\mu)x-\lambda x^2 \Biggr)  = \mu</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mi>x</mi><mo>+</mo><mi>μ</mi><mi>x</mi><mo>−</mo><mi>λ</mi><msup><mi>x</mi><mn>2</mn></msup><mo>=</mo><mi>μ</mi></mrow><annotation encoding="application/x-tex">\lambda x + \mu x -\lambda x^2 = \mu</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mi>x</mi><mo>−</mo><mi>λ</mi><msup><mi>x</mi><mn>2</mn></msup><mo>=</mo><mi>μ</mi><mo>−</mo><mi>μ</mi><mi>x</mi></mrow><annotation encoding="application/x-tex">\lambda x- \lambda x^2 = \mu - \mu x</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mi>x</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>−</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>μ</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>−</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda x (1-x) = \mu(1-x)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mi>x</mi><mo>=</mo><mi>μ</mi></mrow><annotation encoding="application/x-tex">\lambda x = \mu</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>=</mo><mi>x</mi><mo>=</mo><mfrac><mi>μ</mi><mi>λ</mi></mfrac></mrow><annotation encoding="application/x-tex">\eta = x = \frac{\mu}{\lambda}</annotation></semantics></math>
and therefore in this case, the probability of non-extinction
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>−</mo><mi>η</mi><mo>=</mo><mn>1</mn><mo>−</mo><mfrac><mi>μ</mi><mi>λ</mi></mfrac></mrow><annotation encoding="application/x-tex">1-\eta = 1-\frac{\mu}{\lambda}</annotation></semantics></math></p>
<p>This can be interpreted as probability that the outbreak of a disease
is self limiting, or in other words, that an epidemic dies out on it’s
own. Note that a
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>−</mo><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">1-\eta = 1</annotation></semantics></math>
means certainty that the outbreak is self-limiting, and the closer
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>−</mo><mi>η</mi></mrow><annotation encoding="application/x-tex">1-\eta</annotation></semantics></math>
is to 1 the more likely it is to die out on it’s own. Interestingly,
because of the distribution of the infectious periods is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>τ</mi><mo>∈</mo><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mi>/</mi><mi>μ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\tau \in Exp(1/\mu)</annotation></semantics></math>,
then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>τ</mi><mo>=</mo><mi>μ</mi></mrow><annotation encoding="application/x-tex">E\tau = \mu</annotation></semantics></math>
means that as the average infectious period <strong>decreases</strong>,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>−</mo><mi>η</mi><mo>→</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">1-\eta \longrightarrow 1</annotation></semantics></math>
assuming
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
is constant and disease specific. This means that if we can manipulate
the infectious period, we could ensure the extinction of an outbreak. As
we will discuss (and see in our analysis) later, if lock-downs our other
preventive measures are imposed to lessen the period of time an
individual is effectively infectious, this idea rings true.</p>
<h3 id="uniformly-distributed-infectious-periods.">Uniformly Distributed
Infectious Periods.</h3>
<p>We have no reason to believe the infectious periods,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>T</mi><annotation encoding="application/x-tex">T</annotation></semantics></math>,
are exponentially distributed. So, as an alternative example, let
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>T</mi><mo>∈</mo><mi>U</mi><mo stretchy="false" form="prefix">(</mo><mn>0</mn><mo>,</mo><mfrac><mi>b</mi><mi>λ</mi></mfrac><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">T \in U(0, \frac{b}{\lambda})</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mfrac><mi>b</mi><mi>λ</mi></mfrac><annotation encoding="application/x-tex">\frac{b}{\lambda}</annotation></semantics></math>
represents the maximum possible (or observed) infectious period.<br />
Again, by the Law of Total Probability,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>k</mi><mo stretchy="false" form="prefix">|</mo><mi>T</mi><mo>=</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><msub><mi>f</mi><mi>τ</mi></msub><mo stretchy="false" form="prefix">(</mo><mi>t</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">P(Y^{(j)}_k = i) = \int_0^\infty P(Y^{(j)}_k = k|T = t) \cdot f_{\tau}(t) \cdot dt</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><msup><mi>e</mi><mrow><mi>−</mi><mi>λ</mi><mi>t</mi></mrow></msup><mfrac><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>t</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>i</mi></msup></mrow><mrow><mi>i</mi><mi>!</mi></mrow></mfrac><mo>⋅</mo><mfrac><mn>1</mn><mi>b</mi></mfrac><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">=\int_0^\infty e^{-\lambda  t}\frac{(\lambda t)^i}{i!}\cdot \frac{1}{b}dt</annotation></semantics></math>
using the equality
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>i</mi><mi>!</mi></mrow><annotation encoding="application/x-tex">\Gamma(i+1) = i!</annotation></semantics></math>,
we see
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><msup><mi>e</mi><mrow><mi>−</mi><mi>λ</mi><mi>t</mi></mrow></msup><mfrac><mrow><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mi>t</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>i</mi></msup></mrow><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mo>⋅</mo><mfrac><mn>1</mn><mi>b</mi></mfrac><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">=\int_0^\infty e^{-\lambda  t}\frac{(\lambda t)^i}{\Gamma(i+1)}\cdot \frac{1}{b} dt</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mfrac><mn>1</mn><mi>b</mi></mfrac><mo>⋅</mo><mfrac><msup><mi>λ</mi><mi>i</mi></msup><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><msup><mi>t</mi><mi>i</mi></msup><msup><mi>e</mi><mrow><mi>−</mi><mi>λ</mi><mi>t</mi></mrow></msup><mi>d</mi><mi>t</mi></mrow><annotation encoding="application/x-tex">= \frac{1}{b}\cdot \frac{\lambda^i}{\Gamma(i+1)}\int_0^\infty t^i e^{-\lambda  t}dt</annotation></semantics></math>
Recalling that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mo>∫</mo><mn>0</mn><mi>∞</mi></msubsup><msup><mi>t</mi><mi>i</mi></msup><msup><mi>e</mi><mrow><mi>−</mi><mn>1</mn><mo>⋅</mo><mi>t</mi></mrow></msup><mi>d</mi><mi>t</mi><mo>=</mo><mfrac><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><msup><mi>λ</mi><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></msup></mfrac></mrow><annotation encoding="application/x-tex">\int_0^\infty t^ie^{-1\cdot t}dt = \frac{\Gamma(i+1)}{\lambda^{i+1}}</annotation></semantics></math>,
this expression evaluates down to
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mfrac><mn>1</mn><mi>b</mi></mfrac><mo>⋅</mo><mfrac><msup><mi>λ</mi><mi>i</mi></msup><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mo>⋅</mo><mfrac><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><msup><mi>λ</mi><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></msup></mfrac></mrow><annotation encoding="application/x-tex">= \frac{1}{b}\cdot \frac{\lambda^i}{\Gamma(i+1)}\cdot \frac{\Gamma(i+1)}{\lambda^{i+1}}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mn>1</mn><mrow><mi>b</mi><mo>⋅</mo><mi>λ</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(Y^{(j)}_k = i) = \frac{1}{b\cdot\lambda}</annotation></semantics></math>
or, rather
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>U</mi><mo stretchy="false" form="prefix">(</mo><mn>0</mn><mo>,</mo><mi>b</mi><mo>⋅</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in U(0, b\cdot\lambda)</annotation></semantics></math>.<br />
Intuitively, this
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>U</mi><mo stretchy="false" form="prefix">(</mo><mn>0</mn><mo>,</mo><mi>b</mi><mo>⋅</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in U(0, b\cdot\lambda)</annotation></semantics></math>
makes little sense, as it implies that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y^{(j)}_k</annotation></semantics></math>
is a continuous random variable, which it clearly is not. Rather, this
exercise was to show that depending on the distribution of people’s
infectious period for various diseases, the distribution of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y^{(j)}_k</annotation></semantics></math>
varies.<br />
Moving forward, we will continue to assume that the early stages of a
pandemic are well modelled by the typical Galton-Watson process and that
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">(</mo><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="postfix">)</mo><mi>.</mi></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Po(\lambda(=R_0)).</annotation></semantics></math></p>
<h3 id="probability-of-extinction-eta-conclusion.">Probability of
Extinction,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>η</mi><annotation encoding="application/x-tex">\eta</annotation></semantics></math>,
&amp; Conclusion.</h3>
<p>In subsequent analyses throughout this project, we will treat the
infectious periods as a constant number of days across all individuals.
So, again we will be left simply with
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">(</mo><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y_k^{(j)} \in Po(\lambda (=R_0))</annotation></semantics></math>
We have already established
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mi>E</mi><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mi>λ</mi><mo stretchy="false" form="prefix">(</mo><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">m = EY_k^{(j)} = \lambda (=R_0)</annotation></semantics></math>
So, by Theorem 7.3 (c) in Allan Gut’s book <span class="citation"
data-cites="GIP"></span>, we know if
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo stretchy="false" form="prefix">(</mo><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\lambda (=R_0) &lt; 1</annotation></semantics></math>
then the probability of (eventual) extinction,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>η</mi><annotation encoding="application/x-tex">\eta</annotation></semantics></math>,
is
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\eta = 1</annotation></semantics></math>
In other words, if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">R_0 &lt; 1</annotation></semantics></math>,
the epidemic or outbreak will be self-limiting ad will not be able to
proliferate. and</p>
<h2 id="estimating-r_0-using-bayes-theorem.">Estimating
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
using Baye’s Theorem.</h2>
<p>Bearing all this in mind, we will try to estimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
using Baye’s Theorem during the early stages of the pandemic. Using CDC
data which was collected daily from January 22, 2020 to July 27, 2020
that contains the number of confirmed cases and confirmed deaths by
county in the US.<br />
<br />
First, lets’ talk about estimating Poisson Parameters. Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
be the generation, then we can think of each generation as being the
<strong>infectious period</strong> of each infected person. From the
most recent guidance form the CDC, we know that each generation,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>,
is 5 days <span class="citation"
data-cites="isolation_period"></span><span class="citation"
data-cites="serial_int"></span>.<br />
<br />
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>
be the number of newly infected people in a generation. Then
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msubsup><mi>Y</mi><mn>1</mn><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow></msubsup><mo>+</mo><msubsup><mi>Y</mi><mn>2</mn><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow></msubsup><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msubsup><mi>Y</mi><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo>−</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow></msubsup></mrow><annotation encoding="application/x-tex">X(n) = Y_1^{n-1}+Y_2^{n-1}+...+Y_{X(n-1)}^{n-1}</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y_k^{(j)}</annotation></semantics></math>
is infectees ("offspring") of the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>k</mi><mrow><mi>t</mi><mi>h</mi></mrow></msup><annotation encoding="application/x-tex">k^{th}</annotation></semantics></math>
individual from the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n-1</annotation></semantics></math>
generation, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>
is the total number of infected people in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>.
It is very typical to estimate the number of offspring as i.i.d Poisson
random variables:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y_k^{(j)}\in Po(\lambda)</annotation></semantics></math>
Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
is the expected value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y_k^{(j)}</annotation></semantics></math>,
which from Gut’s textbook we know to be
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mi>E</mi><mo stretchy="false" form="prefix">[</mo><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">R_0 = E[Y_k^{(j)}] = \lambda</annotation></semantics></math>
Dr. Jarad Niemi of Iowa State University has many lectures on this
topic. Below, is a synthesized version of his lectures on estimating
Poisson parameters, applied specifically to the case of evaluating
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
<span class="citation" data-cites="iowa"></span>.<br />
<br />
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>
be the observed confirmed cases of SARS-CoV-2 in the CDC dataset and
recall
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">R_0 = \lambda</annotation></semantics></math>.
Baye’s Theorem tells us
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(\lambda|y) = \frac{P(y|\lambda)\cdot P(\lambda)}{P(y)}</annotation></semantics></math>
or even more simply
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>C</mi><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda|y) = C\cdot P(y|\lambda)\cdot P(\lambda)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mo>=</mo><mfrac><mn>1</mn><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mrow><annotation encoding="application/x-tex">C = \frac{1}{P(y)}</annotation></semantics></math>
is a proportionality constant. This leaves us with:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>∝</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda|y) \propto P(y|\lambda)\cdot P(\lambda)</annotation></semantics></math>
Because we have assumed all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y_k^{(j)}</annotation></semantics></math>
to be independent, we can represent
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(y|\lambda)</annotation></semantics></math>
as the <strong>likelihood</strong>, which is product of the individual
observations:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><munderover><mo>∏</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><mfrac><mrow><msup><mi>λ</mi><msub><mi>y</mi><mi>i</mi></msub></msup><mo>⋅</mo><msup><mi>e</mi><mrow><mi>−</mi><mi>λ</mi></mrow></msup></mrow><mrow><msub><mi>y</mi><mi>i</mi></msub><mi>!</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(y|\lambda) = \prod_{i=1}^n \frac{\lambda^{y_i}\cdot e^{-\lambda}}{y_i!}</annotation></semantics></math>
Where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>y</mi><mi>i</mi></msub><annotation encoding="application/x-tex">y_i</annotation></semantics></math>
represents the observed value infectees for a given observed infected
individual. Again using proportionality,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>∝</mo><msup><mi>λ</mi><mrow><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub></mrow></msup><mo>⋅</mo><msup><mi>e</mi><mrow><mi>−</mi><mi>n</mi><mi>λ</mi></mrow></msup></mrow><annotation encoding="application/x-tex">P(y|\lambda)\propto \lambda^{\overset{n}{\sum}y_i}\cdot e^{-n\lambda}</annotation></semantics></math>
So, we can see that the likelihood,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(y|\lambda)</annotation></semantics></math>
takes the form corresponding to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo>∈</mo><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub><mo>,</mo><mfrac><mn>1</mn><mi>n</mi></mfrac><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">y|\lambda \in \Gamma(\overset{n}{\sum}y_i, \frac{1}{n})</annotation></semantics></math>.
So, we can therefore choose
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>∈</mo><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>α</mi><mo>,</mo><mfrac><mn>1</mn><mi>β</mi></mfrac><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda \in \Gamma(\alpha, \frac{1}{\beta})</annotation></semantics></math>
as our <strong>conjugate</strong> prior, where a conjugate prior is
simply one that has the same type of distribution as the posterior. In
fact, we can find the form of the posterior simply by
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msup><mi>C</mi><mo>′</mo></msup><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda|y) = C&#39;P(y|\lambda)\cdot P(\lambda)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>∝</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msup><mi>λ</mi><mrow><mi>α</mi><mo>+</mo><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub><mo>−</mo><mn>1</mn></mrow></msup><mo>⋅</mo><msup><mi>e</mi><mrow><mi>−</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>+</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mi>λ</mi></mrow></msup></mrow><annotation encoding="application/x-tex">P(\lambda|y)\propto P(y|\lambda)\cdot P(\lambda) = \lambda^{\alpha+\overset{n}{\sum}y_i-1}\cdot e^{-(\beta + n)\lambda}</annotation></semantics></math>
So, clearly our posterior is given by
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo>∈</mo><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mi>p</mi><mo>=</mo><mi>α</mi><mo>+</mo><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub><mo>,</mo><mi>a</mi><mo>=</mo><mfrac><mn>1</mn><mrow><mi>β</mi><mo>+</mo><mi>n</mi></mrow></mfrac><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda|y \in \Gamma(p = \alpha + \overset{n}{\sum}y_i, a = \frac{1}{\beta+n})</annotation></semantics></math>
Then, from Gut’s textbook, because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
is Gamma-distributed, we know
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mi>E</mi><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo>=</mo><mi>p</mi><mo>⋅</mo><mi>a</mi><mo>=</mo><mfrac><mrow><mi>α</mi><mo>+</mo><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub></mrow><mrow><mi>β</mi><mo>+</mo><mi>n</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">\hat{R_0} = E\lambda|y = p\cdot a = \frac{\alpha + \overset{n}{\sum}y_i}{\beta+n}</annotation></semantics></math><br />
<br />
In the next section, we will apply this to the CDC’c by county COVID-19
data, for selected US counties and world wide.</p>
<h2 id="assumptions-methodology.">Assumptions &amp; Methodology.</h2>
<h3 id="covid-19.">COVID-19.</h3>
<p>So, we have our
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(i)</annotation></semantics></math>
data for each county, as a function of 1 day steps. This would imply, if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>X</mi><mi>i</mi></msub><mo>=</mo><msub><mi>X</mi><mi>n</mi></msub></mrow><annotation encoding="application/x-tex">X_i = X_n</annotation></semantics></math>,
that
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mtext mathvariant="normal">generation</mtext><mo>=</mo><mn>1</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> day</mtext></mrow></mrow><annotation encoding="application/x-tex">n = \text{generation} = 1\text{   day}</annotation></semantics></math>
With the power of hindsight, we know that this is not the case. The
current CDC guidance is that after symptoms occur, most people are
infectious for the next 5 days <span class="citation"
data-cites="isolation_period"></span>. So, we should instead have:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mtext mathvariant="normal">generation</mtext><mo>=</mo><mn>5</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> days</mtext></mrow></mrow><annotation encoding="application/x-tex">n = \text{generation} = 5\text{   days}</annotation></semantics></math>
This is an easy enough fix, and we can use the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>T</mi><mi>i</mi></msub><annotation encoding="application/x-tex">T_i</annotation></semantics></math>
data for each county to calculate the appropriate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>X</mi><mi>n</mi></msub><annotation encoding="application/x-tex">X_n</annotation></semantics></math>,
given the generation length. This is simply
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msub><mi>T</mi><mi>i</mi></msub><mo>−</mo><msub><mi>T</mi><mrow><mi>i</mi><mo>−</mo><mn>5</mn></mrow></msub></mrow><annotation encoding="application/x-tex">X(n) = T_i - T_{i-5}</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n = 1</annotation></semantics></math>
for each county is with respect to the first detected case in that
county. The data looks similar in shape, but note the peaks are
higher:</p>
<figure data-latex-placement="h">
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/all_newcases_5days.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<!-- <img src="./all_newcases_5days.png" style="width:115.0%" /> -->
<figcaption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>:
New Cases Major US Counties, n = 5 days</figcaption>
</figure>
<p>Recall form before that
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>k</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msup><mi>λ</mi><mi>k</mi></msup></mrow><annotation encoding="application/x-tex">EX(k) = \lambda^k</annotation></semantics></math>
for a branching process, and because we are assuming the number of
infectious interaction to be
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Po(\lambda)</annotation></semantics></math>,
we therefore have
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>Y</mi><mo>=</mo><mi>λ</mi><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub></mrow><annotation encoding="application/x-tex">EY = \lambda = R_0</annotation></semantics></math>
and, thus,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>k</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msubsup><mi>R</mi><mn>0</mn><mi>k</mi></msubsup></mrow><annotation encoding="application/x-tex">EX(k) = R_0^k</annotation></semantics></math>
We can use the data we have graphed above to estimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
for each generation,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>.
We will denote the observed
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>k</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(k)</annotation></semantics></math>
as
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>k</mi></msub><annotation encoding="application/x-tex">x_k</annotation></semantics></math>,
and because for each county we only have 1 data point at each
generation,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>x</mi><mi>n</mi></msub><mo>=</mo><mover><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>k</mi><mo stretchy="false" form="postfix">)</mo></mrow><mo accent="true">‾</mo></mover><mo>≈</mo><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">x_n = \bar{X(k)} \approx EX(n)</annotation></semantics></math>
in this case. The interesting thing is, that even though we only have 1
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>
for each
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>≥</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n \geq 1</annotation></semantics></math>
for each county, because we have several generations and we are assuming
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo>=</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y_k^{(j)}\in Po(\lambda = R_0)</annotation></semantics></math>,
we end up with a point of estimate of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
per generation, per county. Also, let the estimators for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>–
which we will call
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>y</mi><mi>k</mi></msub><annotation encoding="application/x-tex">y_k</annotation></semantics></math>–
are simply derived by
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>y</mi><mi>k</mi></msub><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>k</mi></msub><msup><mo stretchy="false" form="postfix">)</mo><mfrac><mn>1</mn><mi>k</mi></mfrac></msup></mrow><annotation encoding="application/x-tex">y_k = (x_k)^{\frac{1}{k}}</annotation></semantics></math>
for each observed generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>.
In other words, if we let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>k</mi></msub><annotation encoding="application/x-tex">x_k</annotation></semantics></math>
be our observed newly infected at each generation of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">n=5</annotation></semantics></math>
days, then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>y</mi><mi>k</mi></msub><annotation encoding="application/x-tex">y_k</annotation></semantics></math>
will be the observed
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
at that generation.<br />
<br />
Those
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>y</mi><mi>k</mi></msub><annotation encoding="application/x-tex">y_k</annotation></semantics></math>
can be seen in Figure 8.</p>
<figure data-latex-placement="h">
<!-- <img src="./R0_estimations.png" style="width:50.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/R0_estimations.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>y</mi><mi>k</mi></msub><annotation encoding="application/x-tex">y_k</annotation></semantics></math>:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>λ</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{\lambda}</annotation></semantics></math>
estimations by generation, by county, for n = 5 days</figcaption>
</figure>
<p><br />
<br />
Let our prior distribution for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
be
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>∈</mo><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mover><mo>=</mo><mi>d</mi></mover><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda \in \Gamma(1,1) \overset{d}{= }Exp(1)</annotation></semantics></math>
and we can use our expression for the expectation of the posterior that
we derived earlier
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mi>E</mi><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo>=</mo><mi>p</mi><mo>⋅</mo><mi>a</mi><mo>=</mo><mfrac><mrow><mi>α</mi><mo>+</mo><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub></mrow><mrow><mi>β</mi><mo>+</mo><mi>n</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">\hat{R_0} = E\lambda|y = p\cdot a = \frac{\alpha + \overset{n}{\sum}y_i}{\beta+n}</annotation></semantics></math>
to estimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
for each county interest, assuming
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">n = 5</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>α</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\alpha = 1</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\beta = 1</annotation></semantics></math>.
A summary of these results (including varied generation duration) is in
Table 1.</p>
<div id="tab:estimates of r0">
<table>
<caption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
values for various generation lengths (i.e., infectious periods) in
various US counties.</caption>
<thead>
<tr>
<th style="text-align: center;"><strong>Generation days</strong></th>
<th style="text-align: center;"><strong>Berks</strong></th>
<th style="text-align: center;"><strong>Philadelphia</strong></th>
<th style="text-align: center;"><strong>Manhattan</strong></th>
<th style="text-align: center;"><strong>Los Angeles</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;">1.072</td>
<td style="text-align: center;">0.948</td>
<td style="text-align: center;">1.12</td>
<td style="text-align: center;">0.82</td>
</tr>
<tr>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;">1.776</td>
<td style="text-align: center;">1.946</td>
<td style="text-align: center;">2.335</td>
<td style="text-align: center;">1.152</td>
</tr>
<tr>
<td style="text-align: center;"><strong>10</strong></td>
<td style="text-align: center;">2.996</td>
<td style="text-align: center;">3.796</td>
<td style="text-align: center;">5.481</td>
<td style="text-align: center;">1.687</td>
</tr>
</tbody>
</table>
</div>
<h3 id="ebola.">Ebola.</h3>
<p>For our assumptions, we have know that Ebola is not infectious until
the onset of symptoms and it is also accepted that once symptoms emerge,
and untreated Ebola victim will dies in about 10 days <span
class="citation" data-cites="ebola_DeathTime"></span>. Therefore, the
infectious period (or generation length) is
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mi>g</mi><mi>e</mi><mi>n</mi><mi>e</mi><mi>r</mi><mi>a</mi><mi>t</mi><mi>i</mi><mi>o</mi><mi>n</mi><mo>=</mo><mn>10</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> days</mtext></mrow></mrow><annotation encoding="application/x-tex">n = generation = 10 \text{    days}</annotation></semantics></math>
and, recalling our notation that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>i</mi><annotation encoding="application/x-tex">i</annotation></semantics></math>
represents days, while
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
represents generations,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msub><mi>T</mi><mi>i</mi></msub><mo>−</mo><msub><mi>T</mi><mrow><mi>i</mi><mo>−</mo><mn>10</mn></mrow></msub></mrow><annotation encoding="application/x-tex">X(n) = T_i-T_{i-10}</annotation></semantics></math></p>
<p>Something else that is relevant in this case is that we are likely
missing data regarding the earlier generations of this outbreak. As
aforementioned, the outbreak was believed to have originated from bats
in Guinea in December of 2013 <span class="citation"
data-cites="ebola_cdc"></span>, but the data from the CDC <span
class="citation" data-cites="ebola_total1"></span><span class="citation"
data-cites="ebola_total2"></span> begins on March 25, 2014– with an
initial count of 86 Ebola cases. We have already established
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>10</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> days</mtext></mrow></mrow><annotation encoding="application/x-tex">n = 10 \text{ days}</annotation></semantics></math>,
this means that from December 31, 2013 to March 25, 2014 at least 5
generations have passed, as far as our Galton-Watson model is concerned.
So, we will adjust accordingly.</p>
<p>Again, recall that we are assuming the number of offspring Ebola
cases caused by an infected individual to be Poisson distributed,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Po(\lambda)</annotation></semantics></math>.
This means,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>k</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msubsup><mi>R</mi><mn>0</mn><mi>k</mi></msubsup></mrow><annotation encoding="application/x-tex">EX(k) = R_0^k</annotation></semantics></math>
where, to account for the missing generations,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi><mo>≥</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">k \geq 5</annotation></semantics></math>.</p>
<figure data-latex-placement="h">
<!-- <img src="./ebola_xn_py.png" style="width:75.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/ebola_xn_py.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>,
after making reasonable assumptions about the CDC data.</figcaption>
</figure>
<p>Now, using the same prior and estimation of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
we did in our exploration of the COVID-19 Data:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>∈</mo><mi mathvariant="normal">Γ</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mover><mo>=</mo><mi>d</mi></mover><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda \in \Gamma(1,1) \overset{d}{= }Exp(1)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mi>E</mi><mi>λ</mi><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo>=</mo><mi>p</mi><mo>⋅</mo><mi>a</mi><mo>=</mo><mfrac><mrow><mi>α</mi><mo>+</mo><mover><mo>∑</mo><mi>n</mi></mover><msub><mi>y</mi><mi>i</mi></msub></mrow><mrow><mi>β</mi><mo>+</mo><mi>n</mi></mrow></mfrac></mrow><annotation encoding="application/x-tex">\hat{R_0} = E\lambda|y = p\cdot a = \frac{\alpha + \overset{n}{\sum}y_i}{\beta+n}</annotation></semantics></math>
we can also make an estimate for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
of the Ebola outbreak in West Africa, varying some of the assumptions we
have already made:</p>
<div id="tab:estimates of r0">
<table>
<caption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
values for various generation lengths (i.e., infectious periods) in West
Africa.</caption>
<thead>
<tr>
<th style="text-align: center;"><strong>Generation (days)</strong></th>
<th style="text-align: center;"><strong>Initial generation</strong></th>
<th
style="text-align: center;"><strong><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math></strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;">0.528</td>
</tr>
<tr>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;">2.180</td>
</tr>
<tr>
<td style="text-align: center;"><strong>10</strong></td>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;">3.811</td>
</tr>
<tr>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;"><strong>3</strong></td>
<td style="text-align: center;">0.292</td>
</tr>
<tr>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;"><strong>3</strong></td>
<td style="text-align: center;">0.943</td>
</tr>
<tr>
<td style="text-align: center;"><strong>10</strong></td>
<td style="text-align: center;"><strong>3</strong></td>
<td style="text-align: center;">1.293</td>
</tr>
<tr>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;">0.287</td>
</tr>
<tr>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;">0.897</td>
</tr>
<tr>
<td style="text-align: center;"><strong>10</strong></td>
<td style="text-align: center;"><strong>5</strong></td>
<td style="text-align: center;">1.183</td>
</tr>
</tbody>
</table>
</div>
<h3 id="discussion-of-results.">Discussion of Results.</h3>
<p><strong>Methodology Discussion.</strong> This method is only feasible
if the infectious period for each individual is known– as we can see,
the estimated
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
depends quite a bit on this interval. Too low, and we may underestimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>,
and too high and we may overestimate
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
Though, another way to think of the infectious period = 1 day case, is
to think of it as the average number of people an infectious person
infects in a day– though, they maybe infectious for longer.<br />
<br />
<strong>Ebola Discussion.</strong> As previously mentioned in our
discussion of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
versus
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>,
the way the public attempts to mitigate the spread of disease has major
implications on the resultant
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
value. An interesting note, in the case of Ebola, is that unlike
COVID-19, Ebola is spread only through contact with infected fluids
<span class="citation" data-cites="ebola_cdc"></span>. This means one
can’t contract the disease through coughing or other aerosolized methods
of transmission. This means that all of the cases of Ebola in western
Africa from 2014 to 2016 came directly from physical contact with an
infected person’s viscera.<br />
<br />
The initial patient was believed to be a toddler from a village in
Guinea that was infected by bats, during December of 2013 <span
class="citation" data-cites="ebola_cdc"></span>. From there, it was able
to spread into neighboring countries Sierra Leone and Liberia because of
the increased mobility of people in West Africa compared to previous
Ebola outbreaks, and the fact that their were no early detection systems
for the disease and health care workers in the area were untrained on
diagnosing the ancient illness <span class="citation"
data-cites="ebola_who"></span>.<br />
<br />
It is reasonable to wonder how the disease spread so rapidly, given most
people would avoid someone with Ebola-like symptoms. This is where the
unique customs of western Africa shaped the effective reproduction,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>,
of Ebola in 2014. In the region, there is a strong "adherence to
ancestral funeral and burial rites singled out as fuelling large
explosions of new cases" <span class="citation"
data-cites="ebola_who"></span>. Medical anthropologists in the region
had even previously noted that the areas funeral practices were
exceptionally high risk.For example, in Liberia and Sierra Leone "some
mourners bathe in or anoint others with rinse water from the washing of
corpses" <span class="citation" data-cites="ebola_who"></span>. Bathing
in the viscera of a descendant of Ebola explains partially how Ebola was
able spread so rapidly in the region. Other factors include severe
shortage of medical workers, unfamiliarity with the disease, and the
reliance of "traditional" healers over modern medical practitioners all
being prevalent in the area.<br />
<br />
As for the actual results, we can see why making reasonable assumptions
is crucial if this method is to be used to determine
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
for Ebola. Clearly,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
cannot be less than 1, otherwise an outbreak would not occur, as not
enough people would be infected– this is why determining an appropriate
generation length in days is needed. As we can see, if the generation
duration is too low, in this case if we assume it to be 1 or 5 days, we
get
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">R_0 &lt;1</annotation></semantics></math>,
which is clearly false. Determining how far into outbreak we are is also
paramount: we are assuming
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">X(1) = 1</annotation></semantics></math>,
so if we underestimate how many generations of the disease have already
propagated, then we will <strong>overestimate</strong> our
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
For example, in the case of this Ebola data, the first data point we
have is 86 confirmed cases. The assumption
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">X(1) = 1</annotation></semantics></math>,
means if we assume
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>86</mn></mrow><annotation encoding="application/x-tex">X(2) = 86</annotation></semantics></math>
as well, we will get
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mn>9.27</mn></mrow><annotation encoding="application/x-tex">\hat{R_0} = 9.27</annotation></semantics></math>
as our first estimate. But, correcting for the missing early
generations, assume
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>86</mn></mrow><annotation encoding="application/x-tex">X(6) = 86</annotation></semantics></math>
will instead yield
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>86</mn><mo>=</mo><msup><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mn>6</mn></msup></mrow><annotation encoding="application/x-tex">EX(6) = 86= \hat{R_0}^{6}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mn>2.1</mn></mrow><annotation encoding="application/x-tex">\hat{R_0} = 2.1</annotation></semantics></math>
Interestingly, the estimates of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
do seem to level out over time, as seen in Figure 10.</p>
<figure data-latex-placement="h">

<figcaption>Estimates of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
for Ebola.</figcaption>
</figure>
<p>So, given our assumptions, assuming the first generation we have data
for is actually
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">n=5</annotation></semantics></math>
and that the generation length is 10 days,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mn>1.183</mn></mrow><annotation encoding="application/x-tex">\hat{R_0} = 1.183</annotation></semantics></math>
is our estimate for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
of Ebola. The accepted value is anywhere between 1.4-2.0, depending on
the outbreak and the methods used for estimation <span class="citation"
data-cites="ebola_r0"></span><span class="citation"
data-cites="ebola_cdc"></span>.</p>
<h1 id="parameter-estimation-using-the-best-linear-predictor.">Parameter
Estimation Using the Best Linear Predictor.</h1>
<p>From Allan Gut’s <em>An Intermediate Course in Probability</em><span
class="citation" data-cites="GIP"></span>, we know
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>h</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">h(\textbf{x})</annotation></semantics></math>
is called a regression line if
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>h</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>h</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>E</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐘</mtext><mo stretchy="false" form="prefix">|</mo><msub><mi>X</mi><mn>1</mn></msub><mo>=</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>X</mi><mi>n</mi></msub><mo>=</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>E</mi><mo stretchy="false" form="prefix">(</mo><mi>Y</mi><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐗</mtext><mo>=</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">h(\textbf{x}) = h(x_1,...,x_n) = E(\textbf{Y}|X_1=x_1,...,X_n=x_n) = E(Y|\textbf{X}=\textbf{x})</annotation></semantics></math>
This means in order to find the best linear predictor
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>L</mi><mo stretchy="false" form="prefix">(</mo><mi>X</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>β</mi><mo>+</mo><mi>α</mi><mi>X</mi></mrow><annotation encoding="application/x-tex">L(X) = \beta + \alpha X</annotation></semantics></math>
that is, the one that minimizes
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mo stretchy="false" form="prefix">(</mo><mi>Y</mi><mo>−</mo><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>+</mo><mi>α</mi><mi>X</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">E(Y-(\beta+\alpha X))</annotation></semantics></math>,
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>α</mi><mo>,</mo><mi>β</mi></mrow><annotation encoding="application/x-tex">\alpha,\beta</annotation></semantics></math>
are constants, we know <span class="citation" data-cites="GIP"></span>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><msub><mi>μ</mi><mi>y</mi></msub><mo>−</mo><mfrac><msub><mi>σ</mi><mrow><mi>x</mi><mi>y</mi></mrow></msub><msubsup><mi>σ</mi><mi>x</mi><mn>2</mn></msubsup></mfrac><msub><mi>μ</mi><mi>x</mi></msub><mo>=</mo><msub><mi>μ</mi><mi>y</mi></msub><mo>−</mo><mi>ρ</mi><mfrac><msub><mi>σ</mi><mi>y</mi></msub><msub><mi>σ</mi><mi>x</mi></msub></mfrac><msub><mi>μ</mi><mi>x</mi></msub></mrow><annotation encoding="application/x-tex">\beta = \mu_y - \frac{\sigma_{xy}}{\sigma^2_x}\mu_x = \mu_y - \rho\frac{\sigma_y}{\sigma_x}\mu_x</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>α</mi><mo>=</mo><mfrac><msub><mi>σ</mi><mrow><mi>x</mi><mi>y</mi></mrow></msub><msubsup><mi>σ</mi><mrow><mi>x</mi><mi>y</mi></mrow><mn>2</mn></msubsup></mfrac><mo>=</mo><mi>ρ</mi><mfrac><msub><mi>σ</mi><mi>y</mi></msub><msub><mi>σ</mi><mi>x</mi></msub></mfrac></mrow><annotation encoding="application/x-tex">\alpha = \frac{\sigma_{xy}}{\sigma_{xy}^2}=\rho\frac{\sigma_y}{\sigma_x}</annotation></semantics></math>
and thus
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mi>Y</mi><mo accent="true">̂</mo></mover><mo>=</mo><msub><mi>μ</mi><mi>y</mi></msub><mo>+</mo><mi>ρ</mi><mfrac><msub><mi>σ</mi><mi>y</mi></msub><msub><mi>σ</mi><mi>x</mi></msub></mfrac><mo stretchy="false" form="prefix">(</mo><mi>X</mi><mo>−</mo><msub><mi>μ</mi><mi>x</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\hat{Y} = \mu_y+\rho\frac{\sigma_y}{\sigma_x}(X-\mu_x)</annotation></semantics></math>
where
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>μ</mi><mi>y</mi></msub><mo>=</mo><mtext mathvariant="normal">mean of observed responses.</mtext></mrow><annotation encoding="application/x-tex">\mu_y = \text{mean of observed responses.}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>μ</mi><mi>x</mi></msub><mo>=</mo><mtext mathvariant="normal">mean of observed independent variable(s).</mtext></mrow><annotation encoding="application/x-tex">\mu_x = \text{mean of observed independent variable(s).}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>σ</mi><mi>y</mi><mn>2</mn></msubsup><mo>=</mo><mtext mathvariant="normal">variance of observed responses.</mtext></mrow><annotation encoding="application/x-tex">\sigma^2_y = \text{variance of observed responses.}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>σ</mi><mi>x</mi><mn>2</mn></msubsup><mo>=</mo><mtext mathvariant="normal">variance of observed independent variable(s).</mtext></mrow><annotation encoding="application/x-tex">\sigma^2_x = \text{variance of observed independent variable(s).}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>ρ</mi><mo>=</mo><mfrac><mrow><mi>C</mi><mi>o</mi><mi>v</mi><mo stretchy="false" form="prefix">(</mo><mi>X</mi><mo>,</mo><mi>Y</mi><mo stretchy="false" form="postfix">)</mo></mrow><msqrt><mrow><mi>V</mi><mi>a</mi><mi>r</mi><mi>X</mi><mo>⋅</mo><mi>V</mi><mi>a</mi><mi>r</mi><mi>Y</mi></mrow></msqrt></mfrac><mo>=</mo><mtext mathvariant="normal">correlation coefficient.</mtext></mrow><annotation encoding="application/x-tex">\rho = \frac{Cov(X,Y)}{\sqrt{Var X\cdot Var Y}}=\text{correlation coefficient.}</annotation></semantics></math></p>
<h2 id="estimating-r_0-using-regression.">Estimating
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
using Regression.</h2>
<h3 id="covid-19">COVID-19</h3>
<p>Perhaps a better way to estimate our parameter of interest,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>,
it’s just simply take advantage of the fact that the expected value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">Y_k^{(j)}</annotation></semantics></math>
is in fact
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>.
We also know from Theorem 7.2 in Gut’s text <span class="citation"
data-cites="GIP"></span> that the expected value of each generation in a
Galton-Watson branching process is simply
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mi>E</mi><mi>Y</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">EX(n) = (EY)^n</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
is the generation.<br />
<br />
We can use the same data as in our previous method, but representing it
differently, we can instead use <strong>linear regression</strong> to
determine and estimate of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
So, we can rewrite:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mi>E</mi><mi>Y</mi><msup><mo stretchy="false" form="postfix">)</mo><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">EX(n) = (EY)^n</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msup><mi>λ</mi><mi>n</mi></msup><mo>=</mo><msubsup><mi>R</mi><mn>0</mn><mi>n</mi></msubsup></mrow><annotation encoding="application/x-tex">EX(n) = \lambda^n = R_0^n</annotation></semantics></math>
In our data, let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>n</mi></msub><annotation encoding="application/x-tex">x_n</annotation></semantics></math>
be the observed value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>X</mi><mi>n</mi></msub><annotation encoding="application/x-tex">X_n</annotation></semantics></math>
in each generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>≥</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n \geq 1</annotation></semantics></math>,
and let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
be the observed value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
We therefore have
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>x</mi><mi>n</mi></msub><mo>=</mo><msup><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">x_n = \hat{R_0}^n</annotation></semantics></math>
We can easily linearize this by taking the natural logarithm of each
side of our observed data for each county:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>n</mi><mo>⋅</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\ln(x_n) = n\cdot \ln(\hat{R_0})</annotation></semantics></math>
Notice that this is in the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mo>=</mo><mi>α</mi><mo>+</mo><mi>β</mi><mo>⋅</mo><mi>x</mi></mrow><annotation encoding="application/x-tex">R = \alpha + \beta \cdot x</annotation></semantics></math>
format. Therefore, the slope,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>m</mi><annotation encoding="application/x-tex">m</annotation></semantics></math>,
of our transformed data can be used to find
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
as follows
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><msup><mi>e</mi><mi>m</mi></msup></mrow><annotation encoding="application/x-tex">\hat{R_0} = e^m</annotation></semantics></math></p>
<figure data-latex-placement="h">

<figcaption>Best Linear Predictor Regression Analysis on COVID-19
Data.</figcaption>
</figure>
<figure data-latex-placement="h">

<figcaption>Best Linear Predictor Regression Analysis on COVID-19
Data.</figcaption>
</figure>
<p>In some cases, what it actually looks like is <strong>two</strong>
linear functions, with different slopes. Around the third generation in
both the cases of Philadelphia county and Berks county, something
happens where the steep incline originally seen in cases suddenly drops
off. This begs the questions: <strong>did lock-downs decrease
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math></strong>?
Based on the graphs it seems so– in fact, the slopes seem to be
<strong>negative</strong> after generation 4, and a negative slope on
these graphs implies an
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">R_e &lt; 1</annotation></semantics></math>.
We will explore this more in the next section, again using Bayesian A/B
Testing to see if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
before and after lock-downs is actually different in subsequent
sections.</p>
<h3 id="ebola.-1">Ebola.</h3>
<figure data-latex-placement="h">
<!-- <img src="./Ebola_linearization1_genALL.png" style="width:75.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/Ebola_linearization1_genALL.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
estimation for for all generations (3/25/2014-4/13/2016)</figcaption>
</figure>
<p>In the case of Ebola, the distinction between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
becomes even more relevant and visible. As we can see in the figure
above, we can see a distinct drop in the slope somewhere around the 20th
generation (about 200 days, so late November or early December of 2014
in real time). Recall, that the relationship between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
(or rather
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>)
and the slope,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>m</mi><annotation encoding="application/x-tex">m</annotation></semantics></math>,
is
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>⇔</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><msup><mi>e</mi><mi>m</mi></msup></mrow><annotation encoding="application/x-tex">m = \ln(\hat{R_0}) \iff \hat{R_0} = e^m</annotation></semantics></math>
So, the sudden decrease in slope,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>m</mi><annotation encoding="application/x-tex">m</annotation></semantics></math>,
reflects a decrease in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>.
In fact,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>&lt;</mo><mn>0</mn><mo>⇔</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>&lt;</mo><mn>1</mn><mo>⇔</mo><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">m &lt; 0 \iff \hat{R_0} &lt; 1 \iff \eta = 1</annotation></semantics></math>
In fact, if we split the data at the 20th generation and examine the
resultant
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
values, we see that before the 20th generation there is an
<strong>increasing</strong> relationship in between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\ln X(n)</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>,
with a calculated value of
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mn>1.20</mn></mrow><annotation encoding="application/x-tex">\hat{R_0} = 1.20</annotation></semantics></math>
Versus, after the 25th generation a fairly linear
<strong>decreasing</strong>relationship in between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>X</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\ln(X_n)</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>,
with a calculated value of
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><mn>0.739</mn></mrow><annotation encoding="application/x-tex">\hat{R_0} = 0.739</annotation></semantics></math></p>
<figure data-latex-placement="h">

<figcaption>Best Linear Predictor Regression Analysis on Ebola
Data.</figcaption>
</figure>
<p>From Ahlberg’s paper <span class="citation" data-cites="sir3"></span>
and Gut’s book <span class="citation" data-cites="GIP"></span>, we know
that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>&lt;</mo><mn>1</mn><mo>⇔</mo><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\hat{R_0} &lt; 1 \iff \eta = 1</annotation></semantics></math>
means the outbreak will die out. Looking at the data in Figure 13, this
again begs the question of whether or not human intervention
<strong>decreased</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
after generation 20, in the case of the 2014-2016 Ebola outbreak in West
Africa.</p>
<h2 id="bayesian-linear-regression.">Bayesian Linear Regression.</h2>
<p>Instead of simply employing the Best Linear Predictor (BLP), we can
use Bayesian Linear Regression. As the name suggests, this is a method
that instead of delivering point estimates of the regression parameters
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>α</mi><annotation encoding="application/x-tex">\alpha</annotation></semantics></math>
(slope), and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
(intercept), will deliver posterior distributions for these parameters.
We will explore and implement two different methods of Bayesian Linear
Regression.</p>
<h3 id="objective-blr.">Objective BLR.</h3>
<p>From Dr. Jarad Niemi of Iowa State University’s <span
class="citation" data-cites="iowa2"></span> lecture on objective
Bayesian linear regression, we can, in the multivariate case, define our
regression problem as
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐘</mtext><mo>∈</mo><mi>N</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐗</mtext><mi>β</mi><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><mi>I</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\textbf{Y} \in N(\textbf{X}\beta, \sigma^2I)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐘</mtext><mo>,</mo><mtext mathvariant="bold">𝐗</mtext></mrow><annotation encoding="application/x-tex">\textbf{Y}, \textbf{X}</annotation></semantics></math>
are our response variable and independent variables, respectively, of
the forms
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐘</mtext><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>y</mi><mn>1</mn></msub><mo>,</mo><msub><mi>y</mi><mn>2</mn></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>y</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\textbf{Y} = (y_1, y_2, ..., y_n)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐗</mtext><mo>=</mo><mrow><mo stretchy="true" form="prefix">[</mo><mtable><mtr><mtd columnalign="center" style="text-align: center"><msub><mi>X</mi><mn>1</mn></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><msub><mi>X</mi><mn>2</mn></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><msub><mi>X</mi><mi>n</mi></msub></mtd></mtr></mtable><mo stretchy="true" form="postfix">]</mo></mrow><mo>=</mo><mrow><mo stretchy="true" form="prefix">[</mo><mtable><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>12</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>13</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><mi>…</mi></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mn>1</mn><mi>k</mi></mrow></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>22</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>23</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><mi>…</mi></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mn>2</mn><mi>k</mi></mrow></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mi>n</mi><mn>2</mn></mrow></msub></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mi>n</mi><mn>3</mn></mrow></msub></mtd><mtd columnalign="center" style="text-align: center"><mi>…</mi></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mi>n</mi><mi>k</mi></mrow></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"></mtd></mtr></mtable><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">\textbf{X} = \begin{bmatrix}
    X_1\\X_2\\\vdots \\X_n
\end{bmatrix} = \begin{bmatrix}
    1&amp;x_{12}&amp;x_{13}&amp;\hdots&amp;x_{1k}\\
    1&amp;x_{22}&amp;x_{23}&amp;\hdots&amp;x_{2k}\\
    \vdots&amp;\vdots&amp;\vdots&amp;\vdots\\
    1&amp;x_{n2}&amp;x_{n3}&amp;\hdots&amp;x_{nk}\\
\end{bmatrix}</annotation></semantics></math> where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
is the number of observations, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
the number of independent variables.<br />
We are also assuming that our
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mtext mathvariant="bold">𝐗</mtext><mi>i</mi></msub><annotation encoding="application/x-tex">\textbf{X}_i</annotation></semantics></math>’s
are independent random variables, there is a constant variance,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>σ</mi><mn>2</mn></msup><annotation encoding="application/x-tex">\sigma^2</annotation></semantics></math>,
and that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mtext mathvariant="bold">𝐗</mtext><mrow><mi>i</mi><mn>1</mn></mrow></msub><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\textbf{X}_{i1} = 1</annotation></semantics></math>
are our intercepts.<br />
<br />
We will choose a non-informative constant prior
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><mo stretchy="false" form="postfix">)</mo><mo>∝</mo><mfrac><mn>1</mn><msup><mi>σ</mi><mn>2</mn></msup></mfrac></mrow><annotation encoding="application/x-tex">p(\beta, \sigma^2)    \propto \frac{1}{\sigma^2}</annotation></semantics></math>
Then, using Baye’s Theorem
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐘</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo stretchy="false" form="prefix">|</mo><msup><mi>σ</mi><mn>2</mn></msup><mo>,</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>p</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>σ</mi><mn>2</mn></msup><mo>,</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mrow><annotation encoding="application/x-tex">p(\beta, \sigma^2|\textbf{Y}) = \frac{p(\beta|\sigma^2,y)\cdot p(\sigma^2,y)}{p(\beta, \sigma^2)}</annotation></semantics></math>
and because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">p(\beta, \sigma^2)</annotation></semantics></math>
is proportional to a constant
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐘</mtext><mo stretchy="false" form="postfix">)</mo><mo>∝</mo><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>β</mi><mo stretchy="false" form="prefix">|</mo><msup><mi>σ</mi><mn>2</mn></msup><mo>,</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>p</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>σ</mi><mn>2</mn></msup><mo>,</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">p(\beta, \sigma^2|\textbf{Y}) \propto 
p(\beta|\sigma^2,y)\cdot p(\sigma^2,y)</annotation></semantics></math>
This leaves us with the following posteriors for our parameters
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>σ</mi><mn>2</mn></msup><annotation encoding="application/x-tex">\sigma^2</annotation></semantics></math>:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo stretchy="false" form="prefix">|</mo><msup><mi>σ</mi><mn>2</mn></msup><mo>∈</mo><mi>N</mi><mo stretchy="false" form="prefix">(</mo><mover><mi>β</mi><mo accent="true">̂</mo></mover><mo>,</mo><msup><mi>σ</mi><mn>2</mn></msup><msub><mi>V</mi><mi>β</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\beta|\sigma^2 \in N(\hat{\beta}, \sigma^2 V_\beta)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>σ</mi><mn>2</mn></msup><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐘</mtext><mo>∈</mo><mi>I</mi><mi>n</mi><mi>v</mi><mo>−</mo><mi>G</mi><mi>a</mi><mi>m</mi><mi>m</mi><mi>a</mi><mo stretchy="false" form="prefix">(</mo><mfrac><mrow><mi>n</mi><mo>−</mo><mi>k</mi></mrow><mn>2</mn></mfrac><mo>,</mo><mfrac><mrow><mo stretchy="false" form="prefix">[</mo><msup><mi>s</mi><mn>2</mn></msup><mi>n</mi><mo>−</mo><mi>k</mi><mo stretchy="false" form="postfix">]</mo></mrow><mn>2</mn></mfrac><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\sigma^2|\textbf{Y}\in Inv-Gamma(\frac{n-k}{2}, \frac{[s^2n-k]}{2})</annotation></semantics></math>
where, with the addition of QR-factorization of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐗</mtext><mo>=</mo><mtext mathvariant="bold">𝐐𝐑</mtext></mrow><annotation encoding="application/x-tex">\textbf{X} = \textbf{QR}</annotation></semantics></math>,
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mtext mathvariant="bold">𝐐</mtext><annotation encoding="application/x-tex">\textbf{Q}</annotation></semantics></math>
is an orthonormal matrix and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mtext mathvariant="bold">𝐑</mtext><annotation encoding="application/x-tex">\textbf{R}</annotation></semantics></math>
and upper right triangular,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mi>β</mi><mo accent="true">̂</mo></mover><mo>=</mo><msup><mtext mathvariant="bold">𝐑</mtext><mrow><mi>−</mi><mn>1</mn></mrow></msup><mo stretchy="false" form="prefix">[</mo><msup><mtext mathvariant="bold">𝐑</mtext><mo>′</mo></msup><msup><mo stretchy="false" form="postfix">]</mo><mrow><mi>−</mi><mn>1</mn></mrow></msup><mo>=</mo><mtext mathvariant="normal">least squares estimator.</mtext></mrow><annotation encoding="application/x-tex">\hat{\beta} = \textbf{R}^{-1}[\textbf{R}&#39;]^{-1} = \text{least squares estimator.}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>V</mi><mi>β</mi></msub><mo>=</mo><msup><mtext mathvariant="bold">𝐑</mtext><mrow><mi>−</mi><mn>1</mn></mrow></msup><msup><mtext mathvariant="bold">𝐐</mtext><mo>′</mo></msup><mtext mathvariant="bold">𝐘</mtext></mrow><annotation encoding="application/x-tex">V_\beta =\textbf{R}^{-1}\textbf{Q}&#39;\textbf{Y}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>s</mi><mn>2</mn></msup><mo>=</mo><mfrac><mn>1</mn><mrow><mi>n</mi><mo>−</mo><mi>k</mi></mrow></mfrac><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐘</mtext><mo>−</mo><mtext mathvariant="bold">𝐗</mtext><mover><mi>β</mi><mo accent="true">̂</mo></mover><msup><mo stretchy="false" form="postfix">)</mo><mo>′</mo></msup><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐘</mtext><mo>−</mo><mtext mathvariant="bold">𝐗</mtext><mover><mi>β</mi><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mrow><mrow><mtext mathvariant="normal">estimator of </mtext><mspace width="0.333em"></mspace></mrow><msup><mi>σ</mi><mn>2</mn></msup><mtext mathvariant="normal">.</mtext></mrow></mrow><annotation encoding="application/x-tex">s^2 = \frac{1}{n-k}(\textbf{Y}-\textbf{X}\hat{\beta})&#39;(\textbf{Y}-\textbf{X}\hat{\beta}) = \text{estimator of $\sigma^2$.}</annotation></semantics></math></p>
<h3 id="markov-chain-monte-carlo-mcmc-blr.">Markov Chain Monte Carlo
(MCMC) BLR.</h3>
<p>The goal of this method is very similar to that of objective BLR: to
determine and sample from the posterior distributions of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>α</mi><annotation encoding="application/x-tex">\alpha</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>σ</mi><annotation encoding="application/x-tex">\sigma</annotation></semantics></math>.
But, the objective method relies on priors and posteriors that are well
defined. The Markov Chain Monte Carlo (MCMC) method instead uses and
algorithm to traverse and sample from uncommon posterior
distributions.<br />
<br />
<strong>Intuition.</strong> In the context of Bayesian Inference, the
Metropolis-Hastings algorithm can be used to draw random samples from a
posterior distribution. The algorithm works by simulation a Markov
Chain– in essence, MCMC is given some initial value,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mn>1</mn></msub><annotation encoding="application/x-tex">x_1</annotation></semantics></math>,
then a new value, call it
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mn>2</mn></msub><annotation encoding="application/x-tex">x_2</annotation></semantics></math>
is proposed. The ratio between the two values is evaluated, and if the
ratio is found to be acceptable it is kept, otherwise it is disregarded.
Eventually, iterating through this algorithm, the samples will being to
approximate the posterior distribution.<br />
<br />
This is especially useful in Bayesian Inference, where the true
posterior distribution may be difficult or impossible to analytically
derive <span class="citation" data-cites="MH"></span> <span
class="citation" data-cites="intro_to_mcmc"></span>. As we draw more an
more samples from the posterior distribution, it will begin to converge
to the true posterior PDF– and this makes it simple for us to plat the
distributions, and determine key statistics about our parameters of
interest, such as mean and variance, to better understand what we
actually know about the parameter.<br />
<br />
<strong>Metropolis-Hastings.</strong> In the context of our exploration
of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
values for COVID-19, the Metropolis-Hastings algorithm is the following
<span class="citation" data-cites="bu_lec"></span>:</p>
<ol>
<li><p>Begin with some initial initial parameter, call it
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>λ</mi><mi>c</mi></msup><annotation encoding="application/x-tex">\lambda^c</annotation></semantics></math></p></li>
<li><p>Evaluate the posterior:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="prefix">|</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda^c|\hat{R_0})</annotation></semantics></math></p></li>
<li><p>New random draw for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>λ</mi><mo>′</mo></msup><annotation encoding="application/x-tex">\lambda&#39;</annotation></semantics></math>
from the "jump" distribution, which has a mean of the current parameter
value,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>λ</mi><mi>c</mi></msup><annotation encoding="application/x-tex">\lambda^c</annotation></semantics></math></p>
<ul>
<li><p>The most common jump distribution is the Normal distribution
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>J</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>N</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">J(\lambda&#39;|\lambda^c) = N(\lambda&#39;|\lambda^c)</annotation></semantics></math></p></li>
</ul></li>
<li><p>Evaluate the posterior:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda&#39;|\hat{R_0})</annotation></semantics></math></p></li>
<li><p>Decide whether to accept of reject the new value. For example,
the accept criteria,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mo>=</mo><mfrac><mfrac><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>J</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mfrac><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>J</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="prefix">|</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mfrac></mrow><annotation encoding="application/x-tex">a = \frac{\frac{p(\lambda&#39;)}{J(\lambda&#39;|\lambda^c)}}{\frac{p(\lambda^c)}{J(\lambda^c|\lambda&#39;)}}</annotation></semantics></math>,
we will
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mtext mathvariant="bold">𝐀𝐜𝐜𝐞𝐩𝐭: </mtext><mspace width="0.333em"></mspace></mrow><mi>a</mi><mo>&gt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\textbf{Accept:    } a &gt;1</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mtext mathvariant="bold">𝐑𝐞𝐣𝐞𝐜𝐭: </mtext><mspace width="0.333em"></mspace></mrow><mi>a</mi><mo>≤</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\textbf{Reject:    } a \leq 1</annotation></semantics></math>
where to <strong>reject</strong> is to keep the current value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>λ</mi><mi>c</mi></msup><annotation encoding="application/x-tex">\lambda^c</annotation></semantics></math>
In practice, this may look something like:</p>
<ol>
<li><p>Initialize:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>λ</mi><mi>c</mi></msup><mo>=</mo><msub><mi>λ</mi><mn>1</mn></msub></mrow><annotation encoding="application/x-tex">\lambda^c = \lambda_1</annotation></semantics></math></p></li>
<li><p>For
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>t</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><mi>N</mi></mrow><annotation encoding="application/x-tex">t = 1,2,...,N</annotation></semantics></math></p>
<ul>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>λ</mi><mo>′</mo></msup><mo>=</mo><msup><mi>λ</mi><mi>c</mi></msup><mo>+</mo><mi>N</mi><mo stretchy="false" form="prefix">(</mo><mn>0</mn><mo>,</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\lambda&#39; = \lambda^c + N(0,1)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mo>=</mo><mfrac><mfrac><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>J</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="postfix">)</mo></mrow></mfrac><mfrac><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>J</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>λ</mi><mi>c</mi></msup><mo stretchy="false" form="prefix">|</mo><msup><mi>λ</mi><mo>′</mo></msup><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mfrac></mrow><annotation encoding="application/x-tex">a = \frac{\frac{p(\lambda&#39;)}{J(\lambda&#39;|\lambda^c)}}{\frac{p(\lambda^c)}{J(\lambda^c|\lambda&#39;)}}</annotation></semantics></math></p></li>
<li><p>If
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mo>&gt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">a &gt; 1</annotation></semantics></math></p>
<ul>
<li><p><strong>Accept:</strong><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>λ</mi><mi>c</mi></msup><mo>=</mo><msup><mi>λ</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">\lambda^c = \lambda&#39;</annotation></semantics></math></p></li>
</ul></li>
<li><p>Else</p>
<ul>
<li><p><strong>Reject:</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>λ</mi><mi>c</mi></msup><mo>=</mo><msup><mi>λ</mi><mi>c</mi></msup></mrow><annotation encoding="application/x-tex">\lambda^c = \lambda^c</annotation></semantics></math></p></li>
</ul></li>
</ul></li>
</ol></li>
</ol>
<h3 id="covid-19-results-globally-in-los-angeles-county-ca.">COVID-19
Results Globally &amp; in Los Angeles County, CA.</h3>
<figure data-latex-placement="H">

<figcaption>World Wide COVID-19 Bayesian Regression
Methods.</figcaption>
</figure>
<figure data-latex-placement="H">

<figcaption>Los Angeles County COVID-19 Bayesian Regression
Methods.</figcaption>
</figure>
<p>As we discussed earlier, Berks, Philadelphia, and Manhattan (see
Figures 11 &amp; 12) are not particularly linear– they in fact seem to
have two distinct sections, where the slope changes drastically. As
we’ll see in the next section, this is because there is strong evidence
of switch points,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>,
in these counties. That is, there is evidence that a certain generation,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>,
the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
of COVID-19 in these counties changes drastically.<br />
For reasons discussed in the subsequent sections, this does not seem to
be the case for Los Angeles county, or COVID-19 globally (see Figures 15
&amp; 16). So, these data sets are good candidates for continuing our
exploration of linear regression.<br />
Recall that our linear regression model takes the form
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>n</mi><mo>⋅</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\ln(x_n) = n\cdot\ln(\hat{R_0})</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>n</mi></msub><annotation encoding="application/x-tex">x_n</annotation></semantics></math>
represents our observed values of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(n)</annotation></semantics></math>,
the number of newly infected each generation and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_0}</annotation></semantics></math>
our observed values for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>.
Generally regression lines will have the form
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mo>=</mo><mi>α</mi><mo>+</mo><mi>β</mi><mo>⋅</mo><mi>x</mi></mrow><annotation encoding="application/x-tex">R = \alpha + \beta\cdot x</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\beta  = \ln(\hat{R_0})</annotation></semantics></math>
is the slope of the regression line while
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>α</mi><annotation encoding="application/x-tex">\alpha</annotation></semantics></math>
is the intercept of the regression line.<br />
In the global case, we can see that the posterior distributions for both
methods of Bayesian linear regression (BLR) yield fairly similar
results, and for the slope,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\beta = \ln(\hat{R_0})</annotation></semantics></math>,
and intercept,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>α</mi><annotation encoding="application/x-tex">\alpha</annotation></semantics></math>,
yield means of
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.17</mn><mrow><mtext mathvariant="bold">, </mtext><mspace width="0.333em"></mspace></mrow><mi>α</mi><mo>=</mo><mn>8.9</mn></mrow><annotation encoding="application/x-tex">\beta =  \ln(\hat{R_0}) = 0.17\textbf{,  }\alpha = 8.9</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.1660</mn><mrow><mtext mathvariant="bold">, </mtext><mspace width="0.333em"></mspace></mrow><mi>α</mi><mo>=</mo><mn>8.8542</mn></mrow><annotation encoding="application/x-tex">\beta= \ln(\hat{R_0}) =0.1660 \textbf{,  }\alpha = 8.8542</annotation></semantics></math>
for MCMC method and the objective Bayesian regression techniques,
respectively.<br />
And, these compare well to the Best Linear Predictor (BLP) results,
which yielded:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.1706</mn></mrow><annotation encoding="application/x-tex">\beta = \ln(\hat{R_0})=0.1706</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>α</mi><mo>=</mo><mn>8.7661</mn></mrow><annotation encoding="application/x-tex">\alpha = 8.7661</annotation></semantics></math></p>
<p>And we can see similar the two lines BLP and BLR produce are in
Figures 15(c) and 16(c) above, and we can see that both BLP and BLR
estimate about an
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mn>1.18</mn></mrow><annotation encoding="application/x-tex">R_0 = 1.18</annotation></semantics></math>,
globally for the duration of this data (that is, from 1/22/2020 to
7/27/2020). (Note: for the sake of clarity in figure (c), we excluded
the MCMC regression line.)<br />
<br />
Similar parity of results can be in the case of Los Angeles County, CA.
For the MCMC and objectibe BLR methods, respectively, we see parameters
of
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.22</mn><mrow><mtext mathvariant="bold">, </mtext><mspace width="0.333em"></mspace></mrow><mi>α</mi><mo>=</mo><mn>3.1</mn></mrow><annotation encoding="application/x-tex">\beta =  \ln(\hat{R_0}) = 0.22\textbf{,  }\alpha = 3.1</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.2153</mn><mrow><mtext mathvariant="bold">, </mtext><mspace width="0.333em"></mspace></mrow><mi>α</mi><mo>=</mo><mn>3.0632</mn></mrow><annotation encoding="application/x-tex">\beta= \ln(\hat{R_0}) =0.2153 \textbf{,  }\alpha = 3.0632</annotation></semantics></math>
and for the BLP method
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.2228</mn></mrow><annotation encoding="application/x-tex">\beta = \ln(\hat{R_0})=0.2228</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>α</mi><mo>=</mo><mn>2.909</mn></mrow><annotation encoding="application/x-tex">\alpha = 2.909</annotation></semantics></math></p>
<p>We can also examine the posterior distributions of the parameters,
and see thatthe resultant variance is roughly the same in the MCMC and
objective BLR methods, and that these variances are fairly low. We see
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>V</mi><mi>a</mi><mi>r</mi><mi>σ</mi><mo>=</mo><mn>0.0340</mn></mrow><annotation encoding="application/x-tex">Var\sigma = 0.0340</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>V</mi><mi>a</mi><mi>r</mi><mi>β</mi><mo>=</mo><mn>0.0007</mn></mrow><annotation encoding="application/x-tex">Var\beta = 0.0007</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>V</mi><mi>a</mi><mi>r</mi><mi>α</mi><mo>=</mo><mn>0.3776</mn></mrow><annotation encoding="application/x-tex">Var\alpha = 0.3776</annotation></semantics></math>.
The variance of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
is especially low, which means we can be more certain the true value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>,
our slope, and therefore our prediction of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo>=</mo><msup><mi>e</mi><mi>β</mi></msup></mrow><annotation encoding="application/x-tex">\hat{R_0} = e^\beta</annotation></semantics></math>
are well fit and well explained by the available data.<br />
<br />
It is also interesting to consider what these parameters represent in
the real world. We have already discussed this for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\beta =  \ln(\hat{R_0})</annotation></semantics></math>.
The parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
enables us to find and estimate for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>,
which represents the average number of people an infected individual
infects in the next generation, or in the case of our Galton-Watson
branching process model:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>R</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Po(R_0)</annotation></semantics></math>.<br />
The parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>α</mi><annotation encoding="application/x-tex">\alpha</annotation></semantics></math>
is similar. We know
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>α</mi></mrow><annotation encoding="application/x-tex">\ln(x_n) = \alpha</annotation></semantics></math>
when
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">n = 0</annotation></semantics></math>,
so
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mn>0</mn></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>α</mi></mrow><annotation encoding="application/x-tex">\ln(x_0) = \alpha</annotation></semantics></math>.
Therefore,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>x</mi><mn>0</mn></msub><mo>=</mo><msup><mi>e</mi><mi>α</mi></msup></mrow><annotation encoding="application/x-tex">x_0 = e^\alpha</annotation></semantics></math>
gives us a potential estimate for the size of the initial population of
infected in each county or globally.<br />
In both BLP and BLR we also see reasonably high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>R</mi><mn>2</mn></msup><annotation encoding="application/x-tex">R^2</annotation></semantics></math>
values of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>0.7929</mn><annotation encoding="application/x-tex">0.7929</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>0.7935</mn><annotation encoding="application/x-tex">0.7935</annotation></semantics></math>,
respectively, in the global case, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>0.7135</mn><annotation encoding="application/x-tex">0.7135</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>0.7143</mn><annotation encoding="application/x-tex">0.7143</annotation></semantics></math>,
respectively, in the case of Los Angeles county. According to Duke
University <span class="citation" data-cites="duke_r2"></span>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>R</mi><mn>2</mn></msup><annotation encoding="application/x-tex">R^2</annotation></semantics></math>
is the percent of the data’s variance explained by the regression model,
or, in other words, "the fraction by which the variance of the errors is
less than the variance of the dependent variable". This means that about
75% and 71% of the variance in our
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\ln(x_n)</annotation></semantics></math>
data is accounted for by some form of linear regression, and therefore
gives some credibility to our predictions of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mn>1.18</mn></mrow><annotation encoding="application/x-tex">R_0 = 1.18</annotation></semantics></math>
in the global case and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>=</mo><mn>1.20</mn></mrow><annotation encoding="application/x-tex">R_0 = 1.20</annotation></semantics></math>
in the Los Angeles case– both of which are similar to the currently
accepted values for the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
of COVID-19 discussed earlier.</p>
<h1 id="preventive-measures-during-the-covid-19-pandemic.">Preventive
Measures During the COVID-19 Pandemic.</h1>
<h2 id="the-difference-in-lambda-before-after-lockdowns.">The Difference
in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
Before &amp; After Lockdowns.</h2>
<p>The book <em>Bayesian Methods for Hackers</em> <span class="citation"
data-cites="hackers"></span> introduces the idea of using Bayesian
statistics and and Markov Chain Monte Carlo–via the Python package,
PyMC– to determine if the parameter of a random variable being used to
model data changes over time. In particular, we are going to be
examining the COVID-19 data from the counties of interest – Manhattan,
New York, Philadelphia, Pennsylvania, Berks, Pennsylvania, and Los
Angeles, California – to see if we can determine if a switch point
occurs for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>.
Recall that we earlier demonstrated that
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>=</mo><mi>λ</mi></mrow><annotation encoding="application/x-tex">R_e = \lambda</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>Y</mi><mi>k</mi><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>λ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">Y^{(j)}_k \in Po(\lambda)</annotation></semantics></math>
represents the number of new cases causes by (i.e., in Galton-Watson
terms, the offspring of) the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>k</mi><mrow><mi>t</mi><mi>h</mi></mrow></msup><annotation encoding="application/x-tex">k^{th}</annotation></semantics></math>
individual in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>.
This means, we are interested in whether
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
changes as the pandemic progresses in these four counties. To do this,
we are going to return the linearized data used in the previous section.
From this, we can glean spot estimates of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
for each county, at each generation. This will allow us to have data in
the form of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
vs. generation. So, recalling
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>m</mi><annotation encoding="application/x-tex">m</annotation></semantics></math>
means the slope, from the previous section we have
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>m</mi><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>⇔</mo><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><mo>=</mo><msup><mi>e</mi><mi>m</mi></msup></mrow><annotation encoding="application/x-tex">m = \ln(\hat{R_e}) \iff \hat{R_e} = e^m</annotation></semantics></math>
This means a spot estimate of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{{R_0}}</annotation></semantics></math>
at each generation can be found simply from
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msup><mover><mi>λ</mi><mo accent="true">̂</mo></mover><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msup><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msup><mo>=</mo><mrow><mi mathvariant="normal">exp</mi><mo>&#8289;</mo></mrow><mo minsize="300%" maxsize="300%" stretchy="true" form="prefix">(</mo><mfrac><mrow><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mn>1</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> generation</mtext></mrow></mrow></mfrac><mo minsize="300%" maxsize="300%" stretchy="true" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\hat{\lambda}^{(j)}=)\hat{R_e}^{(j)} = \exp\Biggl(\frac{\ln(X(j+1) - \ln(X(j))}{1 \text{  generation}}\Biggr)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(j)</annotation></semantics></math>
is the number of newly infected in generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>.
We can see below the spot estimates of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
over time in each county:</p>
<figure data-latex-placement="h">
<!-- <img src="./all spot ests AB testing.png" style="width:75.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/all%20spot%20ests%20AB%20testing.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
estimation for for all generations during COVID-19 Pandemic
(1/22/20-7/27/20)</figcaption>
</figure>
<p>As we have already seen through out this project so far, and as is
noted by <em>Bayesian Methods for Hackers</em><span class="citation"
data-cites="hackers"></span>, Poisson distributions are appropriate for
estimating this kind of count data. So, we will assume
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
follows a Poisson distribution– in other words,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mn>0</mn></msub><mo>∈</mo><mi>P</mi><mi>o</mi><mo stretchy="false" form="prefix">(</mo><mi>ϵ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">R_0 \in Po(\epsilon)</annotation></semantics></math>,
and the number of newly infected per individual generation is
Poisson-distributed, with parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>ϵ</mi><annotation encoding="application/x-tex">\epsilon</annotation></semantics></math>.<br />
<br />
Now, for our switch point, we are assuming
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>=</mo><mrow><mo stretchy="true" form="prefix">{</mo><mtable><mtr><mtd columnalign="left" style="text-align: left"><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>1</mn></msub><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></mtd><mtd columnalign="left" style="text-align: left"><mi>t</mi><mo>&lt;</mo><mi>τ</mi></mtd></mtr><mtr><mtd columnalign="left" style="text-align: left"><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>2</mn></msub><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup></mtd><mtd columnalign="left" style="text-align: left"><mi>t</mi><mo>≥</mo><mi>τ</mi></mtd></mtr></mtable></mrow></mrow><annotation encoding="application/x-tex">R_e =  \begin{cases} 
      (\lambda_1=)R_e^{(1)} &amp; t&lt;\tau \\
      (\lambda_2=)R_e^{(2)} &amp; t \geq \tau
   \end{cases}</annotation></semantics></math> Where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>
represents the generation at which
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
(noticeably) changes. As for our prior distributions for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>1</mn></msub><annotation encoding="application/x-tex">\lambda_1</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>2</mn></msub><annotation encoding="application/x-tex">\lambda_2</annotation></semantics></math>,
we will use an exponential distribution with parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>α</mi><mo>=</mo><mfrac><mi>N</mi><mrow><msub><mo>∑</mo><mi>k</mi></msub><msub><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mi>k</mi></msub></mrow></mfrac></mrow><annotation encoding="application/x-tex">\alpha = \frac{N}{\sum_k \hat{R_0}_k}</annotation></semantics></math>.
So, as for priors we have <span class="citation"
data-cites="hackers"></span>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>1</mn></msub><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>α</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\lambda_1=)R_e^{(1)} \in Exp(\alpha)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>2</mn></msub><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>∈</mo><mi>E</mi><mi>x</mi><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>α</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\lambda_2=)R_e^{(2)} \in Exp(\alpha)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>τ</mi><mo>∈</mo><mi>U</mi><mo stretchy="false" form="prefix">(</mo><mn>0</mn><mo>,</mo><mi>N</mi><mo>−</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\tau \in U(0,N-1)</annotation></semantics></math>
Then, we will use Markov Chain Monte Carlo (MCMC) to determine the
likelihood of each generation being the switch point. This is relatively
straight froward and looks like:</p>
<ol>
<li><p>Assign each variable the appropriate prior
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>1</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda_1)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>2</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda_2)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>τ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\tau)</annotation></semantics></math></p></li>
<li><p>Assume each generation is the switch point,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>,
and in each case, assign each generation and corresponding
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mover><msub><mi>R</mi><mn>0</mn></msub><mo accent="true">̂</mo></mover><mrow><mo stretchy="false" form="prefix">(</mo><mi>j</mi><mo stretchy="false" form="postfix">)</mo></mrow></msup><annotation encoding="application/x-tex">\hat{R_0}^{(j)}</annotation></semantics></math>
the appropriate value of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>.</p></li>
<li><p>For each potential switch point, determine the posterior
probabilities
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>1</mn></msub><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">{</mo><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">}</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda_1|\{\hat{R_e}\})</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>λ</mi><mn>2</mn></msub><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">{</mo><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">}</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\lambda_2|\{\hat{R_e}\})</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>τ</mi><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">{</mo><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">}</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\tau|\{\hat{R_e}\})</annotation></semantics></math>
by using MCMC, specifically the Metropolis-Hastings algorithm, to sample
from our model.</p></li>
</ol>
<p>We can then use the generated probabilistic data to plot the
posterior distributions of all our unknown parameters– in this case,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>1</mn></msub><annotation encoding="application/x-tex">\lambda_1</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>2</mn></msub><annotation encoding="application/x-tex">\lambda_2</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>–
and determine the mean and variance of those unknowns. In the next
section, we will briefly discuss MCMC, and lay out the algorithm at a
high level, to offer some intuition.</p>
<h3 id="discussion-of-covid-19-results.">Discussion of COVID-19
Results.</h3>
<figure data-latex-placement="h">
<!-- <img src="./AB_berks.png" style="width:100.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/AB_berks.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>A/B Testing Berks, PA</figcaption>
</figure>
<figure data-latex-placement="h">
<!-- <img src="./AB_phl.png" style="width:100.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/AB_phl.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>A/B Testing Philadelphia, PA</figcaption>
</figure>
<figure data-latex-placement="h">
<!-- <img src="./AB_nyc.png" style="width:100.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/AB_nyc.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>A/B Testing Manhattan, NY</figcaption>
</figure>
<figure data-latex-placement="h">
<!-- <img src="./AB_la.png" style="width:100.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/AB_la.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>A/B Testing Los Angeles, CA</figcaption>
</figure>
<p>We can see from our spot estimates of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
charts for each county that the initial generation seemingly have
extremely high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
values. Intuitively, this makes sense, since COVID-19 cases in these
counties were not being tracked until January 22, 2020, but as the name
COVID-19 insinuates, cases began springing up in 2019– before the CDC
began counting. This would naturally make the initial generation’s
population,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">X(1)</annotation></semantics></math>,
will seem much higher and therefore the spot estimate of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
at this generation will be artificially inflated. Because of this, we
will remove the first
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
value from consideration in or A/B testing.<br />
<br />
In fact, in some of the cases, the first few generations seem to have
abnormally high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
spot estimates. This could be for a variety of reasons– a simple idea is
that as COVID-19 was becoming more well known, and influx of people went
to get tested in the first several generations (i.e., the first months
of 2020) which included newly infected people and people with older
infections, whereas as the pandemic progressed, only people with truly
new infections were being counted.<br />
<br />
Around the third generation in both the cases of Philadelphia county and
Berks county, something happens where the steep incline originally seen
in cases suddenly drops off. Both of these counties are in Pennsylvania,
and the first reported cases of COVID in Berks and Philadelphia were
March 18, 2020 and March 10, 2020, respectively <span class="citation"
data-cites="jhu_covid"></span>. Given that our generations are 5 days,
the fourth generation (20 days after patient 0 is detected in each
county) is early April– this is (roughly) where we start to see the
slopes of each graph drop off. According to ABC27, the stay-at-home
orders in Philadelphia county began <strong>March 23, 2020</strong>, and
then Governor Tom Wolff placed all the state on stay-at-home orders on
<strong>April 1, 2020</strong> <span class="citation"
data-cites="PA_timeline"></span>. This begs the questions: <strong>did
lock-downs decrease
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math></strong>?
Based on the graphs it seems so– in fact, the slopes seem to be
<strong>negative</strong> after
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>4</mn></mrow><annotation encoding="application/x-tex">n=4</annotation></semantics></math>,
and a negative slope on these graphs implies an
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>&lt;</mo><mn>1</mn><mo>⇔</mo><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">R_e &lt; 1 \iff \eta = 1</annotation></semantics></math>.
We will explore this more in the next section, again using Baye’s
Analysis to see if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
before and after lock-downs is actually different.<br />
<br />
<strong>Berks County</strong><br />
<br />
As aforementioned, the first case of COVID-19 reported in Berks County
was <strong>March 18, 2020</strong>. Therefore, this is Berks County’s
Eve, or
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">X(1) = 1</annotation></semantics></math>
at generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n=1</annotation></semantics></math>.
So, when then-Governor Tom Wolff declared a stay-at-home order of
<strong>April 1, 2020</strong>, 14 days after Eve, it was around
generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>4</mn></mrow><annotation encoding="application/x-tex">n=4</annotation></semantics></math>.
This is a really interesting result, looking at Figure 18, which
displays all the A/B testing charts for Berks County, and looking at the
posterior distribution of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>,
we can see the peak from
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>4</mn></mrow><annotation encoding="application/x-tex">n=4</annotation></semantics></math>
to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">n=5</annotation></semantics></math>.
This tells us that the expected switch point occurred around
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>4</mn></mrow><annotation encoding="application/x-tex">n=4</annotation></semantics></math>,
corresponding with Pennsylvania’s statewide lock-down. We can also see
that the posterior distribution of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msub><mi>λ</mi><mn>1</mn></msub><mo>=</mo><mn>1.67</mn></mrow><annotation encoding="application/x-tex">(R_e^{(1)}=)\lambda_1 = 1.67</annotation></semantics></math>
which is around the accepted
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
value of COVID. But, after the the lockdown, the posterior of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msub><mi>λ</mi><mn>2</mn></msub><mo>=</mo><mn>0.77</mn></mrow><annotation encoding="application/x-tex">(R_e^{(2)}=) =\lambda_2 = 0.77</annotation></semantics></math>
which is significantly lower. In fact, since
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msub><mi>λ</mi><mn>2</mn></msub><mo>=</mo><mn>0.77</mn><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">(R_e^{(2)}=) =\lambda_2 = 0.77 &lt; 1</annotation></semantics></math>,
we know from Ahlberg’s paper <span class="citation"
data-cites="sir3"></span>, that this is sufficient for
extinction–<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\eta =1</annotation></semantics></math>–
of the disease, in theory.<br />
<br />
<strong>Philadelphia</strong><br />
<br />
Interestingly, other than the large peaks at the beginning spot
estimations of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>,
the estimates
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
do not seem to vary much with time. This is interesting, as the city a
devised stay-at-home or lock-down orders fairly early into the outbreak.
Taking a look at the CDC data we have been using throughout this
project, we can see that the first confirmed case of COVID-19 in
Philadelphia County was on <strong>March 10, 2020.</strong> This was
Philadelphia’s Eve or
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">X(1) = 1</annotation></semantics></math>
At the time, then-Governor Tom Wolff did not lay out a blanket lock-down
across the state. Instead, the most populous and most effected counties
in south eastern Pennsylvania, to include Philadelphia County, were
locked-down on <strong>March 23, 2020</strong>– over a week before Berks
County. This means the lock-down occurred around 13 days after the first
confirmed case, which is equivalent to around generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n=2</annotation></semantics></math>
or
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">n=3</annotation></semantics></math>,
bearing in mind our 5 day generations. Turning our attention to Figure
19, which depicts the A/B testing results for Philadelphia County, we
can see the peaks at
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n=1</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n=2</annotation></semantics></math>.
The peak around
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n=1</annotation></semantics></math>
is most likely caused by the aforementioned over reporting that is bound
to happen in the first several generations. The peak at
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n=2</annotation></semantics></math>
is more interesting, and looking at our spot estimates for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>,
we can see the steady decline in estimates of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><msub><mi>R</mi><mi>e</mi></msub><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R_e}</annotation></semantics></math>
around that time.<br />
<br />
Again, as was the case with Berks, we see from the posterior
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msub><mi>λ</mi><mn>1</mn></msub><mo>=</mo><mn>11.9424</mn></mrow><annotation encoding="application/x-tex">(R_e^{(1)}=)\lambda_1 = 11.9424</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msub><mi>λ</mi><mn>2</mn></msub><mo>=</mo><mn>0.7553</mn></mrow><annotation encoding="application/x-tex">(R_e^{(2)}=)\lambda_2 = 0.7553</annotation></semantics></math>
meaning we observe
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msub><mi>λ</mi><mn>2</mn></msub><mo>=</mo><mn>0.7553</mn><mo>&lt;</mo><mn>1</mn><mo>⇔</mo><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">(R_e^{(2)}=)\lambda_2 = 0.7553 &lt; 1 \iff \eta = 1</annotation></semantics></math>
and a possibility of disease extinction. But, because of the high
variance of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>1</mn></msub><annotation encoding="application/x-tex">\lambda_1</annotation></semantics></math>,
these results are slightly less compelling than those of Berks
County.<br />
<br />
<strong>Manhattan.</strong> Looking in the CDC data, we see Eve,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">X(1) =1</annotation></semantics></math>,
occurred on <strong>March 2, 2020.</strong> According to Spectrum News
NY1 <span class="citation" data-cites="nyc_time"></span>, New York City
as a whole did not shut-down everything at once. Instead, the timeline
is displayed in the Table below.</p>
<div class="center">
<table>
<thead>
<tr>
<th style="text-align: center;">Date</th>
<th style="text-align: center;">Days</th>
<th style="text-align: center;">Generation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math></th>
<th style="text-align: center;">Event</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;">3/14/20</td>
<td style="text-align: center;">6</td>
<td style="text-align: center;">1-2</td>
<td style="text-align: center;">Public school shutdown</td>
</tr>
<tr>
<td style="text-align: center;">3/17/20</td>
<td style="text-align: center;">9</td>
<td style="text-align: center;">2</td>
<td style="text-align: center;">Bars closed</td>
</tr>
<tr>
<td style="text-align: center;">3/22/20</td>
<td style="text-align: center;">14</td>
<td style="text-align: center;">3</td>
<td style="text-align: center;">Non-essential workers ordered home</td>
</tr>
</tbody>
</table>
</div>
<p>This is particularly interesting because the only peak we see on the
posterior of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>
for Manhattan is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">n=3</annotation></semantics></math>
(see Figure 20), which coincides with ordering all non-essential workers
to stay home. One could infer a few things from this– it could be argued
that:</p>
<ol>
<li><p>this supports that ordering nearly everybody home is the only way
keep
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>λ</mi><mo>=</mo><mn>0.43</mn><mo>&lt;</mo><mn>1</mn><mo>⇔</mo><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">(R_e^{(2)}=)=\lambda = 0.43 &lt;1 \iff \eta = 1</annotation></semantics></math>
and therefore drive the disease to extinction, or</p></li>
<li><p>that only all 3 of these efforts in tandem enabled a
<strong>decrease</strong> in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>
after some switchpoint,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>.</p></li>
</ol>
<p>It is also interesting that in this case, the posterior of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><mo>=</mo><mo stretchy="false" form="postfix">)</mo><msub><mi>λ</mi><mn>1</mn></msub><mo>=</mo><mn>8.2245</mn></mrow><annotation encoding="application/x-tex">(R_e^{(1)}=)\lambda_1 = 8.2245</annotation></semantics></math>,
which is much higher than the currently accepted COVID-19
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mn>0</mn></msub><annotation encoding="application/x-tex">R_0</annotation></semantics></math>
value, but the variance is much lower than what we saw in the case of
Philadelphia. This is, again, most likely because of the over reporting
in the first few generations of records keeping you would expect to
see.<br />
<br />
<strong>Los Angeles.</strong><br />
<br />
The first case of COVID-19 confirmed in Los Angeles County, California,
according the CDC data was on <strong>January 26, 2020</strong> (i.e,
Eve,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">X(1) =1</annotation></semantics></math>).
On <strong>March 16, 2020</strong>, 90% of K-12 public school students
are ordered to stay home, and then Governor Newsom ordered a
stay-at-home order on <strong>March 19, 2020</strong>. Thus, these
occurred around
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>10</mn></mrow><annotation encoding="application/x-tex">n=10</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>10</mn><mo>−</mo><mn>11</mn></mrow><annotation encoding="application/x-tex">n=10-11</annotation></semantics></math>,
respectively.<br />
<br />
Interestingly, of the four counties we have explored, this is the only
one where the peak on the posteriors distribution of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>
does not correspond with the being of a shut down (see Figure 21). In
fact, the peak is around
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">n = 5</annotation></semantics></math>,
or in real time around <strong>February 20, 2020</strong>. This
drastically predates the stay-at-home order on March, 19, and it even
predates the first action Los Angeles County took against COVID-19–
banning social gatherings on <strong>March 7, 2020</strong><span
class="citation" data-cites="CA_timeline"></span>– by about 15 days or
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">n=3</annotation></semantics></math>.
It’s interesting to note that even in Figure 3, which depicts the the
number of new cases by day for each of these four counties, Los Angeles
growth is markedly different in shape. Where in Berks, Philadelphia, and
Manhattan, we see a steep increase in the number of new cases between
generations for the first roughly 10 generations, and then a similar
steep descent again into a tail, Los Angeles steadily grows for the
whole six month duration of this data.<br />
<br />
It’s unclear why this is the case, but Los Angeles county did have some
exacerbating circumstances the other counties did not. For one, they
have four active military bases– Ft. MacArthur, San Clemente Island
Naval Test Site, Edwards AFB, and Los Angeles AFB <span class="citation"
data-cites="la_mil"></span>. Military bases are notorious for spreading
pandemics and disease. During the Spanish Flu, the initial outbreak can
be traced back to a group of First World War soldiers who enlisted in
Kansas, than trained in Camp Devens, Massachusetts where one of the
first serious outbreaks occurred. Then, sailors from Massachusetts
sailed to the Navy Yard in Philadelphia, and the rest is history <span
class="citation" data-cites="span_flu"></span>. The First World War and
soldiers in general were responsible for pushing the misnamed Spanish
Flu through out the world. Young, predominantly male, populations are
mobile and come from all corners of the country, making it difficult to
stem the spread, especially since they are considered essential
workers.<br />
<br />
<strong>Summary.</strong> In summary, three of the four counties we have
examined seemed to have a drastic decrease in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msubsup><mi>R</mi><mi>e</mi><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mrow></msubsup><annotation encoding="application/x-tex">R_e^{(2)}</annotation></semantics></math>
corresponding with the implementation of a stay-at-home order, and the
one county that did not show this result is an extremely densely
populated county with many military service members that could
potentially account for the discrepancy. Overall, we have found some
evidence for the efficacy of lock-downs as a measure for reducing the
spread of COVID-19.</p>
<h3 id="discussion-of-ebola-results.">Discussion of Ebola Results.</h3>
<figure data-latex-placement="h">
<!-- <img src="./Ebola_AB.png" style="width:100.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/Ebola_AB.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>A/B Testing Ebola Epidemic, West Africa,
2013-2016</figcaption>
</figure>
<p>The timeline of interventions and actions taken to mitigate the
spread of Ebola in West Africa is less clear than the measures taken by
individual US states and counties during the COVID-19 pandemic. But, the
results are interesting nonetheless. Recall that Ebola has a mean
infectious period of approximately 10 days– that is, 1 generation is 10
days. We see by the posterior distributions of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>1</mn></msub><annotation encoding="application/x-tex">\lambda_1</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>λ</mi><mn>2</mn></msub><annotation encoding="application/x-tex">\lambda_2</annotation></semantics></math>,
average
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>R</mi><mi>e</mi></msub><annotation encoding="application/x-tex">R_e</annotation></semantics></math>s
of 1.99 and 0.8337, respectively. Again, a
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>R</mi><mi>e</mi></msub><mo>&lt;</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">R_e &lt; 1</annotation></semantics></math>
corresponds to eventual extinction of an outbreak,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>η</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">\eta = 1</annotation></semantics></math>.<br />
<br />
Bearing this in mind, we can see a peak in the posterior distribution of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>
around
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">n = 5</annotation></semantics></math>.
This is approximately
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>50</mn><annotation encoding="application/x-tex">50</annotation></semantics></math>
days after the first recorded case in our data. Though this particular
epidemic is thought to have begun in late December of 2013 in a village
in Guinea, the first date we have data for is <strong>March 25,
2014</strong>, which means our peak in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>
is occurring around <strong>May 14, 2014.</strong> There is another peak
in the posterior of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>τ</mi><annotation encoding="application/x-tex">\tau</annotation></semantics></math>
at
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>100</mn></mrow><annotation encoding="application/x-tex">n=100</annotation></semantics></math>
or 100 days after March 25, 2014, which was <strong>July 3,
2014.</strong> Interestingly, the second peak on July 3, 2014
corresponds with the CDC deploying o West Africa, where they "assist
with response efforts, including surveillance, contact tracing, data
management, laboratory testing, and health education" <span
class="citation" data-cites="ebola_cdc"></span>.</p>
<h1 id="bayesian-machine-learning-for-fatality-prediction.">Bayesian
Machine Learning for Fatality Prediction.</h1>
<h2 id="gaussian-naive-bayes-classifier.">Gaussian Naive Bayes
Classifier.</h2>
<p>In general, Naive Bayes Classifiers are a simple supervised machine
learning methods that take advantage of Bayes Theorem to determine the
probability of an observation falling into each possible class. They are
referred to as "naive", because these models assume <strong>conditional
independence</strong> between classification variables– which in
reality, is rarely the case. The Gaussian Naive Bayes Classifier makes
the additional assumption that each variable is normally distributed
<span class="citation" data-cites="gnbc"></span>.</p>
<h3 id="algorithm-implementation.">Algorithm &amp; Implementation.</h3>
<p>Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐲</mtext><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>y</mi><mn>1</mn></msub><mo>,</mo><msub><mi>y</mi><mn>2</mn></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>y</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\textbf{y} = (y_1,y_2,...,y_n)</annotation></semantics></math>
be our observed
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
responses, and let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="bold">𝐗</mtext><mo>=</mo><mrow><mo stretchy="true" form="prefix">[</mo><mtable><mtr><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>11</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>12</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><mi>…</mi></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mn>1</mn><mi>k</mi></mrow></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>21</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mn>22</mn></msub></mtd><mtd columnalign="center" style="text-align: center"><mi>…</mi></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mn>2</mn><mi>k</mi></mrow></msub></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>⋮</mi></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mi>n</mi><mn>1</mn></mrow></msub></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mi>n</mi><mn>2</mn></mrow></msub></mtd><mtd columnalign="center" style="text-align: center"><mi>…</mi></mtd><mtd columnalign="center" style="text-align: center"><msub><mi>x</mi><mrow><mi>n</mi><mi>k</mi></mrow></msub></mtd></mtr></mtable><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">\textbf{X} = \begin{bmatrix}
    x_{11}&amp;x_{12}&amp;\hdots&amp;x_{1k}\\
    x_{21}&amp;x_{22}&amp;\hdots&amp;x_{2k}\\
    \vdots&amp;\vdots&amp;\vdots&amp;\vdots\\
    x_{n1}&amp;x_{n2}&amp;\hdots&amp;x_{nk}
\end{bmatrix}</annotation></semantics></math> be our
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
observed feature variables, where each each row,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mtext mathvariant="bold">𝐱</mtext><mi>i</mi></msub><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mrow><mi>i</mi><mn>1</mn></mrow></msub><mo>,</mo><msub><mi>x</mi><mrow><mi>i</mi><mn>2</mn></mrow></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>x</mi><mrow><mi>i</mi><mi>k</mi></mrow></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\textbf{x}_i =(x_{i1},x_{i2},...,x_{ik})</annotation></semantics></math>,
corresponds to response
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>y</mi><mi>i</mi></msub><annotation encoding="application/x-tex">y_i</annotation></semantics></math>.<br />
<br />
Bayes’ Theorem tells us, given class
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mn>1</mn></msub><annotation encoding="application/x-tex">x_1</annotation></semantics></math>
through
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>k</mi></msub><annotation encoding="application/x-tex">x_k</annotation></semantics></math>
feature variables
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(y|\textbf{x}) = \frac{P(y)P(\textbf{x}|y)}{P(\textbf{x})}</annotation></semantics></math>
And by our assumption of <strong>conditional independence</strong>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>i</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo>,</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>x</mi><mrow><mi>i</mi><mo>−</mo><mn>1</mn></mrow></msub><mo>,</mo><msub><mi>x</mi><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>,</mo><msub><mi>x</mi><mi>k</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>i</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(x_{i}|y, x_{1},...,x_{i-1},x_{i+1},...,x_{k}) = P(x_i|y)</annotation></semantics></math>
So,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><munderover><mo>∏</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><mi>k</mi></munderover><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>j</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(y|\textbf{x}) = \frac{P(y)\prod_{j=1}^k P(x_{j}|y)}{P(\textbf{x})}</annotation></semantics></math>
Naturally,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\textbf{x})</annotation></semantics></math>
is constant, and therefore we can treat this equality instead as a
proportionality
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐱</mtext><mo stretchy="false" form="postfix">)</mo><mo>∝</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><munderover><mo>∏</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><mi>k</mi></munderover><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>j</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(y|\textbf{x}) \propto P(y)\prod_{j=1}^k P(x_{j}|y)</annotation></semantics></math>
From here, in essence the idea is to use this version of Bayes’ Theorem
to determine the probability of our observed data,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mtext mathvariant="bold">𝐱</mtext><annotation encoding="application/x-tex">\textbf{x}</annotation></semantics></math>,
being of each class in particular,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>.
This means our final classification prediction boils down to
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mi>y</mi><mo accent="true">̂</mo></mover><mo>=</mo><msub><mtext mathvariant="normal">arg max</mtext><mi>y</mi></msub><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><munderover><mo>∏</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><mi>k</mi></munderover><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>j</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\hat{y} = \text{arg max}_y P(y)\prod_{j=1}^k P(x_{j}|y)</annotation></semantics></math>
where for each class,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>,
we assume each feature variable,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>x</mi><mi>i</mi></msub><annotation encoding="application/x-tex">x_i</annotation></semantics></math>,
follows a normal distribution as follows:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>j</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mn>1</mn><msqrt><mrow><mn>2</mn><mi>π</mi><msubsup><mi>σ</mi><mi>y</mi><mn>2</mn></msubsup></mrow></msqrt></mfrac><msup><mi>e</mi><mrow><mi>−</mi><mfrac><mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>j</mi></msub><mo>−</mo><msub><mi>μ</mi><mi>y</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><mrow><mn>2</mn><msubsup><mi>σ</mi><mi>y</mi><mn>2</mn></msubsup></mrow></mfrac></mrow></msup></mrow><annotation encoding="application/x-tex">P(x_{j}|y) = \frac{1}{\sqrt{2\pi \sigma_{y}^2}}e^{-\frac{(x_j-\mu_{y})}{2\sigma_{y}^2}}</annotation></semantics></math>
<span class="citation" data-cites="gnbc"></span>.<br />
<br />
While Naive Bayes’ Classifiers are useful in many situations, especially
with a small amount of training data compared to other machine learning
methods. These type of models are extremely fast compared to other
methods, and because of the conditional independence assumption, it
allows for probability estimates of each class as 1-dimensional
distributions.Interestingly, though Naive Bayes’ Classifiers are
generally regarded as good classifiers, they are known to be bad
estimators, and the resultant probabilities,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><msub><mi>x</mi><mi>i</mi></msub><mo stretchy="false" form="prefix">|</mo><mi>y</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(x_{i}|y)</annotation></semantics></math>
for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>1</mn><mo>≤</mo><mi>i</mi><mo>≤</mo><mi>k</mi></mrow><annotation encoding="application/x-tex">1\leq i\leq k</annotation></semantics></math>
are not to be taken as fact <span class="citation"
data-cites="gnbc"></span>.</p>
<h3 id="permutation-importance.">Permutation Importance.</h3>
<p>Permutation importance is a simple method for determining how
influential each feature variable is in the ultimate classification of
data novel to the model.<br />
<br />
First, we take a baseline metric, in this case accuracy, on some data
set not used to construct the Gaussian Naive Bayes’ Classifier model,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mtext mathvariant="bold">𝐗</mtext><annotation encoding="application/x-tex">\textbf{X}</annotation></semantics></math>
<span class="citation" data-cites="scoring"></span>. Then, we permute
each feature column from
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mtext mathvariant="bold">𝐗</mtext><annotation encoding="application/x-tex">\textbf{X}</annotation></semantics></math>–
that is, the values of the predictor are randomly reassigned to
different indices, while the rest of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mtext mathvariant="bold">𝐗</mtext><annotation encoding="application/x-tex">\textbf{X}</annotation></semantics></math>
remains unchanged– and the metric is evaluated again. So, permutation
importance is the difference between the baseline metric and permutation
metric <span class="citation" data-cites="perm_imp"></span>. Thus, we
are breaking the relationship between that feature and the corresponding
response to see if it matters when calculating our metrics <span
class="citation" data-cites="perm_imp"></span>. In the case of Gaussian
Naive Bayes Classifiers, the default scoring metric is simply accuracy,
and this is the metric we will evaluate.<br />
<br />
This is method will use to determine predictor importance in our
Gaussian Naive Bayes’ Classifier Model.</p>
<h3 id="covid-19-severity-risk-factor-results.">COVID-19 Severity Risk
Factor Results.</h3>
<p>Using the Sci-Kit Learn GaussianNB class available in Python, and the
accompanying examples and documentation <span class="citation"
data-cites="gnbc"></span>, models of these classifiers are very easy to
construct.<br />
<br />
In the case of COVID-19, we will be using a case severity data set that
tracks the associated socioeconomic and health markers of various cases,
as well as the ultimate severity of the case <span class="citation"
data-cites="covid_risk"></span> <span class="citation"
data-cites="ieee_covid"></span>.<br />
<br />
For our purposes here, we want to build a <strong>binary</strong>
classification model. In the COVID-19 severity data set <span
class="citation" data-cites="covid_risk"></span>, the ultimate severity
of each case is measured on a scale from 1 to 10, with 10 being the most
severe. To this end, we will split our responses as follows: severe
cases will be called such for severities
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>≥</mo><mn>6</mn></mrow><annotation encoding="application/x-tex">\geq 6</annotation></semantics></math>,
and the cases will be categorized as not severe otherwise. We want to
determine what variables are most associated with severe COVID-19
cases.<br />
<br />
As we can see from the table below, our Gaussian Naive Bayes’ Classifier
has an accuracy of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>0.8217</mn><annotation encoding="application/x-tex">0.8217</annotation></semantics></math>.
The model splits the data using the typical 70-30 split for training and
testing, and therefore this classifier was able to correctly classify
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>82.17</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">82.17\%</annotation></semantics></math>
of the COVID-19 cases in the test set. We can also see the permutation
importances of each feature in descending order. The top five most
important features– that is, the five that change the model’s accuracy
the most– are PltsScore (platelet count in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mfrac><mn>1000</mn><mrow><mi>m</mi><msup><mi>m</mi><mn>3</mn></msup></mrow></mfrac><annotation encoding="application/x-tex">\frac{1000}{mm^3}</annotation></semantics></math>),
Procalctonin concentration, Creatinine (a metabolic waste product)
concentration, Ferritin (a blood component containing iron), and blood
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>O</mi><mn>2</mn></msub><annotation encoding="application/x-tex">O_2</annotation></semantics></math>
saturation
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mn>94</mn></mrow><annotation encoding="application/x-tex">&lt; 94</annotation></semantics></math>
<span class="citation" data-cites="ieee_covid"></span>.<br />
<br />
In other words, according to our Gaussian Naive Bayes’ Classifier, these
are the biological markers most indicative of an individual who will
experience a severe COVID-19 case. The permutation importance reported
next to each variable represents the mean change in each variables
accuracy after
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>
permutations, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>+</mi><mspace width="0.222em"></mspace><mo>−</mo></mrow><annotation encoding="application/x-tex">+\ -</annotation></semantics></math>
the standard deviation after those
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>
permutations.So, even though platelet count (PltsScore) had the greatest
impact on accuracy when shuffled varied by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mn>1</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">&lt; 1\%</annotation></semantics></math>.
Because our accuracy is relatively high, sitting at
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>82</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">82\%</annotation></semantics></math>
for our testing data, we can conclude that in fact all the features are
relatively indicative of the severity of COVID-19 cases.<br />
<br />
<strong>COVID-19 Severity Risk Factors Permutation
Importance.</strong></p>
<pre><code>Accuracy: 0.8217821782178217
PltsScore0.009 +/-    0.002
Procalcitonin0.008 +/-    0.002
Creatinine0.007 +/-    0.002
Ferritin0.006 +/-    0.002
O2 Sat &lt; 940.005 +/-    0.002
BUN     0.005 +/-    0.003
Death   0.004 +/-    0.002
&gt;60     0.003 +/-    0.002
Ddimer  0.003 +/-    0.003
MAP &lt; 700.003 +/-    0.003
INR     0.002 +/-    0.001
Latino  0.002 +/-    0.001
White   0.002 +/-    0.001
Troponin &gt; 0.10.002 +/-    0.003
Plts    0.002 +/-    0.001
DM Complicated0.002 +/-    0.001
BUNYes  0.001 +/-    0.001
IL6     0.001 +/-    0.001
PVD     0.001 +/-    0.001
Lymphocytes &lt; 10.001 +/-    0.001
LOS_Y   0.001 +/-    0.001
LOS     0.001 +/-    0.001
&gt;80     0.001 +/-    0.002
Temp    0.001 +/-    0.002
Asian   0.001 +/-    0.001
CVD     0.001 +/-    0.001
Sodium &lt; 139 or &gt; 1540.001 +/-    0.002
MAP     0.001 +/-    0.002
Stroke  0.001 +/-    0.001
DM Simple0.001 +/-    0.001
CHF     0.001 +/-    0.001
Lympho  0.001 +/-    0.001
ALT     0.001 +/-    0.002
CrctProtein0.001 +/-    0.003
Glucose &lt;60 or &gt; 5000.000 +/-    0.001
WBC     0.000 +/-    0.002
All CNS 0.000 +/-    0.001
AST &gt; 400.000 +/-    0.002
MI      0.000 +/-    0.001
ALT &gt; 400.000 +/-    0.001
Temp &gt; 380.000 +/-    0.000
D-Dimer &gt; 30.000 +/-    0.003
INR &gt; 1.20.000 +/-    0.003
Derivation cohort0.000 +/-    0.001
Seizure 0.000 +/-    0.001
Black   0.000 +/-    0.001
PltsYes 0.000 +/-    0.002
DEMENT  0.000 +/-    0.000
Renal Disease0.000 +/-    0.000
AST     -0.000 +/-    0.001
WBCYes  -0.000 +/-    0.003
LymphoYes-0.000 +/-    0.003
COPD    -0.000 +/-    0.001
ProCalCYes-0.000 +/-    0.001
OldSyncope-0.000 +/-    0.001
CrtnYes -0.000 +/-    0.003
OtherBrnLsn-0.000 +/-    0.001
IL6Yes  -0.000 +/-    0.001
C-Reactive Prot &gt; 10-0.000 +/-    0.003
OsSats  -0.001 +/-    0.002
Procalciton &gt; 0.1-0.001 +/-    0.002
Glucose -0.001 +/-    0.001
Troponin-0.001 +/-    0.001
ASTYes  -0.001 +/-    0.002
GlucoseYese-0.001 +/-    0.001
O2SatsYes-0.001 +/-    0.001
TempYes -0.001 +/-    0.002
BUN &gt; 30-0.001 +/-    0.003
FerritinYes-0.001 +/-    0.002
WBC &lt;1.8 or &gt; 4.8-0.001 +/-    0.001
OldOtherNeuro-0.001 +/-    0.001
MapYes  -0.001 +/-    0.002
IL6 &gt; 150-0.001 +/-    0.002
Ferritin &gt; 300-0.002 +/-    0.002
Sodium  -0.002 +/-    0.002
Pure CNS-0.002 +/-    0.001
ALTYes  -0.002 +/-    0.002
CrctProtYes-0.003 +/-    0.001
SodimuYes-0.003 +/-    0.002
&gt;70     -0.004 +/-    0.002
INRYes  -0.004 +/-    0.002
DDimerYes-0.004 +/-    0.002
0-60    -0.005 +/-    0.004
TropYes -0.005 +/-    0.002
AgeScore-0.005 +/-    0.003
Age.1   -0.006 +/-    0.003</code></pre>
<h3 id="heart-failure-risk-factor-results.">heart failure Risk Factor
Results.</h3>
<p>As another example of the utility of Gaussian Naive Bayes’
Classifiers in mortality prediction in disease, we will also examine a
Heart Failure Risk Factor data set <span class="citation"
data-cites="heart_kaggle"></span>. Again we will split this data into
training and testing sets using the typical 70-30 split. We can see that
we achieved a similar accuracy for prediction in this data set as in the
COVID-19 Risk Factor data set, of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mn>0.8333</mn><annotation encoding="application/x-tex">0.8333</annotation></semantics></math>–
meaning
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>83.33</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">83.33\%</annotation></semantics></math>
of our test set was correctly classified. As for our permutation
importance scores, we see our top five most important features by
permutation importance are: ATA (the presence of atypical angina), Up
(the presence of an Up-trending ST slope on an ECG), Flat (the presence
of an Flat ST slope on an ECG), NAP (the presence of non-anginal pain),
and cholesterol level <span class="citation"
data-cites="heart_kaggle"></span>. Interestingly, compared to the
COVID-19 data set’s most important predictors, the top three predictors
for heart failure– ATA and Up or Flat ST slopes– all, on average,
varying the accuracy
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&gt;</mo><mn>1</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">&gt; 1\%</annotation></semantics></math>
after
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>
permutations. The presence of ATA pain especially changes the Gaussian
Naive Bayes’ Classifiers accuracy by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2.2</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">2.2\%</annotation></semantics></math>
on it’s own. This indicates that though the presence of ATA pain is the
most sindicative predictor of heart failure, given our high overall
accuracy of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>83.33</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">83.33\%</annotation></semantics></math>,
all the features in this data set are potentially important to
consider.<br />
<br />
<strong>heart failure Risk Factors Permutation Importance.</strong></p>
<pre><code>Accuracy: 0.8333333333333334
ATA     0.022 +/- 0.010
Up      0.015 +/- 0.013
Flat    0.010 +/- 0.013
NAP     0.006 +/- 0.005
Cholesterol0.005 +/- 0.009
FastingBS0.005 +/- 0.008
ExerciseAngina0.004 +/- 0.010
RestingBP-0.002 +/- 0.003
LVH     -0.003 +/- 0.003
Age     -0.003 +/- 0.007
Down    -0.003 +/- 0.006
Oldpeak -0.003 +/- 0.011
ST      -0.005 +/- 0.004
Normal  -0.005 +/- 0.004
ASY     -0.005 +/- 0.008
TA      -0.005 +/- 0.004
MaxHR   -0.014 +/- 0.008
M       -0.015 +/- 0.010
F       -0.015 +/- 0.010</code></pre>
<h3 id="conclusion.">Conclusion.</h3>
<p>The beauty of Gaussian Naive Bayes’ Classifiers lie in their
simplicity. Though they make assumptions of conditional independence
that are not necessarily true in reality, such assumptions make these
classifiers easy to compute, use, and interpret. For simple, high
dimensional models, these are clearly decent predictors of disease.</p>
<h2 id="bayesian-logistic-regression.">Bayesian Logistic
Regression.</h2>
<h3 id="methodology.">Methodology.</h3>
<p>The idea of logistic regression is simple: use regression to classify
data. For our purposes, let the regression equation be
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo>=</mo><msub><mi>β</mi><mn>0</mn></msub><mo>+</mo><msub><mi>β</mi><mn>1</mn></msub><msub><mi>x</mi><mn>1</mn></msub><mo>+</mo><msub><mi>β</mi><mn>2</mn></msub><msub><mi>x</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>β</mi><mi>k</mi></msub><msub><mi>x</mi><mi>k</mi></msub><mo>=</mo><mi>β</mi><mo>⋅</mo><mtext mathvariant="bold">𝐗</mtext></mrow><annotation encoding="application/x-tex">p = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + ... + \beta_k x_k = \beta \cdot \textbf{X}</annotation></semantics></math>
We want this to act as our likelihood function (or PDF),
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">p(x)</annotation></semantics></math>–
but the issue is that this expression is unbounded, where we need
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>0</mn><mo>≤</mo><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo><mo>≤</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">0 \leq p(x) \leq 1</annotation></semantics></math>.
So, we will use the logistic function to enforce this range <span
class="citation" data-cites="log"></span>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mn>1</mn><mrow><mn>1</mn><mo>+</mo><msup><mi>e</mi><mrow><mi>β</mi><mo>⋅</mo><mtext mathvariant="bold">𝐗</mtext></mrow></msup></mrow></mfrac></mrow><annotation encoding="application/x-tex">p(x) = \frac{1}{1+ e^{\beta \cdot \textbf{X}}}</annotation></semantics></math>
For our purposes, we are interested in <strong>binary</strong>
classification problems, and so the logistic function will work well. In
multi-class classification problems, we can use the generalized form of
the logistic function, called the softmax function
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo>=</mo><mi>j</mi><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="bold">𝐗</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><msup><mi>e</mi><msub><mi>p</mi><mi>k</mi></msub></msup><mrow><munderover><mo>∑</mo><mrow><mi>k</mi><mo>=</mo><mn>1</mn></mrow><mi>K</mi></munderover><msup><mi>e</mi><msub><mi>p</mi><mi>k</mi></msub></msup></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(y = j|\textbf{X}) = \frac{e^{p_k}}{\sum_{k=1}^K e^{p_k}}</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>p</mi><annotation encoding="application/x-tex">p</annotation></semantics></math>
is defined as above. The beauty of this that the sum of the likelihoods
of each class is 1 <span class="citation" data-cites="log"></span><span
class="citation" data-cites="pymc_ex"></span>.<br />
<br />
The Bayesian aspect of Bayesian Logistic Regression is very similar to
the aforementioned Bayesian Linear Regression. For each class, we will
determine posterior distributions for each
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
parameter. We will select an <strong>uninformative</strong>, normal
prior with mean 0 and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>σ</mi><mo>≥</mo><msup><mn>10</mn><mn>4</mn></msup></mrow><annotation encoding="application/x-tex">\sigma \geq 10^4</annotation></semantics></math>.
Then, we will use MCMC to draw samples from our posteriors, given the
disease data sets.<br />
<br />
In order to make predictions using the resultant posteriors of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>,
we will simply use the mean, and report the variances and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>R</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R}</annotation></semantics></math>–
the measure of convergence for the MCMC of each parameter
(<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>R</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R}</annotation></semantics></math>
approaching 1 indicates convergence).<br />
<br />
For both the COVID-19 Risk Factors and Heart Failure Risk Factors data
sets, we will use the typical 70-30 split for our training and testing
sets and accuracy will be our final fit metric.</p>
<h3 id="heart-failure-risk-factor-results.-1">Heart Failure Risk Factor
Results.</h3>
<figure data-latex-placement="h">
<!-- <img src="./heartdisease_bLogReg_posteriorSummaries.png"
style="width:95.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/heartdisease_bLogReg_posteriorSummaries.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>Heart Failure Bayesian Logistic Regression Parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>,</mo><mi>a</mi></mrow><annotation encoding="application/x-tex">\beta, a</annotation></semantics></math>
Posterior Distribution Summaries.</figcaption>
</figure>
<p>For reference during this discussion,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo stretchy="false" form="prefix">[</mo><mi>i</mi><mo>,</mo><mi>j</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">\beta[i,j]</annotation></semantics></math>
refers to parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>β</mi><mi>i</mi></msub><annotation encoding="application/x-tex">\beta_i</annotation></semantics></math>
for class
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mo stretchy="false" form="prefix">[</mo><mi>j</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">a[j]</annotation></semantics></math>
refers to the intercept of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>p</mi><annotation encoding="application/x-tex">p</annotation></semantics></math>
for class
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math>.<br />
<br />
The first thing to note is that MCMC has trouble converging for this
heart failure risk factor data <span class="citation"
data-cites="heart_kaggle"></span>. We can see this in the relatively
high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>R</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R}</annotation></semantics></math>
values (ee Figure 23). Typically,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mi>R</mi><mo accent="true">̂</mo></mover><mo>&lt;</mo><mn>1.01</mn></mrow><annotation encoding="application/x-tex">\hat{R} &lt; 1.01</annotation></semantics></math>
is considered converged <span class="citation"
data-cites="columbia_rhat"></span>, but we are seeing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>R</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R}</annotation></semantics></math>s
as high as 2.89 for some parameters. This implies we are not confident
about the shape of our posterior distributions and are therefore unsure
about the mean.<br />
<br />
For the sake of time and memory due to the shear number of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
parameters needed in this model (19 features x 2 classes + 2 intercepts
= 40
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
parameters) the number of samples taken by MCMC was only 1000. This
could contribute to the overall lack of convergence we are
seeings.<br />
<br />
All that being said, we are still seeing decent accuracy, with about
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>86.09</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">86.09\%</annotation></semantics></math>
of our test set being correctly classified. This seems to point to the
idea that we simply need more samples from the distribution of each
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>β</mi><annotation encoding="application/x-tex">\beta</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>a</mi><annotation encoding="application/x-tex">a</annotation></semantics></math>
parameter in order to see better convergence.</p>
<h3 id="covid-19-severity-risk-factors-results.">COVID-19 Severity Risk
Factors Results.</h3>
<figure data-latex-placement="h">
<!-- <img src="./BLogReg_COVID2.png" style="width:95.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/BLogReg_COVID2.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>COVID-19 Severity Bayesian Logistic Regression Parameter
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>β</mi><mo>,</mo><mi>a</mi></mrow><annotation encoding="application/x-tex">\beta, a</annotation></semantics></math>
Posterior Distribution Summaries.</figcaption>
</figure>
<p>Because there are 87 features (including one-hot encoded categorical
variables), and therefore 176 parameter posteriors, for the COVID-19
severity risk factors data set <span class="citation"
data-cites="covid_risk"></span>, we cannot display all the parameter
posteriors summaries. So, we have an abridged selection in Figure
24.<br />
<br />
Like the heart failure risk factor Bayesian logistic regression model,
we see very high
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>R</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{R}</annotation></semantics></math>
values, meaning our MCMC sampling did not converge strongly. Also like
the heart failure model, we see a very high accuracy. Using the typical
70-30 training-test split, we saw
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>97.80</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">97.80\%</annotation></semantics></math>
correct classification of the test set. Again, this is most likely
because of the number of features and the lack of computer power used to
build these models, the number of MCMC samples used to build this model
was only 1000. With more samples, we could potentially see better
convergence, and maintain the high accuracy.<br />
<br />
Unlike the heart failure data, the features in the COVID-19 severity
data are robust enough that severe cases are very well predicted. An
accuracy of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>97.80</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">97.80\%</annotation></semantics></math>
means a combined instance of Type I and Type II errors (false positives
and false negatives, respectively) of only
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2.2</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">2.2\%</annotation></semantics></math>.</p>
<h1
id="future-work-bayesian-belief-network-the-back-door-path-criterion.">Future
Work: Bayesian Belief Network &amp; The Back-Door Path Criterion.</h1>
<p>Bayesian Belief Networks (BNNs) are a specific type of
<strong>directed acyclical graphs</strong> (DAGs), where the nodes
represent variables (in our case, discrete) and the edges represent
probabilistic relationships. They are useful for looking at the outcomes
of events and determining the likelihood a possible known variables is a
contributing factor <span class="citation"
data-cites="bnn_wiki"></span>.<br />
<br />
Using the heart failure risk factor data set <span class="citation"
data-cites="heart_kaggle"></span>, we will construct two DAGs and
analyze the relationship between our chosen predictors and the
occurrence of heart disease. Causal networks are a special case of BNNs
<span class="citation" data-cites="bnn_wiki"></span>, and so we will be
looking at some known causal relationships in our BNNs.<br />
<br />
</p>
<h3 id="the-back-door-path-criterion-calculating-probabilities.">The
Back-Door Path Criterion &amp; Calculating Probabilities.</h3>
<p>With causal DAGs, the back-door path criterion (BDPC) can be applied.
The back-door path criterion is a test that can be applied directly to a
causal DAG that tests to see is a set of variables
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Z</mi><mo>⊆</mo><mi>V</mi></mrow><annotation encoding="application/x-tex">Z \subseteq V</annotation></semantics></math>,
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>V</mi><annotation encoding="application/x-tex">V</annotation></semantics></math>
represents all observed (confounding) variables, is sufficient for
identifying
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mover><mi>x</mi><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(y|\hat{x})</annotation></semantics></math>,
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>y</mi><annotation encoding="application/x-tex">y</annotation></semantics></math>
is some response and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>x</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{x}</annotation></semantics></math>
is some specified variable <span class="citation"
data-cites="bdpc_pdf"></span>. It states that, relative to a causally
ordered pair of variables,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>X</mi><mo>,</mo><mi>Y</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(X, Y)</annotation></semantics></math>,</p>
<ol>
<li><p>no node in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Z</mi><annotation encoding="application/x-tex">Z</annotation></semantics></math>
is a descendant of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Z</mi><annotation encoding="application/x-tex">Z</annotation></semantics></math>
blocks every path between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Y</mi><annotation encoding="application/x-tex">Y</annotation></semantics></math>
that contains an arrow into
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math></p></li>
</ol>
<p>If the back-door path criterion is satisfied, then the causal effect
of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>
on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Y</mi><annotation encoding="application/x-tex">Y</annotation></semantics></math>
is simply
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mover><mi>x</mi><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo><mo>=</mo><munder><mo>∑</mo><mi>z</mi></munder><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>y</mi><mo stretchy="false" form="prefix">|</mo><mi>x</mi><mo>,</mo><mi>z</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>z</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(y|\hat{x}) = \sum_z P(y|x,z)\cdot P(z)</annotation></semantics></math>
<span class="citation" data-cites="bdpc_pdf"></span>. In essence, the
back-door path criterion allows us to account for the effect of
confounding variables.<br />
<br />
</p>
<figure data-latex-placement="H">

<figcaption>Directed Acyclical Graphs of Heart Failure Risk Factor Data
Set.</figcaption>
</figure>
<p>Take DAG 1 in Figure 25, as an example. We can see that we have two
paths to the response variable "Heart Disease":
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="normal">High Cholesterol</mtext><mo>→</mo><mtext mathvariant="normal">Heart Disease</mtext></mrow><annotation encoding="application/x-tex">\text{High Cholesterol} \rightarrow \text{Heart Disease}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="normal">High Cholesterol</mtext><mo>→</mo><mtext mathvariant="normal">High Blood Pressure</mtext><mo>→</mo><mtext mathvariant="normal">Heart Disease</mtext></mrow><annotation encoding="application/x-tex">\text{High Cholesterol} \rightarrow\text{High Blood Pressure} \rightarrow\text{Heart Disease}</annotation></semantics></math>
<span class="citation" data-cites="hc_to_hbp"></span>.<br />
<br />
Let us be interested in the relationship between "High Cholesterol" and
"Heart Disease". We need to find
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Z</mi><mo>⊆</mo><mo stretchy="false" form="prefix">{</mo><mtext mathvariant="normal">High Cholesterol, High Blood Pressure, Heart Disease</mtext><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">Z \subseteq \{\text{High Cholesterol, High Blood Pressure, Heart Disease}\}</annotation></semantics></math>
such that (1) "High Cholesterol" is not a descendant of any node in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Z</mi><annotation encoding="application/x-tex">Z</annotation></semantics></math>,
and (2)
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>Z</mi><annotation encoding="application/x-tex">Z</annotation></semantics></math>
blocks all paths to "Heart Disease".<br />
(1) is simple, as regardless of what we pick from in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">{</mo><mtext mathvariant="normal">High Cholesterol, High Blood Pressure, Heart Disease</mtext><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">\{\text{High Cholesterol, High Blood Pressure, Heart Disease}\}</annotation></semantics></math>
"High Cholesterol" is not a descendant. But, in order to satisfy (2) we
need to account for
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mtext mathvariant="normal">High Cholesterol</mtext><mo>→</mo><mtext mathvariant="normal">High Blood Pressure</mtext><mo>→</mo><mtext mathvariant="normal">Heart Disease</mtext></mrow><annotation encoding="application/x-tex">\text{High Cholesterol} \rightarrow\text{High Blood Pressure} \rightarrow\text{Heart Disease}</annotation></semantics></math>
Therefore,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Z</mi><mo>=</mo><mo stretchy="false" form="prefix">{</mo><mtext mathvariant="normal">High Blood Pressure</mtext><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">Z = \{\text{High Blood Pressure}\}</annotation></semantics></math>
and
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">Heart Disease</mtext><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="normal">High Cholesterol</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo><munder><mo>∑</mo><mi>z</mi></munder><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">Heart Disease</mtext><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="normal">High Cholesterol</mtext><mo>,</mo><mi>z</mi><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>z</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\text{Heart Disease}|\text{High Cholesterol}) = \sum_z P(\text{Heart Disease}|\text{High Cholesterol}, z)\cdot P(z)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">Heart Disease</mtext><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="normal">High Cholesterol</mtext><mo>,</mo><mtext mathvariant="normal">High Blood Pressure</mtext><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">High Blood Pressure</mtext><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">= P(\text{Heart Disease}|\text{High Cholesterol}, \text{High Blood Pressure})\cdot P(\text{High Blood Pressure})</annotation></semantics></math>
Even if the back-door path criterion is not satisfied, we can still use
the chain rule of probability to find the joint PDF <span
class="citation" data-cites="bnn_wiki"></span> <span class="citation"
data-cites="pitt_lec"></span>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">Heart Disease, High Blood Pressure, High Cholesterol</mtext><mo stretchy="false" form="postfix">)</mo><mo>=</mo></mrow><annotation encoding="application/x-tex">P(\text{Heart Disease, High Blood Pressure, High Cholesterol}) =</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">Heart Disease</mtext><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="normal">High Blood Pressure, High Cholesterol</mtext><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">High Blood Pressure</mtext><mo stretchy="false" form="prefix">|</mo><mtext mathvariant="normal">High Cholesterol</mtext><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mtext mathvariant="normal">High Cholesterol</mtext><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(\text{Heart Disease}|\text{High Blood Pressure, High Cholesterol})P(\text{High Blood Pressure}|\text{High Cholesterol})P(\text{High Cholesterol})</annotation></semantics></math>
From here on, let
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mo>=</mo><mtext mathvariant="normal">High Cholesterol</mtext></mrow><annotation encoding="application/x-tex">C = \text{High Cholesterol}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mo>=</mo><mtext mathvariant="normal">High Blood Pressure</mtext></mrow><annotation encoding="application/x-tex">B = \text{High Blood Pressure}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>D</mi><mo>=</mo><mtext mathvariant="normal">Heart Disease</mtext></mrow><annotation encoding="application/x-tex">D = \text{Heart Disease}</annotation></semantics></math>
Now, the trick is to identify those conditional probabilities. For that,
we will be using the PGMpy library in Python. The goal is to find the
<strong>conditional probability distributions</strong> (CPDs) between
all the variables involved in DAG 1. There are several ways to
accomplish this, one being the <strong>Maximum Likelihood
Estimator</strong> (MLE) method <span class="citation"
data-cites="pgmy_ex"></span>. In this case, the MLE would simply be all
the relative frequencies in the given data, but, naturally, this method
is strongly susceptible to <strong>overfitting</strong> the given data.
Another method, which we have discussed elsewhere in this project, is
Bayesian parameter estimation.<br />
<br />
For Bayesian parameter estimation of the CPDs we will choose the
Bayesian Dirichlet equivalent uniform distribution as our prior. The
estimated values in the CPDs will be more conservative <span
class="citation" data-cites="pgmy_ex"></span>.<br />
<br />
For the sake of simplicity, we will transform our cholesterol and blood
pressure measurement data in to binary categorical variables, where
<span class="math display">$$B = \begin{cases}
      1 &amp; \text{blood pressure} \geq  \sfrac{130}{80}\text{ mmHg}\\
     0 &amp; \text{otherwise}
   \end{cases}$$</span>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>C</mi><mo>=</mo><mrow><mo stretchy="true" form="prefix">{</mo><mtable><mtr><mtd columnalign="left" style="text-align: left"><mn>1</mn></mtd><mtd columnalign="left" style="text-align: left"><mtext mathvariant="normal">cholesterol</mtext><mo>≥</mo><mn>240</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> mg/dL</mtext></mrow></mtd></mtr><mtr><mtd columnalign="left" style="text-align: left"><mn>0</mn></mtd><mtd columnalign="left" style="text-align: left"><mtext mathvariant="normal">otherwise</mtext></mtd></mtr></mtable></mrow></mrow><annotation encoding="application/x-tex">C= \begin{cases} 
      1 &amp; \text{cholesterol} \geq  240 \text{   mg/dL}\\
     0 &amp; \text{otherwise}
   \end{cases}</annotation></semantics></math> <span class="citation"
data-cites="hc_to_hbp"></span>.<br />
</p>
<figure data-latex-placement="h">
<!-- <img src="./BBN3_cpds.png" style="width:95.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/BBN3_cpds.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>CPDs for DAG 1.</figcaption>
</figure>
<p>We have already established
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>C</mi><mo>,</mo><mi>D</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(C, D)</annotation></semantics></math>
conditioned on
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>Z</mi><mo>=</mo><mo stretchy="false" form="prefix">{</mo><mi>B</mi><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">Z = \{B\}</annotation></semantics></math>
satisfies the BDPC, so we know
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><munder><mo>∑</mo><mrow><mi>b</mi><mo>∈</mo><mo stretchy="false" form="prefix">{</mo><mn>0</mn><mo>,</mo><mn>1</mn><mo stretchy="false" form="postfix">}</mo></mrow></munder><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo>,</mo><mi>B</mi><mo>=</mo><mi>b</mi><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>B</mi><mo>=</mo><mi>b</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(D=1|C=1) = \sum_{b\in\{0,1\}} P(D=1|C=1, B=b)P(B=b)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo>,</mo><mi>B</mi><mo>=</mo><mn>0</mn><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>B</mi><mo>=</mo><mn>0</mn><mo stretchy="false" form="postfix">)</mo><mo>+</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo>,</mo><mi>B</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>B</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">= P(D=1|C=1, B=0)P(B=0)+P(D=1|C=1,B=1)P(B=1)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>0.4135</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>0.4085</mn><mo stretchy="false" form="postfix">)</mo><mo>+</mo><mo stretchy="false" form="prefix">(</mo><mn>0.5512</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>0.5915</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">= (0.4135)(0.4085) + (0.5512)(0.5915)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>0.4950</mn></mrow><annotation encoding="application/x-tex">P(D=1|C=1) = 0.4950</annotation></semantics></math>
Meaning, that if you walk into the ER with high cholesterol, there is a
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>49.50</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">49.50\%</annotation></semantics></math>
chance you have heart disease.<br />
<br />
We can also use the chain rule for probability method, given the CPDs we
have from Python. So, given that
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>,</mo><mi>B</mi><mo>,</mo><mi>C</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo stretchy="false" form="prefix">|</mo><mi>B</mi><mo>,</mo><mi>C</mi><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>B</mi><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>C</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(D,B,C) = P(D|B,C)P(B|C)P(C)</annotation></semantics></math>
if we wanted to find the probability of someone walking into a hospital
who does not have high blood pressure or high cholesterol, we simply
need to compute
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo>,</mo><mi>B</mi><mo>=</mo><mn>0</mn><mo>,</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>B</mi><mo>=</mo><mn>0</mn><mo>,</mo><mi>C</mi><mo>=</mo><mn>0</mn><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>B</mi><mo>=</mo><mn>0</mn><mo stretchy="false" form="prefix">|</mo><mi>C</mi><mo>=</mo><mn>0</mn><mo stretchy="false" form="postfix">)</mo><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>C</mi><mo>=</mo><mn>0</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">P(D=1, B=0, C=1) = P(D=1|B=0,C=0)P(B=0|C=0)P(C=0)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mn>0.6812</mn><mo>⋅</mo><mn>0.4563</mn><mo>⋅</mo><mn>0.3472</mn></mrow><annotation encoding="application/x-tex">= 0.6812\cdot 0.4563 \cdot 0.3472</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mn>0.1079</mn></mrow><annotation encoding="application/x-tex">= 0.1079</annotation></semantics></math>
In other words, if you walk into an ER with normal cholesterol and blood
pressure levels, than the probability you have heart disease drops to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>10.79</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">10.79\%</annotation></semantics></math>.<br />
<br />
We can also work backwards to find things like
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="prefix">|</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mrow><munder><mo>∑</mo><mrow><mi>b</mi><mo>∈</mo><mo stretchy="false" form="prefix">{</mo><mn>0</mn><mo>,</mo><mn>1</mn><mo stretchy="false" form="postfix">}</mo></mrow></munder><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo>,</mo><mi>B</mi><mo>=</mo><mi>b</mi><mo>,</mo><mi>C</mi><mo>=</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><mrow><munder><mo>∑</mo><mrow><mi>b</mi><mo>,</mo><mi>c</mi><mo>∈</mo><mo stretchy="false" form="prefix">{</mo><mn>0</mn><mo>,</mo><mn>1</mn><mo stretchy="false" form="postfix">}</mo></mrow></munder><mi>P</mi><mo stretchy="false" form="prefix">(</mo><mi>D</mi><mo>=</mo><mn>1</mn><mo>,</mo><mi>B</mi><mo>=</mo><mi>b</mi><mo>,</mo><mi>C</mi><mo>=</mo><mi>c</mi><mo stretchy="false" form="postfix">)</mo></mrow></mfrac></mrow><annotation encoding="application/x-tex">P(C=1|D=1) = \frac{\sum_{b\in\{0,1\}} P(D=1, B=b, C=1)}{\sum_{b,c\in\{0,1\}} P(D=1, B=b, C=c)}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>=</mo><mfrac><mrow><mn>0.4135</mn><mo>+</mo><mn>0.5512</mn></mrow><mrow><mn>0.6812</mn><mo>+</mo><mn>0.4135</mn><mo>+</mo><mn>0.6349</mn><mo>+</mo><mn>0.5512</mn></mrow></mfrac><mo>=</mo><mn>0.4230</mn></mrow><annotation encoding="application/x-tex">= \frac{0.4135 + 0.5512}{0.6812+0.4135+0.6349 + 0.5512} = 0.4230</annotation></semantics></math>
So, those who come into the hospital with heart disease, have a
probability of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>42.30</mn><mi>%</mi></mrow><annotation encoding="application/x-tex">42.30\%</annotation></semantics></math>
of also having high cholesterol.<br />
<br />
DAG 2 (see Figure 25) is a little more complicated. We have added two
variables to this DAG: angina and abnormal ECGs. But, there are no
causal cycles, and at least in the case of "High Cholesterol"
(<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>C</mi><annotation encoding="application/x-tex">C</annotation></semantics></math>),
it still satisfies the BDPC. The resultant CPD table is in Figure
27.</p>
<figure data-latex-placement="h">
<!-- <img src="./BBN5_cpds.png" style="width:95.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/BBN5_cpds.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>CPDs for DAG 2.</figcaption>
</figure>
<h2 id="structure-search-methods.">Structure Search Methods.</h2>
<p>But, in the case of DAG 2, it can be difficult to know whether this
DAG is legitimate. That is to say, whether the causal edges we have
chosen seem to be true given the data. It could also be the case that we
do not know the causal relationship between our variables at all, and
that is something we need to glean from the data. Luckily, there are
several search algorithms that sift through DAGs in search of the best
fit.<br />
<br />
The most obvious search method is brute-force. In the case of DAGs, this
is called the <strong>Exhaustive Search</strong> method. For the
variables in DAG 2, exhaustive search using PGMpy in Python yields</p>
<pre><code>    Exhaustive Search (BIC): [(&#39;Abnormal ECG&#39;, &#39;High Blood Pressure&#39;), 
    
    (&#39;HeartDisease&#39;, &#39;Abnormal ECG&#39;), (&#39;HeartDisease&#39;, &#39;Chest Pain&#39;), 
    
    (&#39;HeartDisease&#39;, &#39;High Cholesterol&#39;)]</code></pre>
<p>as our best fitting DAG. Or,<br />
<br />
Of course, exhaustive search becomes unfeasible when there are many
features, as the number of DAGs to check grows exponentially. For
example, think of the case of the COVID-19 severity risk factor data
set, which has 87 features <span class="citation"
data-cites="covid_risk"></span>. Instead, we can use <strong>Hill Climb
Search</strong>. Hill climb search is a heuristic search, very similar
to simulated annealing. Both Hill climb Search and simulated annealing
begin with a random solution (in this case DAG) and make small,
iterative changes to that solution. Then, they decide whether or not to
accept or reject the new solution based on some scoring criteria. The
difference between the two algorithms is that simulated annealing is
probabilistic, and allows for occasional acceptance of slightly worse
solutions in the hopes of exiting a possible <strong>local
extrema</strong>, where Hill Climb Search never accepts a worse solution
<span class="citation" data-cites="hill"></span>. The scoring criteria
used is called <strong>Bayesian Information Criterion</strong> (BIC).
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mi>I</mi><mi>C</mi><mo>=</mo><mi>k</mi><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><mi>L</mi><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">BIC = k\ln(n) - 2\ln(\hat{L})</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
is the number of features in the model,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
is the sample size of the data, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>L</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{L}</annotation></semantics></math>
is the maximized value of the likelihood function of the model <span
class="citation" data-cites="bic_wiki"></span>. Hill Climb search of the
variables in DAG 2 using PGMpy in Python yields:</p>
<pre><code>    Hill Climb Search (BIC): [(&#39;Abnormal ECG&#39;, &#39;HeartDisease&#39;), 
    
    (&#39;High Blood Pressure&#39;, &#39;Abnormal ECG&#39;),
    
    (&#39;HeartDisease&#39;, &#39;Chest Pain&#39;), (&#39;HeartDisease&#39;, &#39;High Cholesterol&#39;)]</code></pre>
<p>The resultant DAGs for each method of search can be seen in Figure
28. The DAG from exhaustive search is on the left, and Hill Climb search
on the right.</p>
<figure data-latex-placement="h">
<!-- <img src="./proposed_DAGS.png" style="width:95.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/proposed_DAGS.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>Proposed DAGs from Exhaustive Search &amp; Hill Climb
Search, respectively.</figcaption>
</figure>
<p>These DAGs are interesting, but some of the causal relationships
being posited by these search methods make little sense. For one, in the
exhaustive search (left) DAG, an abnormal ECG reading would not cause
high blood pressure, and in the Hill Climb search DAG (right) would not
cause heart disease– in fact, an ECG would not cause anything. And, also
in the Hill Climb search DAG (right), heart disease would not cause high
cholesterol– this relationship should be flipped. Given that we are
working with an abridges version of the full heart failure risk factor
data set (four features out of 11 possible), and a relatively small
sample size
(<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>918</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">n = 918)</annotation></semantics></math>,
we cannot expect the DAGs found via these search algorithms to be
perfect.<br />
<br />
In Figure 29, we see a causal DAG that is closer to the true
relationships between these variables <span class="citation"
data-cites="hc_to_hbp"></span> <span class="citation"
data-cites="hc_hbp_to_hd"></span> <span class="citation"
data-cites="hd_ecg"></span> <span class="citation"
data-cites="angina"></span>.</p>
<figure data-latex-placement="h">
<!-- <img src="./BNN_5Nodes.png" style="width:95.0%" /> -->
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="/assets/img/epidemics_projects/BNN_5Nodes.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<figcaption>Probable DAG 2.</figcaption>
</figure>
<p>When we compare the BIC scores of these three DAGs we see:</p>
<div class="center">
<table>
<thead>
<tr>
<th style="text-align: center;">i</th>
<th style="text-align: center;">DAG</th>
<th style="text-align: center;">BIC Score</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;">A</td>
<td style="text-align: center;">Exhaustive (Fig. 28, L)</td>
<td style="text-align: center;">-2977.9408</td>
</tr>
<tr>
<td style="text-align: center;">B</td>
<td style="text-align: center;">Hill Climb (Fig. 28, R)</td>
<td style="text-align: center;">-2978.3965</td>
</tr>
<tr>
<td style="text-align: center;">C</td>
<td style="text-align: center;">Proposed (Fig. 29)</td>
<td style="text-align: center;">-3108.0928</td>
</tr>
</tbody>
</table>
</div>
<h3 id="likelihood-ratio-test.">Likelihood Ratio Test.</h3>
<p>Just because our DAG search algorithms selected DAGs for us, does not
necessarily mean those DAGs fit the data <strong>significantly</strong>
better than our proposed model <span class="citation"
data-cites="probstat_course"></span>.<br />
<br />
We can set up the following likelihood ratio test:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>H</mi><mn>0</mn></msub><mo>:</mo><mi>M</mi><mo>=</mo><msub><mi>M</mi><mi>A</mi></msub></mrow><annotation encoding="application/x-tex">H_0: M = M_A</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>H</mi><mn>1</mn></msub><mo>:</mo><mi>M</mi><mo>=</mo><msub><mi>M</mi><mi>C</mi></msub></mrow><annotation encoding="application/x-tex">H_1: M=M_C</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>=</mo><mfrac><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>A</mi></msub><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>C</mi></msub></mfrac></mrow><annotation encoding="application/x-tex">\lambda =\frac{\hat{L}_A}{\hat{L}_C}</annotation></semantics></math>
So, our null hypothesis is that our data is better modelled by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>M</mi><mi>A</mi></msub><annotation encoding="application/x-tex">M_A</annotation></semantics></math>
(or, the DAG selected by the exhaustive search). We reject
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>H</mi><mn>0</mn></msub><mo>:</mo><mi>M</mi><mo>=</mo><msub><mi>M</mi><mi>A</mi></msub></mrow><annotation encoding="application/x-tex">H_0:M =M_A</annotation></semantics></math>
if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>&lt;</mo><mi>c</mi></mrow><annotation encoding="application/x-tex">\lambda &lt;c</annotation></semantics></math>,
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>c</mi><annotation encoding="application/x-tex">c</annotation></semantics></math>
corresponds to some
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>α</mi><annotation encoding="application/x-tex">\alpha</annotation></semantics></math>
significance <span class="citation"
data-cites="probstat_course"></span>.<br />
<br />
Recall, BIC is given by <span class="citation"
data-cites="bic_wiki"></span>:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mi>I</mi><mi>C</mi><mo>=</mo><mi>k</mi><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><mi>L</mi><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">BIC = k\ln(n) - 2\ln(\hat{L})</annotation></semantics></math>
Regardless of which of these DAGs we are evaluating, the intercept,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">k\ln(n)</annotation></semantics></math>,
will remain the same. In fact,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>5</mn><mo>⋅</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mn>918</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>34.11</mn></mrow><annotation encoding="application/x-tex">k\ln(n) = 5\cdot \ln(918) = 34.11</annotation></semantics></math>
Therefore, the term we care about is difference between
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mover><mi>L</mi><mo accent="true">̂</mo></mover><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">2\ln(\hat{L})</annotation></semantics></math>
for each model. We know
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>L</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{L}</annotation></semantics></math>
is the likelihood function
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mi>L</mi><mo accent="true">̂</mo></mover><mo>=</mo><mi>p</mi><mo stretchy="false" form="prefix">(</mo><mi>x</mi><mo stretchy="false" form="prefix">|</mo><mover><mi>θ</mi><mo accent="true">̂</mo></mover><mo>,</mo><mi>M</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\hat{L} = p(x|\hat{\theta}, M)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>θ</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{\theta}</annotation></semantics></math>
are whatever parameters maximize
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mover><mi>L</mi><mo accent="true">̂</mo></mover><annotation encoding="application/x-tex">\hat{L}</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>M</mi><annotation encoding="application/x-tex">M</annotation></semantics></math>
is the model <span class="citation" data-cites="bic_wiki"></span> <span
class="citation" data-cites="log_like"></span>.<br />
<br />
We can find
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>λ</mi><annotation encoding="application/x-tex">\lambda</annotation></semantics></math>
through the difference of our BIC scores for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mi>I</mi><msub><mi>C</mi><mi>A</mi></msub></mrow><annotation encoding="application/x-tex">BIC_A</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mi>I</mi><msub><mi>C</mi><mi>C</mi></msub></mrow><annotation encoding="application/x-tex">BIC_C</annotation></semantics></math></p>
<p><math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mi>I</mi><msub><mi>C</mi><mi>C</mi></msub><mo>−</mo><mi>B</mi><mi>I</mi><msub><mi>C</mi><mi>A</mi></msub><mo>=</mo><mi>k</mi><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>C</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mo stretchy="false" form="prefix">(</mo><mi>k</mi><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><mi>n</mi><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>A</mi></msub><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">BIC_C - BIC_A = k\ln(n) - 2\ln(\hat{L}_C) - (k\ln(n) - 2\ln(\hat{L}_A))</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>−</mi><mn>3108.0928</mn><mo>+</mo><mn>2977.9408</mn><mo>=</mo><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>A</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mn>2</mn><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>C</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">-3108.0928 + 2977.9408 = 2\ln(\hat{L}_A) - 2\ln(\hat{L}_C)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>−</mi><mn>65.076</mn><mo>=</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>A</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>−</mo><mrow><mi mathvariant="normal">ln</mi><mo>&#8289;</mo></mrow><mo stretchy="false" form="prefix">(</mo><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>C</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">-65.076 = \ln(\hat{L}_A) - \ln(\hat{L}_C)</annotation></semantics></math></p>
<p><math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>e</mi><mrow><mi>−</mi><mn>65.076</mn></mrow></msup><mo>=</mo><mfrac><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>A</mi></msub><msub><mover><mi>L</mi><mo accent="true">̂</mo></mover><mi>C</mi></msub></mfrac></mrow><annotation encoding="application/x-tex">e^{-65.076} = \frac{\hat{L}_A}{\hat{L}_C}</annotation></semantics></math>
So, we can see that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi><mo>=</mo><msup><mi>e</mi><mrow><mi>−</mi><mn>65.076</mn></mrow></msup><mo>≈</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">\lambda = e^{-65.076} \approx 0</annotation></semantics></math>.
This will be less than most
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>c</mi><annotation encoding="application/x-tex">c</annotation></semantics></math>
values, so we can be confident we reject
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>H</mi><mn>0</mn></msub><mo>:</mo><mi>M</mi><mo>=</mo><msub><mi>M</mi><mi>A</mi></msub></mrow><annotation encoding="application/x-tex">H_0: M = M_A</annotation></semantics></math>.
This means that our proposed DAG 2 in Figure 29 is <strong>not</strong>
a significantly worse model than the DAG selected by the exhaustive
search algorithm.</p>
<h1 id="bibliography.">Bibliography.</h1>
<div class="thebibliography">
<p><span>100</span></p>
<h2 id="background-sources."><strong>Background Sources.</strong></h2>
<p>Davidson-Pilon, C. (2016). <em>Bayesian Methods for Hackers:
Probabilistic Programming and Bayesian Inference</em>. Addison-Wesley.
Andrieu, C., de Freitas, N., Doucet, A. <em>et al.</em> (2003). An
Introduction to MCMC for Machine Learning. <em>Machine Learning</em> 50,
5–43. <a href="https://doi.org/10.1023/A:1020281327116"
class="uri">https://doi.org/10.1023/A:1020281327116</a> Tse, K. (2014)
Some Applications of the Poisson Process. <em>Applied
Mathematics</em>,05,3011-3017. DOI: <a href="10.4236/am.2014.519288"
class="uri">10.4236/am.2014.519288</a>. Gut, A. (2009). <em>An
Intermediate Course in Probability</em>. Springer. [DOI] <a
href="10.1007/9781-4419-0162-0" class="uri">10.1007/9781-4419-0162-0</a>
Niemi, Jarad, Ph.D. Jarad Niemi]. (2013, Jan 22). <em>Bayesian inference
for Poisson data</em> [Video]. YouTube. [URL] <a
href="https://www.youtube.com/watch?v=lNrpPNk6InU"
class="uri">https://www.youtube.com/watch?v=lNrpPNk6InU</a> Niemi,
Jarad, Ph.D [Jarad Niemi]. (2013, Mar 24). <em>Bayesian linear
regression</em> [Video]. YouTube. [URL] <a
href="https://www.youtube.com/watch?v=d1iIUtnDngg"
class="uri">https://www.youtube.com/watch?v=d1iIUtnDngg</a> Stephens, M.
(2018, Apr 23). <em>The Metropolis Hastings Algorithm</em>.
fiveMinuteStats. [URL] <a
href="https://stephens999.github.io/fiveMinuteStats/MH_intro.html"
class="uri">https://stephens999.github.io/fiveMinuteStats/MH_intro.html</a>
Dietze, M., Ph.D. (2020). <em>MCMC: Metropolis Algorithm</em> [Lecture
notes]. Boston University. [URL] <a
href="https://people.bu.edu/dietze/Bayes2020/Lesson12_Metropolis.pdf"
class="uri">https://people.bu.edu/dietze/Bayes2020/Lesson12_Metropolis.pdf</a>
Nau, R. (2020).<em>What’s a good value for R-squared?</em> [Lecture
notes]. Duke University. [URL] <a
href="https://people.duke.edu/~rnau/rsquared.htm#percentexplained"
class="uri">https://people.duke.edu/~rnau/rsquared.htm#percentexplained</a>
Sci-Kit Learn. (2023). <em>1.9. Naive Bayes</em>. Sci-Kit Learn
Documentation. [URL] <a
href="https://scikit-learn.org/stable/modules/naive_bayes.html"
class="uri">https://scikit-learn.org/stable/modules/naive_bayes.html</a>
Sci-Kit Learn. (2023). <em>Glossary of Common Terms and API
Elements</em>. Sci-Kit Learn Documentation. [URL] <a
href="https://scikit-learn.org/stable/glossary.html#term-scoring"
class="uri">https://scikit-learn.org/stable/glossary.html#term-scoring</a>
Sci-Kit Learn. (2023). <em>4.2 Permutation feature importance</em>.
Sci-Kit Learn Documentation. [URL] <a
href="https://scikit-learn.org/stable/modules/permutation_importance.html"
class="uri">https://scikit-learn.org/stable/modules/permutation_importance.html</a>
Xu, Z. (2022, Mar 12). <em>Understanding Sigmoid, Logistic, Softmax
Functions, and Cross-Entropy Loss (Log Loss) in Classification
Problems</em>. Towards Data Science. [URL] <a
href="https://towardsdatascience.com/understanding-sigmoid-logistic-softmax-functions-and-cross-entropy-loss-log-loss-dbbbe0a17efb#2ecb"
class="uri">https://towardsdatascience.com/understanding-sigmoid-logistic-softmax-functions-and-cross-entropy-loss-log-loss-dbbbe0a17efb#2ecb</a>
Fonnesbeck C., &amp; Kochurov, M. Introduction to Variational Inference
with PyMC. In <em>PyMC Examples</em>. PyMC Team. [DOI] <a
href="10.5281/zenodo.5654871" class="uri">10.5281/zenodo.5654871</a>
Simpson, D. (2019, Mar 19).<em>Maybe it’s time to let the old ways die;
or We broke R-hat so now we have to fix it.</em> [Discussion]. Columbia
University. [URL] <a
href="https://statmodeling.stat.columbia.edu/2019/03/19/maybe-its-time-to-let-the-old-ways-die-or-we-broke-r-hat-so-now-we-have-to-fix-it/"
class="uri">https://statmodeling.stat.columbia.edu/2019/03/19/maybe-its-time-to-let-the-old-ways-die-or-we-broke-r-hat-so-now-we-have-to-fix-it/</a></p>
<h2 id="epidemiology-specific-sources."><strong>Epidemiology Specific
Sources.</strong></h2>
<p>Lupague, R. M.J.M., Mabborang, R. C., Bansil, A. G., &amp; Lapague,
M. M. (2023). Integrated Machine Learning Model For Comprehensive Heart
Disease Risk Assessment Based On Multi-Dimensional Health Factors.
<em>European Journal of Computer Science and Information
Technology</em>, 11(3), 44-58. <a
href="https://doi.org/10.37745/ejcsit.2013/vol11n34458"
class="uri">https://doi.org/10.37745/ejcsit.2013/vol11n34458</a> Coly,
S., Garrido, M., Abrial, D., &amp; Yao, A. (2021). Bayesian hierarchical
models for disease mapping applied to contagious pathologies. <em>PLoS
ONE</em>, 16(1): e0222898. <a
href="https://doi.org/10.1371/journal.pone.0222898"
class="uri">https://doi.org/10.1371/journal.pone.0222898</a></p>
<h3 id="sir-models.">SIR Models.</h3>
<p>Smith, D. &amp; Moore, L. (2004, December).<em>"The SIR Model for
Spread of Disease - The Differential Equation Model"</em>. The
Mathematical Association of America. <a
href="https://maa.org/press/periodicals/loci/joma/the-sir-model-for-spread-of-disease-the-differential-equation-model"
class="uri">https://maa.org/press/periodicals/loci/joma/the-sir-model-for-spread-of-disease-the-differential-equation-model</a>
Cooper, I., Mondal, A., &amp; Antonopoulos, C. (2020). A SIR model
assumption for the spread of COVID-19 in different communities.
<em>Chaos, Solitons, &amp; Fractals</em>, 139. DOI: <a
href="https://doi.org/10.1016/j.chaos.2020.110057"
class="uri">https://doi.org/10.1016/j.chaos.2020.110057</a>. URL: <a
href="https://www.sciencedirect.com/science/article/pii/S0960077920304549?via%3Dihub"
class="uri">https://www.sciencedirect.com/science/article/pii/S0960077920304549?via%3Dihub</a></p>
<h3 id="branching-models.">Branching Models.</h3>
<p>Jacob, C. (2010). Branching Proceseses: Their Role in Epidemiology.
<em>International Journal of Environmental Research and Public
Health</em>, 7(3), 1186-1204. DOI: <a href="10.3390/ijerph7031204"
class="uri">10.3390/ijerph7031204</a> Bartoszynski, R. (1965). Branching
Processes and the Theory of Epidemics. <em>Berkeley Symposium on
Mathematical Statistics &amp; Probability</em>, 4, 259-269. [URL] <a
href="https://digicoll.lib.berkeley.edu/record/113134"
class="uri">https://digicoll.lib.berkeley.edu/record/113134</a> Laha A.
K., &amp; Majumdar, S. (2022). A multi-type branching process model for
epidemics with application to COVID-19. <em>Stochastic Environmental
Research and Risk Assessment</em>, 4, 259-269. DOI: <a
href="https://doi.org/10.1007/s00477-022-02298-9"
class="uri">https://doi.org/10.1007/s00477-022-02298-9</a> Ahlberg, D.
(2021, May 20). Epidemics and branching processes [Lecture notes].
Stockholm University. URL: <a
href="https://staff.math.su.se/daniel.ahlberg/notes-epidemics.pdf"
class="uri">https://staff.math.su.se/daniel.ahlberg/notes-epidemics.pdf</a>
Cooper, I., Mondal, A., &amp; Antonopoulos, C. G. (2020). Title of
article. A SIR model assumption for the spread of COVID-19 in different
communities, 139. <a href=" 10.1016/j.chaos.2020.110057" class="uri">
10.1016/j.chaos.2020.110057</a></p>
<h2 id="disease-specific-research."><strong>Disease Specific
Research.</strong></h2>
<h3 id="covid-19.-1">COVID-19.</h3>
<p>Liu, Y., Gayle, A. A., Wilder-Smith, A. &amp; Rocklov, J. (2020).The
reproductive number of COVID-19 is higher compared to SARS coronavirus.
Journal of Travel Medicine, 1-4. <a href="10.1093/jtm/taaa021"
class="uri">10.1093/jtm/taaa021</a> Centers for Disease Control and
Prevention. (2023, May 11). Isolation and Precautions for People with
COVID-19. COVID-19. [URL] <a
href="https://www.cdc.gov/coronavirus/2019-ncov/your-health/isolation.html#:~:text=If%20you%20test%20positive%20for,at%20home%20and%20in%20public."
class="uri">https://www.cdc.gov/coronavirus/2019-ncov/your-health/isolation.html#:~:text=If%20you%20test%20positive%20for,at%20home%20and%20in%20public.</a>
Manathunga, S. S., Abeyagunawardena, I. A., &amp; Dharmaratne, S. D.
(2023). A comparison of transmissibility of SARS-CoV-2 variants of
concern. Virology Journal, 20(59). <a
href="https://doi.org/10.1186/s12985-023-02018-x"
class="uri">https://doi.org/10.1186/s12985-023-02018-x</a> Achaiah, N.
C., Subbarajasetty, S. B., &amp; Shetty, R. M. (2020). R0 and Re of
COVID-19: Can We Predict When the Pandemic Outbreak will be Contained?.
Indian Jounrla of Critical Care Medicine, 24(11), 1125-1127. <a
href="10.5005/jp-journals-10071-23649"
class="uri">10.5005/jp-journals-10071-23649</a> Netherlands Ministry of
Health. (2023, June 11). Reproduction Number. Coronavirus Dashboard.
[URL] <a
href="https://coronadashboard.government.nl/landelijk/reproductiegetal"
class="uri">https://coronadashboard.government.nl/landelijk/reproductiegetal</a>
Ryu, S., Kim, D., Ali, S. T., &amp; Cowling, B. J. (2022). Serial
Interval and Transmission Dynamics during SARS-CoV-2 Delta Variant
Predominance, South Korea. Emergine Infectious Diseases (CDC), 28(2),
407-410. <a href="10.3201/eid2802.211774"
class="uri">10.3201/eid2802.211774</a> A Year of COVID in Pennsylvania.
(2021). ABC 27 WHTM. Retrieved November 06, 2023, from <a
href="https://www.abc27.com/timeline-of-a-year-of-covid-19-in-pennsylvania/"
class="uri">https://www.abc27.com/timeline-of-a-year-of-covid-19-in-pennsylvania/</a>
Procter, R. (2021, March 04). Remember when? Timeline marks key events
in California’s year-long pandemic grind. Cal Matters, [URL] <a
href="https://calmatters.org/health/coronavirus/2021/03/timeline-california-pandemic-year-key-points/."
class="uri">https://calmatters.org/health/coronavirus/2021/03/timeline-california-pandemic-year-key-points/.</a>
Adcroft, P., &amp; Toor, F. (2021, Mar 11). Timeline: How COVID-19
Changed NYC. <em>Spectrum News NY1</em>. [URL] <a
href="https://ny1.com/nyc/all-boroughs/news/2021/03/10/timeline--how-covid-19-changed-nyc"
class="uri">https://ny1.com/nyc/all-boroughs/news/2021/03/10/timeline--how-covid-19-changed-nyc</a>
Los Angeles Almanac. (2023). Military Installations in Los Angeles
County Past &amp; Present. In <em>Los Angeles Almanac</em>. [URL] <a
href="https://www.laalmanac.com/military/mi05.php"
class="uri">https://www.laalmanac.com/military/mi05.php</a></p>
<p>Walia, H., &amp; Jeevaraj, S. (2021). Early Mortality Risk Prediction
in Covid-19 Patients Using an Ensemble of Machine Learning Models.
<em>2021 International Conference on Computational Performance
Evaluation (ComPE)</em>, 965-970. [DOI] <a
href="10.1109/ComPE53109.2021.9751945"
class="uri">10.1109/ComPE53109.2021.9751945</a></p>
<h3 id="spanish-flu.">Spanish Flu.</h3>
<p>Barry, J. M. (2005). <em>The Great Influenza: The Story of the
Deadliest Pandemic in History</em>. Viking Press. [ISBN]
978-0670894734</p>
<h3 id="ebola.-2">Ebola.</h3>
<p>Kerkhove, M. D. V., Bento, A. I., Ferguson, N. M., &amp; Donnelly, C.
A. (2015). A review of epidemiological parameters from Ebola outbreaks
to inform early public health decision-making. Scientific Data, 2.
https://doi.org/10.1038/sdata.2015.19 Centers for Disease Control and
Prevention. (2019, March 18). 2014-2016 Ebola Outbreak in West Africa.
CDC. [URL] <a
href="https://www.cdc.gov/vhf/ebola/history/2014-2016-outbreak/index.html"
class="uri">https://www.cdc.gov/vhf/ebola/history/2014-2016-outbreak/index.html</a>
World Health Organization. (2015, January). Factors that contributed to
undetected spread of the Ebola virus and impeded rapid containment. WHO.
[URL] <a
href="https://www.who.int/news-room/spotlight/one-year-into-the-ebola-epidemic/factors-that-contributed-to-undetected-spread-of-the-ebola-virus-and-impeded-rapid-containment"
class="uri">https://www.who.int/news-room/spotlight/one-year-into-the-ebola-epidemic/factors-that-contributed-to-undetected-spread-of-the-ebola-virus-and-impeded-rapid-containment</a>
Johns Hopkins Medicine. Ebola. Health. [URL] <a
href="https://www.hopkinsmedicine.org/health/conditions-and-diseases/ebola#:~:text=If%20treatment%20is%20ineffective%20or,from%20the%20start%20of%20symptoms."
class="uri">https://www.hopkinsmedicine.org/health/conditions-and-diseases/ebola#:~:text=If%20treatment%20is%20ineffective%20or,from%20the%20start%20of%20symptoms.</a></p>
<h2 id="datasets."><strong>Datasets.</strong></h2>
<p>Center for Systems Science and Engineering (CSSE) at Johns Hopkins
(2023). Novel Coronavirus (COVID-19) Cases [Data set]. CSSE Johns
Hopkins. [URL] <a href="https://github.com/CSSEGISandData/COVID-19"
class="uri">https://github.com/CSSEGISandData/COVID-19</a> Centers for
Disease Control and Prevention (2021). Behavioral Risk Factor Analysis
Surveillance System Data [Data set]. CDC. [URL] <a
href="https://www.cdc.gov/brfss/annual_data/annual_2021.html"
class="uri">https://www.cdc.gov/brfss/annual_data/annual_2021.html</a>
Centers for Disease Control and Prevention (2019). 2014 Ebola Outbreak
in West Africa Epidemic Curves [Data set]. CDC. [URL] <a
href="https://www.cdc.gov/vhf/ebola/history/2014-2016-outbreak/cumulative-cases-graphs.html?CDC_AA_refVal=https%3A%2F%2Fwww.cdc.gov%2Fvhf%2Febola%2Foutbreaks%2F2014-west-africa%2Fcumulative-cases-graphs.html."
class="uri">https://www.cdc.gov/vhf/ebola/history/2014-2016-outbreak/cumulative-cases-graphs.html?CDC_AA_refVal=https%3A%2F%2Fwww.cdc.gov%2Fvhf%2Febola%2Foutbreaks%2F2014-west-africa%2Fcumulative-cases-graphs.html.</a>
World Health Organization (2016). Ebola data and statistics [Data set].
WHO. [URL] <a
href="https://apps.who.int/gho/data/node.ebola-sitrep.quick-downloads?lang=en"
class="uri">https://apps.who.int/gho/data/node.ebola-sitrep.quick-downloads?lang=en</a>
Centers for Disease Control and Prevention (2020). Case Counts [Data
set]. CDC. [URL] <a
href="https://www.cdc.gov/vhf/ebola/history/2014-2016-outbreak/case-counts.html."
class="uri">https://www.cdc.gov/vhf/ebola/history/2014-2016-outbreak/case-counts.html.</a>
Walia, H (Kaggle) (2021). <em>Mortality Risk clinical data of COVID-19
Patients</em> (1) [Data set]. [URL] <a
href="https://www.kaggle.com/datasets/harshwalia/mortality-risk-clinincal-data-of-covid19-patients/data"
class="uri">https://www.kaggle.com/datasets/harshwalia/mortality-risk-clinincal-data-of-covid19-patients/data</a></p>
<p>fedesoriano (Kaggle). (September 2021). <em>Heart Failure Prediction
Dataset</em> (1) [Data set]. [URL] <a
href="https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction"
class="uri">https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction</a>.</p>
<h2 id="bayesian-belief-networks."><strong>Bayesian Belief
Networks.</strong></h2>
<p>Bayesian network. (2023, Dec 8). In <em>Wikipedia</em>. [URL] <a
href="https://en.wikipedia.org/wiki/Bayesian_network"
class="uri">https://en.wikipedia.org/wiki/Bayesian_network</a> Pearl, J.
(2009). <em>Causality: Models, Reasoning, and Inference</em> (2).
Cambridge University Press. [ISBN] 978-0521895606. [URL] <a
href="http://bayes.cs.ucla.edu/BOOK-2K/"
class="uri">http://bayes.cs.ucla.edu/BOOK-2K/</a>, <a
href="http://bayes.cs.ucla.edu/BOOK-2K/ch3-3.pdf"
class="uri">http://bayes.cs.ucla.edu/BOOK-2K/ch3-3.pdf</a> Bayesian
Information Criterion. (2023, Apr 18). In <em>Wikipedia</em>. [URL] <a
href="https://en.wikipedia.org/wiki/Bayesian_information_criterion"
class="uri">https://en.wikipedia.org/wiki/Bayesian_information_criterion</a>
Pisho-Nik, H. (2014). <em>Introduction to Probability, Statistics, and
Random Processes</em>. Kappa Research, LLC. [ISBN] 978-0990637202. [URL]
<a
href="https://www.probabilitycourse.com/chapter8/8_4_5_likelihood_ratio_tests.php"
class="uri">https://www.probabilitycourse.com/chapter8/8_4_5_likelihood_ratio_tests.php</a>
Ankan, A. (n.d.). <em>Learning Bayesian Networks from Data</em>. PGMpy.
[URL] <a
href="https://pgmpy.org/detailed_notebooks/10.%20Learning%20Bayesian%20Networks%20from%20Data.html"
class="uri">https://pgmpy.org/detailed_notebooks/10.%20Learning%20Bayesian%20Networks%20from%20Data.html</a>
Geeks For Geeks. (2023, Apr 20). <em>Introduction to Hill Climbing |
Artificial Intelligence</em>. GeeksForGeeks. [URL] <a
href="https://www.geeksforgeeks.org/introduction-hill-climbing-artificial-intelligence/"
class="uri">https://www.geeksforgeeks.org/introduction-hill-climbing-artificial-intelligence/</a>.
Likelihood-ratio test. (2023, Nov 19). In <em>Wikipedia</em>. [URL] <a
href="https://en.wikipedia.org/wiki/Likelihood-ratio_test"
class="uri">https://en.wikipedia.org/wiki/Likelihood-ratio_test</a>.
Hauskrecht, M. (n.d.). <em>Bayesian belief networks</em> [Lecture
notes]. University of Pittsburgh. [URL] <a
href="https://people.cs.pitt.edu/~milos/courses/cs2740/Lectures/class19.pdf"
class="uri">https://people.cs.pitt.edu/~milos/courses/cs2740/Lectures/class19.pdf</a></p>
<p>Cleveland Clinic. (n.d.). <em>High Cholesterol Diseases</em>.
Cleveland Clinic. [URL] <a
href="https://my.clevelandclinic.org/health/articles/11918-cholesterol-high-cholesterol-diseases"
class="uri">https://my.clevelandclinic.org/health/articles/11918-cholesterol-high-cholesterol-diseases</a></p>
<p>Centers for Disease Control and Prevention. (2022, Sep 8). <em>Heart
Disease and Stroke</em>. CDC. [URL]<a
href="https://www.cdc.gov/chronicdisease/resources/publications/factsheets/heart-disease-stroke.htm#:~:text=Leading%20risk%20factors%20for%20heart,unhealthy%20diet%2C%20and%20physical%20inactivity."
class="uri">https://www.cdc.gov/chronicdisease/resources/publications/factsheets/heart-disease-stroke.htm#:~:text=Leading%20risk%20factors%20for%20heart,unhealthy%20diet%2C%20and%20physical%20inactivity.</a>
Mount Sinai. (n.d). <em>Electrocardiogram</em>. Mount Sinai. [URL] <a
href="https://www.mountsinai.org/health-library/tests/electrocardiogram"
class="uri">https://www.mountsinai.org/health-library/tests/electrocardiogram</a>
Mayo Clinic. (n.d.). <em>Angina</em>. Mayo Clinic. [URL] <a
href="https://www.mayoclinic.org/diseases-conditions/angina/symptoms-causes/syc-20369373#:~:text=Too%20much%20bad%20cholesterol%20%E2%80%94%20low,Other%20health%20conditions."
class="uri">https://www.mayoclinic.org/diseases-conditions/angina/symptoms-causes/syc-20369373#:~:text=Too%20much%20bad%20cholesterol%20%E2%80%94%20low,Other%20health%20conditions.</a></p>
</div>
</body>
</html>