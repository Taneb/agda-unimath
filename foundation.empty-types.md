# Empty types

<pre class="Agda"><a id="24" class="Symbol">{-#</a> <a id="28" class="Keyword">OPTIONS</a> <a id="36" class="Pragma">--without-K</a> <a id="48" class="Pragma">--exact-split</a> <a id="62" class="Symbol">#-}</a>

<a id="67" class="Keyword">module</a> <a id="74" href="foundation.empty-types.html" class="Module">foundation.empty-types</a> <a id="97" class="Keyword">where</a>

<a id="104" class="Keyword">open</a> <a id="109" class="Keyword">import</a> <a id="116" href="foundation-core.empty-types.html" class="Module">foundation-core.empty-types</a> <a id="144" class="Keyword">public</a>

<a id="152" class="Keyword">open</a> <a id="157" class="Keyword">import</a> <a id="164" href="foundation-core.dependent-pair-types.html" class="Module">foundation-core.dependent-pair-types</a> <a id="201" class="Keyword">using</a> <a id="207" class="Symbol">(</a><a id="208" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a><a id="212" class="Symbol">;</a> <a id="214" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a><a id="217" class="Symbol">;</a> <a id="219" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a><a id="222" class="Symbol">)</a>
<a id="224" class="Keyword">open</a> <a id="229" class="Keyword">import</a> <a id="236" href="foundation-core.embeddings.html" class="Module">foundation-core.embeddings</a> <a id="263" class="Keyword">using</a> <a id="269" class="Symbol">(</a><a id="270" href="foundation-core.embeddings.html#980" class="Function">is-emb</a><a id="276" class="Symbol">;</a> <a id="278" href="foundation-core.embeddings.html#1062" class="Function Operator">_↪_</a><a id="281" class="Symbol">)</a>
<a id="283" class="Keyword">open</a> <a id="288" class="Keyword">import</a> <a id="295" href="foundation-core.equivalences.html" class="Module">foundation-core.equivalences</a> <a id="324" class="Keyword">using</a>
  <a id="332" class="Symbol">(</a> <a id="334" href="foundation-core.equivalences.html#1542" class="Function">is-equiv</a><a id="342" class="Symbol">;</a> <a id="344" href="foundation-core.equivalences.html#2999" class="Function">is-equiv-has-inverse</a><a id="364" class="Symbol">;</a> <a id="366" href="foundation-core.equivalences.html#1607" class="Function Operator">_≃_</a><a id="369" class="Symbol">;</a> <a id="371" href="foundation-core.equivalences.html#5707" class="Function">inv-equiv</a><a id="380" class="Symbol">;</a> <a id="382" href="foundation-core.equivalences.html#7843" class="Function Operator">_∘e_</a><a id="386" class="Symbol">;</a> <a id="388" href="foundation-core.equivalences.html#5022" class="Function">map-inv-equiv</a><a id="401" class="Symbol">)</a>
<a id="403" class="Keyword">open</a> <a id="408" class="Keyword">import</a> <a id="415" href="foundation-core.functions.html" class="Module">foundation-core.functions</a> <a id="441" class="Keyword">using</a> <a id="447" class="Symbol">(</a><a id="448" href="foundation-core.functions.html#407" class="Function Operator">_∘_</a><a id="451" class="Symbol">;</a> <a id="453" href="foundation-core.functions.html#309" class="Function">id</a><a id="455" class="Symbol">)</a>
<a id="457" class="Keyword">open</a> <a id="462" class="Keyword">import</a> <a id="469" href="foundation-core.homotopies.html" class="Module">foundation-core.homotopies</a> <a id="496" class="Keyword">using</a> <a id="502" class="Symbol">(</a><a id="503" href="foundation-core.homotopies.html#467" class="Function Operator">_~_</a><a id="506" class="Symbol">)</a>
<a id="508" class="Keyword">open</a> <a id="513" class="Keyword">import</a> <a id="520" href="foundation-core.sets.html" class="Module">foundation-core.sets</a> <a id="541" class="Keyword">using</a> <a id="547" class="Symbol">(</a><a id="548" href="foundation-core.sets.html#1099" class="Function">is-set</a><a id="554" class="Symbol">;</a> <a id="556" href="foundation-core.sets.html#1177" class="Function">UU-Set</a><a id="562" class="Symbol">)</a>
<a id="564" class="Keyword">open</a> <a id="569" class="Keyword">import</a> <a id="576" href="foundation-core.truncated-types.html" class="Module">foundation-core.truncated-types</a> <a id="608" class="Keyword">using</a>
  <a id="616" class="Symbol">(</a> <a id="618" href="foundation-core.truncated-types.html#1466" class="Function">is-trunc</a><a id="626" class="Symbol">;</a> <a id="628" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a><a id="645" class="Symbol">)</a>
<a id="647" class="Keyword">open</a> <a id="652" class="Keyword">import</a> <a id="659" href="foundation-core.truncation-levels.html" class="Module">foundation-core.truncation-levels</a> <a id="693" class="Keyword">using</a> <a id="699" class="Symbol">(</a><a id="700" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="701" class="Symbol">;</a> <a id="703" href="foundation-core.truncation-levels.html#419" class="InductiveConstructor">succ-𝕋</a><a id="709" class="Symbol">)</a>
<a id="711" class="Keyword">open</a> <a id="716" class="Keyword">import</a> <a id="723" href="foundation-core.universe-levels.html" class="Module">foundation-core.universe-levels</a> <a id="755" class="Keyword">using</a> <a id="761" class="Symbol">(</a><a id="762" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="767" class="Symbol">;</a> <a id="769" href="Agda.Primitive.html#764" class="Primitive">lzero</a><a id="774" class="Symbol">;</a> <a id="776" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="778" class="Symbol">)</a>

<a id="781" class="Keyword">open</a> <a id="786" class="Keyword">import</a> <a id="793" href="foundation.propositional-truncations.html" class="Module">foundation.propositional-truncations</a> <a id="830" class="Keyword">using</a>
  <a id="838" class="Symbol">(</a> <a id="840" href="foundation.propositional-truncations.html#1701" class="Postulate">type-trunc-Prop</a><a id="855" class="Symbol">;</a> <a id="857" href="foundation.propositional-truncations.html#4789" class="Function">map-universal-property-trunc-Prop</a><a id="890" class="Symbol">;</a> <a id="892" href="foundation.propositional-truncations.html#1756" class="Postulate">unit-trunc-Prop</a><a id="907" class="Symbol">)</a>
<a id="909" class="Keyword">open</a> <a id="914" class="Keyword">import</a> <a id="921" href="foundation.propositions.html" class="Module">foundation.propositions</a> <a id="945" class="Keyword">using</a>
  <a id="953" class="Symbol">(</a> <a id="955" href="foundation-core.propositions.html#1246" class="Function">is-prop</a><a id="962" class="Symbol">;</a> <a id="964" href="foundation-core.propositions.html#1322" class="Function">UU-Prop</a><a id="971" class="Symbol">;</a> <a id="973" href="foundation.propositions.html#940" class="Function">is-trunc-is-prop</a><a id="989" class="Symbol">;</a> <a id="991" href="foundation.propositions.html#3080" class="Function">is-prop-function-type</a><a id="1012" class="Symbol">;</a> <a id="1014" href="foundation-core.propositions.html#4815" class="Function">is-prop-equiv&#39;</a><a id="1028" class="Symbol">)</a>
<a id="1030" class="Keyword">open</a> <a id="1035" class="Keyword">import</a> <a id="1042" href="foundation.raising-universe-levels.html" class="Module">foundation.raising-universe-levels</a> <a id="1077" class="Keyword">using</a> <a id="1083" class="Symbol">(</a><a id="1084" href="foundation.raising-universe-levels.html#765" class="Datatype">raise</a><a id="1089" class="Symbol">;</a> <a id="1091" href="foundation.raising-universe-levels.html#1342" class="Function">equiv-raise</a><a id="1102" class="Symbol">)</a>
</pre>
## Idea

An empty type is a type with no elements. The (standard) empty type is introduced as an inductive type with no constructors. With the standard empty type available, we will say that a type is empty if it maps into the standard empty type.

## Definition

### We raise the empty type to an arbitrary universe level

<pre class="Agda"><a id="raise-empty"></a><a id="1441" href="foundation.empty-types.html#1441" class="Function">raise-empty</a> <a id="1453" class="Symbol">:</a> <a id="1455" class="Symbol">(</a><a id="1456" href="foundation.empty-types.html#1456" class="Bound">l</a> <a id="1458" class="Symbol">:</a> <a id="1460" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1465" class="Symbol">)</a> <a id="1467" class="Symbol">→</a> <a id="1469" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1472" href="foundation.empty-types.html#1456" class="Bound">l</a>
<a id="1474" href="foundation.empty-types.html#1441" class="Function">raise-empty</a> <a id="1486" href="foundation.empty-types.html#1486" class="Bound">l</a> <a id="1488" class="Symbol">=</a> <a id="1490" href="foundation.raising-universe-levels.html#765" class="Datatype">raise</a> <a id="1496" href="foundation.empty-types.html#1486" class="Bound">l</a> <a id="1498" href="foundation-core.empty-types.html#1047" class="Datatype">empty</a>

<a id="equiv-raise-empty"></a><a id="1505" href="foundation.empty-types.html#1505" class="Function">equiv-raise-empty</a> <a id="1523" class="Symbol">:</a> <a id="1525" class="Symbol">(</a><a id="1526" href="foundation.empty-types.html#1526" class="Bound">l</a> <a id="1528" class="Symbol">:</a> <a id="1530" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1535" class="Symbol">)</a> <a id="1537" class="Symbol">→</a> <a id="1539" href="foundation-core.empty-types.html#1047" class="Datatype">empty</a> <a id="1545" href="foundation-core.equivalences.html#1607" class="Function Operator">≃</a> <a id="1547" href="foundation.empty-types.html#1441" class="Function">raise-empty</a> <a id="1559" href="foundation.empty-types.html#1526" class="Bound">l</a>
<a id="1561" href="foundation.empty-types.html#1505" class="Function">equiv-raise-empty</a> <a id="1579" href="foundation.empty-types.html#1579" class="Bound">l</a> <a id="1581" class="Symbol">=</a> <a id="1583" href="foundation.raising-universe-levels.html#1342" class="Function">equiv-raise</a> <a id="1595" href="foundation.empty-types.html#1579" class="Bound">l</a> <a id="1597" href="foundation-core.empty-types.html#1047" class="Datatype">empty</a>
</pre>
## Properties


### Being empty is a proposition

<pre class="Agda"><a id="is-prop-is-empty"></a><a id="1666" href="foundation.empty-types.html#1666" class="Function">is-prop-is-empty</a> <a id="1683" class="Symbol">:</a> <a id="1685" class="Symbol">{</a><a id="1686" href="foundation.empty-types.html#1686" class="Bound">l</a> <a id="1688" class="Symbol">:</a> <a id="1690" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1695" class="Symbol">}</a> <a id="1697" class="Symbol">{</a><a id="1698" href="foundation.empty-types.html#1698" class="Bound">A</a> <a id="1700" class="Symbol">:</a> <a id="1702" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1705" href="foundation.empty-types.html#1686" class="Bound">l</a><a id="1706" class="Symbol">}</a> <a id="1708" class="Symbol">→</a> <a id="1710" href="foundation-core.propositions.html#1246" class="Function">is-prop</a> <a id="1718" class="Symbol">(</a><a id="1719" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="1728" href="foundation.empty-types.html#1698" class="Bound">A</a><a id="1729" class="Symbol">)</a>
<a id="1731" href="foundation.empty-types.html#1666" class="Function">is-prop-is-empty</a> <a id="1748" class="Symbol">=</a> <a id="1750" href="foundation.propositions.html#3080" class="Function">is-prop-function-type</a> <a id="1772" href="foundation-core.empty-types.html#2367" class="Function">is-prop-empty</a>

<a id="is-empty-Prop"></a><a id="1787" href="foundation.empty-types.html#1787" class="Function">is-empty-Prop</a> <a id="1801" class="Symbol">:</a> <a id="1803" class="Symbol">{</a><a id="1804" href="foundation.empty-types.html#1804" class="Bound">l1</a> <a id="1807" class="Symbol">:</a> <a id="1809" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1814" class="Symbol">}</a> <a id="1816" class="Symbol">→</a> <a id="1818" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1821" href="foundation.empty-types.html#1804" class="Bound">l1</a> <a id="1824" class="Symbol">→</a> <a id="1826" href="foundation-core.propositions.html#1322" class="Function">UU-Prop</a> <a id="1834" href="foundation.empty-types.html#1804" class="Bound">l1</a>
<a id="1837" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="1841" class="Symbol">(</a><a id="1842" href="foundation.empty-types.html#1787" class="Function">is-empty-Prop</a> <a id="1856" href="foundation.empty-types.html#1856" class="Bound">A</a><a id="1857" class="Symbol">)</a> <a id="1859" class="Symbol">=</a> <a id="1861" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="1870" href="foundation.empty-types.html#1856" class="Bound">A</a>
<a id="1872" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="1876" class="Symbol">(</a><a id="1877" href="foundation.empty-types.html#1787" class="Function">is-empty-Prop</a> <a id="1891" href="foundation.empty-types.html#1891" class="Bound">A</a><a id="1892" class="Symbol">)</a> <a id="1894" class="Symbol">=</a> <a id="1896" href="foundation.empty-types.html#1666" class="Function">is-prop-is-empty</a>

<a id="is-nonempty-Prop"></a><a id="1914" href="foundation.empty-types.html#1914" class="Function">is-nonempty-Prop</a> <a id="1931" class="Symbol">:</a> <a id="1933" class="Symbol">{</a><a id="1934" href="foundation.empty-types.html#1934" class="Bound">l1</a> <a id="1937" class="Symbol">:</a> <a id="1939" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1944" class="Symbol">}</a> <a id="1946" class="Symbol">→</a> <a id="1948" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1951" href="foundation.empty-types.html#1934" class="Bound">l1</a> <a id="1954" class="Symbol">→</a> <a id="1956" href="foundation-core.propositions.html#1322" class="Function">UU-Prop</a> <a id="1964" href="foundation.empty-types.html#1934" class="Bound">l1</a>
<a id="1967" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="1971" class="Symbol">(</a><a id="1972" href="foundation.empty-types.html#1914" class="Function">is-nonempty-Prop</a> <a id="1989" href="foundation.empty-types.html#1989" class="Bound">A</a><a id="1990" class="Symbol">)</a> <a id="1992" class="Symbol">=</a> <a id="1994" href="foundation-core.empty-types.html#1279" class="Function">is-nonempty</a> <a id="2006" href="foundation.empty-types.html#1989" class="Bound">A</a>
<a id="2008" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="2012" class="Symbol">(</a><a id="2013" href="foundation.empty-types.html#1914" class="Function">is-nonempty-Prop</a> <a id="2030" href="foundation.empty-types.html#2030" class="Bound">A</a><a id="2031" class="Symbol">)</a> <a id="2033" class="Symbol">=</a> <a id="2035" href="foundation.empty-types.html#1666" class="Function">is-prop-is-empty</a>
</pre>
<pre class="Agda"><a id="2065" class="Keyword">abstract</a>
  <a id="is-empty-type-trunc-Prop"></a><a id="2076" href="foundation.empty-types.html#2076" class="Function">is-empty-type-trunc-Prop</a> <a id="2101" class="Symbol">:</a>
    <a id="2107" class="Symbol">{</a><a id="2108" href="foundation.empty-types.html#2108" class="Bound">l1</a> <a id="2111" class="Symbol">:</a> <a id="2113" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2118" class="Symbol">}</a> <a id="2120" class="Symbol">{</a><a id="2121" href="foundation.empty-types.html#2121" class="Bound">X</a> <a id="2123" class="Symbol">:</a> <a id="2125" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2128" href="foundation.empty-types.html#2108" class="Bound">l1</a><a id="2130" class="Symbol">}</a> <a id="2132" class="Symbol">→</a> <a id="2134" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="2143" href="foundation.empty-types.html#2121" class="Bound">X</a> <a id="2145" class="Symbol">→</a> <a id="2147" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="2156" class="Symbol">(</a><a id="2157" href="foundation.propositional-truncations.html#1701" class="Postulate">type-trunc-Prop</a> <a id="2173" href="foundation.empty-types.html#2121" class="Bound">X</a><a id="2174" class="Symbol">)</a>
  <a id="2178" href="foundation.empty-types.html#2076" class="Function">is-empty-type-trunc-Prop</a> <a id="2203" href="foundation.empty-types.html#2203" class="Bound">f</a> <a id="2205" class="Symbol">=</a>
    <a id="2211" href="foundation.propositional-truncations.html#4789" class="Function">map-universal-property-trunc-Prop</a> <a id="2245" href="foundation-core.empty-types.html#2417" class="Function">empty-Prop</a> <a id="2256" href="foundation.empty-types.html#2203" class="Bound">f</a>

<a id="2259" class="Keyword">abstract</a>
  <a id="is-empty-type-trunc-Prop&#39;"></a><a id="2270" href="foundation.empty-types.html#2270" class="Function">is-empty-type-trunc-Prop&#39;</a> <a id="2296" class="Symbol">:</a>
    <a id="2302" class="Symbol">{</a><a id="2303" href="foundation.empty-types.html#2303" class="Bound">l1</a> <a id="2306" class="Symbol">:</a> <a id="2308" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2313" class="Symbol">}</a> <a id="2315" class="Symbol">{</a><a id="2316" href="foundation.empty-types.html#2316" class="Bound">X</a> <a id="2318" class="Symbol">:</a> <a id="2320" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2323" href="foundation.empty-types.html#2303" class="Bound">l1</a><a id="2325" class="Symbol">}</a> <a id="2327" class="Symbol">→</a> <a id="2329" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="2338" class="Symbol">(</a><a id="2339" href="foundation.propositional-truncations.html#1701" class="Postulate">type-trunc-Prop</a> <a id="2355" href="foundation.empty-types.html#2316" class="Bound">X</a><a id="2356" class="Symbol">)</a> <a id="2358" class="Symbol">→</a> <a id="2360" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="2369" href="foundation.empty-types.html#2316" class="Bound">X</a>
  <a id="2373" href="foundation.empty-types.html#2270" class="Function">is-empty-type-trunc-Prop&#39;</a> <a id="2399" href="foundation.empty-types.html#2399" class="Bound">f</a> <a id="2401" class="Symbol">=</a> <a id="2403" href="foundation.empty-types.html#2399" class="Bound">f</a> <a id="2405" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="2407" href="foundation.propositional-truncations.html#1756" class="Postulate">unit-trunc-Prop</a>
</pre>
### Any inhabited type is nonempty

<pre class="Agda"><a id="2472" class="Keyword">abstract</a>
  <a id="is-nonempty-is-inhabited"></a><a id="2483" href="foundation.empty-types.html#2483" class="Function">is-nonempty-is-inhabited</a> <a id="2508" class="Symbol">:</a>
    <a id="2514" class="Symbol">{</a><a id="2515" href="foundation.empty-types.html#2515" class="Bound">l</a> <a id="2517" class="Symbol">:</a> <a id="2519" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2524" class="Symbol">}</a> <a id="2526" class="Symbol">{</a><a id="2527" href="foundation.empty-types.html#2527" class="Bound">X</a> <a id="2529" class="Symbol">:</a> <a id="2531" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2534" href="foundation.empty-types.html#2515" class="Bound">l</a><a id="2535" class="Symbol">}</a> <a id="2537" class="Symbol">→</a> <a id="2539" href="foundation.propositional-truncations.html#1701" class="Postulate">type-trunc-Prop</a> <a id="2555" href="foundation.empty-types.html#2527" class="Bound">X</a> <a id="2557" class="Symbol">→</a> <a id="2559" href="foundation-core.empty-types.html#1279" class="Function">is-nonempty</a> <a id="2571" href="foundation.empty-types.html#2527" class="Bound">X</a>
  <a id="2575" href="foundation.empty-types.html#2483" class="Function">is-nonempty-is-inhabited</a> <a id="2600" class="Symbol">{</a><a id="2601" href="foundation.empty-types.html#2601" class="Bound">l</a><a id="2602" class="Symbol">}</a> <a id="2604" class="Symbol">{</a><a id="2605" href="foundation.empty-types.html#2605" class="Bound">X</a><a id="2606" class="Symbol">}</a> <a id="2608" class="Symbol">=</a>
    <a id="2614" href="foundation.propositional-truncations.html#4789" class="Function">map-universal-property-trunc-Prop</a> <a id="2648" class="Symbol">(</a><a id="2649" href="foundation.empty-types.html#1914" class="Function">is-nonempty-Prop</a> <a id="2666" href="foundation.empty-types.html#2605" class="Bound">X</a><a id="2667" class="Symbol">)</a> <a id="2669" class="Symbol">(λ</a> <a id="2672" href="foundation.empty-types.html#2672" class="Bound">x</a> <a id="2674" href="foundation.empty-types.html#2674" class="Bound">f</a> <a id="2676" class="Symbol">→</a> <a id="2678" href="foundation.empty-types.html#2674" class="Bound">f</a> <a id="2680" href="foundation.empty-types.html#2672" class="Bound">x</a><a id="2681" class="Symbol">)</a>
</pre>
<pre class="Agda"><a id="2696" class="Keyword">abstract</a>
  <a id="is-prop-raise-empty"></a><a id="2707" href="foundation.empty-types.html#2707" class="Function">is-prop-raise-empty</a> <a id="2727" class="Symbol">:</a>
    <a id="2733" class="Symbol">{</a><a id="2734" href="foundation.empty-types.html#2734" class="Bound">l1</a> <a id="2737" class="Symbol">:</a> <a id="2739" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2744" class="Symbol">}</a> <a id="2746" class="Symbol">→</a> <a id="2748" href="foundation-core.propositions.html#1246" class="Function">is-prop</a> <a id="2756" class="Symbol">(</a><a id="2757" href="foundation.empty-types.html#1441" class="Function">raise-empty</a> <a id="2769" href="foundation.empty-types.html#2734" class="Bound">l1</a><a id="2771" class="Symbol">)</a>
  <a id="2775" href="foundation.empty-types.html#2707" class="Function">is-prop-raise-empty</a> <a id="2795" class="Symbol">{</a><a id="2796" href="foundation.empty-types.html#2796" class="Bound">l1</a><a id="2798" class="Symbol">}</a> <a id="2800" class="Symbol">=</a>
    <a id="2806" href="foundation-core.propositions.html#4815" class="Function">is-prop-equiv&#39;</a>
      <a id="2827" class="Symbol">(</a> <a id="2829" href="foundation.raising-universe-levels.html#1342" class="Function">equiv-raise</a> <a id="2841" href="foundation.empty-types.html#2796" class="Bound">l1</a> <a id="2844" href="foundation-core.empty-types.html#1047" class="Datatype">empty</a><a id="2849" class="Symbol">)</a>
      <a id="2857" class="Symbol">(</a> <a id="2859" href="foundation-core.empty-types.html#2367" class="Function">is-prop-empty</a><a id="2872" class="Symbol">)</a>

<a id="raise-empty-Prop"></a><a id="2875" href="foundation.empty-types.html#2875" class="Function">raise-empty-Prop</a> <a id="2892" class="Symbol">:</a>
  <a id="2896" class="Symbol">(</a><a id="2897" href="foundation.empty-types.html#2897" class="Bound">l1</a> <a id="2900" class="Symbol">:</a> <a id="2902" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2907" class="Symbol">)</a> <a id="2909" class="Symbol">→</a> <a id="2911" href="foundation-core.propositions.html#1322" class="Function">UU-Prop</a> <a id="2919" href="foundation.empty-types.html#2897" class="Bound">l1</a>
<a id="2922" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="2926" class="Symbol">(</a><a id="2927" href="foundation.empty-types.html#2875" class="Function">raise-empty-Prop</a> <a id="2944" href="foundation.empty-types.html#2944" class="Bound">l1</a><a id="2946" class="Symbol">)</a> <a id="2948" class="Symbol">=</a> <a id="2950" href="foundation.empty-types.html#1441" class="Function">raise-empty</a> <a id="2962" href="foundation.empty-types.html#2944" class="Bound">l1</a>
<a id="2965" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="2969" class="Symbol">(</a><a id="2970" href="foundation.empty-types.html#2875" class="Function">raise-empty-Prop</a> <a id="2987" href="foundation.empty-types.html#2987" class="Bound">l1</a><a id="2989" class="Symbol">)</a> <a id="2991" class="Symbol">=</a> <a id="2993" href="foundation.empty-types.html#2707" class="Function">is-prop-raise-empty</a>

<a id="3014" class="Keyword">abstract</a>
  <a id="is-empty-raise-empty"></a><a id="3025" href="foundation.empty-types.html#3025" class="Function">is-empty-raise-empty</a> <a id="3046" class="Symbol">:</a>
    <a id="3052" class="Symbol">{</a><a id="3053" href="foundation.empty-types.html#3053" class="Bound">l1</a> <a id="3056" class="Symbol">:</a> <a id="3058" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3063" class="Symbol">}</a> <a id="3065" class="Symbol">→</a> <a id="3067" href="foundation-core.empty-types.html#1218" class="Function">is-empty</a> <a id="3076" class="Symbol">(</a><a id="3077" href="foundation.empty-types.html#1441" class="Function">raise-empty</a> <a id="3089" href="foundation.empty-types.html#3053" class="Bound">l1</a><a id="3091" class="Symbol">)</a>
  <a id="3095" href="foundation.empty-types.html#3025" class="Function">is-empty-raise-empty</a> <a id="3116" class="Symbol">{</a><a id="3117" href="foundation.empty-types.html#3117" class="Bound">l1</a><a id="3119" class="Symbol">}</a> <a id="3121" class="Symbol">=</a> <a id="3123" href="foundation-core.equivalences.html#5022" class="Function">map-inv-equiv</a> <a id="3137" class="Symbol">(</a><a id="3138" href="foundation.empty-types.html#1505" class="Function">equiv-raise-empty</a> <a id="3156" href="foundation.empty-types.html#3117" class="Bound">l1</a><a id="3158" class="Symbol">)</a>
</pre>