# Counting the elements of coproduct types

<pre class="Agda"><a id="53" class="Symbol">{-#</a> <a id="57" class="Keyword">OPTIONS</a> <a id="65" class="Pragma">--without-K</a> <a id="77" class="Pragma">--exact-split</a> <a id="91" class="Symbol">#-}</a>

<a id="96" class="Keyword">module</a> <a id="103" href="univalent-combinatorics.counting-coproduct-types.html" class="Module">univalent-combinatorics.counting-coproduct-types</a> <a id="152" class="Keyword">where</a>

<a id="159" class="Keyword">open</a> <a id="164" class="Keyword">import</a> <a id="171" href="elementary-number-theory.addition-natural-numbers.html" class="Module">elementary-number-theory.addition-natural-numbers</a> <a id="221" class="Keyword">using</a> <a id="227" class="Symbol">(</a><a id="228" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a><a id="233" class="Symbol">)</a>

<a id="236" class="Keyword">open</a> <a id="241" class="Keyword">import</a> <a id="248" href="foundation.coproduct-types.html" class="Module">foundation.coproduct-types</a> <a id="275" class="Keyword">using</a>
  <a id="283" class="Symbol">(</a> <a id="285" href="foundation.coproduct-types.html#1168" class="Datatype">coprod</a><a id="291" class="Symbol">;</a> <a id="293" href="foundation.coproduct-types.html#1239" class="InductiveConstructor">inl</a><a id="296" class="Symbol">;</a> <a id="298" href="foundation.coproduct-types.html#1262" class="InductiveConstructor">inr</a><a id="301" class="Symbol">;</a> <a id="303" href="foundation.coproduct-types.html#1649" class="Function">is-left-Prop</a><a id="315" class="Symbol">;</a> <a id="317" href="foundation.coproduct-types.html#1841" class="Function">is-right-Prop</a><a id="330" class="Symbol">;</a> <a id="332" href="foundation.coproduct-types.html#3260" class="Function">equiv-left-summand</a><a id="350" class="Symbol">;</a>
    <a id="356" href="foundation.coproduct-types.html#4305" class="Function">equiv-right-summand</a><a id="375" class="Symbol">)</a>
<a id="377" class="Keyword">open</a> <a id="382" class="Keyword">import</a> <a id="389" href="foundation.decidable-types.html" class="Module">foundation.decidable-types</a> <a id="416" class="Keyword">using</a>
  <a id="424" class="Symbol">(</a> <a id="426" href="foundation.decidable-types.html#2856" class="Function">is-decidable-is-left</a><a id="446" class="Symbol">;</a> <a id="448" href="foundation.decidable-types.html#3029" class="Function">is-decidable-is-right</a><a id="469" class="Symbol">)</a>
<a id="471" class="Keyword">open</a> <a id="476" class="Keyword">import</a> <a id="483" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="515" class="Keyword">using</a> <a id="521" class="Symbol">(</a><a id="522" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a><a id="523" class="Symbol">;</a> <a id="525" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a><a id="529" class="Symbol">;</a> <a id="531" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a><a id="534" class="Symbol">;</a> <a id="536" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a><a id="539" class="Symbol">)</a>
<a id="541" class="Keyword">open</a> <a id="546" class="Keyword">import</a> <a id="553" href="foundation.equivalences.html" class="Module">foundation.equivalences</a> <a id="577" class="Keyword">using</a> <a id="583" class="Symbol">(</a><a id="584" href="foundation-core.equivalences.html#7843" class="Function Operator">_∘e_</a><a id="588" class="Symbol">;</a> <a id="590" href="foundation-core.equivalences.html#5707" class="Function">inv-equiv</a><a id="599" class="Symbol">;</a> <a id="601" href="foundation-core.equivalences.html#1607" class="Function Operator">_≃_</a><a id="604" class="Symbol">)</a>
<a id="606" class="Keyword">open</a> <a id="611" class="Keyword">import</a> <a id="618" href="foundation.functoriality-coproduct-types.html" class="Module">foundation.functoriality-coproduct-types</a> <a id="659" class="Keyword">using</a> <a id="665" class="Symbol">(</a><a id="666" href="foundation.functoriality-coproduct-types.html#3470" class="Function">equiv-coprod</a><a id="678" class="Symbol">)</a>
<a id="680" class="Keyword">open</a> <a id="685" class="Keyword">import</a> <a id="692" href="foundation.identity-types.html" class="Module">foundation.identity-types</a> <a id="718" class="Keyword">using</a> <a id="724" class="Symbol">(</a><a id="725" href="foundation-core.identity-types.html#641" class="Datatype">Id</a><a id="727" class="Symbol">;</a> <a id="729" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a><a id="733" class="Symbol">;</a> <a id="735" href="foundation-core.identity-types.html#1239" class="Function Operator">_∙_</a><a id="738" class="Symbol">;</a> <a id="740" href="foundation-core.identity-types.html#1552" class="Function">inv</a><a id="743" class="Symbol">)</a>
<a id="745" class="Keyword">open</a> <a id="750" class="Keyword">import</a> <a id="757" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="784" class="Keyword">using</a> <a id="790" class="Symbol">(</a><a id="791" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="796" class="Symbol">;</a> <a id="798" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="800" class="Symbol">;</a> <a id="802" href="Agda.Primitive.html#764" class="Primitive">lzero</a><a id="807" class="Symbol">)</a>

<a id="810" class="Keyword">open</a> <a id="815" class="Keyword">import</a> <a id="822" href="univalent-combinatorics.counting.html" class="Module">univalent-combinatorics.counting</a> <a id="855" class="Keyword">using</a>
  <a id="863" class="Symbol">(</a> <a id="865" href="univalent-combinatorics.counting.html#1746" class="Function">count</a><a id="870" class="Symbol">;</a> <a id="872" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a><a id="896" class="Symbol">;</a> <a id="898" href="univalent-combinatorics.counting.html#5581" class="Function">count-unit</a><a id="908" class="Symbol">;</a> <a id="910" href="univalent-combinatorics.counting.html#4459" class="Function">count-empty</a><a id="921" class="Symbol">;</a> <a id="923" href="univalent-combinatorics.counting.html#2961" class="Function">count-equiv</a><a id="934" class="Symbol">)</a>
<a id="936" class="Keyword">open</a> <a id="941" class="Keyword">import</a> <a id="948" href="univalent-combinatorics.counting-decidable-subtypes.html" class="Module">univalent-combinatorics.counting-decidable-subtypes</a> <a id="1000" class="Keyword">using</a>
  <a id="1008" class="Symbol">(</a> <a id="1010" href="univalent-combinatorics.counting-decidable-subtypes.html#6673" class="Function">count-decidable-subtype</a><a id="1033" class="Symbol">)</a>
<a id="1035" class="Keyword">open</a> <a id="1040" class="Keyword">import</a> <a id="1047" href="univalent-combinatorics.double-counting.html" class="Module">univalent-combinatorics.double-counting</a> <a id="1087" class="Keyword">using</a> <a id="1093" class="Symbol">(</a><a id="1094" href="univalent-combinatorics.double-counting.html#1110" class="Function">double-counting</a><a id="1109" class="Symbol">)</a>
<a id="1111" class="Keyword">open</a> <a id="1116" class="Keyword">import</a> <a id="1123" href="univalent-combinatorics.equivalences-standard-finite-types.html" class="Module">univalent-combinatorics.equivalences-standard-finite-types</a> <a id="1182" class="Keyword">using</a>
  <a id="1190" class="Symbol">(</a> <a id="1192" href="univalent-combinatorics.equivalences-standard-finite-types.html#3020" class="Function">coprod-Fin</a><a id="1202" class="Symbol">)</a>
</pre>
## Idea

A coproduct `X + Y` has a count if and only if both `X` and `Y` have a count

## Properties

### Types equipped with a count are closed under coproducts

<pre class="Agda"><a id="count-coprod"></a><a id="1380" href="univalent-combinatorics.counting-coproduct-types.html#1380" class="Function">count-coprod</a> <a id="1393" class="Symbol">:</a>
  <a id="1397" class="Symbol">{</a><a id="1398" href="univalent-combinatorics.counting-coproduct-types.html#1398" class="Bound">l1</a> <a id="1401" href="univalent-combinatorics.counting-coproduct-types.html#1401" class="Bound">l2</a> <a id="1404" class="Symbol">:</a> <a id="1406" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1411" class="Symbol">}</a> <a id="1413" class="Symbol">{</a><a id="1414" href="univalent-combinatorics.counting-coproduct-types.html#1414" class="Bound">X</a> <a id="1416" class="Symbol">:</a> <a id="1418" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1421" href="univalent-combinatorics.counting-coproduct-types.html#1398" class="Bound">l1</a><a id="1423" class="Symbol">}</a> <a id="1425" class="Symbol">{</a><a id="1426" href="univalent-combinatorics.counting-coproduct-types.html#1426" class="Bound">Y</a> <a id="1428" class="Symbol">:</a> <a id="1430" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1433" href="univalent-combinatorics.counting-coproduct-types.html#1401" class="Bound">l2</a><a id="1435" class="Symbol">}</a> <a id="1437" class="Symbol">→</a>
  <a id="1441" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="1447" href="univalent-combinatorics.counting-coproduct-types.html#1414" class="Bound">X</a> <a id="1449" class="Symbol">→</a> <a id="1451" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="1457" href="univalent-combinatorics.counting-coproduct-types.html#1426" class="Bound">Y</a> <a id="1459" class="Symbol">→</a> <a id="1461" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="1467" class="Symbol">(</a><a id="1468" href="foundation.coproduct-types.html#1168" class="Datatype">coprod</a> <a id="1475" href="univalent-combinatorics.counting-coproduct-types.html#1414" class="Bound">X</a> <a id="1477" href="univalent-combinatorics.counting-coproduct-types.html#1426" class="Bound">Y</a><a id="1478" class="Symbol">)</a>
<a id="1480" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="1484" class="Symbol">(</a><a id="1485" href="univalent-combinatorics.counting-coproduct-types.html#1380" class="Function">count-coprod</a> <a id="1498" class="Symbol">(</a><a id="1499" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="1504" href="univalent-combinatorics.counting-coproduct-types.html#1504" class="Bound">k</a> <a id="1506" href="univalent-combinatorics.counting-coproduct-types.html#1506" class="Bound">e</a><a id="1507" class="Symbol">)</a> <a id="1509" class="Symbol">(</a><a id="1510" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="1515" href="univalent-combinatorics.counting-coproduct-types.html#1515" class="Bound">l</a> <a id="1517" href="univalent-combinatorics.counting-coproduct-types.html#1517" class="Bound">f</a><a id="1518" class="Symbol">))</a> <a id="1521" class="Symbol">=</a> <a id="1523" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a> <a id="1529" href="univalent-combinatorics.counting-coproduct-types.html#1504" class="Bound">k</a> <a id="1531" href="univalent-combinatorics.counting-coproduct-types.html#1515" class="Bound">l</a>
<a id="1533" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="1537" class="Symbol">(</a><a id="1538" href="univalent-combinatorics.counting-coproduct-types.html#1380" class="Function">count-coprod</a> <a id="1551" class="Symbol">(</a><a id="1552" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="1557" href="univalent-combinatorics.counting-coproduct-types.html#1557" class="Bound">k</a> <a id="1559" href="univalent-combinatorics.counting-coproduct-types.html#1559" class="Bound">e</a><a id="1560" class="Symbol">)</a> <a id="1562" class="Symbol">(</a><a id="1563" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="1568" href="univalent-combinatorics.counting-coproduct-types.html#1568" class="Bound">l</a> <a id="1570" href="univalent-combinatorics.counting-coproduct-types.html#1570" class="Bound">f</a><a id="1571" class="Symbol">))</a> <a id="1574" class="Symbol">=</a>
  <a id="1578" class="Symbol">(</a><a id="1579" href="foundation.functoriality-coproduct-types.html#3470" class="Function">equiv-coprod</a> <a id="1592" href="univalent-combinatorics.counting-coproduct-types.html#1559" class="Bound">e</a> <a id="1594" href="univalent-combinatorics.counting-coproduct-types.html#1570" class="Bound">f</a><a id="1595" class="Symbol">)</a> <a id="1597" href="foundation-core.equivalences.html#7843" class="Function Operator">∘e</a> <a id="1600" class="Symbol">(</a><a id="1601" href="foundation-core.equivalences.html#5707" class="Function">inv-equiv</a> <a id="1611" class="Symbol">(</a><a id="1612" href="univalent-combinatorics.equivalences-standard-finite-types.html#3020" class="Function">coprod-Fin</a> <a id="1623" href="univalent-combinatorics.counting-coproduct-types.html#1557" class="Bound">k</a> <a id="1625" href="univalent-combinatorics.counting-coproduct-types.html#1568" class="Bound">l</a><a id="1626" class="Symbol">))</a>

<a id="1630" class="Keyword">abstract</a>
  <a id="number-of-elements-count-coprod"></a><a id="1641" href="univalent-combinatorics.counting-coproduct-types.html#1641" class="Function">number-of-elements-count-coprod</a> <a id="1673" class="Symbol">:</a>
    <a id="1679" class="Symbol">{</a><a id="1680" href="univalent-combinatorics.counting-coproduct-types.html#1680" class="Bound">l1</a> <a id="1683" href="univalent-combinatorics.counting-coproduct-types.html#1683" class="Bound">l2</a> <a id="1686" class="Symbol">:</a> <a id="1688" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1693" class="Symbol">}</a> <a id="1695" class="Symbol">{</a><a id="1696" href="univalent-combinatorics.counting-coproduct-types.html#1696" class="Bound">X</a> <a id="1698" class="Symbol">:</a> <a id="1700" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1703" href="univalent-combinatorics.counting-coproduct-types.html#1680" class="Bound">l1</a><a id="1705" class="Symbol">}</a> <a id="1707" class="Symbol">{</a><a id="1708" href="univalent-combinatorics.counting-coproduct-types.html#1708" class="Bound">Y</a> <a id="1710" class="Symbol">:</a> <a id="1712" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1715" href="univalent-combinatorics.counting-coproduct-types.html#1683" class="Bound">l2</a><a id="1717" class="Symbol">}</a> <a id="1719" class="Symbol">(</a><a id="1720" href="univalent-combinatorics.counting-coproduct-types.html#1720" class="Bound">e</a> <a id="1722" class="Symbol">:</a> <a id="1724" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="1730" href="univalent-combinatorics.counting-coproduct-types.html#1696" class="Bound">X</a><a id="1731" class="Symbol">)</a> <a id="1733" class="Symbol">(</a><a id="1734" href="univalent-combinatorics.counting-coproduct-types.html#1734" class="Bound">f</a> <a id="1736" class="Symbol">:</a> <a id="1738" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="1744" href="univalent-combinatorics.counting-coproduct-types.html#1708" class="Bound">Y</a><a id="1745" class="Symbol">)</a> <a id="1747" class="Symbol">→</a>
    <a id="1753" href="foundation-core.identity-types.html#641" class="Datatype">Id</a> <a id="1756" class="Symbol">(</a> <a id="1758" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="1783" class="Symbol">(</a><a id="1784" href="univalent-combinatorics.counting-coproduct-types.html#1380" class="Function">count-coprod</a> <a id="1797" href="univalent-combinatorics.counting-coproduct-types.html#1720" class="Bound">e</a> <a id="1799" href="univalent-combinatorics.counting-coproduct-types.html#1734" class="Bound">f</a><a id="1800" class="Symbol">))</a>
      <a id="1809" class="Symbol">(</a> <a id="1811" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a> <a id="1817" class="Symbol">(</a><a id="1818" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="1843" href="univalent-combinatorics.counting-coproduct-types.html#1720" class="Bound">e</a><a id="1844" class="Symbol">)</a> <a id="1846" class="Symbol">(</a><a id="1847" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="1872" href="univalent-combinatorics.counting-coproduct-types.html#1734" class="Bound">f</a><a id="1873" class="Symbol">))</a>
  <a id="1878" href="univalent-combinatorics.counting-coproduct-types.html#1641" class="Function">number-of-elements-count-coprod</a> <a id="1910" class="Symbol">(</a><a id="1911" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="1916" href="univalent-combinatorics.counting-coproduct-types.html#1916" class="Bound">k</a> <a id="1918" href="univalent-combinatorics.counting-coproduct-types.html#1918" class="Bound">e</a><a id="1919" class="Symbol">)</a> <a id="1921" class="Symbol">(</a><a id="1922" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="1927" href="univalent-combinatorics.counting-coproduct-types.html#1927" class="Bound">l</a> <a id="1929" href="univalent-combinatorics.counting-coproduct-types.html#1929" class="Bound">f</a><a id="1930" class="Symbol">)</a> <a id="1932" class="Symbol">=</a> <a id="1934" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a>
</pre>
### If `X + Y` has a count, then both `X` and `Y` have a count

<pre class="Agda"><a id="count-left-summand"></a><a id="2016" href="univalent-combinatorics.counting-coproduct-types.html#2016" class="Function">count-left-summand</a> <a id="2035" class="Symbol">:</a>
  <a id="2039" class="Symbol">{</a><a id="2040" href="univalent-combinatorics.counting-coproduct-types.html#2040" class="Bound">l1</a> <a id="2043" href="univalent-combinatorics.counting-coproduct-types.html#2043" class="Bound">l2</a> <a id="2046" class="Symbol">:</a> <a id="2048" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2053" class="Symbol">}</a> <a id="2055" class="Symbol">{</a><a id="2056" href="univalent-combinatorics.counting-coproduct-types.html#2056" class="Bound">X</a> <a id="2058" class="Symbol">:</a> <a id="2060" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2063" href="univalent-combinatorics.counting-coproduct-types.html#2040" class="Bound">l1</a><a id="2065" class="Symbol">}</a> <a id="2067" class="Symbol">{</a><a id="2068" href="univalent-combinatorics.counting-coproduct-types.html#2068" class="Bound">Y</a> <a id="2070" class="Symbol">:</a> <a id="2072" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2075" href="univalent-combinatorics.counting-coproduct-types.html#2043" class="Bound">l2</a><a id="2077" class="Symbol">}</a> <a id="2079" class="Symbol">→</a> <a id="2081" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2087" class="Symbol">(</a><a id="2088" href="foundation.coproduct-types.html#1168" class="Datatype">coprod</a> <a id="2095" href="univalent-combinatorics.counting-coproduct-types.html#2056" class="Bound">X</a> <a id="2097" href="univalent-combinatorics.counting-coproduct-types.html#2068" class="Bound">Y</a><a id="2098" class="Symbol">)</a> <a id="2100" class="Symbol">→</a> <a id="2102" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2108" href="univalent-combinatorics.counting-coproduct-types.html#2056" class="Bound">X</a>
<a id="2110" href="univalent-combinatorics.counting-coproduct-types.html#2016" class="Function">count-left-summand</a> <a id="2129" href="univalent-combinatorics.counting-coproduct-types.html#2129" class="Bound">e</a> <a id="2131" class="Symbol">=</a>
  <a id="2135" href="univalent-combinatorics.counting.html#2961" class="Function">count-equiv</a>
    <a id="2151" class="Symbol">(</a> <a id="2153" href="foundation.coproduct-types.html#3260" class="Function">equiv-left-summand</a><a id="2171" class="Symbol">)</a>
    <a id="2177" class="Symbol">(</a> <a id="2179" href="univalent-combinatorics.counting-decidable-subtypes.html#6673" class="Function">count-decidable-subtype</a> <a id="2203" href="foundation.coproduct-types.html#1649" class="Function">is-left-Prop</a> <a id="2216" href="foundation.decidable-types.html#2856" class="Function">is-decidable-is-left</a> <a id="2237" href="univalent-combinatorics.counting-coproduct-types.html#2129" class="Bound">e</a><a id="2238" class="Symbol">)</a>

<a id="count-right-summand"></a><a id="2241" href="univalent-combinatorics.counting-coproduct-types.html#2241" class="Function">count-right-summand</a> <a id="2261" class="Symbol">:</a>
  <a id="2265" class="Symbol">{</a><a id="2266" href="univalent-combinatorics.counting-coproduct-types.html#2266" class="Bound">l1</a> <a id="2269" href="univalent-combinatorics.counting-coproduct-types.html#2269" class="Bound">l2</a> <a id="2272" class="Symbol">:</a> <a id="2274" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2279" class="Symbol">}</a> <a id="2281" class="Symbol">{</a><a id="2282" href="univalent-combinatorics.counting-coproduct-types.html#2282" class="Bound">X</a> <a id="2284" class="Symbol">:</a> <a id="2286" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2289" href="univalent-combinatorics.counting-coproduct-types.html#2266" class="Bound">l1</a><a id="2291" class="Symbol">}</a> <a id="2293" class="Symbol">{</a><a id="2294" href="univalent-combinatorics.counting-coproduct-types.html#2294" class="Bound">Y</a> <a id="2296" class="Symbol">:</a> <a id="2298" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2301" href="univalent-combinatorics.counting-coproduct-types.html#2269" class="Bound">l2</a><a id="2303" class="Symbol">}</a> <a id="2305" class="Symbol">→</a> <a id="2307" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2313" class="Symbol">(</a><a id="2314" href="foundation.coproduct-types.html#1168" class="Datatype">coprod</a> <a id="2321" href="univalent-combinatorics.counting-coproduct-types.html#2282" class="Bound">X</a> <a id="2323" href="univalent-combinatorics.counting-coproduct-types.html#2294" class="Bound">Y</a><a id="2324" class="Symbol">)</a> <a id="2326" class="Symbol">→</a> <a id="2328" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2334" href="univalent-combinatorics.counting-coproduct-types.html#2294" class="Bound">Y</a>
<a id="2336" href="univalent-combinatorics.counting-coproduct-types.html#2241" class="Function">count-right-summand</a> <a id="2356" href="univalent-combinatorics.counting-coproduct-types.html#2356" class="Bound">e</a> <a id="2358" class="Symbol">=</a>
  <a id="2362" href="univalent-combinatorics.counting.html#2961" class="Function">count-equiv</a>
    <a id="2378" class="Symbol">(</a> <a id="2380" href="foundation.coproduct-types.html#4305" class="Function">equiv-right-summand</a><a id="2399" class="Symbol">)</a>
    <a id="2405" class="Symbol">(</a> <a id="2407" href="univalent-combinatorics.counting-decidable-subtypes.html#6673" class="Function">count-decidable-subtype</a> <a id="2431" href="foundation.coproduct-types.html#1841" class="Function">is-right-Prop</a> <a id="2445" href="foundation.decidable-types.html#3029" class="Function">is-decidable-is-right</a> <a id="2467" href="univalent-combinatorics.counting-coproduct-types.html#2356" class="Bound">e</a><a id="2468" class="Symbol">)</a>
</pre>
### If each of `A`, `B`, and `A + B` come equipped with countings, then the number of elements of `A` and of `B` add up to the number of elements of `A + B`

<pre class="Agda"><a id="2641" class="Keyword">abstract</a>
  <a id="double-counting-coprod"></a><a id="2652" href="univalent-combinatorics.counting-coproduct-types.html#2652" class="Function">double-counting-coprod</a> <a id="2675" class="Symbol">:</a>
    <a id="2681" class="Symbol">{</a> <a id="2683" href="univalent-combinatorics.counting-coproduct-types.html#2683" class="Bound">l1</a> <a id="2686" href="univalent-combinatorics.counting-coproduct-types.html#2686" class="Bound">l2</a> <a id="2689" class="Symbol">:</a> <a id="2691" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2696" class="Symbol">}</a> <a id="2698" class="Symbol">{</a><a id="2699" href="univalent-combinatorics.counting-coproduct-types.html#2699" class="Bound">A</a> <a id="2701" class="Symbol">:</a> <a id="2703" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2706" href="univalent-combinatorics.counting-coproduct-types.html#2683" class="Bound">l1</a><a id="2708" class="Symbol">}</a> <a id="2710" class="Symbol">{</a><a id="2711" href="univalent-combinatorics.counting-coproduct-types.html#2711" class="Bound">B</a> <a id="2713" class="Symbol">:</a> <a id="2715" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2718" href="univalent-combinatorics.counting-coproduct-types.html#2686" class="Bound">l2</a><a id="2720" class="Symbol">}</a>
    <a id="2726" class="Symbol">(</a> <a id="2728" href="univalent-combinatorics.counting-coproduct-types.html#2728" class="Bound">count-A</a> <a id="2736" class="Symbol">:</a> <a id="2738" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2744" href="univalent-combinatorics.counting-coproduct-types.html#2699" class="Bound">A</a><a id="2745" class="Symbol">)</a> <a id="2747" class="Symbol">(</a><a id="2748" href="univalent-combinatorics.counting-coproduct-types.html#2748" class="Bound">count-B</a> <a id="2756" class="Symbol">:</a> <a id="2758" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2764" href="univalent-combinatorics.counting-coproduct-types.html#2711" class="Bound">B</a><a id="2765" class="Symbol">)</a> <a id="2767" class="Symbol">(</a><a id="2768" href="univalent-combinatorics.counting-coproduct-types.html#2768" class="Bound">count-C</a> <a id="2776" class="Symbol">:</a> <a id="2778" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="2784" class="Symbol">(</a><a id="2785" href="foundation.coproduct-types.html#1168" class="Datatype">coprod</a> <a id="2792" href="univalent-combinatorics.counting-coproduct-types.html#2699" class="Bound">A</a> <a id="2794" href="univalent-combinatorics.counting-coproduct-types.html#2711" class="Bound">B</a><a id="2795" class="Symbol">))</a> <a id="2798" class="Symbol">→</a>
    <a id="2804" href="foundation-core.identity-types.html#641" class="Datatype">Id</a> <a id="2807" class="Symbol">(</a> <a id="2809" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="2834" href="univalent-combinatorics.counting-coproduct-types.html#2768" class="Bound">count-C</a><a id="2841" class="Symbol">)</a>
       <a id="2850" class="Symbol">(</a> <a id="2852" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a>
         <a id="2867" class="Symbol">(</a> <a id="2869" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="2894" href="univalent-combinatorics.counting-coproduct-types.html#2728" class="Bound">count-A</a><a id="2901" class="Symbol">)</a>
         <a id="2912" class="Symbol">(</a> <a id="2914" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="2939" href="univalent-combinatorics.counting-coproduct-types.html#2748" class="Bound">count-B</a><a id="2946" class="Symbol">))</a>
  <a id="2951" href="univalent-combinatorics.counting-coproduct-types.html#2652" class="Function">double-counting-coprod</a> <a id="2974" href="univalent-combinatorics.counting-coproduct-types.html#2974" class="Bound">count-A</a> <a id="2982" href="univalent-combinatorics.counting-coproduct-types.html#2982" class="Bound">count-B</a> <a id="2990" href="univalent-combinatorics.counting-coproduct-types.html#2990" class="Bound">count-C</a> <a id="2998" class="Symbol">=</a>
    <a id="3004" class="Symbol">(</a> <a id="3006" href="univalent-combinatorics.double-counting.html#1110" class="Function">double-counting</a> <a id="3022" href="univalent-combinatorics.counting-coproduct-types.html#2990" class="Bound">count-C</a> <a id="3030" class="Symbol">(</a><a id="3031" href="univalent-combinatorics.counting-coproduct-types.html#1380" class="Function">count-coprod</a> <a id="3044" href="univalent-combinatorics.counting-coproduct-types.html#2974" class="Bound">count-A</a> <a id="3052" href="univalent-combinatorics.counting-coproduct-types.html#2982" class="Bound">count-B</a><a id="3059" class="Symbol">))</a> <a id="3062" href="foundation-core.identity-types.html#1239" class="Function Operator">∙</a>
    <a id="3068" class="Symbol">(</a> <a id="3070" href="univalent-combinatorics.counting-coproduct-types.html#1641" class="Function">number-of-elements-count-coprod</a> <a id="3102" href="univalent-combinatorics.counting-coproduct-types.html#2974" class="Bound">count-A</a> <a id="3110" href="univalent-combinatorics.counting-coproduct-types.html#2982" class="Bound">count-B</a><a id="3117" class="Symbol">)</a>

<a id="3120" class="Keyword">abstract</a>
  <a id="sum-number-of-elements-coprod"></a><a id="3131" href="univalent-combinatorics.counting-coproduct-types.html#3131" class="Function">sum-number-of-elements-coprod</a> <a id="3161" class="Symbol">:</a>
    <a id="3167" class="Symbol">{</a><a id="3168" href="univalent-combinatorics.counting-coproduct-types.html#3168" class="Bound">l1</a> <a id="3171" href="univalent-combinatorics.counting-coproduct-types.html#3171" class="Bound">l2</a> <a id="3174" class="Symbol">:</a> <a id="3176" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3181" class="Symbol">}</a> <a id="3183" class="Symbol">{</a><a id="3184" href="univalent-combinatorics.counting-coproduct-types.html#3184" class="Bound">A</a> <a id="3186" class="Symbol">:</a> <a id="3188" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3191" href="univalent-combinatorics.counting-coproduct-types.html#3168" class="Bound">l1</a><a id="3193" class="Symbol">}</a> <a id="3195" class="Symbol">{</a><a id="3196" href="univalent-combinatorics.counting-coproduct-types.html#3196" class="Bound">B</a> <a id="3198" class="Symbol">:</a> <a id="3200" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3203" href="univalent-combinatorics.counting-coproduct-types.html#3171" class="Bound">l2</a><a id="3205" class="Symbol">}</a> <a id="3207" class="Symbol">(</a><a id="3208" href="univalent-combinatorics.counting-coproduct-types.html#3208" class="Bound">e</a> <a id="3210" class="Symbol">:</a> <a id="3212" href="univalent-combinatorics.counting.html#1746" class="Function">count</a> <a id="3218" class="Symbol">(</a><a id="3219" href="foundation.coproduct-types.html#1168" class="Datatype">coprod</a> <a id="3226" href="univalent-combinatorics.counting-coproduct-types.html#3184" class="Bound">A</a> <a id="3228" href="univalent-combinatorics.counting-coproduct-types.html#3196" class="Bound">B</a><a id="3229" class="Symbol">))</a> <a id="3232" class="Symbol">→</a>
    <a id="3238" href="foundation-core.identity-types.html#641" class="Datatype">Id</a> <a id="3241" class="Symbol">(</a> <a id="3243" href="elementary-number-theory.addition-natural-numbers.html#988" class="Function">add-ℕ</a> <a id="3249" class="Symbol">(</a> <a id="3251" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="3276" class="Symbol">(</a><a id="3277" href="univalent-combinatorics.counting-coproduct-types.html#2016" class="Function">count-left-summand</a> <a id="3296" href="univalent-combinatorics.counting-coproduct-types.html#3208" class="Bound">e</a><a id="3297" class="Symbol">))</a>
               <a id="3315" class="Symbol">(</a> <a id="3317" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="3342" class="Symbol">(</a><a id="3343" href="univalent-combinatorics.counting-coproduct-types.html#2241" class="Function">count-right-summand</a> <a id="3363" href="univalent-combinatorics.counting-coproduct-types.html#3208" class="Bound">e</a><a id="3364" class="Symbol">)))</a>
       <a id="3375" class="Symbol">(</a> <a id="3377" href="univalent-combinatorics.counting.html#1874" class="Function">number-of-elements-count</a> <a id="3402" href="univalent-combinatorics.counting-coproduct-types.html#3208" class="Bound">e</a><a id="3403" class="Symbol">)</a>
  <a id="3407" href="univalent-combinatorics.counting-coproduct-types.html#3131" class="Function">sum-number-of-elements-coprod</a> <a id="3437" href="univalent-combinatorics.counting-coproduct-types.html#3437" class="Bound">e</a> <a id="3439" class="Symbol">=</a>
    <a id="3445" class="Symbol">(</a> <a id="3447" href="foundation-core.identity-types.html#1552" class="Function">inv</a>
      <a id="3457" class="Symbol">(</a> <a id="3459" href="univalent-combinatorics.counting-coproduct-types.html#1641" class="Function">number-of-elements-count-coprod</a>
        <a id="3499" class="Symbol">(</a> <a id="3501" href="univalent-combinatorics.counting-coproduct-types.html#2016" class="Function">count-left-summand</a> <a id="3520" href="univalent-combinatorics.counting-coproduct-types.html#3437" class="Bound">e</a><a id="3521" class="Symbol">)</a>
        <a id="3531" class="Symbol">(</a> <a id="3533" href="univalent-combinatorics.counting-coproduct-types.html#2241" class="Function">count-right-summand</a> <a id="3553" href="univalent-combinatorics.counting-coproduct-types.html#3437" class="Bound">e</a><a id="3554" class="Symbol">)))</a> <a id="3558" href="foundation-core.identity-types.html#1239" class="Function Operator">∙</a>
    <a id="3564" class="Symbol">(</a> <a id="3566" href="foundation-core.identity-types.html#1552" class="Function">inv</a>
      <a id="3576" class="Symbol">(</a> <a id="3578" href="univalent-combinatorics.counting-coproduct-types.html#2652" class="Function">double-counting-coprod</a>
        <a id="3609" class="Symbol">(</a> <a id="3611" href="univalent-combinatorics.counting-coproduct-types.html#2016" class="Function">count-left-summand</a> <a id="3630" href="univalent-combinatorics.counting-coproduct-types.html#3437" class="Bound">e</a><a id="3631" class="Symbol">)</a>
        <a id="3641" class="Symbol">(</a> <a id="3643" href="univalent-combinatorics.counting-coproduct-types.html#2241" class="Function">count-right-summand</a> <a id="3663" href="univalent-combinatorics.counting-coproduct-types.html#3437" class="Bound">e</a><a id="3664" class="Symbol">)</a> <a id="3666" href="univalent-combinatorics.counting-coproduct-types.html#3437" class="Bound">e</a><a id="3667" class="Symbol">))</a>
</pre>