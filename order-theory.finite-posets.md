---
title: Formalisation of the Symmetry Book
---

<pre class="Agda"><a id="60" class="Symbol">{-#</a> <a id="64" class="Keyword">OPTIONS</a> <a id="72" class="Pragma">--without-K</a> <a id="84" class="Pragma">--exact-split</a> <a id="98" class="Pragma">--allow-unsolved-metas</a> <a id="121" class="Symbol">#-}</a>

<a id="126" class="Keyword">module</a> <a id="133" href="order-theory.finite-posets.html" class="Module">order-theory.finite-posets</a> <a id="160" class="Keyword">where</a>

<a id="167" class="Keyword">open</a> <a id="172" class="Keyword">import</a> <a id="179" href="univalent-combinatorics.html" class="Module">univalent-combinatorics</a>

<a id="204" class="Keyword">open</a> <a id="209" class="Keyword">import</a> <a id="216" href="order-theory.posets.html" class="Module">order-theory.posets</a>
<a id="236" class="Keyword">open</a> <a id="241" class="Keyword">import</a> <a id="248" href="order-theory.finite-preorders.html" class="Module">order-theory.finite-preorders</a> <a id="278" class="Keyword">public</a>
</pre>
## Finite Posets

We say that a poset is finite if its underlying preorder is finite.

<pre class="Agda"><a id="385" class="Keyword">module</a> <a id="392" href="order-theory.finite-posets.html#392" class="Module">_</a>
  <a id="396" class="Symbol">{</a><a id="397" href="order-theory.finite-posets.html#397" class="Bound">l1</a> <a id="400" href="order-theory.finite-posets.html#400" class="Bound">l2</a> <a id="403" class="Symbol">:</a> <a id="405" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="410" class="Symbol">}</a> <a id="412" class="Symbol">(</a><a id="413" href="order-theory.finite-posets.html#413" class="Bound">X</a> <a id="415" class="Symbol">:</a> <a id="417" href="order-theory.posets.html#226" class="Function">Poset</a> <a id="423" href="order-theory.finite-posets.html#397" class="Bound">l1</a> <a id="426" href="order-theory.finite-posets.html#400" class="Bound">l2</a><a id="428" class="Symbol">)</a>
  <a id="432" class="Keyword">where</a>

  <a id="441" href="order-theory.finite-posets.html#441" class="Function">is-finite-poset-Prop</a> <a id="462" class="Symbol">:</a> <a id="464" href="foundation-core.propositions.html#1322" class="Function">UU-Prop</a> <a id="472" class="Symbol">(</a><a id="473" href="order-theory.finite-posets.html#397" class="Bound">l1</a> <a id="476" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="478" href="order-theory.finite-posets.html#400" class="Bound">l2</a><a id="480" class="Symbol">)</a>
  <a id="484" href="order-theory.finite-posets.html#441" class="Function">is-finite-poset-Prop</a> <a id="505" class="Symbol">=</a> <a id="507" href="order-theory.finite-preorders.html#455" class="Function">is-finite-preorder-Prop</a> <a id="531" class="Symbol">(</a><a id="532" href="order-theory.posets.html#1256" class="Function">preorder-Poset</a> <a id="547" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="548" class="Symbol">)</a>

  <a id="553" href="order-theory.finite-posets.html#553" class="Function">is-finite-Poset</a> <a id="569" class="Symbol">:</a> <a id="571" href="Agda.Primitive.html#326" class="Primitive">UU</a> <a id="574" class="Symbol">(</a><a id="575" href="order-theory.finite-posets.html#397" class="Bound">l1</a> <a id="578" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="580" href="order-theory.finite-posets.html#400" class="Bound">l2</a><a id="582" class="Symbol">)</a>
  <a id="586" href="order-theory.finite-posets.html#553" class="Function">is-finite-Poset</a> <a id="602" class="Symbol">=</a> <a id="604" href="order-theory.finite-preorders.html#768" class="Function">is-finite-Preorder</a> <a id="623" class="Symbol">(</a><a id="624" href="order-theory.posets.html#1256" class="Function">preorder-Poset</a> <a id="639" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="640" class="Symbol">)</a>

  <a id="645" href="order-theory.finite-posets.html#645" class="Function">is-prop-is-finite-Poset</a> <a id="669" class="Symbol">:</a> <a id="671" href="foundation-core.propositions.html#1246" class="Function">is-prop</a> <a id="679" href="order-theory.finite-posets.html#553" class="Function">is-finite-Poset</a>
  <a id="697" href="order-theory.finite-posets.html#645" class="Function">is-prop-is-finite-Poset</a> <a id="721" class="Symbol">=</a> <a id="723" href="order-theory.finite-preorders.html#862" class="Function">is-prop-is-finite-Preorder</a> <a id="750" class="Symbol">(</a><a id="751" href="order-theory.posets.html#1256" class="Function">preorder-Poset</a> <a id="766" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="767" class="Symbol">)</a>

  <a id="772" href="order-theory.finite-posets.html#772" class="Function">is-finite-element-is-finite-Poset</a> <a id="806" class="Symbol">:</a>
    <a id="812" href="order-theory.finite-posets.html#553" class="Function">is-finite-Poset</a> <a id="828" class="Symbol">→</a> <a id="830" href="univalent-combinatorics.finite-types.html#3732" class="Function">is-finite</a> <a id="840" class="Symbol">(</a><a id="841" href="order-theory.posets.html#640" class="Function">element-Poset</a> <a id="855" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="856" class="Symbol">)</a>
  <a id="860" href="order-theory.finite-posets.html#772" class="Function">is-finite-element-is-finite-Poset</a> <a id="894" class="Symbol">=</a>
    <a id="900" href="order-theory.finite-preorders.html#994" class="Function">is-finite-element-is-finite-Preorder</a> <a id="937" class="Symbol">(</a><a id="938" href="order-theory.posets.html#1256" class="Function">preorder-Poset</a> <a id="953" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="954" class="Symbol">)</a>

  <a id="959" href="order-theory.finite-posets.html#959" class="Function">is-decidable-leq-is-finite-Poset</a> <a id="992" class="Symbol">:</a>
    <a id="998" href="order-theory.finite-posets.html#553" class="Function">is-finite-Poset</a> <a id="1014" class="Symbol">→</a>
    <a id="1020" class="Symbol">(</a><a id="1021" href="order-theory.finite-posets.html#1021" class="Bound">x</a> <a id="1023" href="order-theory.finite-posets.html#1023" class="Bound">y</a> <a id="1025" class="Symbol">:</a> <a id="1027" href="order-theory.posets.html#640" class="Function">element-Poset</a> <a id="1041" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="1042" class="Symbol">)</a> <a id="1044" class="Symbol">→</a> <a id="1046" href="foundation.decidable-types.html#1741" class="Function">is-decidable</a> <a id="1059" class="Symbol">(</a><a id="1060" href="order-theory.posets.html#775" class="Function">leq-Poset</a> <a id="1070" href="order-theory.finite-posets.html#413" class="Bound">X</a> <a id="1072" href="order-theory.finite-posets.html#1021" class="Bound">x</a> <a id="1074" href="order-theory.finite-posets.html#1023" class="Bound">y</a><a id="1075" class="Symbol">)</a>
  <a id="1079" href="order-theory.finite-posets.html#959" class="Function">is-decidable-leq-is-finite-Poset</a> <a id="1112" class="Symbol">=</a>
    <a id="1118" href="order-theory.finite-preorders.html#1137" class="Function">is-decidable-leq-is-finite-Preorder</a> <a id="1154" class="Symbol">(</a><a id="1155" href="order-theory.posets.html#1256" class="Function">preorder-Poset</a> <a id="1170" href="order-theory.finite-posets.html#413" class="Bound">X</a><a id="1171" class="Symbol">)</a>
</pre>