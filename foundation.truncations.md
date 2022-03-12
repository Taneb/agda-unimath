# Truncations

<pre class="Agda"><a id="24" class="Symbol">{-#</a> <a id="28" class="Keyword">OPTIONS</a> <a id="36" class="Pragma">--without-K</a> <a id="48" class="Pragma">--exact-split</a> <a id="62" class="Symbol">#-}</a>

<a id="67" class="Keyword">module</a> <a id="74" href="foundation.truncations.html" class="Module">foundation.truncations</a> <a id="97" class="Keyword">where</a>

<a id="104" class="Keyword">open</a> <a id="109" class="Keyword">import</a> <a id="116" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="148" class="Keyword">using</a> <a id="154" class="Symbol">(</a><a id="155" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a><a id="156" class="Symbol">;</a> <a id="158" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a><a id="162" class="Symbol">;</a> <a id="164" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a><a id="167" class="Symbol">;</a> <a id="169" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a><a id="172" class="Symbol">)</a>
<a id="174" class="Keyword">open</a> <a id="179" class="Keyword">import</a> <a id="186" href="foundation.equivalences.html" class="Module">foundation.equivalences</a> <a id="210" class="Keyword">using</a> <a id="216" class="Symbol">(</a><a id="217" href="foundation-core.equivalences.html#1607" class="Function Operator">_≃_</a><a id="220" class="Symbol">;</a> <a id="222" href="foundation-core.equivalences.html#1542" class="Function">is-equiv</a><a id="230" class="Symbol">;</a> <a id="232" href="foundation-core.equivalences.html#5022" class="Function">map-inv-equiv</a><a id="245" class="Symbol">)</a>
<a id="247" class="Keyword">open</a> <a id="252" class="Keyword">import</a> <a id="259" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="280" class="Keyword">using</a> <a id="286" class="Symbol">(</a><a id="287" href="foundation-core.functions.html#407" class="Function Operator">_∘_</a><a id="290" class="Symbol">)</a>
<a id="292" class="Keyword">open</a> <a id="297" class="Keyword">import</a> <a id="304" href="foundation.homotopies.html" class="Module">foundation.homotopies</a> <a id="326" class="Keyword">using</a> <a id="332" class="Symbol">(</a><a id="333" href="foundation-core.homotopies.html#467" class="Function Operator">_~_</a><a id="336" class="Symbol">)</a>
<a id="338" class="Keyword">open</a> <a id="343" class="Keyword">import</a> <a id="350" href="foundation.truncated-types.html" class="Module">foundation.truncated-types</a> <a id="377" class="Keyword">using</a>
  <a id="385" class="Symbol">(</a> <a id="387" href="foundation-core.truncated-types.html#1466" class="Function">is-trunc</a><a id="395" class="Symbol">;</a> <a id="397" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a><a id="411" class="Symbol">;</a> <a id="413" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a><a id="432" class="Symbol">)</a>
<a id="434" class="Keyword">open</a> <a id="439" class="Keyword">import</a> <a id="446" href="foundation.truncation-levels.html" class="Module">foundation.truncation-levels</a> <a id="475" class="Keyword">using</a> <a id="481" class="Symbol">(</a><a id="482" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="483" class="Symbol">)</a>
<a id="485" class="Keyword">open</a> <a id="490" class="Keyword">import</a> <a id="497" href="foundation.universal-property-truncation.html" class="Module">foundation.universal-property-truncation</a> <a id="538" class="Keyword">using</a>
  <a id="546" class="Symbol">(</a> <a id="548" href="foundation.universal-property-truncation.html#1980" class="Function">is-truncation</a><a id="561" class="Symbol">;</a> <a id="563" href="foundation.universal-property-truncation.html#1754" class="Function">precomp-Trunc</a><a id="576" class="Symbol">;</a> <a id="578" href="foundation.universal-property-truncation.html#2270" class="Function">universal-property-truncation</a><a id="607" class="Symbol">;</a>
    <a id="613" href="foundation.universal-property-truncation.html#4590" class="Function">universal-property-truncation-is-truncation</a><a id="656" class="Symbol">;</a> <a id="658" href="foundation.universal-property-truncation.html#4968" class="Function">map-is-truncation</a><a id="675" class="Symbol">;</a>
    <a id="681" href="foundation.universal-property-truncation.html#5241" class="Function">triangle-is-truncation</a><a id="703" class="Symbol">;</a> <a id="705" href="foundation.universal-property-truncation.html#2678" class="Function">precomp-Π-Truncated-Type</a><a id="729" class="Symbol">;</a>
    <a id="735" href="foundation.universal-property-truncation.html#5799" class="Function">dependent-universal-property-truncation-is-truncation</a><a id="788" class="Symbol">;</a>
    <a id="794" href="foundation.universal-property-truncation.html#2934" class="Function">dependent-universal-property-truncation</a><a id="833" class="Symbol">)</a>
<a id="835" class="Keyword">open</a> <a id="840" class="Keyword">import</a> <a id="847" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="874" class="Keyword">using</a> <a id="880" class="Symbol">(</a><a id="881" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="886" class="Symbol">;</a> <a id="888" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="890" class="Symbol">)</a>
</pre>
## Idea

We postulate the existence of truncations

## Postulates

<pre class="Agda"><a id="972" class="Keyword">postulate</a>
  <a id="type-trunc"></a><a id="984" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="995" class="Symbol">:</a> <a id="997" class="Symbol">{</a><a id="998" href="foundation.truncations.html#998" class="Bound">l</a> <a id="1000" class="Symbol">:</a> <a id="1002" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1007" class="Symbol">}</a> <a id="1009" class="Symbol">(</a><a id="1010" href="foundation.truncations.html#1010" class="Bound">k</a> <a id="1012" class="Symbol">:</a> <a id="1014" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1015" class="Symbol">)</a> <a id="1017" class="Symbol">→</a> <a id="1019" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1022" href="foundation.truncations.html#998" class="Bound">l</a> <a id="1024" class="Symbol">→</a> <a id="1026" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1029" href="foundation.truncations.html#998" class="Bound">l</a>

<a id="1032" class="Keyword">postulate</a>
  <a id="is-trunc-type-trunc"></a><a id="1044" href="foundation.truncations.html#1044" class="Postulate">is-trunc-type-trunc</a> <a id="1064" class="Symbol">:</a>
    <a id="1070" class="Symbol">{</a><a id="1071" href="foundation.truncations.html#1071" class="Bound">l</a> <a id="1073" class="Symbol">:</a> <a id="1075" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1080" class="Symbol">}</a> <a id="1082" class="Symbol">{</a><a id="1083" href="foundation.truncations.html#1083" class="Bound">k</a> <a id="1085" class="Symbol">:</a> <a id="1087" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1088" class="Symbol">}</a> <a id="1090" class="Symbol">{</a><a id="1091" href="foundation.truncations.html#1091" class="Bound">A</a> <a id="1093" class="Symbol">:</a> <a id="1095" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1098" href="foundation.truncations.html#1071" class="Bound">l</a><a id="1099" class="Symbol">}</a> <a id="1101" class="Symbol">→</a> <a id="1103" href="foundation-core.truncated-types.html#1466" class="Function">is-trunc</a> <a id="1112" href="foundation.truncations.html#1083" class="Bound">k</a> <a id="1114" class="Symbol">(</a><a id="1115" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="1126" href="foundation.truncations.html#1083" class="Bound">k</a> <a id="1128" href="foundation.truncations.html#1091" class="Bound">A</a><a id="1129" class="Symbol">)</a>

<a id="trunc"></a><a id="1132" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="1138" class="Symbol">:</a> <a id="1140" class="Symbol">{</a><a id="1141" href="foundation.truncations.html#1141" class="Bound">l</a> <a id="1143" class="Symbol">:</a> <a id="1145" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1150" class="Symbol">}</a> <a id="1152" class="Symbol">(</a><a id="1153" href="foundation.truncations.html#1153" class="Bound">k</a> <a id="1155" class="Symbol">:</a> <a id="1157" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1158" class="Symbol">)</a> <a id="1160" class="Symbol">→</a> <a id="1162" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1165" href="foundation.truncations.html#1141" class="Bound">l</a> <a id="1167" class="Symbol">→</a> <a id="1169" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="1184" href="foundation.truncations.html#1141" class="Bound">l</a> <a id="1186" href="foundation.truncations.html#1153" class="Bound">k</a>
<a id="1188" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="1192" class="Symbol">(</a><a id="1193" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="1199" href="foundation.truncations.html#1199" class="Bound">k</a> <a id="1201" href="foundation.truncations.html#1201" class="Bound">A</a><a id="1202" class="Symbol">)</a> <a id="1204" class="Symbol">=</a> <a id="1206" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="1217" href="foundation.truncations.html#1199" class="Bound">k</a> <a id="1219" href="foundation.truncations.html#1201" class="Bound">A</a>
<a id="1221" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="1225" class="Symbol">(</a><a id="1226" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="1232" href="foundation.truncations.html#1232" class="Bound">k</a> <a id="1234" href="foundation.truncations.html#1234" class="Bound">A</a><a id="1235" class="Symbol">)</a> <a id="1237" class="Symbol">=</a> <a id="1239" href="foundation.truncations.html#1044" class="Postulate">is-trunc-type-trunc</a>

<a id="1260" class="Keyword">postulate</a>
  <a id="unit-trunc"></a><a id="1272" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="1283" class="Symbol">:</a> <a id="1285" class="Symbol">{</a><a id="1286" href="foundation.truncations.html#1286" class="Bound">l</a> <a id="1288" class="Symbol">:</a> <a id="1290" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1295" class="Symbol">}</a> <a id="1297" class="Symbol">{</a><a id="1298" href="foundation.truncations.html#1298" class="Bound">k</a> <a id="1300" class="Symbol">:</a> <a id="1302" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1303" class="Symbol">}</a> <a id="1305" class="Symbol">{</a><a id="1306" href="foundation.truncations.html#1306" class="Bound">A</a> <a id="1308" class="Symbol">:</a> <a id="1310" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1313" href="foundation.truncations.html#1286" class="Bound">l</a><a id="1314" class="Symbol">}</a> <a id="1316" class="Symbol">→</a> <a id="1318" href="foundation.truncations.html#1306" class="Bound">A</a> <a id="1320" class="Symbol">→</a> <a id="1322" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="1333" href="foundation.truncations.html#1298" class="Bound">k</a> <a id="1335" href="foundation.truncations.html#1306" class="Bound">A</a>

<a id="1338" class="Keyword">postulate</a>
  <a id="is-truncation-trunc"></a><a id="1350" href="foundation.truncations.html#1350" class="Postulate">is-truncation-trunc</a> <a id="1370" class="Symbol">:</a>
    <a id="1376" class="Symbol">{</a><a id="1377" href="foundation.truncations.html#1377" class="Bound">l1</a> <a id="1380" href="foundation.truncations.html#1380" class="Bound">l2</a> <a id="1383" class="Symbol">:</a> <a id="1385" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1390" class="Symbol">}</a> <a id="1392" class="Symbol">{</a><a id="1393" href="foundation.truncations.html#1393" class="Bound">k</a> <a id="1395" class="Symbol">:</a> <a id="1397" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1398" class="Symbol">}</a> <a id="1400" class="Symbol">{</a><a id="1401" href="foundation.truncations.html#1401" class="Bound">A</a> <a id="1403" class="Symbol">:</a> <a id="1405" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1408" href="foundation.truncations.html#1377" class="Bound">l1</a><a id="1410" class="Symbol">}</a> <a id="1412" class="Symbol">→</a>
    <a id="1418" href="foundation.universal-property-truncation.html#1980" class="Function">is-truncation</a> <a id="1432" href="foundation.truncations.html#1380" class="Bound">l2</a> <a id="1435" class="Symbol">(</a><a id="1436" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="1442" href="foundation.truncations.html#1393" class="Bound">k</a> <a id="1444" href="foundation.truncations.html#1401" class="Bound">A</a><a id="1445" class="Symbol">)</a> <a id="1447" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a>

<a id="equiv-universal-property-trunc"></a><a id="1459" href="foundation.truncations.html#1459" class="Function">equiv-universal-property-trunc</a> <a id="1490" class="Symbol">:</a>
  <a id="1494" class="Symbol">{</a><a id="1495" href="foundation.truncations.html#1495" class="Bound">l1</a> <a id="1498" href="foundation.truncations.html#1498" class="Bound">l2</a> <a id="1501" class="Symbol">:</a> <a id="1503" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1508" class="Symbol">}</a> <a id="1510" class="Symbol">{</a><a id="1511" href="foundation.truncations.html#1511" class="Bound">k</a> <a id="1513" class="Symbol">:</a> <a id="1515" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1516" class="Symbol">}</a> <a id="1518" class="Symbol">(</a><a id="1519" href="foundation.truncations.html#1519" class="Bound">A</a> <a id="1521" class="Symbol">:</a> <a id="1523" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1526" href="foundation.truncations.html#1495" class="Bound">l1</a><a id="1528" class="Symbol">)</a> <a id="1530" class="Symbol">(</a><a id="1531" href="foundation.truncations.html#1531" class="Bound">B</a> <a id="1533" class="Symbol">:</a> <a id="1535" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="1550" href="foundation.truncations.html#1498" class="Bound">l2</a> <a id="1553" href="foundation.truncations.html#1511" class="Bound">k</a><a id="1554" class="Symbol">)</a> <a id="1556" class="Symbol">→</a>
  <a id="1560" class="Symbol">(</a><a id="1561" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="1572" href="foundation.truncations.html#1511" class="Bound">k</a> <a id="1574" href="foundation.truncations.html#1519" class="Bound">A</a> <a id="1576" class="Symbol">→</a> <a id="1578" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="1598" href="foundation.truncations.html#1531" class="Bound">B</a><a id="1599" class="Symbol">)</a> <a id="1601" href="foundation-core.equivalences.html#1607" class="Function Operator">≃</a> <a id="1603" class="Symbol">(</a><a id="1604" href="foundation.truncations.html#1519" class="Bound">A</a> <a id="1606" class="Symbol">→</a> <a id="1608" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="1628" href="foundation.truncations.html#1531" class="Bound">B</a><a id="1629" class="Symbol">)</a>
<a id="1631" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="1635" class="Symbol">(</a><a id="1636" href="foundation.truncations.html#1459" class="Function">equiv-universal-property-trunc</a> <a id="1667" href="foundation.truncations.html#1667" class="Bound">A</a> <a id="1669" href="foundation.truncations.html#1669" class="Bound">B</a><a id="1670" class="Symbol">)</a> <a id="1672" class="Symbol">=</a> <a id="1674" href="foundation.universal-property-truncation.html#1754" class="Function">precomp-Trunc</a> <a id="1688" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="1699" href="foundation.truncations.html#1669" class="Bound">B</a>
<a id="1701" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="1705" class="Symbol">(</a><a id="1706" href="foundation.truncations.html#1459" class="Function">equiv-universal-property-trunc</a> <a id="1737" href="foundation.truncations.html#1737" class="Bound">A</a> <a id="1739" href="foundation.truncations.html#1739" class="Bound">B</a><a id="1740" class="Symbol">)</a> <a id="1742" class="Symbol">=</a> <a id="1744" href="foundation.truncations.html#1350" class="Postulate">is-truncation-trunc</a> <a id="1764" href="foundation.truncations.html#1739" class="Bound">B</a>
</pre>
## Properties

### The n-truncations satisfy the universal property

<pre class="Agda"><a id="universal-property-trunc"></a><a id="1848" href="foundation.truncations.html#1848" class="Function">universal-property-trunc</a> <a id="1873" class="Symbol">:</a>
  <a id="1877" class="Symbol">{</a><a id="1878" href="foundation.truncations.html#1878" class="Bound">l1</a> <a id="1881" class="Symbol">:</a> <a id="1883" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1888" class="Symbol">}</a> <a id="1890" class="Symbol">(</a><a id="1891" href="foundation.truncations.html#1891" class="Bound">k</a> <a id="1893" class="Symbol">:</a> <a id="1895" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1896" class="Symbol">)</a> <a id="1898" class="Symbol">(</a><a id="1899" href="foundation.truncations.html#1899" class="Bound">A</a> <a id="1901" class="Symbol">:</a> <a id="1903" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1906" href="foundation.truncations.html#1878" class="Bound">l1</a><a id="1908" class="Symbol">)</a> <a id="1910" class="Symbol">→</a>
  <a id="1914" class="Symbol">{</a><a id="1915" href="foundation.truncations.html#1915" class="Bound">l2</a> <a id="1918" class="Symbol">:</a> <a id="1920" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1925" class="Symbol">}</a> <a id="1927" class="Symbol">→</a> <a id="1929" href="foundation.universal-property-truncation.html#2270" class="Function">universal-property-truncation</a> <a id="1959" href="foundation.truncations.html#1915" class="Bound">l2</a> <a id="1962" class="Symbol">(</a><a id="1963" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="1969" href="foundation.truncations.html#1891" class="Bound">k</a> <a id="1971" href="foundation.truncations.html#1899" class="Bound">A</a><a id="1972" class="Symbol">)</a> <a id="1974" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a>
<a id="1985" href="foundation.truncations.html#1848" class="Function">universal-property-trunc</a> <a id="2010" href="foundation.truncations.html#2010" class="Bound">k</a> <a id="2012" href="foundation.truncations.html#2012" class="Bound">A</a> <a id="2014" class="Symbol">=</a>
  <a id="2018" href="foundation.universal-property-truncation.html#4590" class="Function">universal-property-truncation-is-truncation</a>
    <a id="2066" class="Symbol">(</a> <a id="2068" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="2074" href="foundation.truncations.html#2010" class="Bound">k</a> <a id="2076" href="foundation.truncations.html#2012" class="Bound">A</a><a id="2077" class="Symbol">)</a>
    <a id="2083" class="Symbol">(</a> <a id="2085" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a><a id="2095" class="Symbol">)</a>
    <a id="2101" class="Symbol">(</a> <a id="2103" href="foundation.truncations.html#1350" class="Postulate">is-truncation-trunc</a><a id="2122" class="Symbol">)</a>

<a id="2125" class="Keyword">module</a> <a id="2132" href="foundation.truncations.html#2132" class="Module">_</a>
  <a id="2136" class="Symbol">{</a><a id="2137" href="foundation.truncations.html#2137" class="Bound">l1</a> <a id="2140" href="foundation.truncations.html#2140" class="Bound">l2</a> <a id="2143" class="Symbol">:</a> <a id="2145" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2150" class="Symbol">}</a> <a id="2152" class="Symbol">{</a><a id="2153" href="foundation.truncations.html#2153" class="Bound">k</a> <a id="2155" class="Symbol">:</a> <a id="2157" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="2158" class="Symbol">}</a> <a id="2160" class="Symbol">{</a><a id="2161" href="foundation.truncations.html#2161" class="Bound">A</a> <a id="2163" class="Symbol">:</a> <a id="2165" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2168" href="foundation.truncations.html#2137" class="Bound">l1</a><a id="2170" class="Symbol">}</a>
  <a id="2174" class="Keyword">where</a>
  
  <a id="2185" href="foundation.truncations.html#2185" class="Function">map-universal-property-trunc</a> <a id="2214" class="Symbol">:</a>
    <a id="2220" class="Symbol">(</a><a id="2221" href="foundation.truncations.html#2221" class="Bound">B</a> <a id="2223" class="Symbol">:</a> <a id="2225" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="2240" href="foundation.truncations.html#2140" class="Bound">l2</a> <a id="2243" href="foundation.truncations.html#2153" class="Bound">k</a><a id="2244" class="Symbol">)</a> <a id="2246" class="Symbol">→</a> <a id="2248" class="Symbol">(</a><a id="2249" href="foundation.truncations.html#2161" class="Bound">A</a> <a id="2251" class="Symbol">→</a> <a id="2253" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="2273" href="foundation.truncations.html#2221" class="Bound">B</a><a id="2274" class="Symbol">)</a> <a id="2276" class="Symbol">→</a>
    <a id="2282" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="2293" href="foundation.truncations.html#2153" class="Bound">k</a> <a id="2295" href="foundation.truncations.html#2161" class="Bound">A</a> <a id="2297" class="Symbol">→</a> <a id="2299" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="2319" href="foundation.truncations.html#2221" class="Bound">B</a>
  <a id="2323" href="foundation.truncations.html#2185" class="Function">map-universal-property-trunc</a> <a id="2352" class="Symbol">=</a>
    <a id="2358" href="foundation.universal-property-truncation.html#4968" class="Function">map-is-truncation</a> <a id="2376" class="Symbol">(</a><a id="2377" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="2383" href="foundation.truncations.html#2153" class="Bound">k</a> <a id="2385" href="foundation.truncations.html#2161" class="Bound">A</a><a id="2386" class="Symbol">)</a> <a id="2388" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="2399" href="foundation.truncations.html#1350" class="Postulate">is-truncation-trunc</a>

  <a id="2422" href="foundation.truncations.html#2422" class="Function">triangle-universal-property-trunc</a> <a id="2456" class="Symbol">:</a>
    <a id="2462" class="Symbol">(</a><a id="2463" href="foundation.truncations.html#2463" class="Bound">B</a> <a id="2465" class="Symbol">:</a> <a id="2467" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="2482" href="foundation.truncations.html#2140" class="Bound">l2</a> <a id="2485" href="foundation.truncations.html#2153" class="Bound">k</a><a id="2486" class="Symbol">)</a> <a id="2488" class="Symbol">(</a><a id="2489" href="foundation.truncations.html#2489" class="Bound">f</a> <a id="2491" class="Symbol">:</a> <a id="2493" href="foundation.truncations.html#2161" class="Bound">A</a> <a id="2495" class="Symbol">→</a> <a id="2497" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="2517" href="foundation.truncations.html#2463" class="Bound">B</a><a id="2518" class="Symbol">)</a> <a id="2520" class="Symbol">→</a>
    <a id="2526" class="Symbol">(</a><a id="2527" href="foundation.truncations.html#2185" class="Function">map-universal-property-trunc</a> <a id="2556" href="foundation.truncations.html#2463" class="Bound">B</a> <a id="2558" href="foundation.truncations.html#2489" class="Bound">f</a> <a id="2560" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="2562" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a><a id="2572" class="Symbol">)</a> <a id="2574" href="foundation-core.homotopies.html#467" class="Function Operator">~</a> <a id="2576" href="foundation.truncations.html#2489" class="Bound">f</a>
  <a id="2580" href="foundation.truncations.html#2422" class="Function">triangle-universal-property-trunc</a> <a id="2614" class="Symbol">=</a>
    <a id="2620" href="foundation.universal-property-truncation.html#5241" class="Function">triangle-is-truncation</a> <a id="2643" class="Symbol">(</a><a id="2644" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="2650" href="foundation.truncations.html#2153" class="Bound">k</a> <a id="2652" href="foundation.truncations.html#2161" class="Bound">A</a><a id="2653" class="Symbol">)</a> <a id="2655" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="2666" href="foundation.truncations.html#1350" class="Postulate">is-truncation-trunc</a>

  <a id="2689" href="foundation.truncations.html#2689" class="Function">apply-universal-property-trunc</a> <a id="2720" class="Symbol">:</a>
    <a id="2726" class="Symbol">(</a><a id="2727" href="foundation.truncations.html#2727" class="Bound">x</a> <a id="2729" class="Symbol">:</a> <a id="2731" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="2742" href="foundation.truncations.html#2153" class="Bound">k</a> <a id="2744" href="foundation.truncations.html#2161" class="Bound">A</a><a id="2745" class="Symbol">)</a> <a id="2747" class="Symbol">(</a><a id="2748" href="foundation.truncations.html#2748" class="Bound">B</a> <a id="2750" class="Symbol">:</a> <a id="2752" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="2767" href="foundation.truncations.html#2140" class="Bound">l2</a> <a id="2770" href="foundation.truncations.html#2153" class="Bound">k</a><a id="2771" class="Symbol">)</a> <a id="2773" class="Symbol">→</a>
    <a id="2779" class="Symbol">(</a><a id="2780" href="foundation.truncations.html#2161" class="Bound">A</a> <a id="2782" class="Symbol">→</a> <a id="2784" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="2804" href="foundation.truncations.html#2748" class="Bound">B</a><a id="2805" class="Symbol">)</a> <a id="2807" class="Symbol">→</a> <a id="2809" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="2829" href="foundation.truncations.html#2748" class="Bound">B</a>
  <a id="2833" href="foundation.truncations.html#2689" class="Function">apply-universal-property-trunc</a> <a id="2864" href="foundation.truncations.html#2864" class="Bound">x</a> <a id="2866" href="foundation.truncations.html#2866" class="Bound">B</a> <a id="2868" href="foundation.truncations.html#2868" class="Bound">f</a> <a id="2870" class="Symbol">=</a>
    <a id="2876" href="foundation.truncations.html#2185" class="Function">map-universal-property-trunc</a> <a id="2905" href="foundation.truncations.html#2866" class="Bound">B</a> <a id="2907" href="foundation.truncations.html#2868" class="Bound">f</a> <a id="2909" href="foundation.truncations.html#2864" class="Bound">x</a>
</pre>
### The n-truncations satisfy the dependent universal property

<pre class="Agda"><a id="2988" class="Keyword">module</a> <a id="2995" href="foundation.truncations.html#2995" class="Module">_</a>
  <a id="2999" class="Symbol">{</a><a id="3000" href="foundation.truncations.html#3000" class="Bound">l1</a> <a id="3003" class="Symbol">:</a> <a id="3005" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3010" class="Symbol">}</a> <a id="3012" class="Symbol">{</a><a id="3013" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3015" class="Symbol">:</a> <a id="3017" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="3018" class="Symbol">}</a> <a id="3020" class="Symbol">{</a><a id="3021" href="foundation.truncations.html#3021" class="Bound">A</a> <a id="3023" class="Symbol">:</a> <a id="3025" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3028" href="foundation.truncations.html#3000" class="Bound">l1</a><a id="3030" class="Symbol">}</a>
  <a id="3034" class="Keyword">where</a>

  <a id="3043" href="foundation.truncations.html#3043" class="Function">dependent-universal-property-trunc</a> <a id="3078" class="Symbol">:</a>
    <a id="3084" class="Symbol">{</a><a id="3085" href="foundation.truncations.html#3085" class="Bound">l</a> <a id="3087" class="Symbol">:</a> <a id="3089" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3094" class="Symbol">}</a> <a id="3096" class="Symbol">→</a>
    <a id="3102" href="foundation.universal-property-truncation.html#2934" class="Function">dependent-universal-property-truncation</a> <a id="3142" href="foundation.truncations.html#3085" class="Bound">l</a> <a id="3144" class="Symbol">(</a><a id="3145" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="3151" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3153" href="foundation.truncations.html#3021" class="Bound">A</a><a id="3154" class="Symbol">)</a> <a id="3156" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a>
  <a id="3169" href="foundation.truncations.html#3043" class="Function">dependent-universal-property-trunc</a> <a id="3204" class="Symbol">=</a>
    <a id="3210" href="foundation.universal-property-truncation.html#5799" class="Function">dependent-universal-property-truncation-is-truncation</a>
      <a id="3270" class="Symbol">(</a> <a id="3272" href="foundation.truncations.html#1132" class="Function">trunc</a> <a id="3278" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3280" href="foundation.truncations.html#3021" class="Bound">A</a><a id="3281" class="Symbol">)</a>
      <a id="3289" class="Symbol">(</a> <a id="3291" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a><a id="3301" class="Symbol">)</a>
      <a id="3309" class="Symbol">(</a> <a id="3311" href="foundation.truncations.html#1350" class="Postulate">is-truncation-trunc</a><a id="3330" class="Symbol">)</a>

  <a id="3335" href="foundation.truncations.html#3335" class="Function">equiv-dependent-universal-property-trunc</a> <a id="3376" class="Symbol">:</a>
    <a id="3382" class="Symbol">{</a><a id="3383" href="foundation.truncations.html#3383" class="Bound">l2</a> <a id="3386" class="Symbol">:</a> <a id="3388" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3393" class="Symbol">}</a> <a id="3395" class="Symbol">(</a><a id="3396" href="foundation.truncations.html#3396" class="Bound">B</a> <a id="3398" class="Symbol">:</a> <a id="3400" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="3411" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3413" href="foundation.truncations.html#3021" class="Bound">A</a> <a id="3415" class="Symbol">→</a> <a id="3417" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="3432" href="foundation.truncations.html#3383" class="Bound">l2</a> <a id="3435" href="foundation.truncations.html#3013" class="Bound">k</a><a id="3436" class="Symbol">)</a> <a id="3438" class="Symbol">→</a>
    <a id="3444" class="Symbol">((</a><a id="3446" href="foundation.truncations.html#3446" class="Bound">x</a> <a id="3448" class="Symbol">:</a> <a id="3450" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="3461" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3463" href="foundation.truncations.html#3021" class="Bound">A</a><a id="3464" class="Symbol">)</a> <a id="3466" class="Symbol">→</a> <a id="3468" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="3488" class="Symbol">(</a><a id="3489" href="foundation.truncations.html#3396" class="Bound">B</a> <a id="3491" href="foundation.truncations.html#3446" class="Bound">x</a><a id="3492" class="Symbol">))</a> <a id="3495" href="foundation-core.equivalences.html#1607" class="Function Operator">≃</a>
    <a id="3501" class="Symbol">((</a><a id="3503" href="foundation.truncations.html#3503" class="Bound">a</a> <a id="3505" class="Symbol">:</a> <a id="3507" href="foundation.truncations.html#3021" class="Bound">A</a><a id="3508" class="Symbol">)</a> <a id="3510" class="Symbol">→</a> <a id="3512" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="3532" class="Symbol">(</a><a id="3533" href="foundation.truncations.html#3396" class="Bound">B</a> <a id="3535" class="Symbol">(</a><a id="3536" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="3547" href="foundation.truncations.html#3503" class="Bound">a</a><a id="3548" class="Symbol">)))</a>
  <a id="3554" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="3558" class="Symbol">(</a><a id="3559" href="foundation.truncations.html#3335" class="Function">equiv-dependent-universal-property-trunc</a> <a id="3600" href="foundation.truncations.html#3600" class="Bound">B</a><a id="3601" class="Symbol">)</a> <a id="3603" class="Symbol">=</a>
    <a id="3609" href="foundation.universal-property-truncation.html#2678" class="Function">precomp-Π-Truncated-Type</a> <a id="3634" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="3645" href="foundation.truncations.html#3600" class="Bound">B</a>
  <a id="3649" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="3653" class="Symbol">(</a><a id="3654" href="foundation.truncations.html#3335" class="Function">equiv-dependent-universal-property-trunc</a> <a id="3695" href="foundation.truncations.html#3695" class="Bound">B</a><a id="3696" class="Symbol">)</a> <a id="3698" class="Symbol">=</a>
    <a id="3704" href="foundation.truncations.html#3043" class="Function">dependent-universal-property-trunc</a> <a id="3739" href="foundation.truncations.html#3695" class="Bound">B</a>

  <a id="3744" href="foundation.truncations.html#3744" class="Function">apply-dependent-universal-property-trunc</a> <a id="3785" class="Symbol">:</a>
    <a id="3791" class="Symbol">{</a><a id="3792" href="foundation.truncations.html#3792" class="Bound">l2</a> <a id="3795" class="Symbol">:</a> <a id="3797" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3802" class="Symbol">}</a> <a id="3804" class="Symbol">(</a><a id="3805" href="foundation.truncations.html#3805" class="Bound">B</a> <a id="3807" class="Symbol">:</a> <a id="3809" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="3820" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3822" href="foundation.truncations.html#3021" class="Bound">A</a> <a id="3824" class="Symbol">→</a> <a id="3826" href="foundation-core.truncated-types.html#1651" class="Function">Truncated-Type</a> <a id="3841" href="foundation.truncations.html#3792" class="Bound">l2</a> <a id="3844" href="foundation.truncations.html#3013" class="Bound">k</a><a id="3845" class="Symbol">)</a> <a id="3847" class="Symbol">→</a>
    <a id="3853" class="Symbol">((</a><a id="3855" href="foundation.truncations.html#3855" class="Bound">x</a> <a id="3857" class="Symbol">:</a> <a id="3859" href="foundation.truncations.html#3021" class="Bound">A</a><a id="3860" class="Symbol">)</a> <a id="3862" class="Symbol">→</a> <a id="3864" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="3884" class="Symbol">(</a><a id="3885" href="foundation.truncations.html#3805" class="Bound">B</a> <a id="3887" class="Symbol">(</a><a id="3888" href="foundation.truncations.html#1272" class="Postulate">unit-trunc</a> <a id="3899" href="foundation.truncations.html#3855" class="Bound">x</a><a id="3900" class="Symbol">)))</a> <a id="3904" class="Symbol">→</a>
    <a id="3910" class="Symbol">(</a><a id="3911" href="foundation.truncations.html#3911" class="Bound">x</a> <a id="3913" class="Symbol">:</a> <a id="3915" href="foundation.truncations.html#984" class="Postulate">type-trunc</a> <a id="3926" href="foundation.truncations.html#3013" class="Bound">k</a> <a id="3928" href="foundation.truncations.html#3021" class="Bound">A</a><a id="3929" class="Symbol">)</a> <a id="3931" class="Symbol">→</a> <a id="3933" href="foundation-core.truncated-types.html#1786" class="Function">type-Truncated-Type</a> <a id="3953" class="Symbol">(</a><a id="3954" href="foundation.truncations.html#3805" class="Bound">B</a> <a id="3956" href="foundation.truncations.html#3911" class="Bound">x</a><a id="3957" class="Symbol">)</a>
  <a id="3961" href="foundation.truncations.html#3744" class="Function">apply-dependent-universal-property-trunc</a> <a id="4002" href="foundation.truncations.html#4002" class="Bound">B</a> <a id="4004" class="Symbol">=</a>
    <a id="4010" href="foundation-core.equivalences.html#5022" class="Function">map-inv-equiv</a> <a id="4024" class="Symbol">(</a><a id="4025" href="foundation.truncations.html#3335" class="Function">equiv-dependent-universal-property-trunc</a> <a id="4066" href="foundation.truncations.html#4002" class="Bound">B</a><a id="4067" class="Symbol">)</a>
</pre>