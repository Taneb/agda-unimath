---
title: Univalent Mathematics in Agda
---

# The Goldbach conjecture

<pre class="Agda"><a id="82" class="Symbol">{-#</a> <a id="86" class="Keyword">OPTIONS</a> <a id="94" class="Pragma">--without-K</a> <a id="106" class="Pragma">--exact-split</a> <a id="120" class="Symbol">#-}</a>

<a id="125" class="Keyword">module</a> <a id="132" href="elementary-number-theory.goldbach-conjecture.html" class="Module">elementary-number-theory.goldbach-conjecture</a> <a id="177" class="Keyword">where</a>

<a id="184" class="Keyword">open</a> <a id="189" class="Keyword">import</a> <a id="196" href="elementary-number-theory.addition-natural-numbers.html" class="Module">elementary-number-theory.addition-natural-numbers</a> <a id="246" class="Keyword">using</a> <a id="252" class="Symbol">(</a><a id="253" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a><a id="258" class="Symbol">)</a>
<a id="260" class="Keyword">open</a> <a id="265" class="Keyword">import</a>
  <a id="274" href="elementary-number-theory.divisibility-natural-numbers.html" class="Module">elementary-number-theory.divisibility-natural-numbers</a> <a id="328" class="Keyword">using</a> <a id="334" class="Symbol">(</a><a id="335" href="elementary-number-theory.divisibility-natural-numbers.html#2390" class="Function">is-even-ℕ</a><a id="344" class="Symbol">)</a>
<a id="346" class="Keyword">open</a> <a id="351" class="Keyword">import</a> <a id="358" href="elementary-number-theory.inequality-natural-numbers.html" class="Module">elementary-number-theory.inequality-natural-numbers</a> <a id="410" class="Keyword">using</a> <a id="416" class="Symbol">(</a><a id="417" href="elementary-number-theory.inequality-natural-numbers.html#9976" class="Function">le-ℕ</a><a id="421" class="Symbol">)</a>
<a id="423" class="Keyword">open</a> <a id="428" class="Keyword">import</a> <a id="435" href="elementary-number-theory.natural-numbers.html" class="Module">elementary-number-theory.natural-numbers</a> <a id="476" class="Keyword">using</a> <a id="482" class="Symbol">(</a><a id="483" href="elementary-number-theory.natural-numbers.html#1444" class="Datatype">ℕ</a><a id="484" class="Symbol">)</a>
<a id="486" class="Keyword">open</a> <a id="491" class="Keyword">import</a> <a id="498" href="elementary-number-theory.prime-numbers.html" class="Module">elementary-number-theory.prime-numbers</a> <a id="537" class="Keyword">using</a> <a id="543" class="Symbol">(</a><a id="544" href="elementary-number-theory.prime-numbers.html#1945" class="Function">is-prime-ℕ</a><a id="554" class="Symbol">)</a>
<a id="556" class="Keyword">open</a> <a id="561" class="Keyword">import</a> <a id="568" href="foundation.cartesian-product-types.html" class="Module">foundation.cartesian-product-types</a> <a id="603" class="Keyword">using</a> <a id="609" class="Symbol">(</a><a id="610" href="foundation-core.cartesian-product-types.html#577" class="Function Operator">_×_</a><a id="613" class="Symbol">)</a>
<a id="615" class="Keyword">open</a> <a id="620" class="Keyword">import</a> <a id="627" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="659" class="Keyword">using</a> <a id="665" class="Symbol">(</a><a id="666" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a><a id="667" class="Symbol">)</a>
<a id="669" class="Keyword">open</a> <a id="674" class="Keyword">import</a> <a id="681" href="foundation.identity-types.html" class="Module">foundation.identity-types</a> <a id="707" class="Keyword">using</a> <a id="713" class="Symbol">(</a><a id="714" href="foundation-core.identity-types.html#641" class="Datatype">Id</a><a id="716" class="Symbol">)</a>
<a id="718" class="Keyword">open</a> <a id="723" class="Keyword">import</a> <a id="730" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="757" class="Keyword">using</a> <a id="763" class="Symbol">(</a><a id="764" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="766" class="Symbol">;</a> <a id="768" href="Agda.Primitive.html#764" class="Primitive">lzero</a><a id="773" class="Symbol">)</a>
</pre>
# The Goldbach Conjecture

<pre class="Agda"><a id="Goldbach-conjecture"></a><a id="815" href="elementary-number-theory.goldbach-conjecture.html#815" class="Function">Goldbach-conjecture</a> <a id="835" class="Symbol">:</a> <a id="837" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="840" href="Agda.Primitive.html#764" class="Primitive">lzero</a>
<a id="846" href="elementary-number-theory.goldbach-conjecture.html#815" class="Function">Goldbach-conjecture</a> <a id="866" class="Symbol">=</a>
  <a id="870" class="Symbol">(</a> <a id="872" href="elementary-number-theory.goldbach-conjecture.html#872" class="Bound">n</a> <a id="874" class="Symbol">:</a> <a id="876" href="elementary-number-theory.natural-numbers.html#1444" class="Datatype">ℕ</a><a id="877" class="Symbol">)</a> <a id="879" class="Symbol">→</a> <a id="881" class="Symbol">(</a><a id="882" href="elementary-number-theory.inequality-natural-numbers.html#9976" class="Function">le-ℕ</a> <a id="887" class="Number">2</a> <a id="889" href="elementary-number-theory.goldbach-conjecture.html#872" class="Bound">n</a><a id="890" class="Symbol">)</a> <a id="892" class="Symbol">→</a> <a id="894" class="Symbol">(</a><a id="895" href="elementary-number-theory.divisibility-natural-numbers.html#2390" class="Function">is-even-ℕ</a> <a id="905" href="elementary-number-theory.goldbach-conjecture.html#872" class="Bound">n</a><a id="906" class="Symbol">)</a> <a id="908" class="Symbol">→</a>
    <a id="914" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a> <a id="916" href="elementary-number-theory.natural-numbers.html#1444" class="Datatype">ℕ</a> <a id="918" class="Symbol">(λ</a> <a id="921" href="elementary-number-theory.goldbach-conjecture.html#921" class="Bound">p</a> <a id="923" class="Symbol">→</a> <a id="925" class="Symbol">(</a><a id="926" href="elementary-number-theory.prime-numbers.html#1945" class="Function">is-prime-ℕ</a> <a id="937" href="elementary-number-theory.goldbach-conjecture.html#921" class="Bound">p</a><a id="938" class="Symbol">)</a> <a id="940" href="foundation-core.cartesian-product-types.html#577" class="Function Operator">×</a> <a id="942" class="Symbol">(</a><a id="943" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a> <a id="945" href="elementary-number-theory.natural-numbers.html#1444" class="Datatype">ℕ</a> <a id="947" class="Symbol">(λ</a> <a id="950" href="elementary-number-theory.goldbach-conjecture.html#950" class="Bound">q</a> <a id="952" class="Symbol">→</a> <a id="954" class="Symbol">(</a><a id="955" href="elementary-number-theory.prime-numbers.html#1945" class="Function">is-prime-ℕ</a> <a id="966" href="elementary-number-theory.goldbach-conjecture.html#950" class="Bound">q</a><a id="967" class="Symbol">)</a> <a id="969" href="foundation-core.cartesian-product-types.html#577" class="Function Operator">×</a> <a id="971" href="foundation-core.identity-types.html#641" class="Datatype">Id</a> <a id="974" class="Symbol">(</a><a id="975" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a> <a id="981" href="elementary-number-theory.goldbach-conjecture.html#921" class="Bound">p</a> <a id="983" href="elementary-number-theory.goldbach-conjecture.html#950" class="Bound">q</a><a id="984" class="Symbol">)</a> <a id="986" href="elementary-number-theory.goldbach-conjecture.html#872" class="Bound">n</a><a id="987" class="Symbol">)))</a>
</pre>