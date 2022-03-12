---
title: Formalisation of the Symmetry Book
---

<pre class="Agda"><a id="60" class="Symbol">{-#</a> <a id="64" class="Keyword">OPTIONS</a> <a id="72" class="Pragma">--without-K</a> <a id="84" class="Pragma">--exact-split</a> <a id="98" class="Symbol">#-}</a>

<a id="103" class="Keyword">module</a> <a id="110" href="category-theory.html" class="Module">category-theory</a> <a id="126" class="Keyword">where</a>

<a id="133" class="Keyword">open</a> <a id="138" class="Keyword">import</a> <a id="145" href="category-theory.adjunctions-large-precategories.html" class="Module">category-theory.adjunctions-large-precategories</a> <a id="193" class="Keyword">public</a>
<a id="200" class="Keyword">open</a> <a id="205" class="Keyword">import</a> <a id="212" href="category-theory.categories.html" class="Module">category-theory.categories</a> <a id="239" class="Keyword">public</a>
<a id="246" class="Keyword">open</a> <a id="251" class="Keyword">import</a> <a id="258" href="category-theory.equivalences-categories.html" class="Module">category-theory.equivalences-categories</a> <a id="298" class="Keyword">public</a>
<a id="305" class="Keyword">open</a> <a id="310" class="Keyword">import</a> <a id="317" href="category-theory.equivalences-large-precategories.html" class="Module">category-theory.equivalences-large-precategories</a> <a id="366" class="Keyword">public</a>
<a id="373" class="Keyword">open</a> <a id="378" class="Keyword">import</a> <a id="385" href="category-theory.equivalences-precategories.html" class="Module">category-theory.equivalences-precategories</a> <a id="428" class="Keyword">public</a>
<a id="435" class="Keyword">open</a> <a id="440" class="Keyword">import</a> <a id="447" href="category-theory.functors-categories.html" class="Module">category-theory.functors-categories</a> <a id="483" class="Keyword">public</a>
<a id="490" class="Keyword">open</a> <a id="495" class="Keyword">import</a> <a id="502" href="category-theory.functors-large-precategories.html" class="Module">category-theory.functors-large-precategories</a> <a id="547" class="Keyword">public</a>
<a id="554" class="Keyword">open</a> <a id="559" class="Keyword">import</a> <a id="566" href="category-theory.functors-precategories.html" class="Module">category-theory.functors-precategories</a> <a id="605" class="Keyword">public</a>
<a id="612" class="Keyword">open</a> <a id="617" class="Keyword">import</a> <a id="624" href="category-theory.homotopies-natural-transformations-large-precategories.html" class="Module">category-theory.homotopies-natural-transformations-large-precategories</a> <a id="695" class="Keyword">public</a>
<a id="702" class="Keyword">open</a> <a id="707" class="Keyword">import</a> <a id="714" href="category-theory.isomorphisms-categories.html" class="Module">category-theory.isomorphisms-categories</a> <a id="754" class="Keyword">public</a>
<a id="761" class="Keyword">open</a> <a id="766" class="Keyword">import</a> <a id="773" href="category-theory.isomorphisms-large-precategories.html" class="Module">category-theory.isomorphisms-large-precategories</a> <a id="822" class="Keyword">public</a>
<a id="829" class="Keyword">open</a> <a id="834" class="Keyword">import</a> <a id="841" href="category-theory.isomorphisms-precategories.html" class="Module">category-theory.isomorphisms-precategories</a> <a id="884" class="Keyword">public</a>
<a id="891" class="Keyword">open</a> <a id="896" class="Keyword">import</a> <a id="903" href="category-theory.large-categories.html" class="Module">category-theory.large-categories</a> <a id="936" class="Keyword">public</a>
<a id="943" class="Keyword">open</a> <a id="948" class="Keyword">import</a> <a id="955" href="category-theory.large-precategories.html" class="Module">category-theory.large-precategories</a> <a id="991" class="Keyword">public</a>
<a id="998" class="Keyword">open</a> <a id="1003" class="Keyword">import</a> <a id="1010" href="category-theory.monomorphisms-large-precategories.html" class="Module">category-theory.monomorphisms-large-precategories</a> <a id="1060" class="Keyword">public</a>
<a id="1067" class="Keyword">open</a> <a id="1072" class="Keyword">import</a> <a id="1079" href="category-theory.natural-isomorphisms-categories.html" class="Module">category-theory.natural-isomorphisms-categories</a> <a id="1127" class="Keyword">public</a>
<a id="1134" class="Keyword">open</a> <a id="1139" class="Keyword">import</a> <a id="1146" href="category-theory.natural-isomorphisms-large-precategories.html" class="Module">category-theory.natural-isomorphisms-large-precategories</a> <a id="1203" class="Keyword">public</a>
<a id="1210" class="Keyword">open</a> <a id="1215" class="Keyword">import</a> <a id="1222" href="category-theory.natural-isomorphisms-precategories.html" class="Module">category-theory.natural-isomorphisms-precategories</a> <a id="1273" class="Keyword">public</a>
<a id="1280" class="Keyword">open</a> <a id="1285" class="Keyword">import</a> <a id="1292" href="category-theory.natural-transformations-categories.html" class="Module">category-theory.natural-transformations-categories</a> <a id="1343" class="Keyword">public</a>
<a id="1350" class="Keyword">open</a> <a id="1355" class="Keyword">import</a> <a id="1362" href="category-theory.natural-transformations-large-precategories.html" class="Module">category-theory.natural-transformations-large-precategories</a> <a id="1422" class="Keyword">public</a>
<a id="1429" class="Keyword">open</a> <a id="1434" class="Keyword">import</a> <a id="1441" href="category-theory.natural-transformations-precategories.html" class="Module">category-theory.natural-transformations-precategories</a> <a id="1495" class="Keyword">public</a>
<a id="1502" class="Keyword">open</a> <a id="1507" class="Keyword">import</a> <a id="1514" href="category-theory.precategories.html" class="Module">category-theory.precategories</a> <a id="1544" class="Keyword">public</a>
</pre>