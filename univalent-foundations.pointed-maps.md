# Pointed maps

<pre class="Agda"><a id="25" class="Symbol">{-#</a> <a id="29" class="Keyword">OPTIONS</a> <a id="37" class="Pragma">--without-K</a> <a id="49" class="Pragma">--exact-split</a> <a id="63" class="Symbol">#-}</a>

<a id="68" class="Keyword">module</a> <a id="75" href="univalent-foundations.pointed-maps.html" class="Module">univalent-foundations.pointed-maps</a> <a id="110" class="Keyword">where</a>

<a id="117" class="Keyword">open</a> <a id="122" class="Keyword">import</a> <a id="129" href="foundation.constant-maps.html" class="Module">foundation.constant-maps</a> <a id="154" class="Keyword">using</a> <a id="160" class="Symbol">(</a><a id="161" href="foundation-core.constant-maps.html#203" class="Function">const</a><a id="166" class="Symbol">)</a>
<a id="168" class="Keyword">open</a> <a id="173" class="Keyword">import</a> <a id="180" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="212" class="Keyword">using</a> <a id="218" class="Symbol">(</a><a id="219" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a><a id="220" class="Symbol">;</a> <a id="222" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a><a id="226" class="Symbol">;</a> <a id="228" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a><a id="231" class="Symbol">;</a> <a id="233" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a><a id="236" class="Symbol">)</a>
<a id="238" class="Keyword">open</a> <a id="243" class="Keyword">import</a> <a id="250" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="271" class="Keyword">using</a> <a id="277" class="Symbol">(</a><a id="278" href="foundation-core.functions.html#407" class="Function Operator">_∘_</a><a id="281" class="Symbol">;</a> <a id="283" href="foundation-core.functions.html#309" class="Function">id</a><a id="285" class="Symbol">)</a>
<a id="287" class="Keyword">open</a> <a id="292" class="Keyword">import</a> <a id="299" href="foundation.identity-types.html" class="Module">foundation.identity-types</a> <a id="325" class="Keyword">using</a> <a id="331" class="Symbol">(</a><a id="332" href="foundation-core.identity-types.html#641" class="Datatype">Id</a><a id="334" class="Symbol">;</a> <a id="336" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a><a id="340" class="Symbol">;</a> <a id="342" href="foundation-core.identity-types.html#4584" class="Function">tr</a><a id="344" class="Symbol">;</a> <a id="346" href="foundation-core.identity-types.html#1552" class="Function">inv</a><a id="349" class="Symbol">;</a> <a id="351" href="foundation-core.identity-types.html#7971" class="Function">apd</a><a id="354" class="Symbol">;</a> <a id="356" href="foundation-core.identity-types.html#1239" class="Function Operator">_∙_</a><a id="359" class="Symbol">;</a> <a id="361" href="foundation-core.identity-types.html#2853" class="Function">ap</a><a id="363" class="Symbol">)</a>
<a id="365" class="Keyword">open</a> <a id="370" class="Keyword">import</a> <a id="377" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="404" class="Keyword">using</a> <a id="410" class="Symbol">(</a><a id="411" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="416" class="Symbol">;</a> <a id="418" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="420" class="Symbol">;</a> <a id="422" href="Agda.Primitive.html#810" class="Primitive Operator">_⊔_</a><a id="425" class="Symbol">)</a>
<a id="427" class="Keyword">open</a> <a id="432" class="Keyword">import</a> <a id="439" href="univalent-foundations.pointed-dependent-functions.html" class="Module">univalent-foundations.pointed-dependent-functions</a> <a id="489" class="Keyword">using</a>
  <a id="497" class="Symbol">(</a> <a id="499" href="univalent-foundations.pointed-dependent-functions.html#824" class="Function">pointed-Π</a><a id="508" class="Symbol">;</a> <a id="510" href="univalent-foundations.pointed-dependent-functions.html#988" class="Function">function-pointed-Π</a><a id="528" class="Symbol">;</a> <a id="530" href="univalent-foundations.pointed-dependent-functions.html#1109" class="Function">preserves-point-function-pointed-Π</a><a id="564" class="Symbol">)</a>
<a id="566" class="Keyword">open</a> <a id="571" class="Keyword">import</a> <a id="578" href="univalent-foundations.pointed-families-of-types.html" class="Module">univalent-foundations.pointed-families-of-types</a> <a id="626" class="Keyword">using</a>
  <a id="634" class="Symbol">(</a> <a id="636" href="univalent-foundations.pointed-families-of-types.html#689" class="Function">Pointed-Fam</a><a id="647" class="Symbol">;</a> <a id="649" href="univalent-foundations.pointed-families-of-types.html#936" class="Function">fam-Pointed-Fam</a><a id="664" class="Symbol">;</a> <a id="666" href="univalent-foundations.pointed-families-of-types.html#1011" class="Function">pt-Pointed-Fam</a><a id="680" class="Symbol">;</a> <a id="682" href="univalent-foundations.pointed-families-of-types.html#1186" class="Function">constant-Pointed-Fam</a><a id="702" class="Symbol">)</a>
<a id="704" class="Keyword">open</a> <a id="709" class="Keyword">import</a> <a id="716" href="univalent-foundations.pointed-types.html" class="Module">univalent-foundations.pointed-types</a> <a id="752" class="Keyword">using</a>
  <a id="760" class="Symbol">(</a> <a id="762" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a><a id="774" class="Symbol">;</a> <a id="776" href="univalent-foundations.pointed-types.html#363" class="Function">type-Pointed-Type</a><a id="793" class="Symbol">;</a> <a id="795" href="univalent-foundations.pointed-types.html#421" class="Function">pt-Pointed-Type</a><a id="810" class="Symbol">)</a>
</pre>
## Idea

A pointed map from a pointed type `A` to a pointed type `B` is a base point preserving function from `A` to `B`.

<pre class="Agda"><a id="948" class="Keyword">module</a> <a id="955" href="univalent-foundations.pointed-maps.html#955" class="Module">_</a>
  <a id="959" class="Symbol">{</a><a id="960" href="univalent-foundations.pointed-maps.html#960" class="Bound">l1</a> <a id="963" href="univalent-foundations.pointed-maps.html#963" class="Bound">l2</a> <a id="966" class="Symbol">:</a> <a id="968" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="973" class="Symbol">}</a>
  <a id="977" class="Keyword">where</a>

  <a id="986" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">_→*_</a> <a id="991" class="Symbol">:</a> <a id="993" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1006" href="univalent-foundations.pointed-maps.html#960" class="Bound">l1</a> <a id="1009" class="Symbol">→</a> <a id="1011" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1024" href="univalent-foundations.pointed-maps.html#963" class="Bound">l2</a> <a id="1027" class="Symbol">→</a> <a id="1029" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1032" class="Symbol">(</a><a id="1033" href="univalent-foundations.pointed-maps.html#960" class="Bound">l1</a> <a id="1036" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="1038" href="univalent-foundations.pointed-maps.html#963" class="Bound">l2</a><a id="1040" class="Symbol">)</a>
  <a id="1044" href="univalent-foundations.pointed-maps.html#1044" class="Bound">A</a> <a id="1046" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="1049" href="univalent-foundations.pointed-maps.html#1049" class="Bound">B</a> <a id="1051" class="Symbol">=</a> <a id="1053" href="univalent-foundations.pointed-dependent-functions.html#824" class="Function">pointed-Π</a> <a id="1063" href="univalent-foundations.pointed-maps.html#1044" class="Bound">A</a> <a id="1065" class="Symbol">(</a><a id="1066" href="univalent-foundations.pointed-families-of-types.html#1186" class="Function">constant-Pointed-Fam</a> <a id="1087" href="univalent-foundations.pointed-maps.html#1044" class="Bound">A</a> <a id="1089" href="univalent-foundations.pointed-maps.html#1049" class="Bound">B</a><a id="1090" class="Symbol">)</a>

  <a id="1095" href="univalent-foundations.pointed-maps.html#1095" class="Function Operator">[_→*_]</a> <a id="1102" class="Symbol">:</a> <a id="1104" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1117" href="univalent-foundations.pointed-maps.html#960" class="Bound">l1</a> <a id="1120" class="Symbol">→</a> <a id="1122" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1135" href="univalent-foundations.pointed-maps.html#963" class="Bound">l2</a> <a id="1138" class="Symbol">→</a> <a id="1140" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1153" class="Symbol">(</a><a id="1154" href="univalent-foundations.pointed-maps.html#960" class="Bound">l1</a> <a id="1157" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="1159" href="univalent-foundations.pointed-maps.html#963" class="Bound">l2</a><a id="1161" class="Symbol">)</a>
  <a id="1165" href="univalent-foundations.pointed-maps.html#1095" class="Function Operator">[</a> <a id="1167" href="univalent-foundations.pointed-maps.html#1167" class="Bound">A</a> <a id="1169" href="univalent-foundations.pointed-maps.html#1095" class="Function Operator">→*</a> <a id="1172" href="univalent-foundations.pointed-maps.html#1172" class="Bound">B</a> <a id="1174" href="univalent-foundations.pointed-maps.html#1095" class="Function Operator">]</a> <a id="1176" class="Symbol">=</a>
    <a id="1182" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a>
      <a id="1193" class="Symbol">(</a> <a id="1195" href="univalent-foundations.pointed-maps.html#1167" class="Bound">A</a> <a id="1197" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="1200" href="univalent-foundations.pointed-maps.html#1172" class="Bound">B</a><a id="1201" class="Symbol">)</a>
      <a id="1209" class="Symbol">(</a> <a id="1211" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a>
        <a id="1224" class="Symbol">(</a> <a id="1226" href="foundation-core.constant-maps.html#203" class="Function">const</a> <a id="1232" class="Symbol">(</a><a id="1233" href="univalent-foundations.pointed-types.html#363" class="Function">type-Pointed-Type</a> <a id="1251" href="univalent-foundations.pointed-maps.html#1167" class="Bound">A</a><a id="1252" class="Symbol">)</a> <a id="1254" class="Symbol">(</a><a id="1255" href="univalent-foundations.pointed-types.html#363" class="Function">type-Pointed-Type</a> <a id="1273" href="univalent-foundations.pointed-maps.html#1172" class="Bound">B</a><a id="1274" class="Symbol">)</a> <a id="1276" class="Symbol">(</a><a id="1277" href="univalent-foundations.pointed-types.html#421" class="Function">pt-Pointed-Type</a> <a id="1293" href="univalent-foundations.pointed-maps.html#1172" class="Bound">B</a><a id="1294" class="Symbol">))</a>
        <a id="1305" class="Symbol">(</a> <a id="1307" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a><a id="1311" class="Symbol">))</a>

<a id="1315" class="Keyword">module</a> <a id="1322" href="univalent-foundations.pointed-maps.html#1322" class="Module">_</a>
  <a id="1326" class="Symbol">{</a><a id="1327" href="univalent-foundations.pointed-maps.html#1327" class="Bound">l1</a> <a id="1330" href="univalent-foundations.pointed-maps.html#1330" class="Bound">l2</a> <a id="1333" class="Symbol">:</a> <a id="1335" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1340" class="Symbol">}</a> <a id="1342" class="Symbol">(</a><a id="1343" href="univalent-foundations.pointed-maps.html#1343" class="Bound">A</a> <a id="1345" class="Symbol">:</a> <a id="1347" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1360" href="univalent-foundations.pointed-maps.html#1327" class="Bound">l1</a><a id="1362" class="Symbol">)</a> <a id="1364" class="Symbol">(</a><a id="1365" href="univalent-foundations.pointed-maps.html#1365" class="Bound">B</a> <a id="1367" class="Symbol">:</a> <a id="1369" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1382" href="univalent-foundations.pointed-maps.html#1330" class="Bound">l2</a><a id="1384" class="Symbol">)</a>
  <a id="1388" class="Keyword">where</a>
  
  <a id="1399" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="1415" class="Symbol">:</a> <a id="1417" href="univalent-foundations.pointed-maps.html#1343" class="Bound">A</a> <a id="1419" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="1422" href="univalent-foundations.pointed-maps.html#1365" class="Bound">B</a> <a id="1424" class="Symbol">→</a> <a id="1426" href="univalent-foundations.pointed-types.html#363" class="Function">type-Pointed-Type</a> <a id="1444" href="univalent-foundations.pointed-maps.html#1343" class="Bound">A</a> <a id="1446" class="Symbol">→</a> <a id="1448" href="univalent-foundations.pointed-types.html#363" class="Function">type-Pointed-Type</a> <a id="1466" href="univalent-foundations.pointed-maps.html#1365" class="Bound">B</a>
  <a id="1470" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="1486" href="univalent-foundations.pointed-maps.html#1486" class="Bound">f</a> <a id="1488" class="Symbol">=</a> <a id="1490" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="1494" href="univalent-foundations.pointed-maps.html#1486" class="Bound">f</a>

  <a id="1499" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="1531" class="Symbol">:</a>
    <a id="1537" class="Symbol">(</a><a id="1538" href="univalent-foundations.pointed-maps.html#1538" class="Bound">f</a> <a id="1540" class="Symbol">:</a> <a id="1542" href="univalent-foundations.pointed-maps.html#1343" class="Bound">A</a> <a id="1544" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="1547" href="univalent-foundations.pointed-maps.html#1365" class="Bound">B</a><a id="1548" class="Symbol">)</a> <a id="1550" class="Symbol">→</a>
    <a id="1556" href="foundation-core.identity-types.html#641" class="Datatype">Id</a> <a id="1559" class="Symbol">(</a><a id="1560" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="1576" href="univalent-foundations.pointed-maps.html#1538" class="Bound">f</a> <a id="1578" class="Symbol">(</a><a id="1579" href="univalent-foundations.pointed-types.html#421" class="Function">pt-Pointed-Type</a> <a id="1595" href="univalent-foundations.pointed-maps.html#1343" class="Bound">A</a><a id="1596" class="Symbol">))</a> <a id="1599" class="Symbol">(</a><a id="1600" href="univalent-foundations.pointed-types.html#421" class="Function">pt-Pointed-Type</a> <a id="1616" href="univalent-foundations.pointed-maps.html#1365" class="Bound">B</a><a id="1617" class="Symbol">)</a>
  <a id="1621" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="1653" href="univalent-foundations.pointed-maps.html#1653" class="Bound">f</a> <a id="1655" class="Symbol">=</a> <a id="1657" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="1661" href="univalent-foundations.pointed-maps.html#1653" class="Bound">f</a>

<a id="1664" class="Keyword">module</a> <a id="1671" href="univalent-foundations.pointed-maps.html#1671" class="Module">_</a>
  <a id="1675" class="Symbol">{</a><a id="1676" href="univalent-foundations.pointed-maps.html#1676" class="Bound">l1</a> <a id="1679" href="univalent-foundations.pointed-maps.html#1679" class="Bound">l2</a> <a id="1682" href="univalent-foundations.pointed-maps.html#1682" class="Bound">l3</a> <a id="1685" class="Symbol">:</a> <a id="1687" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1692" class="Symbol">}</a> <a id="1694" class="Symbol">(</a><a id="1695" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="1697" class="Symbol">:</a> <a id="1699" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1712" href="univalent-foundations.pointed-maps.html#1676" class="Bound">l1</a><a id="1714" class="Symbol">)</a> <a id="1716" class="Symbol">(</a><a id="1717" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="1719" class="Symbol">:</a> <a id="1721" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="1734" href="univalent-foundations.pointed-maps.html#1679" class="Bound">l2</a><a id="1736" class="Symbol">)</a>
  <a id="1740" class="Symbol">(</a><a id="1741" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a> <a id="1743" class="Symbol">:</a> <a id="1745" href="univalent-foundations.pointed-families-of-types.html#689" class="Function">Pointed-Fam</a> <a id="1757" href="univalent-foundations.pointed-maps.html#1682" class="Bound">l3</a> <a id="1760" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a><a id="1761" class="Symbol">)</a> <a id="1763" class="Symbol">(</a><a id="1764" href="univalent-foundations.pointed-maps.html#1764" class="Bound">f</a> <a id="1766" class="Symbol">:</a> <a id="1768" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="1770" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="1773" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a><a id="1774" class="Symbol">)</a>
  <a id="1778" class="Keyword">where</a>

  <a id="1787" href="univalent-foundations.pointed-maps.html#1787" class="Function">precomp-Pointed-Fam</a> <a id="1807" class="Symbol">:</a> <a id="1809" href="univalent-foundations.pointed-families-of-types.html#689" class="Function">Pointed-Fam</a> <a id="1821" href="univalent-foundations.pointed-maps.html#1682" class="Bound">l3</a> <a id="1824" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a>
  <a id="1828" href="univalent-foundations.pointed-maps.html#1787" class="Function">precomp-Pointed-Fam</a> <a id="1848" class="Symbol">=</a>
    <a id="1854" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a>
      <a id="1865" class="Symbol">(</a> <a id="1867" href="univalent-foundations.pointed-families-of-types.html#936" class="Function">fam-Pointed-Fam</a> <a id="1883" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="1885" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a> <a id="1887" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="1889" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="1905" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="1907" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="1909" href="univalent-foundations.pointed-maps.html#1764" class="Bound">f</a><a id="1910" class="Symbol">)</a>
      <a id="1918" class="Symbol">(</a> <a id="1920" href="foundation-core.identity-types.html#4584" class="Function">tr</a>
        <a id="1931" class="Symbol">(</a> <a id="1933" href="univalent-foundations.pointed-families-of-types.html#936" class="Function">fam-Pointed-Fam</a> <a id="1949" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="1951" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a><a id="1952" class="Symbol">)</a>
        <a id="1962" class="Symbol">(</a> <a id="1964" href="foundation-core.identity-types.html#1552" class="Function">inv</a> <a id="1968" class="Symbol">(</a><a id="1969" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="2001" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="2003" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2005" href="univalent-foundations.pointed-maps.html#1764" class="Bound">f</a><a id="2006" class="Symbol">))</a>
        <a id="2017" class="Symbol">(</a> <a id="2019" href="univalent-foundations.pointed-families-of-types.html#1011" class="Function">pt-Pointed-Fam</a> <a id="2034" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2036" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a><a id="2037" class="Symbol">))</a>

  <a id="2043" href="univalent-foundations.pointed-maps.html#2043" class="Function">precomp-pointed-Π</a> <a id="2061" class="Symbol">:</a> <a id="2063" href="univalent-foundations.pointed-dependent-functions.html#824" class="Function">pointed-Π</a> <a id="2073" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2075" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a> <a id="2077" class="Symbol">→</a> <a id="2079" href="univalent-foundations.pointed-dependent-functions.html#824" class="Function">pointed-Π</a> <a id="2089" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="2091" href="univalent-foundations.pointed-maps.html#1787" class="Function">precomp-Pointed-Fam</a>
  <a id="2113" href="univalent-foundations.pointed-maps.html#2043" class="Function">precomp-pointed-Π</a> <a id="2131" href="univalent-foundations.pointed-maps.html#2131" class="Bound">g</a> <a id="2133" class="Symbol">=</a>
    <a id="2139" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a>
      <a id="2150" class="Symbol">(</a> <a id="2152" class="Symbol">λ</a> <a id="2154" href="univalent-foundations.pointed-maps.html#2154" class="Bound">x</a> <a id="2156" class="Symbol">→</a> <a id="2158" href="univalent-foundations.pointed-dependent-functions.html#988" class="Function">function-pointed-Π</a> <a id="2177" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2179" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a> <a id="2181" href="univalent-foundations.pointed-maps.html#2131" class="Bound">g</a> <a id="2183" class="Symbol">(</a><a id="2184" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="2200" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="2202" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2204" href="univalent-foundations.pointed-maps.html#1764" class="Bound">f</a> <a id="2206" href="univalent-foundations.pointed-maps.html#2154" class="Bound">x</a><a id="2207" class="Symbol">))</a>
      <a id="2216" class="Symbol">(</a> <a id="2218" class="Symbol">(</a> <a id="2220" href="foundation-core.identity-types.html#1552" class="Function">inv</a>
          <a id="2234" class="Symbol">(</a> <a id="2236" href="foundation-core.identity-types.html#7971" class="Function">apd</a>
            <a id="2252" class="Symbol">(</a> <a id="2254" href="univalent-foundations.pointed-dependent-functions.html#988" class="Function">function-pointed-Π</a> <a id="2273" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2275" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a> <a id="2277" href="univalent-foundations.pointed-maps.html#2131" class="Bound">g</a><a id="2278" class="Symbol">)</a>
            <a id="2292" class="Symbol">(</a> <a id="2294" href="foundation-core.identity-types.html#1552" class="Function">inv</a> <a id="2298" class="Symbol">(</a><a id="2299" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="2331" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="2333" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2335" href="univalent-foundations.pointed-maps.html#1764" class="Bound">f</a><a id="2336" class="Symbol">))))</a> <a id="2341" href="foundation-core.identity-types.html#1239" class="Function Operator">∙</a>
        <a id="2351" class="Symbol">(</a> <a id="2353" href="foundation-core.identity-types.html#2853" class="Function">ap</a>
          <a id="2366" class="Symbol">(</a> <a id="2368" href="foundation-core.identity-types.html#4584" class="Function">tr</a>
            <a id="2383" class="Symbol">(</a> <a id="2385" href="univalent-foundations.pointed-families-of-types.html#936" class="Function">fam-Pointed-Fam</a> <a id="2401" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2403" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a><a id="2404" class="Symbol">)</a>
            <a id="2418" class="Symbol">(</a> <a id="2420" href="foundation-core.identity-types.html#1552" class="Function">inv</a> <a id="2424" class="Symbol">(</a><a id="2425" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="2457" href="univalent-foundations.pointed-maps.html#1695" class="Bound">A</a> <a id="2459" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2461" href="univalent-foundations.pointed-maps.html#1764" class="Bound">f</a><a id="2462" class="Symbol">)))</a>
          <a id="2476" class="Symbol">(</a> <a id="2478" href="univalent-foundations.pointed-dependent-functions.html#1109" class="Function">preserves-point-function-pointed-Π</a> <a id="2513" href="univalent-foundations.pointed-maps.html#1717" class="Bound">B</a> <a id="2515" href="univalent-foundations.pointed-maps.html#1741" class="Bound">C</a> <a id="2517" href="univalent-foundations.pointed-maps.html#2131" class="Bound">g</a><a id="2518" class="Symbol">)))</a>

<a id="2523" class="Keyword">module</a> <a id="2530" href="univalent-foundations.pointed-maps.html#2530" class="Module">_</a>
  <a id="2534" class="Symbol">{</a><a id="2535" href="univalent-foundations.pointed-maps.html#2535" class="Bound">l1</a> <a id="2538" href="univalent-foundations.pointed-maps.html#2538" class="Bound">l2</a> <a id="2541" href="univalent-foundations.pointed-maps.html#2541" class="Bound">l3</a> <a id="2544" class="Symbol">:</a> <a id="2546" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2551" class="Symbol">}</a> <a id="2553" class="Symbol">(</a><a id="2554" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2556" class="Symbol">:</a> <a id="2558" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="2571" href="univalent-foundations.pointed-maps.html#2535" class="Bound">l1</a><a id="2573" class="Symbol">)</a> <a id="2575" class="Symbol">(</a><a id="2576" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2578" class="Symbol">:</a> <a id="2580" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="2593" href="univalent-foundations.pointed-maps.html#2538" class="Bound">l2</a><a id="2595" class="Symbol">)</a>
  <a id="2599" class="Symbol">(</a><a id="2600" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a> <a id="2602" class="Symbol">:</a> <a id="2604" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="2617" href="univalent-foundations.pointed-maps.html#2541" class="Bound">l3</a><a id="2619" class="Symbol">)</a>
  <a id="2623" class="Keyword">where</a>

  <a id="2632" href="univalent-foundations.pointed-maps.html#2632" class="Function">precomp-pointed-map</a> <a id="2652" class="Symbol">:</a> <a id="2654" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2656" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="2659" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2661" class="Symbol">→</a> <a id="2663" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2665" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="2668" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a> <a id="2670" class="Symbol">→</a> <a id="2672" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2674" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="2677" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a>
  <a id="2681" href="univalent-foundations.pointed-maps.html#2632" class="Function">precomp-pointed-map</a> <a id="2701" href="univalent-foundations.pointed-maps.html#2701" class="Bound">f</a> <a id="2703" href="univalent-foundations.pointed-maps.html#2703" class="Bound">g</a> <a id="2705" class="Symbol">=</a>
    <a id="2711" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a>
      <a id="2722" class="Symbol">(</a> <a id="2724" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="2740" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2742" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a> <a id="2744" href="univalent-foundations.pointed-maps.html#2703" class="Bound">g</a> <a id="2746" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="2748" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="2764" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2766" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2768" href="univalent-foundations.pointed-maps.html#2701" class="Bound">f</a><a id="2769" class="Symbol">)</a>
      <a id="2777" class="Symbol">(</a> <a id="2779" class="Symbol">(</a> <a id="2781" href="foundation-core.identity-types.html#2853" class="Function">ap</a> <a id="2784" class="Symbol">(</a><a id="2785" href="univalent-foundations.pointed-maps.html#1399" class="Function">map-pointed-map</a> <a id="2801" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2803" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a> <a id="2805" href="univalent-foundations.pointed-maps.html#2703" class="Bound">g</a><a id="2806" class="Symbol">)</a> <a id="2808" class="Symbol">(</a><a id="2809" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="2841" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2843" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2845" href="univalent-foundations.pointed-maps.html#2701" class="Bound">f</a><a id="2846" class="Symbol">))</a> <a id="2849" href="foundation-core.identity-types.html#1239" class="Function Operator">∙</a>
        <a id="2859" class="Symbol">(</a> <a id="2861" href="univalent-foundations.pointed-maps.html#1499" class="Function">preserves-point-map-pointed-map</a> <a id="2893" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2895" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a> <a id="2897" href="univalent-foundations.pointed-maps.html#2703" class="Bound">g</a><a id="2898" class="Symbol">))</a>

  <a id="2904" href="univalent-foundations.pointed-maps.html#2904" class="Function">comp-pointed-map</a> <a id="2921" class="Symbol">:</a> <a id="2923" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2925" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="2928" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a> <a id="2930" class="Symbol">→</a> <a id="2932" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2934" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="2937" href="univalent-foundations.pointed-maps.html#2576" class="Bound">B</a> <a id="2939" class="Symbol">→</a> <a id="2941" href="univalent-foundations.pointed-maps.html#2554" class="Bound">A</a> <a id="2943" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="2946" href="univalent-foundations.pointed-maps.html#2600" class="Bound">C</a>
  <a id="2950" href="univalent-foundations.pointed-maps.html#2904" class="Function">comp-pointed-map</a> <a id="2967" href="univalent-foundations.pointed-maps.html#2967" class="Bound">g</a> <a id="2969" href="univalent-foundations.pointed-maps.html#2969" class="Bound">f</a> <a id="2971" class="Symbol">=</a> <a id="2973" href="univalent-foundations.pointed-maps.html#2632" class="Function">precomp-pointed-map</a> <a id="2993" href="univalent-foundations.pointed-maps.html#2969" class="Bound">f</a> <a id="2995" href="univalent-foundations.pointed-maps.html#2967" class="Bound">g</a>

<a id="2998" class="Keyword">module</a> <a id="3005" href="univalent-foundations.pointed-maps.html#3005" class="Module">_</a>
  <a id="3009" class="Symbol">{</a><a id="3010" href="univalent-foundations.pointed-maps.html#3010" class="Bound">l1</a> <a id="3013" class="Symbol">:</a> <a id="3015" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3020" class="Symbol">}</a> <a id="3022" class="Symbol">{</a><a id="3023" href="univalent-foundations.pointed-maps.html#3023" class="Bound">A</a> <a id="3025" class="Symbol">:</a> <a id="3027" href="univalent-foundations.pointed-types.html#228" class="Function">Pointed-Type</a> <a id="3040" href="univalent-foundations.pointed-maps.html#3010" class="Bound">l1</a><a id="3042" class="Symbol">}</a>
  <a id="3046" class="Keyword">where</a>

  <a id="3055" href="univalent-foundations.pointed-maps.html#3055" class="Function">id-pointed-map</a> <a id="3070" class="Symbol">:</a> <a id="3072" href="univalent-foundations.pointed-maps.html#3023" class="Bound">A</a> <a id="3074" href="univalent-foundations.pointed-maps.html#986" class="Function Operator">→*</a> <a id="3077" href="univalent-foundations.pointed-maps.html#3023" class="Bound">A</a>
  <a id="3081" href="univalent-foundations.pointed-maps.html#3055" class="Function">id-pointed-map</a> <a id="3096" class="Symbol">=</a> <a id="3098" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="3103" href="foundation-core.functions.html#309" class="Function">id</a> <a id="3106" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a>
</pre>