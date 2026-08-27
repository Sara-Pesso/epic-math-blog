---
layout: page
title: Rubik's Cube Solvability Using Group Theory
description: A mathematical approach to modelling the solvability of a Rubik's Cube
img: /assets/img/12.jpg
---


<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="initial-scale=1.0, user-scalable=yes" />
  <meta name="author" content="Sara Pessognelli" />
  <title>Rubik’s Cube Solvability using Group Theory</title>
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
      overflow-x: auto;
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
<!-- <header id="title-block-header">
<h1 class="title">Rubik’s Cube Solvability using Group Theory</h1>
<p class="author">Sara Pessognelli</p>
<p class="date">April 2026</p>
</header> -->
<h1 id="introduction">Introduction</h1>
<p>In 1878, puzzle maker Sam Loyd released a 15-square puzzle with a
prize of $1000 for the first person to solve it. Legend has it that
“people became infatuated with puzzle" in hopes of winning the money. In
this pursuit, “pilots are said to have wrecked their ships, and
engineers rush theirs trains past their stations", people would claim to
have solved the puzzle only to mysteriously fail to recollect the exact
sequence of moves that solved the puzzle. Ultimately, no one was ever
able to claim the prize from Loyd for one simple reason: the puzzle was
unsolvable– and using basic group theory, it is easy to prove!<span
class="citation" data-cites="textbook"></span><br />
<br />
Using the same group theory ideas and applying them to the Rubik’s Cube,
we will explore the Rubik’s Cube Group for both the 3x3 and 2x2 Rubik’s
Cubes. We will also discuss an algorithm to solve the cube, why it
works, and how to make impossible Rubik’s Cubes so you, too, can prank
puzzle-solvers everywhere.</p>
<h1 id="group-theory-in-the-rubiks-cube">Group Theory in the Rubik’s
Cube</h1>
<h2 id="notation">Notation</h2>
<p>We will represent each cube using Singmaster notation, which
represents a clockwise (cw), 90 degree turn of each side of the Rubik’s
cube using a letter, with respect to a stationary observer <span
class="citation" data-cites="sfunotation"></span>. These are known as
the 6 Basic Moves and are explained further in Figure <a
href="#tab:placeholder" data-reference-type="ref"
data-reference="tab:placeholder">1</a>.</p>
<div id="tab:placeholder">
<table>
<caption>Table of the 6 Basic Cube Moves</caption>
<tbody>
<tr>
<td style="text-align: center;">R</td>
<td style="text-align: center;">90 deg. cw rotation of the RIGHT
face</td>
</tr>
<tr>
<td style="text-align: center;">L</td>
<td style="text-align: center;">90 deg. cw rotation of the LEFT
face</td>
</tr>
<tr>
<td style="text-align: center;">U</td>
<td style="text-align: center;">90 deg. cw rotation of the UP face</td>
</tr>
<tr>
<td style="text-align: center;">D</td>
<td style="text-align: center;">90 deg. cw rotation of the DOWN
face</td>
</tr>
<tr>
<td style="text-align: center;">F</td>
<td style="text-align: center;">90 deg. cw rotation of the FRONT
face</td>
</tr>
<tr>
<td style="text-align: center;">B</td>
<td style="text-align: center;">90 deg. cw rotation of the BACK
face</td>
</tr>
</tbody>
</table>
</div>
<p>Note that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>R</mi><mo>′</mo></msup><mo>,</mo><msup><mi>L</mi><mo>′</mo></msup><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><mo>,</mo><msup><mi>D</mi><mo>′</mo></msup><mo>,</mo><msup><mi>F</mi><mo>′</mo></msup><mo>,</mo><msup><mi>B</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">R&#39;, L&#39;, U&#39;, D&#39;,  F&#39;, B&#39;</annotation></semantics></math>
represent the inverse of each cube move, or a 90 degree counter
clockwise (ccw) rotation of the face.<br />
<br />
Comprising the 3x3 Rubik’s Cube, there are 26 individual
<strong>cubelets</strong> (or <strong>cubies</strong>). Of these, only
20 are mutable, while the center cubelets never change position or
reorient when moves are applied. There are 8 <strong>corner
cubelets</strong> and 12 <strong>edge cubelets</strong>. Each cubelet
occupies a different <strong>cubicle</strong> (it’s position relative to
the user).<br />
These cubelets are comprised of 54 <strong>facelets</strong> (that is,
the colorful, “sticker" sides of the cubelets). Again, only 48 are
mutable, while the center facelet on each face of the Rubik’s Cube never
changes.<br />
<br />
The 2x2 Rubik’s Cube (known as the Pocket Cube) has 8 cubelets (8 corner
and 0 edge cubelets) and 24 facelets, all of which are mutable.</p>
<h2 id="the-rubiks-cube-group.">The Rubik’s Cube Group.</h2>
<p>Let’s briefly discuss how the set of all legal moves of the Rubik’s
Cube (which is equivalent to all legal configurations of the Rubik’s
Cube) form a group:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G, \cdot)</annotation></semantics></math>.
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mn>1</mn></msub><annotation encoding="application/x-tex">g_1</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mn>2</mn></msub><annotation encoding="application/x-tex">g_2</annotation></semantics></math>
be two moves within the set of possible Rubik’s Cube moves,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>,</mo><msub><mi>g</mi><mn>2</mn></msub><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g_1, g_2 \in G</annotation></semantics></math>,
and let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>⋅</mi><annotation encoding="application/x-tex">\cdot</annotation></semantics></math>
be defined as performing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mn>1</mn></msub><annotation encoding="application/x-tex">g_1</annotation></semantics></math>
followed by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mn>2</mn></msub><annotation encoding="application/x-tex">g_2</annotation></semantics></math>.
In order to be a group,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>
must satisfy the following four criteria:</p>
<ul>
<li><p><strong>Closure.</strong> Under
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>⋅</mi><annotation encoding="application/x-tex">\cdot</annotation></semantics></math>,
since
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mn>1</mn></msub><annotation encoding="application/x-tex">g_1</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mn>2</mn></msub><annotation encoding="application/x-tex">g_2</annotation></semantics></math>
are legal Rubik’s Cube moves, clearly
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>g</mi><mn>2</mn></msub></mrow><annotation encoding="application/x-tex">g_1\cdot g_2</annotation></semantics></math>
is a legal configuration. Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>g</mi><mn>2</mn></msub><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g_1\cdot g_2 \in G</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is closed.</p></li>
<li><p><strong>Identity elements.</strong> Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>e</mi><annotation encoding="application/x-tex">e</annotation></semantics></math>
be the empty move, where we do nothing to the Rubik’s Cube. Then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>e</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">e\in G</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">\forall g\in G</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>e</mi><mo>⋅</mo><mi>g</mi><mo>=</mo><mi>g</mi><mo>⋅</mo><mi>e</mi><mo>=</mo><mi>g</mi></mrow><annotation encoding="application/x-tex">e\cdot g = g\cdot e = g</annotation></semantics></math>,
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>e</mi><annotation encoding="application/x-tex">e</annotation></semantics></math>
is the identity element.</p></li>
<li><p><strong>Associativity.</strong> Clearly,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is associative under
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>⋅</mi><annotation encoding="application/x-tex">\cdot</annotation></semantics></math>.
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>,</mo><msub><mi>g</mi><mn>2</mn></msub><mo>,</mo><msub><mi>g</mi><mn>3</mn></msub><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g_1, g_2, g_3 \in G</annotation></semantics></math>,
we can see that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><msub><mi>g</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>g</mi><mn>2</mn></msub><mo stretchy="false" form="postfix">)</mo><mo>⋅</mo><msub><mi>g</mi><mn>3</mn></msub><mo>=</mo><msub><mi>g</mi><mn>1</mn></msub><mo>⋅</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>g</mi><mn>2</mn></msub><mo>⋅</mo><msub><mi>g</mi><mn>3</mn></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(g_1\cdot g_2)\cdot g_3 = g_1 \cdot(g_2\cdot g_3)</annotation></semantics></math>,
because the 6 Basic Moves that each
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>g</mi><mi>i</mi></msub><annotation encoding="application/x-tex">g_i</annotation></semantics></math>
consists of are associative. Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>
is associative.</p></li>
<li><p><strong>Inverses.</strong> There must exist an inverse for every
Rubik’s Cube move. Earlier, we defined for each basic move
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>X</mi><annotation encoding="application/x-tex">X</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>X</mi><mo>′</mo></msup><annotation encoding="application/x-tex">X&#39;</annotation></semantics></math>
as it’s inverse– which simply performing a 90 degree ccw rotation on the
same face. So,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">\forall g\in G</annotation></semantics></math>,
we can write
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>X</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>X</mi><mn>2</mn></msub><mi>.</mi><mi>.</mi><mi>.</mi><mo>⋅</mo><msub><mi>X</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">g= (X_1\cdot X_2 ... \cdot X_n)</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>X</mi><mn>1</mn></msub><mo>,</mo><msub><mi>X</mi><mn>2</mn></msub><mo>,</mo><mi>.</mi><mi>.</mi><mi>.</mi><msub><mi>X</mi><mi>n</mi></msub></mrow><annotation encoding="application/x-tex">X_1,X_2,...X_n</annotation></semantics></math>
are each one of the 6 Basic Moves. Then, we can easily find the inverse
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>g</mi><mo>′</mo></msup><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>X</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>X</mi><mn>2</mn></msub><mi>.</mi><mi>.</mi><mi>.</mi><mo>⋅</mo><msub><mi>X</mi><mi>n</mi></msub><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>−</mi><mn>1</mn></mrow></msup><mo>=</mo><msubsup><mi>X</mi><mi>n</mi><mo>′</mo></msubsup><mo>⋅</mo><msubsup><mi>X</mi><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><mo>′</mo></msubsup><mi>.</mi><mi>.</mi><mi>.</mi><msubsup><mi>X</mi><mn>1</mn><mo>′</mo></msubsup></mrow><annotation encoding="application/x-tex">g&#39; = (X_1\cdot X_2 ... \cdot X_n)^{-1} = X_n&#39;\cdot X_{n-1}&#39;...X_1&#39;</annotation></semantics></math>.
This is the inverse of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>g</mi><annotation encoding="application/x-tex">g</annotation></semantics></math>,
because
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msubsup><mi>X</mi><mi>n</mi><mo>′</mo></msubsup><mo>⋅</mo><msubsup><mi>X</mi><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><mo>′</mo></msubsup><mi>.</mi><mi>.</mi><mi>.</mi><msubsup><mi>X</mi><mn>1</mn><mo>′</mo></msubsup><mo>⋅</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>X</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>X</mi><mn>2</mn></msub><mi>.</mi><mi>.</mi><mi>.</mi><mo>⋅</mo><msub><mi>X</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><msubsup><mi>X</mi><mi>n</mi><mo>′</mo></msubsup><mo>⋅</mo><msubsup><mi>X</mi><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><mo>′</mo></msubsup><mi>.</mi><mi>.</mi><mi>.</mi><msubsup><mi>X</mi><mn>1</mn><mo>′</mo></msubsup><mo>⋅</mo><mo stretchy="false" form="prefix">(</mo><msub><mi>X</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>X</mi><mn>2</mn></msub><mi>.</mi><mi>.</mi><mi>.</mi><mo>⋅</mo><msub><mi>X</mi><mi>n</mi></msub><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>e</mi></mrow><annotation encoding="application/x-tex">X_n&#39;\cdot X_{n-1}&#39;...X_1&#39; \cdot(X_1\cdot X_2 ... \cdot X_n) = X_n&#39;\cdot X_{n-1}&#39;...X_1&#39;\cdot (X_1\cdot X_2 ... \cdot X_n) = e</annotation></semantics></math>
(for a more formal proof by induction see <span class="citation"
data-cites="chen"></span>). Essentially, just do all Basic Moves that
comprise
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
in reverse, and we have the inverse.</p></li>
</ul>
<p>Now that We have established
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>
is a group, we can move on to more interesting explorations. It is also
important to note that the group of Rubik’s Cube moves is the same for
both the 3x3 and 2x2 Rubik’s Cube. For
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> x </mtext><mspace width="0.333em"></mspace></mrow><mi>n</mi></mrow><annotation encoding="application/x-tex">n \text{ x } n</annotation></semantics></math>
Rubik’s Cubes with
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>&gt;</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">n&gt;3</annotation></semantics></math>,
we would need to define more moves for the interior, movable cubes, so
we will only be discussing the 3x3 or 2x2 Cubes here.</p>
<h2 id="showing-g-is-non-abelian.">Showing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is Non-Abelian.</h2>
<p>We can do this with a counter example. Consider
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mo>⋅</mo><mi>U</mi></mrow><annotation encoding="application/x-tex">R\cdot U</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>U</mi><mo>⋅</mo><mi>R</mi></mrow><annotation encoding="application/x-tex">U\cdot R</annotation></semantics></math>.
Performing each of these moves on the Pocket Cube starting in the solved
state, results in the states in Figure <a href="#fig:RU"
data-reference-type="ref" data-reference="fig:RU">[fig:RU]</a> and
Figure <a href="#fig:UR" data-reference-type="ref"
data-reference="fig:UR">1</a>, respectively. Clearly,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mi>U</mi><mo>≠</mo><mi>U</mi><mi>R</mi></mrow><annotation encoding="application/x-tex">RU \not = UR</annotation></semantics></math>.
Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is non-abelian in the 2x2 case.<br />
<br />
This result generalizes to the 3x3 Rubik’s Cube as well, since the
Pocket Cube represents the corners of the 3x3 Rubik’s Cube. Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is also non-abelian for the 3x3 Rubik’s Cube.</p>
<figure id="fig:UR">
<div class="minipage">
<p><img src="./RU.JPG" alt="image" /> <span id="fig:RU"
data-label="fig:RU"></span></p>
</div>
<div class="minipage">
<p><img src="./UR.JPG" alt="image" /> <span id="fig:UR"
data-label="fig:UR"></span></p>
</div>
</figure>
<h2 id="generators.">Generators.</h2>
<p>Because we have shown that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is not abelian, we know that it is <strong>not cyclic</strong>. That is,
<span class="math inline">$\not \exists g \in G$</span> such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>=</mo><mo stretchy="false" form="prefix">{</mo><msup><mi>g</mi><mi>n</mi></msup><mo>:</mo><mi>n</mi><mo>∈</mo><mi mathvariant="double-struck">ℕ</mi><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">&lt;g&gt; = \{g^n: n\in \mathbb{N}\}</annotation></semantics></math>
<span class="citation" data-cites="textbook"></span>. But, there are
some generating sets. An obvious generator is the set of our 6 Basic
Moves (plus the identity or empty move) with their inverses:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>e</mi><mo>,</mo><mi>L</mi><mo>,</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo>,</mo><msup><mi>L</mi><mo>′</mo></msup><mo>,</mo><msup><mi>R</mi><mo>′</mo></msup><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><mo>,</mo><msup><mi>D</mi><mo>′</mo></msup><mo>,</mo><msup><mi>F</mi><mo>′</mo></msup><mo>,</mo><msup><mi>B</mi><mo>′</mo></msup><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">&lt;e,L,R,U,D,F,B,L&#39;,R&#39;,U&#39;,D&#39;,F&#39;,B&#39;&gt;</annotation></semantics></math>.
Maybe less obvious is that just the 6 Basic Moves themselves constitute
a generator of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
<span class="citation" data-cites="Garron"></span>, that is:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>L</mi><mo>,</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo>&gt;</mo><mo>=</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">&lt;L,R,U,D,F,B&gt; = G</annotation></semantics></math>
we can undo each of these using combinations of the other five moves
<span class="citation" data-cites="Garron"></span>. Also, observe that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>X</mi><mo>∈</mo><mo stretchy="false" form="prefix">{</mo><mi>R</mi><mo>,</mo><mi>L</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">\forall X\in \{R,L,U,D,F,B\}</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>X</mi><mi>X</mi><mi>X</mi><mi>X</mi><mo>=</mo><msup><mi>X</mi><mn>4</mn></msup><mo>=</mo><mi>e</mi></mrow><annotation encoding="application/x-tex">XXXX = X^4 = e</annotation></semantics></math>,
so the identity is always available.<br />
<br />
Using the previous observation, it becomes more obvious that any one of
the 6 Basic Moves can be generated from the other 5. That is,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>L</mi><mo>,</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;L,R,U,D,F&gt;</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>L</mi><mo>,</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>B</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;L,R,U,D,B&gt;</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>L</mi><mo>,</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;L,R,U,F,B&gt;</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>L</mi><mo>,</mo><mi>R</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;L,R,D,F,B&gt;</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>L</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;L,U,D,F,B&gt;</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo>,</mo><mi>D</mi><mo>,</mo><mi>F</mi><mo>,</mo><mi>B</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;R,U,D,F,B&gt;</annotation></semantics></math>
are all generating sets, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>
is <strong>five-generated</strong> <span class="citation"
data-cites="Garron"></span>. An example from Garron’s paper is that</p>
<p><math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>D</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><msup><mi>L</mi><mo>′</mo></msup><mi>R</mi><mi>F</mi><mi>F</mi><mi>B</mi><mi>B</mi><msup><mi>L</mi><mo>′</mo></msup><mi>R</mi><mo stretchy="false" form="postfix">)</mo><mi>U</mi><mo stretchy="false" form="prefix">(</mo><msup><mi>L</mi><mo>′</mo></msup><mi>R</mi><mi>F</mi><mi>F</mi><mi>B</mi><mi>B</mi><msup><mi>L</mi><mo>′</mo></msup><mi>R</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">D = (L&#39; R FF BB L&#39; R) U (L&#39; R FF BB L&#39; R)</annotation></semantics></math></p>
<p>Furthermore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is <strong>two-generated</strong> when using compound moves. An example
from Garron is
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>=</mo><mo>&lt;</mo><mi>U</mi><mi>B</mi><mi>L</mi><mi>U</mi><msup><mi>L</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup><msup><mi>B</mi><mo>′</mo></msup><mo>,</mo><mi>R</mi><mi>R</mi><mi>F</mi><mi>L</mi><msup><mi>D</mi><mo>′</mo></msup><msup><mi>R</mi><mo>′</mo></msup><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">G = &lt;UBLUL&#39;U&#39;B&#39;, RRFLD&#39;R&#39;&gt;</annotation></semantics></math></p>
<h2 id="subgroups.">Subgroups.</h2>
<p>Recall that a subgroup,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>H</mi><annotation encoding="application/x-tex">H</annotation></semantics></math>,
is a subset of a group that is a group itself under the same operation
<span class="citation" data-cites="textbook"></span>. This written as
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>H</mi><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">H \leq G</annotation></semantics></math>.
In fact,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>≤</mo><msub><mi>S</mi><mn>54</mn></msub><mo>,</mo><mi>G</mi><mo>≤</mo><msub><mi>S</mi><mn>48</mn></msub></mrow><annotation encoding="application/x-tex">G\leq S_{54}, G\leq S_{48}</annotation></semantics></math>
for the 3x3 Rubik’s Cube <span class="citation"
data-cites="Bobzien"></span>, and in the Pocket Cube case
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>≤</mo><msub><mi>S</mi><mn>24</mn></msub></mrow><annotation encoding="application/x-tex">G\leq S_{24}</annotation></semantics></math>.<br />
<br />
Recall that the symmetric group,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>S</mi><mi>n</mi></msub><annotation encoding="application/x-tex">S_n</annotation></semantics></math>,
consists permutations of a set of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>n</mi><annotation encoding="application/x-tex">n</annotation></semantics></math>
items. In the case of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>S</mi><mn>54</mn></msub><annotation encoding="application/x-tex">S_{54}</annotation></semantics></math>,
we can see that the 3x3 Rubik’s Cube has 54 facelets that can be
permuted, but as aforementioned not all these permutations are possible.
Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>≤</mo><msub><mi>S</mi><mn>54</mn></msub></mrow><annotation encoding="application/x-tex">G \leq S_{54}</annotation></semantics></math>.
The case for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>S</mi><mn>48</mn></msub><annotation encoding="application/x-tex">S_{48}</annotation></semantics></math>
is similar, except here we observe that that center facelet on each face
of the Rubik’s Cube never move, leaving only 48 facelets to permute.
Again, not all permutations of these 48 facelets are legal, so it
follows that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>≤</mo><msub><mi>S</mi><mn>48</mn></msub></mrow><annotation encoding="application/x-tex">G \leq S_{48}</annotation></semantics></math>
<span class="citation" data-cites="Bobzien"></span>.<br />
Similarly, the Pocket Cube is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>≤</mo><msub><mi>S</mi><mn>24</mn></msub></mrow><annotation encoding="application/x-tex">G \leq S_{24}</annotation></semantics></math>.
It has 24 facelets that can be permuted, but not all these permutations
are legal.<br />
<br />
More interesting are the subgroups of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G, \cdot)</annotation></semantics></math>,
Garron lays out many examples, the obvious being <span class="citation"
data-cites="textbook"></span>:</p>
<ul>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">G\leq G</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>e</mi><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">e \leq G</annotation></semantics></math></p></li>
</ul>
<p>Unfortunately, because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>
is not cyclic, the number and orders of the subgroups is not obvious.
So, we will just discuss an interesting one here:<br />
<br />
For any
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g \in G</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">&lt;g&gt; \leq G</annotation></semantics></math>
<span class="citation" data-cites="Garron"></span>. Garron doesn’t prove
this in his paper, so we will show it here:</p>
<ul>
<li><p><strong>Subset.</strong>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>⊂</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">&lt;g&gt; \subset G</annotation></semantics></math>,
since
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>
is closed under
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>⋅</mi><annotation encoding="application/x-tex">\cdot</annotation></semantics></math></p></li>
<li><p><strong>Closure</strong>. Because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>=</mo><mo stretchy="false" form="prefix">{</mo><msup><mi>g</mi><mi>n</mi></msup><mo>:</mo><mi>n</mi><mo>∈</mo><mi mathvariant="double-struck">ℕ</mi><mo stretchy="false" form="postfix">}</mo></mrow><annotation encoding="application/x-tex">&lt;g&gt; = \{g^n:n\in\mathbb{N}\}</annotation></semantics></math>,
any
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>,</mo><msub><mi>g</mi><mn>2</mn></msub><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">g_1,g_2 \in &lt;g&gt;</annotation></semantics></math>
take the form
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>=</mo><msup><mi>g</mi><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">g_1 = g^n</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>2</mn></msub><mo>=</mo><msup><mi>g</mi><mi>m</mi></msup></mrow><annotation encoding="application/x-tex">g_2 = g^m</annotation></semantics></math>.
Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mn>1</mn></msub><mo>⋅</mo><msub><mi>g</mi><mn>2</mn></msub><mo>=</mo><msup><mi>g</mi><mrow><mi>n</mi><mo>+</mo><mi>m</mi></mrow></msup><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">g_1\cdot g_2 = g^{n+m} \in &lt;g&gt;</annotation></semantics></math>
by definition of a generator, so
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">&lt;g&gt;</annotation></semantics></math>
is closed under
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>⋅</mi><annotation encoding="application/x-tex">\cdot</annotation></semantics></math></p></li>
<li><p><strong>Identity element.</strong> In order for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">&lt;g&gt;</annotation></semantics></math>
to be a subgroup of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>e</mi><mi>G</mi></msub><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">e_G \in &lt;g&gt;</annotation></semantics></math>.
Recall that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>e</mi><mi>G</mi></msub><annotation encoding="application/x-tex">e_G</annotation></semantics></math>
is the empty move. We know that repeating the same move over and over
will eventually result in original state of the cube <span
class="citation" data-cites="Garron"></span>. This means
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∃</mo><mi>k</mi></mrow><annotation encoding="application/x-tex">\exists k</annotation></semantics></math>
such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>g</mi><mi>k</mi></msup><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">g^k = e_G</annotation></semantics></math>
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">\forall g\in G</annotation></semantics></math>.
Since
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>g</mi><mi>k</mi></msup><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">g^k \in &lt;g&gt;</annotation></semantics></math>,
it follows that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>e</mi><mi>G</mi></msub><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>,</mo><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">e_G\in &lt;g&gt;, \forall g\in G</annotation></semantics></math>.</p></li>
<li><p><strong>Inverses.</strong> Recall that for an element
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">x \in &lt;g&gt;</annotation></semantics></math>
the inverse is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>x</mi><mo>′</mo></msup><mo>∈</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">x&#39;\in &lt;g&gt;</annotation></semantics></math>,
such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><msup><mi>x</mi><mo>′</mo></msup><mo>=</mo><msup><mi>x</mi><mo>′</mo></msup><mi>x</mi><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">xx&#39; = x&#39;x = e_G</annotation></semantics></math>.
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>x</mi><mo>′</mo></msup><mo>=</mo><msup><mi>g</mi><mrow><mi>k</mi><mo>−</mo><mn>1</mn></mrow></msup></mrow><annotation encoding="application/x-tex">x&#39; = g^{k-1}</annotation></semantics></math>,
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>k</mi><annotation encoding="application/x-tex">k</annotation></semantics></math>
is such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>g</mi><mi>k</mi></msup><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">g^k = e_G</annotation></semantics></math>
from the proof of the Identity Element. Then,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>x</mi><msup><mi>x</mi><mo>′</mo></msup><mo>=</mo><msup><mi>x</mi><mo>′</mo></msup><mi>x</mi><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">xx&#39; = x&#39;x = e_G</annotation></semantics></math>
becomes
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>⋅</mo><msup><mi>g</mi><mrow><mi>k</mi><mo>−</mo><mn>1</mn></mrow></msup><mo>=</mo><msup><mi>g</mi><mrow><mi>k</mi><mo>−</mo><mn>1</mn></mrow></msup><mo>⋅</mo><mi>g</mi><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">g\cdot g^{k-1} = g^{k-1}\cdot g = e_G</annotation></semantics></math>
which holds
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">\forall g\in G</annotation></semantics></math>.
Therefore, the inverses of all elements exist in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo></mrow><annotation encoding="application/x-tex">&lt;g&gt;</annotation></semantics></math>.</p></li>
<li><p><strong>Associativity.</strong> Associativity is inherited from
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>.</p></li>
</ul>
<p>Therefore, we have proven that for any legal move
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">&lt;g&gt; \leq G</annotation></semantics></math>.
Unlike
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>,
this subgroup is clearly abelian, since only one move is involved. This
also means that the generators we discussed in Section 2.4 Generators
are also subgroups of
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>G</mi><annotation encoding="application/x-tex">G</annotation></semantics></math>.</p>
<h2 id="normal-subgroups.">Normal Subgroups.</h2>
<p>According to the Rubik’s Cube Group Wikipedia page <span
class="citation" data-cites="wiki"></span>, the group
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>C</mi><mi>o</mi></msub><annotation encoding="application/x-tex">C_o</annotation></semantics></math>,
or the subset of moves that leaves every cubelet fixed, but change their
orientations is a normal subgroup. They omit the proof of this, so we
will verify it here. First, let’s make sure
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>C</mi><mi>o</mi></msub><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">C_o \leq G</annotation></semantics></math>
by making sure it fulfills the subgroup criteria:</p>
<ol>
<li><p><strong>Subset.</strong> Clearly,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>C</mi><mi>o</mi></msub><mo>⊂</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">C_o \subset G</annotation></semantics></math>,
by definition since these are legal moves that also have the special
property of leaving the cubelets fixed, but rotating the
facelets.</p></li>
<li><p><strong>Identity element.</strong> Recall
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>e</mi><mi>G</mi></msub><annotation encoding="application/x-tex">e_G</annotation></semantics></math>
is the empty move. Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>e</mi><mi>G</mi></msub><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">e_G \in C_o</annotation></semantics></math>
since the cubelets are left fixed by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>e</mi><mi>G</mi></msub><annotation encoding="application/x-tex">e_G</annotation></semantics></math>.</p></li>
<li><p><strong>Closure.</strong> Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>A</mi><mo>,</mo><mi>B</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">A,B \in C_o</annotation></semantics></math>,
then
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>A</mi><mo>⋅</mo><mi>B</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">A\cdot B \in C_o</annotation></semantics></math>
because neither
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>A</mi><annotation encoding="application/x-tex">A</annotation></semantics></math>
nor
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>B</mi><annotation encoding="application/x-tex">B</annotation></semantics></math>
move any cubelets, and therefore their composition
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>A</mi><mi>B</mi></mrow><annotation encoding="application/x-tex">AB</annotation></semantics></math>
also will not move any cubelets.</p></li>
<li><p><strong>Inverses.</strong> Recall that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">\forall c \in C_o</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>c</mi><mo>′</mo></msup><annotation encoding="application/x-tex">c&#39;</annotation></semantics></math>
is the move that undoes
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>c</mi><annotation encoding="application/x-tex">c</annotation></semantics></math>,
such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><msup><mi>c</mi><mo>′</mo></msup><mo>=</mo><msup><mi>c</mi><mo>′</mo></msup><mi>c</mi><mo>=</mo><mi>e</mi></mrow><annotation encoding="application/x-tex">cc&#39; = c&#39;c = e</annotation></semantics></math>.
If we have configuration
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
then applying
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>c</mi><annotation encoding="application/x-tex">c</annotation></semantics></math>
will not move any cubelets. Reversing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>c</mi><annotation encoding="application/x-tex">c</annotation></semantics></math>,
(applying
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>c</mi><mo>′</mo></msup><annotation encoding="application/x-tex">c&#39;</annotation></semantics></math>)
will only reorient the facelets, not permute any cubelets. Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub><mo>,</mo><mo>∃</mo><msup><mi>c</mi><mo>′</mo></msup><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">\forall c\in C_o, \exists c&#39; \in C_o</annotation></semantics></math>
such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><msup><mi>c</mi><mo>′</mo></msup><mo>=</mo><msup><mi>c</mi><mo>′</mo></msup><mi>c</mi><mo>=</mo><mi>e</mi></mrow><annotation encoding="application/x-tex">cc&#39;=c&#39;c = e</annotation></semantics></math>,
as desired.</p></li>
</ol>
<p>Because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msub><mi>C</mi><mi>o</mi></msub><annotation encoding="application/x-tex">C_o</annotation></semantics></math>
meets these criteria, we can confirm
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>C</mi><mi>o</mi></msub><mo>&lt;</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">C_o &lt; G</annotation></semantics></math>.
Now, we know that a normal subgroup <span class="citation"
data-cites="textbook"></span> is such that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub><mo>,</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">\forall c \in C_o, g\in G</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><msub><mi>C</mi><mi>o</mi></msub><msup><mi>g</mi><mo>′</mo></msup><mo>=</mo><mo stretchy="false" form="prefix">{</mo><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub><mo stretchy="false" form="postfix">}</mo><mo>=</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">gC_og&#39; =\{gcg&#39; |c\in C_o\} = C_o</annotation></semantics></math></p>
<p>From above we know that in order for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>C</mi><mi>o</mi></msub><mo>⊲</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">C_o \triangleleft G</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub><mo>,</mo><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub><mo>,</mo><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">gcg&#39; \in C_o, \forall c\in C_o, \forall g\in G</annotation></semantics></math>.
This implies that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">gcg&#39;</annotation></semantics></math>
cannot permute cubelets, but can alter the orientation of the cubelets.
Since, we do not care about how the cubelets are oriented, it will be
useful to write
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">c\in C_o</annotation></semantics></math>
as cubelet-level permutations, so we can assess whether
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">gcg&#39;\in C_o</annotation></semantics></math>.
Let
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>θ</mi><mo>∈</mo><msub><mi>S</mi><mn>24</mn></msub></mrow><annotation encoding="application/x-tex">\theta\in S_{24}</annotation></semantics></math>
(for the 3x3 Rubik’s Cube, or
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>θ</mi><mo>∈</mo><msub><mi>S</mi><mn>8</mn></msub></mrow><annotation encoding="application/x-tex">\theta\in S_8</annotation></semantics></math>
for the Pocket Cube) be the cubelet-level bijective map for all
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">c \in C_o</annotation></semantics></math>.
These will take the form
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>↦</mo><msub><mi>g</mi><mi>C</mi></msub><mo>=</mo><mrow><mo stretchy="true" form="prefix">[</mo><mtable><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><mn>2</mn></mtd><mtd columnalign="center" style="text-align: center"><mi>.</mi><mi>.</mi><mi>.</mi></mtd><mtd columnalign="center" style="text-align: center"><mn>24</mn></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mtd><mtd columnalign="center" style="text-align: center"><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mtd><mtd columnalign="center" style="text-align: center"><mi>.</mi><mi>.</mi><mi>.</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mn>24</mn><mo stretchy="false" form="postfix">)</mo></mtd></mtr></mtable><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">g \mapsto g_C = \begin{bmatrix}
    1&amp;2&amp;...&amp;24\\ \theta(1)&amp;\theta(2)&amp;...&amp;\theta(24)
\end{bmatrix}</annotation></semantics></math> where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\theta(i)</annotation></semantics></math>
is the new cubicle occupied by the cubelet leaving cubicle i. Without
loss of generality for the ordering of items:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>g</mi><mo>′</mo></msup><mo>↦</mo><msubsup><mi>g</mi><mi>C</mi><mo>′</mo></msubsup><mo>=</mo><mrow><mo stretchy="true" form="prefix">[</mo><mtable><mtr><mtd columnalign="center" style="text-align: center"><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mtd><mtd columnalign="center" style="text-align: center"><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo></mtd><mtd columnalign="center" style="text-align: center"><mi>.</mi><mi>.</mi><mi>.</mi></mtd><mtd columnalign="center" style="text-align: center"><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mn>24</mn><mo stretchy="false" form="postfix">)</mo></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><mn>2</mn></mtd><mtd columnalign="center" style="text-align: center"><mi>.</mi><mi>.</mi><mi>.</mi></mtd><mtd columnalign="center" style="text-align: center"><mn>24</mn></mtd></mtr></mtable><mo stretchy="true" form="postfix">]</mo></mrow></mrow><annotation encoding="application/x-tex">g&#39;\mapsto g_C&#39;=\begin{bmatrix}
    \theta(1)&amp;\theta(2)&amp;...&amp;\theta(24) \\1&amp;2&amp;...&amp;24
\end{bmatrix}</annotation></semantics></math> and at the cubelet-level,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>g</mi><mi>C</mi></msub><msubsup><mi>g</mi><mi>C</mi><mo>′</mo></msubsup><mo>=</mo><msubsup><mi>g</mi><mi>C</mi><mo>′</mo></msubsup><msub><mi>g</mi><mi>C</mi></msub><mo>=</mo><msub><mi>e</mi><mi>C</mi></msub></mrow><annotation encoding="application/x-tex">g_Cg_C&#39; = g_C&#39;g_C  =e_C</annotation></semantics></math>.<br />
<br />
Notice
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mn>0</mn></msub></mrow><annotation encoding="application/x-tex">\forall c\in C_0</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mo>↦</mo><msub><mi>c</mi><mi>C</mi></msub><mo>=</mo><mrow><mo stretchy="true" form="prefix">[</mo><mtable><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><mn>2</mn></mtd><mtd columnalign="center" style="text-align: center"><mi>.</mi><mi>.</mi><mi>.</mi></mtd><mtd columnalign="center" style="text-align: center"><mn>24</mn></mtd></mtr><mtr><mtd columnalign="center" style="text-align: center"><mn>1</mn></mtd><mtd columnalign="center" style="text-align: center"><mn>2</mn></mtd><mtd columnalign="center" style="text-align: center"><mi>.</mi><mi>.</mi><mi>.</mi></mtd><mtd columnalign="center" style="text-align: center"><mn>24</mn></mtd></mtr></mtable><mo stretchy="true" form="postfix">]</mo></mrow><mo>=</mo><msub><mi>e</mi><mi>C</mi></msub></mrow><annotation encoding="application/x-tex">c\mapsto c_C=\begin{bmatrix}
    1&amp;2&amp;...&amp;24\\1&amp;2&amp;...&amp;24
\end{bmatrix} = e_C</annotation></semantics></math> since
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">\forall c\in C_o</annotation></semantics></math>
they do not permute cubelets, only orientations within cubicles. So,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">\forall c\in C_o</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mo>=</mo><mi>e</mi></mrow><annotation encoding="application/x-tex">c = e</annotation></semantics></math>
or the identity at the cubelet level. Now, it is easy to see at the
cubelet level
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">\forall c\in C_o</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup><mo>↦</mo><msub><mi>g</mi><mi>C</mi></msub><msub><mi>c</mi><mi>C</mi></msub><msubsup><mi>g</mi><mi>C</mi><mo>′</mo></msubsup><mo>=</mo><msub><mi>g</mi><mi>C</mi></msub><msub><mi>e</mi><mi>C</mi></msub><msubsup><mi>g</mi><mi>C</mi><mo>′</mo></msubsup><mo>=</mo><msub><mi>g</mi><mi>C</mi></msub><msubsup><mi>g</mi><mi>C</mi><mo>′</mo></msubsup><mo>=</mo><msub><mi>e</mi><mi>C</mi></msub></mrow><annotation encoding="application/x-tex">gcg&#39; \mapsto g_Cc_Cg_C&#39; = g_Ce_Cg_C&#39; = g_Cg_C&#39; = e_C</annotation></semantics></math>
This means that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">gcg&#39;</annotation></semantics></math>
does not permute any cubelets
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>c</mi><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">\forall c\in C_o</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>∀</mo><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">\forall g\in G</annotation></semantics></math>.
Therefore,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mi>c</mi><msup><mi>g</mi><mo>′</mo></msup><mo>∈</mo><msub><mi>C</mi><mi>o</mi></msub></mrow><annotation encoding="application/x-tex">gcg&#39; \in C_o</annotation></semantics></math>,
implying
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>C</mi><mi>o</mi></msub><mo>⊲</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">C_o \triangleleft G</annotation></semantics></math>,
as desired.</p>
<h1 id="the-fundamental-theorem-of-cube-theory.">The Fundamental Theorem
of Cube Theory.</h1>
<h2 id="cube-orientation.">Cube Orientation.</h2>
<figure id="fig:cube1" data-latex-placement="h">
<img src="./cube_orientation1.png" style="width:75.0%" />
<figcaption>Visualizing the 8 corner positions and 12 edge positions on
the 3x3 Rubik’s Cube <span class="citation"
data-cites="sfunotation"></span>.</figcaption>
</figure>
<figure id="fig:cube2" data-latex-placement="h">
<img src="./cube_orientation2.png" style="width:75.0%" />
<figcaption>Visualizing the orientation for the corner and edge facelets
<span class="citation" data-cites="sfunotation"></span>.</figcaption>
</figure>
<p>Borrowing the orientation graphics for Mulholand’s webpage (see
Figure <a href="#cube1" data-reference-type="ref"
data-reference="cube1">[cube1]</a> and <a href="#cube2"
data-reference-type="ref" data-reference="cube2">[cube2]</a>), we can
see how we are labeling each cube. The corner cubicles are labeled 1
through 8. Relative to the user, the cubilcles are not mutable, only the
cubelet occupying that cubicle. For example, cubicle 3 will always be
the top-right cubicle to the user, but any of the 8 corner cubes may be
filling that position (see Figure <a href="#fig:cube1"
data-reference-type="ref" data-reference="fig:cube1">2</a>).The smae is
done for the 12 edge cubicles.<br />
<br />
We also need to keep track of how each corner and edge piece are
oriented within their current cubicles. To facilitate this, we will need
two things:</p>
<ol>
<li><p>Label each facelet of each corner cube as follows: (a) in the
solved position, the facelets Upper and Downward faces are labeled as
the 0 face, and (2) following each cube clockwise, label the other
facelets 1 and 2, respectively.</p></li>
</ol>
<p>So, when we discuss the orientation of the cube, each of the 3
possible orientations of cubelet are described by which facelet is
facing the Upper or Downward face. For example, after move
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>F</mi><mo>′</mo></msup><annotation encoding="application/x-tex">F&#39;</annotation></semantics></math>,
the yellow-green-red corner cube is now in cubicle 3, with orientation 2
(see Figure <a href="#fig:moveB" data-reference-type="ref"
data-reference="fig:moveB">4</a>).</p>
<figure id="fig:moveB">
<div class="minipage">
<p><img src="./pocket_orientation.JPG" style="width:50.0%"
alt="image" /> <span id="fig:2x2cube"
data-label="fig:2x2cube"></span></p>
</div>
<div class="minipage">
<p><img src="./moveB_ex.JPG" style="width:50.0%" alt="image" /> <span
id="fig:moveB" data-label="fig:moveB"></span></p>
</div>
</figure>
<h2 id="ftct-3x3-rubiks-cube.">FTCT: 3x3 Rubik’s Cube.</h2>
<p>We can represent the state of our 3x3 Rubik’s Cube using a 4-tuple,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo>,</mo><mi>θ</mi><mo>,</mo><mi>v</mi><mo>,</mo><mi>w</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\rho, \theta, v, w)</annotation></semantics></math>,
where:</p>
<ul>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>ρ</mi><mo>∈</mo><msub><mi>S</mi><mn>8</mn></msub></mrow><annotation encoding="application/x-tex">\rho\in S_8</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>ρ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>j</mi></mrow><annotation encoding="application/x-tex">\rho(i) = j</annotation></semantics></math>
represents corner
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>i</mi><annotation encoding="application/x-tex">i</annotation></semantics></math>
in position
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>j</mi><annotation encoding="application/x-tex">j</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>θ</mi><mo>∈</mo><msub><mi>S</mi><mn>12</mn></msub></mrow><annotation encoding="application/x-tex">\theta \in S_{12}</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>θ</mi><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>j</mi></mrow><annotation encoding="application/x-tex">\theta(i) = j</annotation></semantics></math>
represents edge i in position j</p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>v</mi><mo>∈</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup></mrow><annotation encoding="application/x-tex">v\in \mathbb{Z}^8_3</annotation></semantics></math>,
represents the orientation of corners</p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>w</mi><mo>∈</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup></mrow><annotation encoding="application/x-tex">w \in \mathbb{Z}_2^{12}</annotation></semantics></math>,
represents the orientation of the edge pieces.</p></li>
</ul>
<p>The 4-tuple
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo>,</mo><mi>θ</mi><mo>,</mo><mi>v</mi><mo>,</mo><mi>w</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(\rho, \theta, v, w)</annotation></semantics></math>
corresponds to a <strong>legal</strong> configuration of our Rubik’s
Cube if and only if The Fundamental Theorem of Cube Theory (FTCT) for
the 3x3 Rubik’s Cube is satisfied<span class="citation"
data-cites="Bobzien"></span><span class="citation"
data-cites="sfucubology"></span>. The FTCT has three criteria:</p>
<ul>
<li><p>Equal parity of permutations:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>θ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">sgn(\rho) = sgn(\theta)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>8</mn></msub><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_8 \equiv  0</annotation></semantics></math>
(mod 3)</p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>w</mi><mn>1</mn></msub><mo>+</mo><msub><mi>w</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>w</mi><mn>12</mn></msub><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">w_1+w_2+...+w_12 \equiv 0</annotation></semantics></math>
(mod 2)</p></li>
</ul>
<p>In the FTCT, (1) says that there must be equal parity between the
permutations of the corners and edges (equal twists in orientation), (2)
is the conservation of corner twists: for every corner that flips
clockwise, another flips counter-clockwise, and (3) is the conservation
of the edge twists <span class="citation"
data-cites="sweeney2022"></span>.<br />
<br />
To expand on the group theory we can represent the group of <strong>All
Rubik’s Cube positions</strong> (legal and illegal) as</p>
<p><math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo>,</mo><mi>θ</mi><mo>,</mo><mi>v</mi><mo>,</mo><mi>w</mi><mo stretchy="false" form="postfix">)</mo><mo>∈</mo><msub><mi>S</mi><mn>8</mn></msub><mo>×</mo><msub><mi>S</mi><mn>12</mn></msub><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup></mrow><annotation encoding="application/x-tex">(\rho, \theta, v, w) \in S_8 \times S_12 \times \mathbb{Z}_3^8 \times\mathbb{Z}_2^{12}</annotation></semantics></math>
which is the direct product between all these groups. Keep in mind the
symmetric groups that the corners and edge pieces constitute will come
in handy in the section on the solving algorithm and understanding how
it works.</p>
<h2 id="ftct-pocket-cube.">FTCT: Pocket Cube.</h2>
<p>For the Pocket Cube, because we have no edge pieces to worry about,
we can represent our state with the 2-tuple,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo>,</mo><mi>v</mi><mo stretchy="false" form="postfix">)</mo><mo>∈</mo><msub><mi>S</mi><mn>8</mn></msub><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup></mrow><annotation encoding="application/x-tex">(\rho,v) \in S_8 \times \mathbb{Z}_3^8</annotation></semantics></math>
and corresponds to a <strong>legal</strong> configuration of our Pocket
Cube if and only if
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>8</mn></msub><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_8 \equiv 0</annotation></semantics></math>
(mod 3). There are no edge pieces and parity of permutations to worry
about for The Pocket Cube.</p>
<h2 id="cardinality.">Cardinality.</h2>
<p>Normally, calculating the order of a group is trivial for small,
finite groups because we can simply count the elements in our group.
But, as we will see, there is not enough time in a lifetime to count to
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mi>G</mi><mo stretchy="false" form="prefix">|</mo></mrow><annotation encoding="application/x-tex">|G|</annotation></semantics></math>
for a 3x3 Rubik’s Cube, so we need to get creative!<br />
<br />
Recall from the FTCT, we can represent the <strong>Illegal Cube
Group</strong> as the direct product of the groups
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>S</mi><mn>8</mn></msub><mo>×</mo><msub><mi>S</mi><mn>12</mn></msub><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup></mrow><annotation encoding="application/x-tex">S_8\times  S_{12}\times \mathbb{Z}_3^8\times\mathbb{Z}_2^{12}</annotation></semantics></math>
From Lauritzen, we know that the order of a product group is given by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>G</mi><mo>×</mo><mi>H</mi><mo>=</mo><mo stretchy="false" form="prefix">|</mo><mi>G</mi><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">|</mo><mi>H</mi><mo stretchy="false" form="prefix">|</mo></mrow><annotation encoding="application/x-tex">G\times H = |G||H|</annotation></semantics></math>.
Therefore,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><msub><mi>S</mi><mn>8</mn></msub><mo>×</mo><msub><mi>S</mi><mn>12</mn></msub><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">|</mo><msub><mi>S</mi><mn>8</mn></msub><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">|</mo><msub><mi>S</mi><mn>12</mn></msub><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">|</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">|</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>8</mn><mi>!</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>12</mn><mi>!</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><msup><mn>3</mn><mn>8</mn></msup><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><msup><mn>2</mn><mn>12</mn></msup><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">|S_8\times  S_{12}\times \mathbb{Z}_3^8\times\mathbb{Z}_2^{12}| = |S_8||S_{12}||\mathbb{Z}_3^8||\mathbb{Z}_2^{12}| = (8!)(12!)(3^8)(2^{12})</annotation></semantics></math>
which is the same as the number of all permutations of the Rubik’s Cube
we found earlier, regardless of legality.</p>
<ul>
<li><p><strong>Group order for the 3x3 Rubik’s Cube.</strong> Using the
FTCT, we can compute
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mi>G</mi><mo stretchy="false" form="prefix">|</mo></mrow><annotation encoding="application/x-tex">|G|</annotation></semantics></math>.
From the product group,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><msup><mn>3</mn><mn>8</mn></msup></mrow><annotation encoding="application/x-tex">|\mathbb{Z}^8_{3}| = 3^8</annotation></semantics></math>,
but the sum of the corner orientations,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>8</mn></msub></mrow><annotation encoding="application/x-tex">v_1+...+v_8</annotation></semantics></math>,
needs to be
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">\equiv 0</annotation></semantics></math>
(mod 3), which only happens for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mfrac><mn>1</mn><mn>3</mn></mfrac><annotation encoding="application/x-tex">\frac{1}{3}</annotation></semantics></math>
of all possible sums. Similarly,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><msup><mn>2</mn><mn>12</mn></msup></mrow><annotation encoding="application/x-tex">|\mathbb{Z}_2^{12}| =2^{12}</annotation></semantics></math>,
but the sum of the edge orientations,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>w</mi><mn>1</mn></msub><mo>+</mo><msub><mi>w</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>w</mi><mn>12</mn></msub><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">w_1+w_2+..+w_{12} \equiv 0</annotation></semantics></math>
(mod 2), which only happens for
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mfrac><mn>1</mn><mn>2</mn></mfrac><annotation encoding="application/x-tex">\frac{1}{2}</annotation></semantics></math>
of the sums. Finally,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>θ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">sgn(\rho) = sgn(\theta)</annotation></semantics></math>,
clearly, this only happens
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mfrac><mn>1</mn><mn>2</mn></mfrac><annotation encoding="application/x-tex">\frac{1}{2}</annotation></semantics></math>
of the time as well. So, only
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mfrac><mn>1</mn><mn>3</mn></mfrac><mo stretchy="false" form="prefix">(</mo><mfrac><mn>1</mn><mn>2</mn></mfrac><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mfrac><mn>1</mn><mn>2</mn></mfrac><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mfrac><mn>1</mn><mn>12</mn></mfrac></mrow><annotation encoding="application/x-tex">\frac{1}{3}(\frac{1}{2})(\frac{1}{2}) = \frac{1}{12}</annotation></semantics></math>
of the total permutations are legal <span class="citation"
data-cites="Bobzien"></span>. Using our result from earlier:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mi>G</mi><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mfrac><mn>1</mn><mn>12</mn></mfrac><mo stretchy="false" form="prefix">|</mo><msub><mi>S</mi><mn>8</mn></msub><mo>×</mo><msub><mi>S</mi><mn>12</mn></msub><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>2</mn><mn>12</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mfrac><mn>1</mn><mn>12</mn></mfrac><mo stretchy="false" form="prefix">(</mo><msup><mn>3</mn><mn>8</mn></msup><mo stretchy="false" form="prefix">(</mo><mn>8</mn><mi>!</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><msup><mn>2</mn><mn>12</mn></msup><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>12</mn><mi>!</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>43</mn><mo>,</mo><mn>252</mn><mo>,</mo><mn>003</mn><mo>,</mo><mn>274</mn><mo>,</mo><mn>489</mn><mo>,</mo><mn>856</mn><mo>,</mo><mn>000</mn><mo>≈</mo><mn>43</mn><mi>x</mi><msup><mn>10</mn><mn>19</mn></msup></mrow><annotation encoding="application/x-tex">|G| = \frac{1}{12}|S_8\times  S_{12}\times \mathbb{Z}_3^8\times\mathbb{Z}_2^{12}|=\frac{1}{12}(3^8(8!)(2^{12})(12!)) = 43,252,003,274,489,856,000 \approx 43x10^{19}</annotation></semantics></math>
Which is a pretty big (but finite) group! For a person counting elements
in this group at a rate of 3 elements per second, it would take them
over 400 billion years to count them all!</p></li>
<li><p><strong>Group order for the Pocket Cube.</strong> Again, we know
we can represent the cube moves of the Pocket Cube as the direct product
of the following groups:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><msub><mi>S</mi><mn>8</mn></msub><mo>×</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">|</mo><msub><mi>S</mi><mn>8</mn></msub><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">|</mo><msubsup><mi mathvariant="double-struck">ℤ</mi><mn>3</mn><mn>8</mn></msubsup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>8</mn><mi>!</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><msup><mn>3</mn><mn>8</mn></msup><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">|S_8\times\mathbb{Z}_3^8|=|S_8||\mathbb{Z}_3^8| = (8!)(3^8)</annotation></semantics></math>
Because the Pocket Cube is essentially only the corners of the 3x3
Rubik’s Cube, only 7 of the corners can be rotated independently and we
divide by 24 to account for the lack of fixed centers
(<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>3</mn><mo stretchy="false" form="prefix">(</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>24</mn></mrow><annotation encoding="application/x-tex">3(8) = 24</annotation></semantics></math>,
where there are 3 orientations and 8 locations for the fixed cube) <span
class="citation" data-cites="jaap"></span>.
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mi>G</mi><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mfrac><mn>1</mn><mn>24</mn></mfrac><mo>⋅</mo><mfrac><mn>1</mn><mn>3</mn></mfrac><mo stretchy="false" form="prefix">(</mo><mn>8</mn><mi>!</mi><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><msup><mn>3</mn><mn>8</mn></msup><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>3</mn><mo>,</mo><mn>674</mn><mo>,</mo><mn>160</mn></mrow><annotation encoding="application/x-tex">|G| = \frac{1}{24}\cdot\frac{1}{3}(8!)(3^8) = 3,674,160</annotation></semantics></math>
possible configurations for the Pocket Cube– quite a few less than the
3x3 Rubik’s Cube, but still way too many to count!</p></li>
<li><p><strong>Element &amp; Subgroup orders.</strong> Because we have
shown previously that for any
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo>≤</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">&lt;g&gt; \leq G</annotation></semantics></math>,
we know that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mi>g</mi><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">|</mo><mo>&lt;</mo><mi>g</mi><mo>&gt;</mo><mo stretchy="false" form="prefix">|</mo></mrow><annotation encoding="application/x-tex">|g| = |&lt;g&gt;|</annotation></semantics></math>.
Furthermore, from Garron, we know that there are 73 possible orders of
subgroups, ranging from 1 to 1260. The trivial subgroup has order 1,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">{</mo><mi>e</mi><mo stretchy="false" form="postfix">}</mo><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">|\{e\}| = 1</annotation></semantics></math>,
and an example of an element with order 1260 is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mi>R</mi><mi>F</mi><mi>F</mi><msup><mi>B</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup><msup><mi>B</mi><mo>′</mo></msup><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mn>1260</mn></mrow><annotation encoding="application/x-tex">|RFFB&#39;U&#39;B&#39;| = 1260</annotation></semantics></math>
<span class="citation" data-cites="Garron"></span>.</p></li>
</ul>
<h1 id="the-2-x-2-rubiks-cube-the-pocket-cube">The 2 x 2 Rubik’s Cube:
The Pocket Cube</h1>
<p>For sake of simplicity, we are going to focus our explorations on the
Pocket Cube as just the 3x3 Rubik’s Cube’s corners. This means we can
apply what we know about permuting the 3x3 Rubik’s Cube’s corners,
without having to worry about permutation any edge cubelets or center
cubelets. So, we will label our cubicles the same way (with respect to
the user) as in Figure <a href="#fig:cube1" data-reference-type="ref"
data-reference="fig:cube1">2</a>. When we talk about some of the group
theory (particularly cycles) behind this algorithm it will also be
helpful to refer to Figure <a href="#fig:cubelayout"
data-reference-type="ref"
data-reference="fig:cubelayout">[fig:cubelayout]</a> for the name of
each facelet, as well as Figure <a href="#fig:2x2cube_ori"
data-reference-type="ref" data-reference="fig:2x2cube_ori">5</a>, which
shows a 3-D Pocket Cube with it’s facelets labeled.</p>
<figure id="fig:2x2cube_ori">
<div class="minipage">
<p><img src="./CUBE LAYOUT2.png" style="width:100.0%" alt="image" />
<span id="fig:cubelayout" data-label="fig:cubelayout"></span></p>
</div>
<div class="minipage">
<p><img src="./pocket_orientation.JPG" style="width:50.0%"
alt="image" /> <span id="fig:2x2cube_ori"
data-label="fig:2x2cube_ori"></span></p>
</div>
</figure>
<h1 id="how-to-solve-the-pocket-cube.">How to Solve the Pocket
Cube.</h1>
<h2 id="the-quickest-method.">The Quickest Method.</h2>
<p>We will walk through the algorithm then discuss the group theory
related to why it works.</p>
<h2 id="algorithm.">Algorithm.</h2>
<p>For the sake of clarity in this algorithm, we are going to assume
that a white facelet is occupying facelet 21. There is mention of
something called <strong>commutators</strong> and
<strong>conjugates</strong> in this algorithm. These are just moves that
take a special form and have useful properties when solving a Rubik’s
Cube. We will discuss how and way these work in a subsequent section!
For now, just bear with it through this algorithm:</p>
<ol>
<li><p>Regardless of orientation, find the cubelet we need to move into
cubicle 7, and perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>U</mi><annotation encoding="application/x-tex">U</annotation></semantics></math>
until it is in cubicle 3.</p></li>
<li><p>Repeat the following commutator until the cubelet in cubicle 3 is
oriented correctly in cubicle 7:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>R</mi><mi>U</mi><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">[R,U] = RUR&#39;U&#39;</annotation></semantics></math></p></li>
<li><p>Once complete, perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>D</mi><mo>′</mo></msup><annotation encoding="application/x-tex">D&#39;</annotation></semantics></math>.</p></li>
<li><p>Repeat steps 2-3 until the bottom layer (white side) is
completely solved.</p></li>
<li><p>On the top layer of cubelets, see if they are in the correct
cubicle, regardless of orientation. There will either be 1, 2, or 4
cubes in the correct cubicles. If there are 4, skip to step (8). If
there are 1 or 2, perform the following commutator, performing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>U</mi><msup><mi>D</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">UD&#39;</annotation></semantics></math>
to get a correctly positioned cubelet into cubicle 4 (i.e., front left):
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>R</mi><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup><mi>L</mi><mi>U</mi></mrow><annotation encoding="application/x-tex">[R,U&#39;L&#39;U] = RU&#39;L&#39;UR&#39;U&#39;LU</annotation></semantics></math></p></li>
<li><p>Check again, performing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>U</mi><annotation encoding="application/x-tex">U</annotation></semantics></math>
if necessary to get 1 cubelet in the correct position.</p></li>
<li><p>Repeat steps 5-6 until all 4 cubelets are in the correct
cubicles, regardless of orientation.</p></li>
<li><p>Flip the entire Pocket Cube the solved Down (white) face to the
Up face. This is equivalent to performing:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mi>R</mi><mi>L</mi><mi>L</mi></mrow><annotation encoding="application/x-tex">RRLL</annotation></semantics></math></p></li>
<li><p>Since white is on our Up face, yellow will be our bottom face.
Perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>D</mi><mo>′</mo></msup><annotation encoding="application/x-tex">D&#39;</annotation></semantics></math>
to get an incorrectly orientated cubelet into cubicle 7. Then perform
the commutator from (2) until it is correctly orientated:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>R</mi><mi>U</mi><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">[R,U] = RUR&#39;U&#39;</annotation></semantics></math></p></li>
<li><p>Perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>D</mi><mo>′</mo></msup><annotation encoding="application/x-tex">D&#39;</annotation></semantics></math>
to move the newly solved cubelet into cubicle 8.</p></li>
<li><p>Repeat steps 9-10 until the Down (yellow) face is completely
solved.</p></li>
<li><p>Perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>U</mi><annotation encoding="application/x-tex">U</annotation></semantics></math>
as needed to align the colors on the Front, Back, Left and Right
Face.</p></li>
<li><p>Your Pocket Cube is now solved! <span class="citation"
data-cites="youtube"></span> <span class="citation"
data-cites="youtube_solve"></span></p></li>
</ol>
<h2 id="why-it-works">Why it works!</h2>
<h3 id="commutators.">Commutators.</h3>
<p>Commutators are moves in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>G</mi><mo>,</mo><mi>⋅</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(G,\cdot)</annotation></semantics></math>
that take the form <span class="citation"
data-cites="sweeney2022"></span>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>A</mi><mo>,</mo><mi>B</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>A</mi><mi>B</mi><msup><mi>A</mi><mo>′</mo></msup><msup><mi>B</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">[A,B] = ABA&#39;B&#39;</annotation></semantics></math>
As an example, let’s examine the first commutator from the 2x2
Algorithm:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>R</mi><mi>U</mi><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">[R,U]=RUR&#39;U&#39;</annotation></semantics></math>
There are only 2 faces that are being permuted by
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>R</mi><annotation encoding="application/x-tex">R</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>U</mi><annotation encoding="application/x-tex">U</annotation></semantics></math>.
We move both, and then undo both. These faces have one cubicle in
common: cubicle 3 (see Figure <a href="#fig:randu"
data-reference-type="ref" data-reference="fig:randu">6</a>). But, then
performing
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">R&#39;U&#39;</annotation></semantics></math>,
also permutes cubicles 1 and 2.If we perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>
again, cubicle 7 permutes with cubicle 3. So, we can see that if we
repeatedly perform the commutator
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>,
cubicles 1 and 2 and 3 and 7 cycle and rotate, while the rest of the
cube remains unchanged <span class="citation"
data-cites="sweeney2022"></span>.</p>
<figure id="fig:randu" data-latex-placement="h">
<img src="./randu.png" style="width:100.0%" />
<figcaption>Cubes permuted by both
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>.</figcaption>
</figure>
<p>In short, the first half of the commutator
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>A</mi><mo>,</mo><mi>B</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>A</mi><mi>B</mi><msup><mi>A</mi><mo>′</mo></msup><msup><mi>B</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">[A,B] = ABA&#39;B&#39;</annotation></semantics></math>–
that is
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>A</mi><mi>B</mi></mrow><annotation encoding="application/x-tex">AB</annotation></semantics></math>
– will overlap on some subset of the cublets,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>K</mi><annotation encoding="application/x-tex">K</annotation></semantics></math>.
Then, when we undo the moves in the second half –
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>A</mi><mo>′</mo></msup><msup><mi>B</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">A&#39;B&#39;</annotation></semantics></math>
– we change all the cublets back to their original cubicle – except for
those in
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>K</mi><annotation encoding="application/x-tex">K</annotation></semantics></math>.
So, we can effectively work with only a subset of the cublets, without
effecting the rest of the cube.</p>
<h3 id="conjugates.">Conjugates.</h3>
<p>Conjugates in the Rubik’s Cube world are exactly the same as in group
theory. The are moves that take the form:
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>A</mi><mi>B</mi><msup><mi>A</mi><mo>′</mo></msup></mrow><annotation encoding="application/x-tex">ABA&#39;</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>A</mi><annotation encoding="application/x-tex">A</annotation></semantics></math>
is a set up move, and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><msup><mi>A</mi><mo>′</mo></msup><annotation encoding="application/x-tex">A&#39;</annotation></semantics></math>
the reverse of that set up move. These are useful for using the same
commutator to affect a different area of the cube, by letting
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mo>=</mo><mo stretchy="false" form="prefix">[</mo><mi>X</mi><mo>,</mo><mi>Y</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">B = [X,Y]</annotation></semantics></math>
where
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>X</mi><mo>,</mo><mi>Y</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[X,Y]</annotation></semantics></math>
is some commutator <span class="citation"
data-cites="sweeney2022"></span>.</p>
<h3 id="symmetric-groups-k-cycles.">Symmetric Groups &amp;
K-Cycles.</h3>
<p>As touched on in the section on Normal Subgroups, the moves
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>g</mi><mo>∈</mo><mi>G</mi></mrow><annotation encoding="application/x-tex">g\in G</annotation></semantics></math>
can be represented by bijective maps in the form of permutations.<br />
<br />
We can write this in more detail using symmetric groups and cycles. The
6 Basic Moves can be represented with the following cycles, using the
facelet notation <span class="citation"
data-cites="textbook"></span><span class="citation"
data-cites="sfunotation"></span>:</p>
<ul>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>13</mn><mo>,</mo><mn>14</mn><mo>,</mo><mn>16</mn><mo>,</mo><mn>15</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>10</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>19</mn><mo>,</mo><mn>22</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>12</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>24</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">R = (13,14,16,15)(10,2,19,22)(12,4,17,24)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>L</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>5</mn><mo>,</mo><mn>6</mn><mo>,</mo><mn>8</mn><mo>,</mo><mn>7</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>11</mn><mo>,</mo><mn>23</mn><mo>,</mo><mn>18</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>9</mn><mo>,</mo><mn>21</mn><mo>,</mo><mn>20</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">L = (5,6,8,7)(3,11,23,18)(1,9,21,20)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>U</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>9</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>13</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>10</mn><mo>,</mo><mn>6</mn><mo>,</mo><mn>18</mn><mo>,</mo><mn>14</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">U = (1,2,4,3)(9,5,17,13)(10,6,18,14)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>D</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>21</mn><mo>,</mo><mn>22</mn><mo>,</mo><mn>24</mn><mo>,</mo><mn>23</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>11</mn><mo>,</mo><mn>15</mn><mo>,</mo><mn>19</mn><mo>,</mo><mn>7</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>12</mn><mo>,</mo><mn>16</mn><mo>,</mo><mn>20</mn><mo>,</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">D = (21,22,24,23)(11,15,19,7)(12,16,20,8)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>F</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>9</mn><mo>,</mo><mn>10</mn><mo>,</mo><mn>12</mn><mo>,</mo><mn>11</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>22</mn><mo>,</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>15</mn><mo>,</mo><mn>21</mn><mo>,</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">F = (9,10,12,11)(3,13,22,8)(4,15,21,6)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>17</mn><mo>,</mo><mn>18</mn><mo>,</mo><mn>20</mn><mo>,</mo><mn>19</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>7</mn><mo>,</mo><mn>24</mn><mo>,</mo><mn>14</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>23</mn><mo>,</mo><mn>16</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">B = (17,18,20,19)(1,7,24,14)(2,5,23,16)</annotation></semantics></math></p></li>
</ul>
<p>or cubelet-level notation</p>
<ul>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>R</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>6</mn><mo>,</mo><mn>7</mn><mo>,</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">R = (2,6,7,3)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>L</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>8</mn><mo>,</mo><mn>5</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">L = (1,4,8,5)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>U</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mn>4</mn><mo>,</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">U = (1,2,4,3)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>D</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>5</mn><mo>,</mo><mn>6</mn><mo>,</mo><mn>7</mn><mo>,</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">D = (5,6,7,8)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>F</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>7</mn><mo>,</mo><mn>8</mn><mo>,</mo><mn>4</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">F = (3,7,8,4)</annotation></semantics></math></p></li>
<li><p><math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>1</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">B = (2,1,5,6)</annotation></semantics></math></p></li>
</ul>
<p>Using these cycles, we can use the Python SymPy library <span
class="citation" data-cites="sympy"></span> (Appendix A &amp; B) to
calculate the cycles in terms of facelets or just cubelets:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>R</mi><mi>U</mi><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>14</mn><mo>,</mo><mn>18</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>15</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>22</mn><mo>,</mo><mn>10</mn><mo>,</mo><mn>12</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(1) [R,U] = RUR&#39;U&#39; = (1, 14, 18, 17, 5, 2)(4, 15, 13, 22, 10, 12)</annotation></semantics></math>
or
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mi>R</mi><mi>U</mi><msup><mi>R</mi><mo>′</mo></msup><msup><mi>U</mi><mo>′</mo></msup><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>7</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>4</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>5</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>5</mn><mo>,</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>6</mn><mo>,</mo><mn>7</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>5</mn><mo>,</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>5</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>4</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(2)[R,U] = RUR&#39;U&#39; = (1,2)(3,7) = (1,2)(3,4)(4,5)(5,6)(6,7)(5,6)(4,5)(3,4)</annotation></semantics></math></p>
<p>So, we can see from (2) using this commutator cubicles 1 and 2
continually switch cubelets, and so do cubicles 3 and 7 (2-cycles). We
can also see from (1) how the facelets swap as the cubicles switch
location and rotate in 6-cycles, and also that all the facelet positions
in the first cycle of (1) are on cubicles 1 and 2 while all the facelet
positions in the second cycle are on cubicles 3 and 7. It is also
important to notice that cubicles 4,5,6, and 8 and their respective
facelets are completely unaffected by this cycle– which is of course
useful when trying to solve one layer of the Pocket Cube at a
time.<br />
<br />
The facelet notation is also useful to the user when trying to figure
out how many times to perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>
to correctly position their needed facelet. For example, if the user is
trying to correctly position the facelet in facelet 15, they need to
perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><msup><mo stretchy="false" form="postfix">]</mo><mn>2</mn></msup></mrow><annotation encoding="application/x-tex">[R,U]^2</annotation></semantics></math>.
If the facelet is in facelet 12, they need to perform
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><msup><mo stretchy="false" form="postfix">]</mo><mn>4</mn></msup></mrow><annotation encoding="application/x-tex">[R,U]^4</annotation></semantics></math>.<br />
<br />
From Lauritzen, we also know that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>σ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">n(\sigma)</annotation></semantics></math>
is the number of simple transpositions of which
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>σ</mi><annotation encoding="application/x-tex">\sigma</annotation></semantics></math>
is a product, where the simple transposition is of the form
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> </mtext><mspace width="0.333em"></mspace></mrow><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">s = (i\text{   }i+1)</annotation></semantics></math>.
So, from (2)
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>8</mn></mrow><annotation encoding="application/x-tex">n([R,U]) = 8</annotation></semantics></math>
and
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mn>1</mn><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo></mrow></msup><mo>=</mo><mi>+</mi><mn>1</mn></mrow><annotation encoding="application/x-tex">sgn([R,U]) = (-1)^{n([R,U])} = +1</annotation></semantics></math>
Therefore
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>
is an even permutation. Because
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>
is a legal move. And, by Lauritzen we know
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>14</mn><mo>,</mo><mn>18</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>15</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>22</mn><mo>,</mo><mn>10</mn><mo>,</mo><mn>12</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mi>l</mi><mi>c</mi><mi>m</mi><mo stretchy="false" form="prefix">(</mo><mn>6</mn><mo>,</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>6</mn></mrow><annotation encoding="application/x-tex">|[R,U]| =|(1, 14, 18, 17, 5, 2)(4, 15, 13, 22, 10, 12)| =lcm(6,6) = 6</annotation></semantics></math>
Meaning this commutator takes 6 repetitions (i.e.,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><msup><mo stretchy="false" form="postfix">]</mo><mn>6</mn></msup><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">[R,U]^6 = e_G</annotation></semantics></math>)
to get back the the start configuration.<br />
<br />
We can do the same thing for our other commutator
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R, U&#39;L&#39;U ]</annotation></semantics></math>:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>7</mn><mo>,</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(3) [R,U&#39;L&#39;U] = (2,3)(7,8)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>14</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>10</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>18</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(4) [R, U&#39;L&#39;U] = (1,13,14)(2,5,10)(4,17,18)</annotation></semantics></math>
Again, in terms of cubelets, it is the product of two 2-cycles. When
looking at the facelets we have the product of three 3-cycles. So,
cubicles 2 and 3, and 7 and 8 are continually swapping cubelets and
reorienting the cubelet within the cubicle each cycle. Also,
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mo stretchy="false" form="prefix">|</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo>,</mo><mn>13</mn><mo>,</mo><mn>14</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>5</mn><mo>,</mo><mn>10</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo>,</mo><mn>17</mn><mo>,</mo><mn>18</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">|</mo><mo>=</mo><mi>l</mi><mi>c</mi><mi>m</mi><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo>,</mo><mn>3</mn><mo>,</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">|[R,U&#39;L&#39;U]| = |(1,13,14)(2,5,10)(4,17,18)|=lcm(3,3,3) = 3</annotation></semantics></math>
SO it only takes 3 repetitions to get back to the start configuration
(i.e.,
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><msup><mo stretchy="false" form="postfix">]</mo><mn>3</mn></msup><mo>=</mo><msub><mi>e</mi><mi>G</mi></msub></mrow><annotation encoding="application/x-tex">[R, U&#39;L&#39;U]^3 = e_G</annotation></semantics></math>).
Since
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo>,</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>7</mn><mo>,</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">(2,3)(7,8)</annotation></semantics></math>
are already simple transpositions
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n([R,U&#39;L&#39;U]) = 2</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mn>1</mn><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><msup><mi>U</mi><mo>′</mo></msup><msup><mi>L</mi><mo>′</mo></msup><mi>U</mi><mo stretchy="false" form="postfix">]</mo><mo stretchy="false" form="postfix">)</mo></mrow></msup><mo>=</mo><mi>+</mi><mn>1</mn></mrow><annotation encoding="application/x-tex">sgn([R,U&#39;L&#39;U]) = (-1)^{n([R,U&#39;L&#39;U])} = +1</annotation></semantics></math>
so it is an even permutation.</p>
<h1 id="how-to-make-an-impossible-rubiks-cube">How to Make an Impossible
Rubik’s Cube</h1>
<p>Finally, we have all the information we need to make our impossible
Rubik’s Cubes. All we need to do is perform an illegal move (obviously
on a physical Rubik’s Cube we cannot do this without removing and
rearranging the cubelets or the stickers on the facelets, but suspend
your disbelief here), and then all solving algorithms will fail. All our
illegal move needs to do is violate any one of the three criteria in the
3x3 Rubik’s Cubes FTCT. Any Move that violates the
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>v</mi><annotation encoding="application/x-tex">v</annotation></semantics></math>
criteria is also an illegal move for the Pocket Cube. So, some illegal
moves we could use to make our impossible Rubik’s Cube is:</p>
<ol>
<li><p>Rotate any 1 corner cube.</p></li>
<li><p>Rotate any 1 edge cube.</p></li>
<li><p>Swap any 2 adjacent cubes.</p></li>
</ol>
<p>To begin, let’s examine and verify that
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">[</mo><mi>R</mi><mo>,</mo><mi>U</mi><mo stretchy="false" form="postfix">]</mo></mrow><annotation encoding="application/x-tex">[R,U]</annotation></semantics></math>
from the solving algorithm is legal move and justify it. Looking at the
Pocket Cube FTCT, the only criteria we need to meet is
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>≡</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_2 \equiv  0 \text{ (mod 3)}</annotation></semantics></math>
From Figures <a href="#fig:ru_up" data-reference-type="ref"
data-reference="fig:ru_up">[fig:ru_up]</a> and <a href="#fig:ru_d"
data-reference-type="ref" data-reference="fig:ru_d">7</a> we can
calculate this quantity.</p>
<figure id="fig:ru_d">
<div class="minipage">
<p><img src="./ru_up.JPG" style="width:50.0%" alt="image" /> <span
id="fig:ru_up" data-label="fig:ru_up"></span></p>
</div>
<div class="minipage">
<p><img src="./ru_down.JPG" style="width:50.0%" alt="image" /> <span
id="fig:ru_d" data-label="fig:ru_d"></span></p>
</div>
</figure>
<p>Summing from cubicle 1 to 8:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>≡</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>0</mn><mo>+</mo><mn>1</mn><mo>+</mo><mn>1</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>1</mn><mo>+</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>3</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_2 \equiv 0 \text{ (mod 3)} \equiv 0+1+1+0+0+0+1+0\text{ (mod 3)} \equiv 3\text{ (mod 3)} \equiv 0</annotation></semantics></math>
So, we can tell this is a legal move on the Pocket Cube via the Pocket’s
Cube FTCT.</p>
<p>Now, examining the illegal moves, Illegal Move (1) Rotating any one
corner cube is a very simple option. Without loss of generality to all
legal positions, consider the solved Rubik’s Cube configuration. Here,
we have
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>≡</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_2 \equiv 0 \text{ (mod 3)} \equiv 0+0+0+0+0+0+0+0\text{ (mod 3)} \equiv 0</annotation></semantics></math>
Rotating any one corner cube would result in, without loss of generality
to the cubicle of the corner we’re working with
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>≡</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>1</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>1</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≢</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_2 \equiv 0 \text{ (mod 3)} \equiv 1+0+0+0+0+0+0+0\text{ (mod 3)}\equiv 1\text{ (mod 3)} \not \equiv 0</annotation></semantics></math>
or
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msub><mi>v</mi><mn>1</mn></msub><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>+</mo><mi>.</mi><mi>.</mi><mi>.</mi><mo>+</mo><msub><mi>v</mi><mn>2</mn></msub><mo>≡</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>2</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mo>+</mo><mn>0</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≡</mo><mn>2</mn><mrow><mspace width="0.333em"></mspace><mtext mathvariant="normal"> (mod 3)</mtext></mrow><mo>≢</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">v_1+v_2+...+v_2 \equiv 0 \text{ (mod 3)} \equiv 2+0+0+0+0+0+0+0\text{ (mod 3)} \equiv 2\text{ (mod 3)} \not \equiv 0</annotation></semantics></math>
Clearly, this violates the conservation of corner rotations. Rotating
more than 1 corner might accidentally result in a sum that is congruent
to 0 (mod 3), so best to only rotate one! Illegal Move (2) works the
same way, but instead violates the conservation of edge flips, and is
only applicable to the 3x3 Rubik’s Cube.</p>
<p>Illegal Move (3) is a little more interesting, but is only applicable
to the 3x3 Cube. Obviously, we cannot swap a corner with an edge cube,
because they have a different number of facelets. Let’s find
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>ρ</mi><annotation encoding="application/x-tex">\rho</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>θ</mi><annotation encoding="application/x-tex">\theta</annotation></semantics></math>
in disjoint cycle notation, in the case where the 2 pieces swapped are
corner cubes in adjacent cubicles
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mi>i</mi><annotation encoding="application/x-tex">i</annotation></semantics></math>
and
<math display="inline" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">i+1</annotation></semantics></math>,
clearly:
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>ρ</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mi>i</mi><mo>,</mo><mi>i</mi><mo>+</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\rho = (i,i+1)</annotation></semantics></math>
which consists of 1 simple transposition. Because no edge pieces are
involved in this swap we have
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>θ</mi><mo>=</mo><mo stretchy="false" form="prefix">(</mo><mn>1</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>2</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>3</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>4</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>5</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>6</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>7</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>8</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>9</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>10</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>11</mn><mo stretchy="false" form="postfix">)</mo><mo stretchy="false" form="prefix">(</mo><mn>12</mn><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">\theta = (1)(2)(3)(4)(5)(6)(7)(8)(9)(10)(11)(12)</annotation></semantics></math>
which has 0 simple transpositions. Therefore, we have</p>
<p><math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo stretchy="false" form="postfix">)</mo><mo>≠</mo><mi>s</mi><mi>g</mi><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>θ</mi><mo stretchy="false" form="postfix">)</mo></mrow><annotation encoding="application/x-tex">sgn(\rho) \not= sgn(\theta)</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mn>1</mn><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>ρ</mi><mo stretchy="false" form="postfix">)</mo></mrow></msup><mo>≠</mo><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mn>1</mn><msup><mo stretchy="false" form="postfix">)</mo><mrow><mi>n</mi><mo stretchy="false" form="prefix">(</mo><mi>θ</mi><mo stretchy="false" form="postfix">)</mo></mrow></msup></mrow><annotation encoding="application/x-tex">(-1)^{n(\rho)}\not=(-1)^{n(\theta)}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mn>1</mn><msup><mo stretchy="false" form="postfix">)</mo><mn>1</mn></msup><mo>≠</mo><mo stretchy="false" form="prefix">(</mo><mi>−</mi><mn>1</mn><msup><mo stretchy="false" form="postfix">)</mo><mn>0</mn></msup></mrow><annotation encoding="application/x-tex">(-1)^{1}\not=(-1)^{0}</annotation></semantics></math>
<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>−</mi><mn>1</mn><mo>≠</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">-1 \not = 1</annotation></semantics></math>
which violates the FTCT criteria on Equal Parity. Therefore, this is an
illegal move and will render the Rubik’s Cube unsolvable.<br />
<br />
So, if we are handed a Rubik’s Cube, by simply finding the 4-tuple
representing it’s configuration we can easily determine if it is
solvable! Conversely, we can easily make our own trick Illegal Rubik’s
Cubes using the same group theory!</p>
<h1 id="bibliography.">Bibliography.</h1>
<div class="appendices">
<p>All code is available here: <a
href="https://github.com/Sara-Pesso/rubiks-cube-group-theory"
class="uri">https://github.com/Sara-Pesso/rubiks-cube-group-theory</a>.</p>
<h1 id="rubiks-cube-permutations-script">Rubik’s Cube Permutations
Script</h1>
<div class="spverbatim">
<p>from sympy.combinatorics.permutations import Permutation</p>
<p># Define permutations using array notation (0-indexed) # SymPy
indexes from 0, so we put 0 to nonexistent 0-cubicle # so it doesn’t
effect or calculations or notation in our paper</p>
<p># Cubicle Permutations (disregards cube orientation within cubicle) R
= Permutation(2,6,7,3) U = Permutation(1,2,3,4) L = Permutation(1,4,8,5)
D = Permutation(8,7,6,5) B = Permutation(2,1,5,6) F =
Permutation(3,7,8,4)</p>
<p>R_inv =  R U_inv =  U L_inv =  L D_inv =  D B_inv =  B F_inv =  F</p>
<p># Facelet Permutations: Using Jamie Mulholand’s notation
(https://www.sfu.ca/ jtmulhol/math302/puzzles-rc-representation.html)</p>
<p>Rf = Permutation(13,14,16,15)(10,2,19,22)(12,4,17,24) Uf =
Permutation(1,2,4,3)(9,5,17,13)(10,6,18,14) Lf =
Permutation(5,6,8,7)(3,11,23,18)(1,9,21,20) Df =
Permutation(21,22,24,23)(11,15,19,7)(12,16,20,8) Bf =
Permutation(17,18,20,19)(1,7,24,14)(2,5,23,16) Ff =
Permutation(9,10,12,11)(3,13,22,8)(4,15,21,6)</p>
<p>Rf_inv =  Rf Uf_inv =  Uf Lf_inv =  Lf Df_inv =  Df Ff_inv =  Ff</p>
</div>
<h1 id="permutation-exploration-script">Permutation Exploration
Script</h1>
<div class="spverbatim">
<p>from rubiks_cube_permutations import * # Group Theory Operations! #
Commutator RUR’U’ commutator = R*U*R_inv*U_inv print("Commutator: [R,U]
= RUR’U’") print("Cubicle notation:") print(f"Commutator:
<span>commutator</span>") # Permutation multiplication print(f"Order:
<span>commutator.order()</span>") # Order of the permutation
print(f"Cycle Form: <span>commutator.cyclic_form</span>") # Cycle
notation print(f"Permutation Form: <span>commutator.array_form</span>")
# Permutaion notation print(f"Sign:
<span>commutator.signature()</span>") # Sign of permutation</p>
<p>print("Facelet notation:") commutator = Rf*Uf*Rf_inv*Uf_inv
print(f"Commutator: <span>commutator</span>") # Permutation
multiplication print(f"Order: <span>commutator.order()</span>") # Order
of the permutation print(f"Cycle Form:
<span>commutator.cyclic_form</span>") # Cycle notation
print(f"Permutation Form: <span>commutator.array_form</span>") #
Permutaion notation print(f"Sign: <span>commutator.signature()</span>")
# Sign of permutation</p>
<p># Commutator [R, U ’L’U ] = RU ’L’U R’U ’LU commutator =
R*U_inv*L_inv*U*R_inv*U_inv*L*U print("Commutator: [R, U’L’U ] =
RU’L’UR’U’LU") print("Cubicle notation:") print(f"Commutator:
<span>commutator</span>") # Permutation multiplication print(f"Order:
<span>commutator.order()</span>") # Order of the permutation
print(f"Cycle Form: <span>commutator.cyclic_form</span>") # Cycle
notation print(f"Permutation Form: <span>commutator.array_form</span>")
# Permutaion notation print(f"Simple Transpositions:
<span>commutator.transpositions()</span>") print(f"Sign:
<span>commutator.signature()</span>") # Sign of permutation</p>
<p>print("Facelet notation:") commutator =
Rf*Uf_inv*Lf_inv*Uf*Rf_inv*Uf_inv*Lf*Uf print(f"Commutator:
<span>commutator</span>") # Permutation multiplication print(f"Order:
<span>commutator.order()</span>") # Order of the permutation
print(f"Cycle Form: <span>commutator.cyclic_form</span>") # Cycle
notation print(f"Permutation Form: <span>commutator.array_form</span>")
# Permutaion notation print(f"Simple Transpositions:
<span>commutator.transpositions()</span>") print(f"Sign:
<span>commutator.signature()</span>") # Sign of permutation</p>
</div>
<p><strong>Output:</strong></p>
<div class="spverbatim">
<p>Commutator: [R,U] = RUR’U’ Cubicle notation: Commutator: (1 2)(3 7)
Order: 2 Cycle Form: [[1, 2], [3, 7]] Permutation Form: [0, 2, 1, 7, 4,
5, 6, 3] Sign: 1 Facelet notation: Commutator: (24)(1 14 18 17 5 2)(4 15
13 22 10 12) Order: 6 Cycle Form: [[1, 14, 18, 17, 5, 2], [4, 15, 13,
22, 10, 12]] Permutation Form: [0, 14, 1, 3, 15, 2, 6, 7, 8, 9, 12, 11,
4, 22, 18, 13, 16, 5, 17, 19, 20, 21, 10, 23, 24] Sign: 1 Commutator:
[R, U’L’U ] = RU’L’UR’U’LU Cubicle notation: Commutator: (8)(1 3 2)
Order: 3 Cycle Form: [[1, 3, 2]] Permutation Form: [0, 3, 1, 2, 4, 5, 6,
7, 8] Simple Transpositions: [(1, 2), (1, 3)] Sign: 1 Facelet notation:
Commutator: (24)(1 13 14)(2 5 10)(4 17 18) Order: 3 Cycle Form: [[1, 13,
14], [2, 5, 10], [4, 17, 18]] Permutation Form: [0, 13, 5, 3, 17, 10, 6,
7, 8, 9, 2, 11, 12, 14, 1, 15, 16, 18, 4, 19, 20, 21, 22, 23, 24] Simple
Transpositions: [(1, 14), (1, 13), (2, 10), (2, 5), (4, 18), (4, 17)]
Sign: 1</p>
</div>
</div>
</body>