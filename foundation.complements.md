# Complements of type families

<pre class="Agda"><a id="41" class="Symbol">{-#</a> <a id="45" class="Keyword">OPTIONS</a> <a id="53" class="Pragma">--without-K</a> <a id="65" class="Pragma">--exact-split</a> <a id="79" class="Symbol">#-}</a>

<a id="84" class="Keyword">module</a> <a id="91" href="foundation.complements.html" class="Module">foundation.complements</a> <a id="114" class="Keyword">where</a>

<a id="121" class="Keyword">open</a> <a id="126" class="Keyword">import</a> <a id="133" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="165" class="Keyword">using</a> <a id="171" class="Symbol">(</a><a id="172" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a><a id="173" class="Symbol">)</a>
<a id="175" class="Keyword">open</a> <a id="180" class="Keyword">import</a> <a id="187" href="foundation.empty-types.html" class="Module">foundation.empty-types</a> <a id="210" class="Keyword">using</a> <a id="216" class="Symbol">(</a><a id="217" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a><a id="225" class="Symbol">)</a>
<a id="227" class="Keyword">open</a> <a id="232" class="Keyword">import</a> <a id="239" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="260" class="Keyword">using</a> <a id="266" class="Symbol">(</a><a id="267" href="foundation-core.functions.html#407" class="Function Operator">_∘_</a><a id="270" class="Symbol">)</a>
<a id="272" class="Keyword">open</a> <a id="277" class="Keyword">import</a> <a id="284" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="311" class="Keyword">using</a> <a id="317" class="Symbol">(</a><a id="318" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="323" class="Symbol">;</a> <a id="325" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="327" class="Symbol">;</a> <a id="329" href="Agda.Primitive.html#810" class="Primitive Operator">_⊔_</a><a id="332" class="Symbol">)</a>
</pre>
## Idea

The complement of a type family `B` over `A` consists of the type of points in `A` at which `B x` is empty.

<pre class="Agda"><a id="complement"></a><a id="465" href="foundation.complements.html#465" class="Function">complement</a> <a id="476" class="Symbol">:</a>
  <a id="480" class="Symbol">{</a><a id="481" href="foundation.complements.html#481" class="Bound">l1</a> <a id="484" href="foundation.complements.html#484" class="Bound">l2</a> <a id="487" class="Symbol">:</a> <a id="489" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="494" class="Symbol">}</a> <a id="496" class="Symbol">{</a><a id="497" href="foundation.complements.html#497" class="Bound">A</a> <a id="499" class="Symbol">:</a> <a id="501" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="504" href="foundation.complements.html#481" class="Bound">l1</a><a id="506" class="Symbol">}</a> <a id="508" class="Symbol">(</a><a id="509" href="foundation.complements.html#509" class="Bound">B</a> <a id="511" class="Symbol">:</a> <a id="513" href="foundation.complements.html#497" class="Bound">A</a> <a id="515" class="Symbol">→</a> <a id="517" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="520" href="foundation.complements.html#484" class="Bound">l2</a><a id="522" class="Symbol">)</a> <a id="524" class="Symbol">→</a> <a id="526" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="529" class="Symbol">(</a><a id="530" href="foundation.complements.html#481" class="Bound">l1</a> <a id="533" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="535" href="foundation.complements.html#484" class="Bound">l2</a><a id="537" class="Symbol">)</a>
<a id="539" href="foundation.complements.html#465" class="Function">complement</a> <a id="550" class="Symbol">{</a><a id="551" href="foundation.complements.html#551" class="Bound">l1</a><a id="553" class="Symbol">}</a> <a id="555" class="Symbol">{</a><a id="556" href="foundation.complements.html#556" class="Bound">l2</a><a id="558" class="Symbol">}</a> <a id="560" class="Symbol">{</a><a id="561" href="foundation.complements.html#561" class="Bound">A</a><a id="562" class="Symbol">}</a> <a id="564" href="foundation.complements.html#564" class="Bound">B</a> <a id="566" class="Symbol">=</a> <a id="568" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a> <a id="570" href="foundation.complements.html#561" class="Bound">A</a> <a id="572" class="Symbol">(</a><a id="573" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="582" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="584" href="foundation.complements.html#564" class="Bound">B</a><a id="585" class="Symbol">)</a>
</pre>