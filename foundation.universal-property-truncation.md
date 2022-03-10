# The universal property of truncations

<pre class="Agda"><a id="50" class="Symbol">{-#</a> <a id="54" class="Keyword">OPTIONS</a> <a id="62" class="Pragma">--without-K</a> <a id="74" class="Pragma">--exact-split</a> <a id="88" class="Symbol">#-}</a>

<a id="93" class="Keyword">module</a> <a id="100" href="foundation.universal-property-truncation.html" class="Module">foundation.universal-property-truncation</a> <a id="141" class="Keyword">where</a>

<a id="148" class="Keyword">open</a> <a id="153" class="Keyword">import</a> <a id="160" href="foundation.contractible-maps.html" class="Module">foundation.contractible-maps</a> <a id="189" class="Keyword">using</a>
  <a id="197" class="Symbol">(</a> <a id="199" href="foundation-core.contractible-maps.html#2368" class="Function">is-equiv-is-contr-map</a><a id="220" class="Symbol">;</a> <a id="222" href="foundation-core.contractible-maps.html#3850" class="Function">is-contr-map-is-equiv</a><a id="243" class="Symbol">)</a>
<a id="245" class="Keyword">open</a> <a id="250" class="Keyword">import</a> <a id="257" href="foundation.contractible-types.html" class="Module">foundation.contractible-types</a> <a id="287" class="Keyword">using</a>
  <a id="295" class="Symbol">(</a> <a id="297" href="foundation-core.contractible-types.html#925" class="Function">is-contr</a><a id="305" class="Symbol">;</a> <a id="307" href="foundation-core.contractible-types.html#3230" class="Function">is-contr-equiv</a><a id="321" class="Symbol">;</a> <a id="323" href="foundation-core.contractible-types.html#3739" class="Function">is-contr-equiv&#39;</a><a id="338" class="Symbol">;</a> <a id="340" href="foundation-core.contractible-types.html#1018" class="Function">center</a><a id="346" class="Symbol">)</a>
<a id="348" class="Keyword">open</a> <a id="353" class="Keyword">import</a> <a id="360" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="392" class="Keyword">using</a> <a id="398" class="Symbol">(</a><a id="399" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a><a id="400" class="Symbol">;</a> <a id="402" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a><a id="406" class="Symbol">;</a> <a id="408" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a><a id="411" class="Symbol">;</a> <a id="413" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a><a id="416" class="Symbol">;</a> <a id="418" href="foundation-core.dependent-pair-types.html#687" class="Function">ind-Σ</a><a id="423" class="Symbol">)</a>
<a id="425" class="Keyword">open</a> <a id="430" class="Keyword">import</a>
  <a id="439" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html" class="Module">foundation.distributivity-of-dependent-functions-over-dependent-pairs</a> <a id="509" class="Keyword">using</a>
  <a id="517" class="Symbol">(</a> <a id="519" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html#5106" class="Function">inv-distributive-Π-Σ</a><a id="539" class="Symbol">;</a> <a id="541" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html#2808" class="Function">map-distributive-Π-Σ</a><a id="561" class="Symbol">)</a>
<a id="563" class="Keyword">open</a> <a id="568" class="Keyword">import</a> <a id="575" href="foundation.equivalences.html" class="Module">foundation.equivalences</a> <a id="599" class="Keyword">using</a>
  <a id="607" class="Symbol">(</a> <a id="609" href="foundation-core.equivalences.html#1542" class="Function">is-equiv</a><a id="617" class="Symbol">;</a> <a id="619" href="foundation-core.equivalences.html#12773" class="Function">is-equiv-equiv</a><a id="633" class="Symbol">;</a> <a id="635" href="foundation-core.equivalences.html#4173" class="Function">map-inv-is-equiv</a><a id="651" class="Symbol">;</a> <a id="653" href="foundation.equivalences.html#9064" class="Function">is-equiv-precomp-is-equiv</a><a id="678" class="Symbol">;</a>
    <a id="684" href="foundation-core.equivalences.html#2309" class="Function">is-equiv-id</a><a id="695" class="Symbol">;</a> <a id="697" href="foundation-core.equivalences.html#1607" class="Function Operator">_≃_</a><a id="700" class="Symbol">;</a> <a id="702" href="foundation-core.equivalences.html#1807" class="Function">map-equiv</a><a id="711" class="Symbol">;</a> <a id="713" href="foundation-core.equivalences.html#1862" class="Function">is-equiv-map-equiv</a><a id="731" class="Symbol">)</a>
<a id="733" class="Keyword">open</a> <a id="738" class="Keyword">import</a> <a id="745" href="foundation.function-extensionality.html" class="Module">foundation.function-extensionality</a> <a id="780" class="Keyword">using</a> <a id="786" class="Symbol">(</a><a id="787" href="foundation.function-extensionality.html#1283" class="Function">equiv-funext</a><a id="799" class="Symbol">)</a>
<a id="801" class="Keyword">open</a> <a id="806" class="Keyword">import</a> <a id="813" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="834" class="Keyword">using</a> <a id="840" class="Symbol">(</a><a id="841" href="foundation-core.functions.html#925" class="Function">precomp</a><a id="848" class="Symbol">;</a> <a id="850" href="foundation-core.functions.html#407" class="Function Operator">_∘_</a><a id="853" class="Symbol">;</a> <a id="855" href="foundation-core.functions.html#309" class="Function">id</a><a id="857" class="Symbol">)</a>
<a id="859" class="Keyword">open</a> <a id="864" class="Keyword">import</a> <a id="871" href="foundation.functoriality-dependent-pair-types.html" class="Module">foundation.functoriality-dependent-pair-types</a> <a id="917" class="Keyword">using</a>
  <a id="925" class="Symbol">(</a> <a id="927" href="foundation-core.functoriality-dependent-pair-types.html#6804" class="Function">equiv-tot</a><a id="936" class="Symbol">;</a> <a id="938" href="foundation-core.functoriality-dependent-pair-types.html#10750" class="Function">is-fiberwise-equiv-is-equiv-map-Σ</a><a id="971" class="Symbol">)</a>
<a id="973" class="Keyword">open</a> <a id="978" class="Keyword">import</a> <a id="985" href="foundation.homotopies.html" class="Module">foundation.homotopies</a> <a id="1007" class="Keyword">using</a> <a id="1013" class="Symbol">(</a><a id="1014" href="foundation-core.homotopies.html#467" class="Function Operator">_~_</a><a id="1017" class="Symbol">)</a>
<a id="1019" class="Keyword">open</a> <a id="1024" class="Keyword">import</a> <a id="1031" href="foundation.identity-types.html" class="Module">foundation.identity-types</a> <a id="1057" class="Keyword">using</a> <a id="1063" class="Symbol">(</a><a id="1064" href="foundation-core.identity-types.html#641" class="Datatype">Id</a><a id="1066" class="Symbol">;</a> <a id="1068" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a><a id="1072" class="Symbol">;</a> <a id="1074" href="foundation-core.identity-types.html#1552" class="Function">inv</a><a id="1077" class="Symbol">)</a>
<a id="1079" class="Keyword">open</a> <a id="1084" class="Keyword">import</a> <a id="1091" href="foundation.sections.html" class="Module">foundation.sections</a> <a id="1111" class="Keyword">using</a> <a id="1117" class="Symbol">(</a><a id="1118" href="foundation-core.sections.html#521" class="Function">sec</a><a id="1121" class="Symbol">)</a>
<a id="1123" class="Keyword">open</a> <a id="1128" class="Keyword">import</a> <a id="1135" href="foundation.truncated-types.html" class="Module">foundation.truncated-types</a> <a id="1162" class="Keyword">using</a>
  <a id="1170" class="Symbol">(</a> <a id="1172" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a><a id="1189" class="Symbol">;</a> <a id="1191" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a><a id="1210" class="Symbol">;</a> <a id="1212" href="foundation.truncated-types.html#3516" class="Function">type-hom-Truncated-Type</a><a id="1235" class="Symbol">;</a>
    <a id="1241" href="foundation-core.truncated-types.html#6052" class="Function">Σ-Truncated-Type</a><a id="1257" class="Symbol">;</a> <a id="1259" href="foundation-core.truncated-types.html#6435" class="Function">fib-Truncated-Type</a><a id="1277" class="Symbol">;</a> <a id="1279" href="foundation-core.truncated-types.html#1466" class="Function">is-trunc</a><a id="1287" class="Symbol">)</a>
<a id="1289" class="Keyword">open</a> <a id="1294" class="Keyword">import</a> <a id="1301" href="foundation.truncation-levels.html" class="Module">foundation.truncation-levels</a> <a id="1330" class="Keyword">using</a> <a id="1336" class="Symbol">(</a><a id="1337" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1338" class="Symbol">)</a>
<a id="1340" class="Keyword">open</a> <a id="1345" class="Keyword">import</a> <a id="1352" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="1379" class="Keyword">using</a> <a id="1385" class="Symbol">(</a><a id="1386" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="1388" class="Symbol">;</a> <a id="1390" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1395" class="Symbol">;</a> <a id="1397" href="Agda.Primitive.html#810" class="Primitive Operator">_⊔_</a><a id="1400" class="Symbol">;</a> <a id="1402" href="Agda.Primitive.html#780" class="Primitive">lsuc</a><a id="1406" class="Symbol">)</a>
</pre>
## Idea

We say that a map `f : A → B` into a `k`-truncated type `B` is a `k`-truncation of `A` -- or that it satisfies the universal property of the `k`-truncation of `A` -- if any map `g : A → C` into a `k`-truncated type `C` extends uniquely along `f` to a map `B → C`.

## Definition

### The condition on a map to be a truncation

<pre class="Agda"><a id="precomp-Trunc"></a><a id="1757" href="foundation.universal-property-truncation.html#1757" class="Function">precomp-Trunc</a> <a id="1771" class="Symbol">:</a>
  <a id="1775" class="Symbol">{</a><a id="1776" href="foundation.universal-property-truncation.html#1776" class="Bound">l1</a> <a id="1779" href="foundation.universal-property-truncation.html#1779" class="Bound">l2</a> <a id="1782" href="foundation.universal-property-truncation.html#1782" class="Bound">l3</a> <a id="1785" class="Symbol">:</a> <a id="1787" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="1792" class="Symbol">}</a> <a id="1794" class="Symbol">{</a><a id="1795" href="foundation.universal-property-truncation.html#1795" class="Bound">k</a> <a id="1797" class="Symbol">:</a> <a id="1799" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="1800" class="Symbol">}</a> <a id="1802" class="Symbol">{</a><a id="1803" href="foundation.universal-property-truncation.html#1803" class="Bound">A</a> <a id="1805" class="Symbol">:</a> <a id="1807" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1810" href="foundation.universal-property-truncation.html#1776" class="Bound">l1</a><a id="1812" class="Symbol">}</a> <a id="1814" class="Symbol">{</a><a id="1815" href="foundation.universal-property-truncation.html#1815" class="Bound">B</a> <a id="1817" class="Symbol">:</a> <a id="1819" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1822" href="foundation.universal-property-truncation.html#1779" class="Bound">l2</a><a id="1824" class="Symbol">}</a> <a id="1826" class="Symbol">(</a><a id="1827" href="foundation.universal-property-truncation.html#1827" class="Bound">f</a> <a id="1829" class="Symbol">:</a> <a id="1831" href="foundation.universal-property-truncation.html#1803" class="Bound">A</a> <a id="1833" class="Symbol">→</a> <a id="1835" href="foundation.universal-property-truncation.html#1815" class="Bound">B</a><a id="1836" class="Symbol">)</a>
  <a id="1840" class="Symbol">(</a><a id="1841" href="foundation.universal-property-truncation.html#1841" class="Bound">C</a> <a id="1843" class="Symbol">:</a> <a id="1845" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="1863" href="foundation.universal-property-truncation.html#1782" class="Bound">l3</a> <a id="1866" href="foundation.universal-property-truncation.html#1795" class="Bound">k</a><a id="1867" class="Symbol">)</a> <a id="1869" class="Symbol">→</a>
  <a id="1873" class="Symbol">(</a><a id="1874" href="foundation.universal-property-truncation.html#1815" class="Bound">B</a> <a id="1876" class="Symbol">→</a> <a id="1878" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="1898" href="foundation.universal-property-truncation.html#1841" class="Bound">C</a><a id="1899" class="Symbol">)</a> <a id="1901" class="Symbol">→</a> <a id="1903" class="Symbol">(</a><a id="1904" href="foundation.universal-property-truncation.html#1803" class="Bound">A</a> <a id="1906" class="Symbol">→</a> <a id="1908" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="1928" href="foundation.universal-property-truncation.html#1841" class="Bound">C</a><a id="1929" class="Symbol">)</a>
<a id="1931" href="foundation.universal-property-truncation.html#1757" class="Function">precomp-Trunc</a> <a id="1945" href="foundation.universal-property-truncation.html#1945" class="Bound">f</a> <a id="1947" href="foundation.universal-property-truncation.html#1947" class="Bound">C</a> <a id="1949" class="Symbol">=</a> <a id="1951" href="foundation-core.functions.html#925" class="Function">precomp</a> <a id="1959" href="foundation.universal-property-truncation.html#1945" class="Bound">f</a> <a id="1961" class="Symbol">(</a><a id="1962" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="1982" href="foundation.universal-property-truncation.html#1947" class="Bound">C</a><a id="1983" class="Symbol">)</a>

<a id="is-truncation"></a><a id="1986" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="2000" class="Symbol">:</a>
  <a id="2004" class="Symbol">{</a><a id="2005" href="foundation.universal-property-truncation.html#2005" class="Bound">l1</a> <a id="2008" href="foundation.universal-property-truncation.html#2008" class="Bound">l2</a> <a id="2011" class="Symbol">:</a> <a id="2013" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2018" class="Symbol">}</a> <a id="2020" class="Symbol">(</a><a id="2021" href="foundation.universal-property-truncation.html#2021" class="Bound">l</a> <a id="2023" class="Symbol">:</a> <a id="2025" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2030" class="Symbol">)</a> <a id="2032" class="Symbol">{</a><a id="2033" href="foundation.universal-property-truncation.html#2033" class="Bound">k</a> <a id="2035" class="Symbol">:</a> <a id="2037" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="2038" class="Symbol">}</a> <a id="2040" class="Symbol">{</a><a id="2041" href="foundation.universal-property-truncation.html#2041" class="Bound">A</a> <a id="2043" class="Symbol">:</a> <a id="2045" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2048" href="foundation.universal-property-truncation.html#2005" class="Bound">l1</a><a id="2050" class="Symbol">}</a>
  <a id="2054" class="Symbol">(</a><a id="2055" href="foundation.universal-property-truncation.html#2055" class="Bound">B</a> <a id="2057" class="Symbol">:</a> <a id="2059" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="2077" href="foundation.universal-property-truncation.html#2008" class="Bound">l2</a> <a id="2080" href="foundation.universal-property-truncation.html#2033" class="Bound">k</a><a id="2081" class="Symbol">)</a> <a id="2083" class="Symbol">→</a> <a id="2085" class="Symbol">(</a><a id="2086" href="foundation.universal-property-truncation.html#2041" class="Bound">A</a> <a id="2088" class="Symbol">→</a> <a id="2090" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="2110" href="foundation.universal-property-truncation.html#2055" class="Bound">B</a><a id="2111" class="Symbol">)</a> <a id="2113" class="Symbol">→</a>
  <a id="2117" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2120" class="Symbol">(</a><a id="2121" href="foundation.universal-property-truncation.html#2005" class="Bound">l1</a> <a id="2124" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2126" href="foundation.universal-property-truncation.html#2008" class="Bound">l2</a> <a id="2129" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2131" href="Agda.Primitive.html#780" class="Primitive">lsuc</a> <a id="2136" href="foundation.universal-property-truncation.html#2021" class="Bound">l</a><a id="2137" class="Symbol">)</a>
<a id="2139" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="2153" href="foundation.universal-property-truncation.html#2153" class="Bound">l</a> <a id="2155" class="Symbol">{</a><a id="2156" href="foundation.universal-property-truncation.html#2156" class="Bound">k</a><a id="2157" class="Symbol">}</a> <a id="2159" href="foundation.universal-property-truncation.html#2159" class="Bound">B</a> <a id="2161" href="foundation.universal-property-truncation.html#2161" class="Bound">f</a> <a id="2163" class="Symbol">=</a>
  <a id="2167" class="Symbol">(</a><a id="2168" href="foundation.universal-property-truncation.html#2168" class="Bound">C</a> <a id="2170" class="Symbol">:</a> <a id="2172" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="2190" href="foundation.universal-property-truncation.html#2153" class="Bound">l</a> <a id="2192" href="foundation.universal-property-truncation.html#2156" class="Bound">k</a><a id="2193" class="Symbol">)</a> <a id="2195" class="Symbol">→</a> <a id="2197" href="foundation-core.equivalences.html#1542" class="Function">is-equiv</a> <a id="2206" class="Symbol">(</a><a id="2207" href="foundation.universal-property-truncation.html#1757" class="Function">precomp-Trunc</a> <a id="2221" href="foundation.universal-property-truncation.html#2161" class="Bound">f</a> <a id="2223" href="foundation.universal-property-truncation.html#2168" class="Bound">C</a><a id="2224" class="Symbol">)</a>
</pre>
### The universal property of truncations

<pre class="Agda"><a id="universal-property-truncation"></a><a id="2282" href="foundation.universal-property-truncation.html#2282" class="Function">universal-property-truncation</a> <a id="2312" class="Symbol">:</a>
  <a id="2316" class="Symbol">(</a><a id="2317" href="foundation.universal-property-truncation.html#2317" class="Bound">l</a> <a id="2319" class="Symbol">:</a> <a id="2321" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2326" class="Symbol">)</a> <a id="2328" class="Symbol">{</a><a id="2329" href="foundation.universal-property-truncation.html#2329" class="Bound">l1</a> <a id="2332" href="foundation.universal-property-truncation.html#2332" class="Bound">l2</a> <a id="2335" class="Symbol">:</a> <a id="2337" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2342" class="Symbol">}</a> <a id="2344" class="Symbol">{</a><a id="2345" href="foundation.universal-property-truncation.html#2345" class="Bound">k</a> <a id="2347" class="Symbol">:</a> <a id="2349" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="2350" class="Symbol">}</a> <a id="2352" class="Symbol">{</a><a id="2353" href="foundation.universal-property-truncation.html#2353" class="Bound">A</a> <a id="2355" class="Symbol">:</a> <a id="2357" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2360" href="foundation.universal-property-truncation.html#2329" class="Bound">l1</a><a id="2362" class="Symbol">}</a>
  <a id="2366" class="Symbol">(</a><a id="2367" href="foundation.universal-property-truncation.html#2367" class="Bound">B</a> <a id="2369" class="Symbol">:</a> <a id="2371" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="2389" href="foundation.universal-property-truncation.html#2332" class="Bound">l2</a> <a id="2392" href="foundation.universal-property-truncation.html#2345" class="Bound">k</a><a id="2393" class="Symbol">)</a> <a id="2395" class="Symbol">(</a><a id="2396" href="foundation.universal-property-truncation.html#2396" class="Bound">f</a> <a id="2398" class="Symbol">:</a> <a id="2400" href="foundation.universal-property-truncation.html#2353" class="Bound">A</a> <a id="2402" class="Symbol">→</a> <a id="2404" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="2424" href="foundation.universal-property-truncation.html#2367" class="Bound">B</a><a id="2425" class="Symbol">)</a> <a id="2427" class="Symbol">→</a>
  <a id="2431" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2434" class="Symbol">(</a><a id="2435" href="Agda.Primitive.html#780" class="Primitive">lsuc</a> <a id="2440" href="foundation.universal-property-truncation.html#2317" class="Bound">l</a> <a id="2442" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2444" href="foundation.universal-property-truncation.html#2329" class="Bound">l1</a> <a id="2447" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="2449" href="foundation.universal-property-truncation.html#2332" class="Bound">l2</a><a id="2451" class="Symbol">)</a>
<a id="2453" href="foundation.universal-property-truncation.html#2282" class="Function">universal-property-truncation</a> <a id="2483" href="foundation.universal-property-truncation.html#2483" class="Bound">l</a> <a id="2485" class="Symbol">{</a><a id="2486" class="Argument">k</a> <a id="2488" class="Symbol">=</a> <a id="2490" href="foundation.universal-property-truncation.html#2490" class="Bound">k</a><a id="2491" class="Symbol">}</a> <a id="2493" class="Symbol">{</a><a id="2494" href="foundation.universal-property-truncation.html#2494" class="Bound">A</a><a id="2495" class="Symbol">}</a> <a id="2497" href="foundation.universal-property-truncation.html#2497" class="Bound">B</a> <a id="2499" href="foundation.universal-property-truncation.html#2499" class="Bound">f</a> <a id="2501" class="Symbol">=</a>
  <a id="2505" class="Symbol">(</a><a id="2506" href="foundation.universal-property-truncation.html#2506" class="Bound">C</a> <a id="2508" class="Symbol">:</a> <a id="2510" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="2528" href="foundation.universal-property-truncation.html#2483" class="Bound">l</a> <a id="2530" href="foundation.universal-property-truncation.html#2490" class="Bound">k</a><a id="2531" class="Symbol">)</a> <a id="2533" class="Symbol">(</a><a id="2534" href="foundation.universal-property-truncation.html#2534" class="Bound">g</a> <a id="2536" class="Symbol">:</a> <a id="2538" href="foundation.universal-property-truncation.html#2494" class="Bound">A</a> <a id="2540" class="Symbol">→</a> <a id="2542" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="2562" href="foundation.universal-property-truncation.html#2506" class="Bound">C</a><a id="2563" class="Symbol">)</a> <a id="2565" class="Symbol">→</a>
  <a id="2569" href="foundation-core.contractible-types.html#925" class="Function">is-contr</a> <a id="2578" class="Symbol">(</a><a id="2579" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a> <a id="2581" class="Symbol">(</a><a id="2582" href="foundation.truncated-types.html#3516" class="Function">type-hom-Truncated-Type</a> <a id="2606" href="foundation.universal-property-truncation.html#2490" class="Bound">k</a> <a id="2608" href="foundation.universal-property-truncation.html#2497" class="Bound">B</a> <a id="2610" href="foundation.universal-property-truncation.html#2506" class="Bound">C</a><a id="2611" class="Symbol">)</a> <a id="2613" class="Symbol">(λ</a> <a id="2616" href="foundation.universal-property-truncation.html#2616" class="Bound">h</a> <a id="2618" class="Symbol">→</a> <a id="2620" class="Symbol">(</a><a id="2621" href="foundation.universal-property-truncation.html#2616" class="Bound">h</a> <a id="2623" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="2625" href="foundation.universal-property-truncation.html#2499" class="Bound">f</a><a id="2626" class="Symbol">)</a> <a id="2628" href="foundation-core.homotopies.html#467" class="Function Operator">~</a> <a id="2630" href="foundation.universal-property-truncation.html#2534" class="Bound">g</a><a id="2631" class="Symbol">))</a>
</pre>
### The dependent universal property of truncations

<pre class="Agda"><a id="precomp-Π-Truncated-Type"></a><a id="2696" href="foundation.universal-property-truncation.html#2696" class="Function">precomp-Π-Truncated-Type</a> <a id="2721" class="Symbol">:</a>
  <a id="2725" class="Symbol">{</a><a id="2726" href="foundation.universal-property-truncation.html#2726" class="Bound">l1</a> <a id="2729" href="foundation.universal-property-truncation.html#2729" class="Bound">l2</a> <a id="2732" href="foundation.universal-property-truncation.html#2732" class="Bound">l3</a> <a id="2735" class="Symbol">:</a> <a id="2737" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="2742" class="Symbol">}</a> <a id="2744" class="Symbol">{</a><a id="2745" href="foundation.universal-property-truncation.html#2745" class="Bound">k</a> <a id="2747" class="Symbol">:</a> <a id="2749" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="2750" class="Symbol">}</a> <a id="2752" class="Symbol">{</a><a id="2753" href="foundation.universal-property-truncation.html#2753" class="Bound">A</a> <a id="2755" class="Symbol">:</a> <a id="2757" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2760" href="foundation.universal-property-truncation.html#2726" class="Bound">l1</a><a id="2762" class="Symbol">}</a> <a id="2764" class="Symbol">{</a><a id="2765" href="foundation.universal-property-truncation.html#2765" class="Bound">B</a> <a id="2767" class="Symbol">:</a> <a id="2769" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="2772" href="foundation.universal-property-truncation.html#2729" class="Bound">l2</a><a id="2774" class="Symbol">}</a> <a id="2776" class="Symbol">(</a><a id="2777" href="foundation.universal-property-truncation.html#2777" class="Bound">f</a> <a id="2779" class="Symbol">:</a> <a id="2781" href="foundation.universal-property-truncation.html#2753" class="Bound">A</a> <a id="2783" class="Symbol">→</a> <a id="2785" href="foundation.universal-property-truncation.html#2765" class="Bound">B</a><a id="2786" class="Symbol">)</a>
  <a id="2790" class="Symbol">(</a><a id="2791" href="foundation.universal-property-truncation.html#2791" class="Bound">C</a> <a id="2793" class="Symbol">:</a> <a id="2795" href="foundation.universal-property-truncation.html#2765" class="Bound">B</a> <a id="2797" class="Symbol">→</a> <a id="2799" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="2817" href="foundation.universal-property-truncation.html#2732" class="Bound">l3</a> <a id="2820" href="foundation.universal-property-truncation.html#2745" class="Bound">k</a><a id="2821" class="Symbol">)</a> <a id="2823" class="Symbol">→</a>
  <a id="2827" class="Symbol">((</a><a id="2829" href="foundation.universal-property-truncation.html#2829" class="Bound">b</a> <a id="2831" class="Symbol">:</a> <a id="2833" href="foundation.universal-property-truncation.html#2765" class="Bound">B</a><a id="2834" class="Symbol">)</a> <a id="2836" class="Symbol">→</a> <a id="2838" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="2858" class="Symbol">(</a><a id="2859" href="foundation.universal-property-truncation.html#2791" class="Bound">C</a> <a id="2861" href="foundation.universal-property-truncation.html#2829" class="Bound">b</a><a id="2862" class="Symbol">))</a> <a id="2865" class="Symbol">→</a>
  <a id="2869" class="Symbol">((</a><a id="2871" href="foundation.universal-property-truncation.html#2871" class="Bound">a</a> <a id="2873" class="Symbol">:</a> <a id="2875" href="foundation.universal-property-truncation.html#2753" class="Bound">A</a><a id="2876" class="Symbol">)</a> <a id="2878" class="Symbol">→</a> <a id="2880" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="2900" class="Symbol">(</a><a id="2901" href="foundation.universal-property-truncation.html#2791" class="Bound">C</a> <a id="2903" class="Symbol">(</a><a id="2904" href="foundation.universal-property-truncation.html#2777" class="Bound">f</a> <a id="2906" href="foundation.universal-property-truncation.html#2871" class="Bound">a</a><a id="2907" class="Symbol">)))</a>
<a id="2911" href="foundation.universal-property-truncation.html#2696" class="Function">precomp-Π-Truncated-Type</a> <a id="2936" href="foundation.universal-property-truncation.html#2936" class="Bound">f</a> <a id="2938" href="foundation.universal-property-truncation.html#2938" class="Bound">C</a> <a id="2940" href="foundation.universal-property-truncation.html#2940" class="Bound">h</a> <a id="2942" href="foundation.universal-property-truncation.html#2942" class="Bound">a</a> <a id="2944" class="Symbol">=</a> <a id="2946" href="foundation.universal-property-truncation.html#2940" class="Bound">h</a> <a id="2948" class="Symbol">(</a><a id="2949" href="foundation.universal-property-truncation.html#2936" class="Bound">f</a> <a id="2951" href="foundation.universal-property-truncation.html#2942" class="Bound">a</a><a id="2952" class="Symbol">)</a>

<a id="dependent-universal-property-truncation"></a><a id="2955" href="foundation.universal-property-truncation.html#2955" class="Function">dependent-universal-property-truncation</a> <a id="2995" class="Symbol">:</a>
  <a id="2999" class="Symbol">{</a><a id="3000" href="foundation.universal-property-truncation.html#3000" class="Bound">l1</a> <a id="3003" href="foundation.universal-property-truncation.html#3003" class="Bound">l2</a> <a id="3006" class="Symbol">:</a> <a id="3008" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3013" class="Symbol">}</a> <a id="3015" class="Symbol">(</a><a id="3016" href="foundation.universal-property-truncation.html#3016" class="Bound">l</a> <a id="3018" class="Symbol">:</a> <a id="3020" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3025" class="Symbol">)</a> <a id="3027" class="Symbol">{</a><a id="3028" href="foundation.universal-property-truncation.html#3028" class="Bound">k</a> <a id="3030" class="Symbol">:</a> <a id="3032" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="3033" class="Symbol">}</a> <a id="3035" class="Symbol">{</a><a id="3036" href="foundation.universal-property-truncation.html#3036" class="Bound">A</a> <a id="3038" class="Symbol">:</a> <a id="3040" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3043" href="foundation.universal-property-truncation.html#3000" class="Bound">l1</a><a id="3045" class="Symbol">}</a> <a id="3047" class="Symbol">(</a><a id="3048" href="foundation.universal-property-truncation.html#3048" class="Bound">B</a> <a id="3050" class="Symbol">:</a> <a id="3052" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="3070" href="foundation.universal-property-truncation.html#3003" class="Bound">l2</a> <a id="3073" href="foundation.universal-property-truncation.html#3028" class="Bound">k</a><a id="3074" class="Symbol">)</a>
  <a id="3078" class="Symbol">(</a><a id="3079" href="foundation.universal-property-truncation.html#3079" class="Bound">f</a> <a id="3081" class="Symbol">:</a> <a id="3083" href="foundation.universal-property-truncation.html#3036" class="Bound">A</a> <a id="3085" class="Symbol">→</a> <a id="3087" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="3107" href="foundation.universal-property-truncation.html#3048" class="Bound">B</a><a id="3108" class="Symbol">)</a> <a id="3110" class="Symbol">→</a> <a id="3112" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3115" class="Symbol">(</a><a id="3116" href="foundation.universal-property-truncation.html#3000" class="Bound">l1</a> <a id="3119" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="3121" href="foundation.universal-property-truncation.html#3003" class="Bound">l2</a> <a id="3124" href="Agda.Primitive.html#810" class="Primitive Operator">⊔</a> <a id="3126" href="Agda.Primitive.html#780" class="Primitive">lsuc</a> <a id="3131" href="foundation.universal-property-truncation.html#3016" class="Bound">l</a><a id="3132" class="Symbol">)</a>
<a id="3134" href="foundation.universal-property-truncation.html#2955" class="Function">dependent-universal-property-truncation</a> <a id="3174" href="foundation.universal-property-truncation.html#3174" class="Bound">l</a> <a id="3176" class="Symbol">{</a><a id="3177" href="foundation.universal-property-truncation.html#3177" class="Bound">k</a><a id="3178" class="Symbol">}</a> <a id="3180" href="foundation.universal-property-truncation.html#3180" class="Bound">B</a> <a id="3182" href="foundation.universal-property-truncation.html#3182" class="Bound">f</a> <a id="3184" class="Symbol">=</a>
  <a id="3188" class="Symbol">(</a><a id="3189" href="foundation.universal-property-truncation.html#3189" class="Bound">X</a> <a id="3191" class="Symbol">:</a> <a id="3193" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="3213" href="foundation.universal-property-truncation.html#3180" class="Bound">B</a> <a id="3215" class="Symbol">→</a> <a id="3217" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="3235" href="foundation.universal-property-truncation.html#3174" class="Bound">l</a> <a id="3237" href="foundation.universal-property-truncation.html#3177" class="Bound">k</a><a id="3238" class="Symbol">)</a> <a id="3240" class="Symbol">→</a>
  <a id="3244" href="foundation-core.equivalences.html#1542" class="Function">is-equiv</a> <a id="3253" class="Symbol">(</a><a id="3254" href="foundation.universal-property-truncation.html#2696" class="Function">precomp-Π-Truncated-Type</a> <a id="3279" href="foundation.universal-property-truncation.html#3182" class="Bound">f</a> <a id="3281" href="foundation.universal-property-truncation.html#3189" class="Bound">X</a><a id="3282" class="Symbol">)</a>
</pre>
## Properties

### Equivalences into `k`-truncated types are truncations

<pre class="Agda"><a id="3371" class="Keyword">abstract</a>
  <a id="is-truncation-id"></a><a id="3382" href="foundation.universal-property-truncation.html#3382" class="Function">is-truncation-id</a> <a id="3399" class="Symbol">:</a>
    <a id="3405" class="Symbol">{</a><a id="3406" href="foundation.universal-property-truncation.html#3406" class="Bound">l1</a> <a id="3409" class="Symbol">:</a> <a id="3411" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3416" class="Symbol">}</a> <a id="3418" class="Symbol">{</a><a id="3419" href="foundation.universal-property-truncation.html#3419" class="Bound">k</a> <a id="3421" class="Symbol">:</a> <a id="3423" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="3424" class="Symbol">}</a> <a id="3426" class="Symbol">{</a><a id="3427" href="foundation.universal-property-truncation.html#3427" class="Bound">A</a> <a id="3429" class="Symbol">:</a> <a id="3431" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3434" href="foundation.universal-property-truncation.html#3406" class="Bound">l1</a><a id="3436" class="Symbol">}</a> <a id="3438" class="Symbol">(</a><a id="3439" href="foundation.universal-property-truncation.html#3439" class="Bound">H</a> <a id="3441" class="Symbol">:</a> <a id="3443" href="foundation-core.truncated-types.html#1466" class="Function">is-trunc</a> <a id="3452" href="foundation.universal-property-truncation.html#3419" class="Bound">k</a> <a id="3454" href="foundation.universal-property-truncation.html#3427" class="Bound">A</a><a id="3455" class="Symbol">)</a> <a id="3457" class="Symbol">→</a>
    <a id="3463" class="Symbol">{</a><a id="3464" href="foundation.universal-property-truncation.html#3464" class="Bound">l</a> <a id="3466" class="Symbol">:</a> <a id="3468" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3473" class="Symbol">}</a> <a id="3475" class="Symbol">→</a> <a id="3477" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="3491" href="foundation.universal-property-truncation.html#3464" class="Bound">l</a> <a id="3493" class="Symbol">(</a><a id="3494" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="3499" href="foundation.universal-property-truncation.html#3427" class="Bound">A</a> <a id="3501" href="foundation.universal-property-truncation.html#3439" class="Bound">H</a><a id="3502" class="Symbol">)</a> <a id="3504" href="foundation-core.functions.html#309" class="Function">id</a>
  <a id="3509" href="foundation.universal-property-truncation.html#3382" class="Function">is-truncation-id</a> <a id="3526" href="foundation.universal-property-truncation.html#3526" class="Bound">H</a> <a id="3528" href="foundation.universal-property-truncation.html#3528" class="Bound">B</a> <a id="3530" class="Symbol">=</a>
    <a id="3536" href="foundation.equivalences.html#9064" class="Function">is-equiv-precomp-is-equiv</a> <a id="3562" href="foundation-core.functions.html#309" class="Function">id</a> <a id="3565" href="foundation-core.equivalences.html#2309" class="Function">is-equiv-id</a> <a id="3577" class="Symbol">(</a><a id="3578" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="3598" href="foundation.universal-property-truncation.html#3528" class="Bound">B</a><a id="3599" class="Symbol">)</a>

<a id="3602" class="Keyword">abstract</a>
  <a id="is-truncation-equiv"></a><a id="3613" href="foundation.universal-property-truncation.html#3613" class="Function">is-truncation-equiv</a> <a id="3633" class="Symbol">:</a>
    <a id="3639" class="Symbol">{</a><a id="3640" href="foundation.universal-property-truncation.html#3640" class="Bound">l1</a> <a id="3643" href="foundation.universal-property-truncation.html#3643" class="Bound">l2</a> <a id="3646" class="Symbol">:</a> <a id="3648" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3653" class="Symbol">}</a> <a id="3655" class="Symbol">{</a><a id="3656" href="foundation.universal-property-truncation.html#3656" class="Bound">k</a> <a id="3658" class="Symbol">:</a> <a id="3660" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="3661" class="Symbol">}</a> <a id="3663" class="Symbol">{</a><a id="3664" href="foundation.universal-property-truncation.html#3664" class="Bound">A</a> <a id="3666" class="Symbol">:</a> <a id="3668" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="3671" href="foundation.universal-property-truncation.html#3640" class="Bound">l1</a><a id="3673" class="Symbol">}</a> <a id="3675" class="Symbol">(</a><a id="3676" href="foundation.universal-property-truncation.html#3676" class="Bound">B</a> <a id="3678" class="Symbol">:</a> <a id="3680" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="3698" href="foundation.universal-property-truncation.html#3643" class="Bound">l2</a> <a id="3701" href="foundation.universal-property-truncation.html#3656" class="Bound">k</a><a id="3702" class="Symbol">)</a>
    <a id="3708" class="Symbol">(</a><a id="3709" href="foundation.universal-property-truncation.html#3709" class="Bound">e</a> <a id="3711" class="Symbol">:</a> <a id="3713" href="foundation.universal-property-truncation.html#3664" class="Bound">A</a> <a id="3715" href="foundation-core.equivalences.html#1607" class="Function Operator">≃</a> <a id="3717" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="3737" href="foundation.universal-property-truncation.html#3676" class="Bound">B</a><a id="3738" class="Symbol">)</a> <a id="3740" class="Symbol">→</a>
    <a id="3746" class="Symbol">{</a><a id="3747" href="foundation.universal-property-truncation.html#3747" class="Bound">l</a> <a id="3749" class="Symbol">:</a> <a id="3751" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="3756" class="Symbol">}</a> <a id="3758" class="Symbol">→</a> <a id="3760" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="3774" href="foundation.universal-property-truncation.html#3747" class="Bound">l</a> <a id="3776" href="foundation.universal-property-truncation.html#3676" class="Bound">B</a> <a id="3778" class="Symbol">(</a><a id="3779" href="foundation-core.equivalences.html#1807" class="Function">map-equiv</a> <a id="3789" href="foundation.universal-property-truncation.html#3709" class="Bound">e</a><a id="3790" class="Symbol">)</a>
  <a id="3794" href="foundation.universal-property-truncation.html#3613" class="Function">is-truncation-equiv</a> <a id="3814" href="foundation.universal-property-truncation.html#3814" class="Bound">B</a> <a id="3816" href="foundation.universal-property-truncation.html#3816" class="Bound">e</a> <a id="3818" href="foundation.universal-property-truncation.html#3818" class="Bound">C</a> <a id="3820" class="Symbol">=</a>
    <a id="3826" href="foundation.equivalences.html#9064" class="Function">is-equiv-precomp-is-equiv</a>
      <a id="3858" class="Symbol">(</a> <a id="3860" href="foundation-core.equivalences.html#1807" class="Function">map-equiv</a> <a id="3870" href="foundation.universal-property-truncation.html#3816" class="Bound">e</a><a id="3871" class="Symbol">)</a>
      <a id="3879" class="Symbol">(</a> <a id="3881" href="foundation-core.equivalences.html#1862" class="Function">is-equiv-map-equiv</a> <a id="3900" href="foundation.universal-property-truncation.html#3816" class="Bound">e</a><a id="3901" class="Symbol">)</a>
      <a id="3909" class="Symbol">(</a> <a id="3911" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="3931" href="foundation.universal-property-truncation.html#3818" class="Bound">C</a><a id="3932" class="Symbol">)</a>
</pre>
### A map into a truncated type is a truncation if and only if it satisfies the universal property of the truncation

<pre class="Agda"><a id="4065" class="Keyword">module</a> <a id="4072" href="foundation.universal-property-truncation.html#4072" class="Module">_</a>
  <a id="4076" class="Symbol">{</a><a id="4077" href="foundation.universal-property-truncation.html#4077" class="Bound">l1</a> <a id="4080" href="foundation.universal-property-truncation.html#4080" class="Bound">l2</a> <a id="4083" class="Symbol">:</a> <a id="4085" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="4090" class="Symbol">}</a> <a id="4092" class="Symbol">{</a><a id="4093" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a> <a id="4095" class="Symbol">:</a> <a id="4097" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="4098" class="Symbol">}</a> <a id="4100" class="Symbol">{</a><a id="4101" href="foundation.universal-property-truncation.html#4101" class="Bound">A</a> <a id="4103" class="Symbol">:</a> <a id="4105" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="4108" href="foundation.universal-property-truncation.html#4077" class="Bound">l1</a><a id="4110" class="Symbol">}</a> <a id="4112" class="Symbol">(</a><a id="4113" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4115" class="Symbol">:</a> <a id="4117" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="4135" href="foundation.universal-property-truncation.html#4080" class="Bound">l2</a> <a id="4138" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a><a id="4139" class="Symbol">)</a>
  <a id="4143" class="Symbol">(</a><a id="4144" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a> <a id="4146" class="Symbol">:</a> <a id="4148" href="foundation.universal-property-truncation.html#4101" class="Bound">A</a> <a id="4150" class="Symbol">→</a> <a id="4152" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="4172" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a><a id="4173" class="Symbol">)</a>
  <a id="4177" class="Keyword">where</a>

  <a id="4186" class="Keyword">abstract</a>
    <a id="4199" href="foundation.universal-property-truncation.html#4199" class="Function">is-truncation-universal-property-truncation</a> <a id="4243" class="Symbol">:</a>
      <a id="4251" class="Symbol">({</a><a id="4253" href="foundation.universal-property-truncation.html#4253" class="Bound">l</a> <a id="4255" class="Symbol">:</a> <a id="4257" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="4262" class="Symbol">}</a> <a id="4264" class="Symbol">→</a> <a id="4266" href="foundation.universal-property-truncation.html#2282" class="Function">universal-property-truncation</a> <a id="4296" href="foundation.universal-property-truncation.html#4253" class="Bound">l</a> <a id="4298" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4300" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="4301" class="Symbol">)</a> <a id="4303" class="Symbol">→</a>
      <a id="4311" class="Symbol">({</a><a id="4313" href="foundation.universal-property-truncation.html#4313" class="Bound">l</a> <a id="4315" class="Symbol">:</a> <a id="4317" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="4322" class="Symbol">}</a> <a id="4324" class="Symbol">→</a> <a id="4326" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="4340" href="foundation.universal-property-truncation.html#4313" class="Bound">l</a> <a id="4342" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4344" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="4345" class="Symbol">)</a>
    <a id="4351" href="foundation.universal-property-truncation.html#4199" class="Function">is-truncation-universal-property-truncation</a> <a id="4395" href="foundation.universal-property-truncation.html#4395" class="Bound">H</a> <a id="4397" href="foundation.universal-property-truncation.html#4397" class="Bound">C</a> <a id="4399" class="Symbol">=</a>
      <a id="4407" href="foundation-core.contractible-maps.html#2368" class="Function">is-equiv-is-contr-map</a>
        <a id="4437" class="Symbol">(</a> <a id="4439" class="Symbol">λ</a> <a id="4441" href="foundation.universal-property-truncation.html#4441" class="Bound">g</a> <a id="4443" class="Symbol">→</a>
          <a id="4455" href="foundation-core.contractible-types.html#3230" class="Function">is-contr-equiv</a>
            <a id="4482" class="Symbol">(</a> <a id="4484" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a> <a id="4486" class="Symbol">(</a><a id="4487" href="foundation.truncated-types.html#3516" class="Function">type-hom-Truncated-Type</a> <a id="4511" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a> <a id="4513" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4515" href="foundation.universal-property-truncation.html#4397" class="Bound">C</a><a id="4516" class="Symbol">)</a> <a id="4518" class="Symbol">(λ</a> <a id="4521" href="foundation.universal-property-truncation.html#4521" class="Bound">h</a> <a id="4523" class="Symbol">→</a> <a id="4525" class="Symbol">(</a><a id="4526" href="foundation.universal-property-truncation.html#4521" class="Bound">h</a> <a id="4528" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="4530" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="4531" class="Symbol">)</a> <a id="4533" href="foundation-core.homotopies.html#467" class="Function Operator">~</a> <a id="4535" href="foundation.universal-property-truncation.html#4441" class="Bound">g</a><a id="4536" class="Symbol">))</a>
            <a id="4551" class="Symbol">(</a> <a id="4553" href="foundation-core.functoriality-dependent-pair-types.html#6804" class="Function">equiv-tot</a> <a id="4563" class="Symbol">(λ</a> <a id="4566" href="foundation.universal-property-truncation.html#4566" class="Bound">h</a> <a id="4568" class="Symbol">→</a> <a id="4570" href="foundation.function-extensionality.html#1283" class="Function">equiv-funext</a><a id="4582" class="Symbol">))</a>
            <a id="4597" class="Symbol">(</a> <a id="4599" href="foundation.universal-property-truncation.html#4395" class="Bound">H</a> <a id="4601" href="foundation.universal-property-truncation.html#4397" class="Bound">C</a> <a id="4603" href="foundation.universal-property-truncation.html#4441" class="Bound">g</a><a id="4604" class="Symbol">))</a>

  <a id="4610" class="Keyword">abstract</a>
    <a id="4623" href="foundation.universal-property-truncation.html#4623" class="Function">universal-property-truncation-is-truncation</a> <a id="4667" class="Symbol">:</a>
      <a id="4675" class="Symbol">({</a><a id="4677" href="foundation.universal-property-truncation.html#4677" class="Bound">l</a> <a id="4679" class="Symbol">:</a> <a id="4681" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="4686" class="Symbol">}</a> <a id="4688" class="Symbol">→</a> <a id="4690" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="4704" href="foundation.universal-property-truncation.html#4677" class="Bound">l</a> <a id="4706" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4708" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="4709" class="Symbol">)</a> <a id="4711" class="Symbol">→</a>
      <a id="4719" class="Symbol">({</a><a id="4721" href="foundation.universal-property-truncation.html#4721" class="Bound">l</a> <a id="4723" class="Symbol">:</a> <a id="4725" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="4730" class="Symbol">}</a> <a id="4732" class="Symbol">→</a> <a id="4734" href="foundation.universal-property-truncation.html#2282" class="Function">universal-property-truncation</a> <a id="4764" href="foundation.universal-property-truncation.html#4721" class="Bound">l</a> <a id="4766" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4768" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="4769" class="Symbol">)</a>
    <a id="4775" href="foundation.universal-property-truncation.html#4623" class="Function">universal-property-truncation-is-truncation</a> <a id="4819" href="foundation.universal-property-truncation.html#4819" class="Bound">H</a> <a id="4821" href="foundation.universal-property-truncation.html#4821" class="Bound">C</a> <a id="4823" href="foundation.universal-property-truncation.html#4823" class="Bound">g</a> <a id="4825" class="Symbol">=</a>
      <a id="4833" href="foundation-core.contractible-types.html#3739" class="Function">is-contr-equiv&#39;</a>
        <a id="4857" class="Symbol">(</a> <a id="4859" href="foundation-core.dependent-pair-types.html#502" class="Record">Σ</a> <a id="4861" class="Symbol">(</a><a id="4862" href="foundation.truncated-types.html#3516" class="Function">type-hom-Truncated-Type</a> <a id="4886" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a> <a id="4888" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="4890" href="foundation.universal-property-truncation.html#4821" class="Bound">C</a><a id="4891" class="Symbol">)</a> <a id="4893" class="Symbol">(λ</a> <a id="4896" href="foundation.universal-property-truncation.html#4896" class="Bound">h</a> <a id="4898" class="Symbol">→</a> <a id="4900" href="foundation-core.identity-types.html#641" class="Datatype">Id</a> <a id="4903" class="Symbol">(</a><a id="4904" href="foundation.universal-property-truncation.html#4896" class="Bound">h</a> <a id="4906" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="4908" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="4909" class="Symbol">)</a> <a id="4911" href="foundation.universal-property-truncation.html#4823" class="Bound">g</a><a id="4912" class="Symbol">))</a>
        <a id="4923" class="Symbol">(</a> <a id="4925" href="foundation-core.functoriality-dependent-pair-types.html#6804" class="Function">equiv-tot</a> <a id="4935" class="Symbol">(λ</a> <a id="4938" href="foundation.universal-property-truncation.html#4938" class="Bound">h</a> <a id="4940" class="Symbol">→</a> <a id="4942" href="foundation.function-extensionality.html#1283" class="Function">equiv-funext</a><a id="4954" class="Symbol">))</a>
        <a id="4965" class="Symbol">(</a> <a id="4967" href="foundation-core.contractible-maps.html#3850" class="Function">is-contr-map-is-equiv</a> <a id="4989" class="Symbol">(</a><a id="4990" href="foundation.universal-property-truncation.html#4819" class="Bound">H</a> <a id="4992" href="foundation.universal-property-truncation.html#4821" class="Bound">C</a><a id="4993" class="Symbol">)</a> <a id="4995" href="foundation.universal-property-truncation.html#4823" class="Bound">g</a><a id="4996" class="Symbol">)</a>

  <a id="5001" href="foundation.universal-property-truncation.html#5001" class="Function">map-is-truncation</a> <a id="5019" class="Symbol">:</a>
    <a id="5025" class="Symbol">({</a><a id="5027" href="foundation.universal-property-truncation.html#5027" class="Bound">l</a> <a id="5029" class="Symbol">:</a> <a id="5031" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5036" class="Symbol">}</a> <a id="5038" class="Symbol">→</a> <a id="5040" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="5054" href="foundation.universal-property-truncation.html#5027" class="Bound">l</a> <a id="5056" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="5058" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="5059" class="Symbol">)</a> <a id="5061" class="Symbol">→</a>
    <a id="5067" class="Symbol">({</a><a id="5069" href="foundation.universal-property-truncation.html#5069" class="Bound">l</a> <a id="5071" class="Symbol">:</a> <a id="5073" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5078" class="Symbol">}</a> <a id="5080" class="Symbol">(</a><a id="5081" href="foundation.universal-property-truncation.html#5081" class="Bound">C</a> <a id="5083" class="Symbol">:</a> <a id="5085" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="5103" href="foundation.universal-property-truncation.html#5069" class="Bound">l</a> <a id="5105" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a><a id="5106" class="Symbol">)</a> <a id="5108" class="Symbol">(</a><a id="5109" href="foundation.universal-property-truncation.html#5109" class="Bound">g</a> <a id="5111" class="Symbol">:</a> <a id="5113" href="foundation.universal-property-truncation.html#4101" class="Bound">A</a> <a id="5115" class="Symbol">→</a> <a id="5117" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="5137" href="foundation.universal-property-truncation.html#5081" class="Bound">C</a><a id="5138" class="Symbol">)</a> <a id="5140" class="Symbol">→</a>
    <a id="5146" href="foundation.truncated-types.html#3516" class="Function">type-hom-Truncated-Type</a> <a id="5170" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a> <a id="5172" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="5174" href="foundation.universal-property-truncation.html#5081" class="Bound">C</a><a id="5175" class="Symbol">)</a>
  <a id="5179" href="foundation.universal-property-truncation.html#5001" class="Function">map-is-truncation</a> <a id="5197" href="foundation.universal-property-truncation.html#5197" class="Bound">H</a> <a id="5199" href="foundation.universal-property-truncation.html#5199" class="Bound">C</a> <a id="5201" href="foundation.universal-property-truncation.html#5201" class="Bound">g</a> <a id="5203" class="Symbol">=</a>
    <a id="5209" href="foundation-core.dependent-pair-types.html#592" class="Field">pr1</a> <a id="5213" class="Symbol">(</a><a id="5214" href="foundation-core.contractible-types.html#1018" class="Function">center</a> <a id="5221" class="Symbol">(</a><a id="5222" href="foundation.universal-property-truncation.html#4623" class="Function">universal-property-truncation-is-truncation</a> <a id="5266" href="foundation.universal-property-truncation.html#5197" class="Bound">H</a> <a id="5268" href="foundation.universal-property-truncation.html#5199" class="Bound">C</a> <a id="5270" href="foundation.universal-property-truncation.html#5201" class="Bound">g</a><a id="5271" class="Symbol">))</a>

  <a id="5277" href="foundation.universal-property-truncation.html#5277" class="Function">triangle-is-truncation</a> <a id="5300" class="Symbol">:</a>
    <a id="5306" class="Symbol">(</a><a id="5307" href="foundation.universal-property-truncation.html#5307" class="Bound">H</a> <a id="5309" class="Symbol">:</a> <a id="5311" class="Symbol">{</a><a id="5312" href="foundation.universal-property-truncation.html#5312" class="Bound">l</a> <a id="5314" class="Symbol">:</a> <a id="5316" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5321" class="Symbol">}</a> <a id="5323" class="Symbol">→</a> <a id="5325" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="5339" href="foundation.universal-property-truncation.html#5312" class="Bound">l</a> <a id="5341" href="foundation.universal-property-truncation.html#4113" class="Bound">B</a> <a id="5343" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="5344" class="Symbol">)</a> <a id="5346" class="Symbol">→</a>
    <a id="5352" class="Symbol">{</a><a id="5353" href="foundation.universal-property-truncation.html#5353" class="Bound">l</a> <a id="5355" class="Symbol">:</a> <a id="5357" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5362" class="Symbol">}</a> <a id="5364" class="Symbol">(</a><a id="5365" href="foundation.universal-property-truncation.html#5365" class="Bound">C</a> <a id="5367" class="Symbol">:</a> <a id="5369" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="5387" href="foundation.universal-property-truncation.html#5353" class="Bound">l</a> <a id="5389" href="foundation.universal-property-truncation.html#4093" class="Bound">k</a><a id="5390" class="Symbol">)</a> <a id="5392" class="Symbol">(</a><a id="5393" href="foundation.universal-property-truncation.html#5393" class="Bound">g</a> <a id="5395" class="Symbol">:</a> <a id="5397" href="foundation.universal-property-truncation.html#4101" class="Bound">A</a> <a id="5399" class="Symbol">→</a> <a id="5401" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="5421" href="foundation.universal-property-truncation.html#5365" class="Bound">C</a><a id="5422" class="Symbol">)</a> <a id="5424" class="Symbol">→</a>
    <a id="5430" class="Symbol">(</a><a id="5431" href="foundation.universal-property-truncation.html#5001" class="Function">map-is-truncation</a> <a id="5449" href="foundation.universal-property-truncation.html#5307" class="Bound">H</a> <a id="5451" href="foundation.universal-property-truncation.html#5365" class="Bound">C</a> <a id="5453" href="foundation.universal-property-truncation.html#5393" class="Bound">g</a> <a id="5455" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="5457" href="foundation.universal-property-truncation.html#4144" class="Bound">f</a><a id="5458" class="Symbol">)</a> <a id="5460" href="foundation-core.homotopies.html#467" class="Function Operator">~</a> <a id="5462" href="foundation.universal-property-truncation.html#5393" class="Bound">g</a>
  <a id="5466" href="foundation.universal-property-truncation.html#5277" class="Function">triangle-is-truncation</a> <a id="5489" href="foundation.universal-property-truncation.html#5489" class="Bound">H</a> <a id="5491" href="foundation.universal-property-truncation.html#5491" class="Bound">C</a> <a id="5493" href="foundation.universal-property-truncation.html#5493" class="Bound">g</a> <a id="5495" class="Symbol">=</a>
    <a id="5501" href="foundation-core.dependent-pair-types.html#604" class="Field">pr2</a> <a id="5505" class="Symbol">(</a><a id="5506" href="foundation-core.contractible-types.html#1018" class="Function">center</a> <a id="5513" class="Symbol">(</a><a id="5514" href="foundation.universal-property-truncation.html#4623" class="Function">universal-property-truncation-is-truncation</a> <a id="5558" href="foundation.universal-property-truncation.html#5489" class="Bound">H</a> <a id="5560" href="foundation.universal-property-truncation.html#5491" class="Bound">C</a> <a id="5562" href="foundation.universal-property-truncation.html#5493" class="Bound">g</a><a id="5563" class="Symbol">))</a>
</pre>
### A map into a truncated type is a truncation if and only if it satisfies the dependent universal property of the truncation

<pre class="Agda"><a id="5707" class="Keyword">module</a> <a id="5714" href="foundation.universal-property-truncation.html#5714" class="Module">_</a>
  <a id="5718" class="Symbol">{</a><a id="5719" href="foundation.universal-property-truncation.html#5719" class="Bound">l1</a> <a id="5722" href="foundation.universal-property-truncation.html#5722" class="Bound">l2</a> <a id="5725" class="Symbol">:</a> <a id="5727" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5732" class="Symbol">}</a> <a id="5734" class="Symbol">{</a><a id="5735" href="foundation.universal-property-truncation.html#5735" class="Bound">k</a> <a id="5737" class="Symbol">:</a> <a id="5739" href="foundation-core.truncation-levels.html#382" class="Datatype">𝕋</a><a id="5740" class="Symbol">}</a> <a id="5742" class="Symbol">{</a><a id="5743" href="foundation.universal-property-truncation.html#5743" class="Bound">A</a> <a id="5745" class="Symbol">:</a> <a id="5747" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="5750" href="foundation.universal-property-truncation.html#5719" class="Bound">l1</a><a id="5752" class="Symbol">}</a> <a id="5754" class="Symbol">(</a><a id="5755" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="5757" class="Symbol">:</a> <a id="5759" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="5777" href="foundation.universal-property-truncation.html#5722" class="Bound">l2</a> <a id="5780" href="foundation.universal-property-truncation.html#5735" class="Bound">k</a><a id="5781" class="Symbol">)</a>
  <a id="5785" class="Symbol">(</a><a id="5786" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a> <a id="5788" class="Symbol">:</a> <a id="5790" href="foundation.universal-property-truncation.html#5743" class="Bound">A</a> <a id="5792" class="Symbol">→</a> <a id="5794" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="5814" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a><a id="5815" class="Symbol">)</a>
  <a id="5819" class="Keyword">where</a>

  <a id="5828" class="Keyword">abstract</a>
    <a id="5841" href="foundation.universal-property-truncation.html#5841" class="Function">dependent-universal-property-truncation-is-truncation</a> <a id="5895" class="Symbol">:</a>
      <a id="5903" class="Symbol">({</a><a id="5905" href="foundation.universal-property-truncation.html#5905" class="Bound">l</a> <a id="5907" class="Symbol">:</a> <a id="5909" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5914" class="Symbol">}</a> <a id="5916" class="Symbol">→</a> <a id="5918" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="5932" href="foundation.universal-property-truncation.html#5905" class="Bound">l</a> <a id="5934" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="5936" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a><a id="5937" class="Symbol">)</a> <a id="5939" class="Symbol">→</a>
      <a id="5947" class="Symbol">{</a><a id="5948" href="foundation.universal-property-truncation.html#5948" class="Bound">l</a> <a id="5950" class="Symbol">:</a> <a id="5952" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="5957" class="Symbol">}</a> <a id="5959" class="Symbol">→</a> <a id="5961" href="foundation.universal-property-truncation.html#2955" class="Function">dependent-universal-property-truncation</a> <a id="6001" href="foundation.universal-property-truncation.html#5948" class="Bound">l</a> <a id="6003" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="6005" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a>
    <a id="6011" href="foundation.universal-property-truncation.html#5841" class="Function">dependent-universal-property-truncation-is-truncation</a> <a id="6065" href="foundation.universal-property-truncation.html#6065" class="Bound">H</a> <a id="6067" href="foundation.universal-property-truncation.html#6067" class="Bound">X</a> <a id="6069" class="Symbol">=</a>
      <a id="6077" href="foundation-core.functoriality-dependent-pair-types.html#10750" class="Function">is-fiberwise-equiv-is-equiv-map-Σ</a>
        <a id="6119" class="Symbol">(</a> <a id="6121" class="Symbol">λ</a> <a id="6123" class="Symbol">(</a><a id="6124" href="foundation.universal-property-truncation.html#6124" class="Bound">h</a> <a id="6126" class="Symbol">:</a> <a id="6128" href="foundation.universal-property-truncation.html#5743" class="Bound">A</a> <a id="6130" class="Symbol">→</a> <a id="6132" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6152" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a><a id="6153" class="Symbol">)</a> <a id="6155" class="Symbol">→</a>
          <a id="6167" class="Symbol">(</a><a id="6168" href="foundation.universal-property-truncation.html#6168" class="Bound">a</a> <a id="6170" class="Symbol">:</a> <a id="6172" href="foundation.universal-property-truncation.html#5743" class="Bound">A</a><a id="6173" class="Symbol">)</a> <a id="6175" class="Symbol">→</a> <a id="6177" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6197" class="Symbol">(</a><a id="6198" href="foundation.universal-property-truncation.html#6067" class="Bound">X</a> <a id="6200" class="Symbol">(</a><a id="6201" href="foundation.universal-property-truncation.html#6124" class="Bound">h</a> <a id="6203" href="foundation.universal-property-truncation.html#6168" class="Bound">a</a><a id="6204" class="Symbol">)))</a>
        <a id="6216" class="Symbol">(</a> <a id="6218" class="Symbol">λ</a> <a id="6220" class="Symbol">(</a><a id="6221" href="foundation.universal-property-truncation.html#6221" class="Bound">g</a> <a id="6223" class="Symbol">:</a> <a id="6225" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6245" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="6247" class="Symbol">→</a> <a id="6249" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6269" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a><a id="6270" class="Symbol">)</a> <a id="6272" class="Symbol">→</a> <a id="6274" href="foundation.universal-property-truncation.html#6221" class="Bound">g</a> <a id="6276" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="6278" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a><a id="6279" class="Symbol">)</a>
        <a id="6289" class="Symbol">(</a> <a id="6291" class="Symbol">λ</a> <a id="6293" href="foundation.universal-property-truncation.html#6293" class="Bound">g</a> <a id="6295" class="Symbol">(</a><a id="6296" href="foundation.universal-property-truncation.html#6296" class="Bound">s</a> <a id="6298" class="Symbol">:</a> <a id="6300" class="Symbol">(</a><a id="6301" href="foundation.universal-property-truncation.html#6301" class="Bound">b</a> <a id="6303" class="Symbol">:</a> <a id="6305" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6325" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a><a id="6326" class="Symbol">)</a> <a id="6328" class="Symbol">→</a>
          <a id="6340" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6360" class="Symbol">(</a><a id="6361" href="foundation.universal-property-truncation.html#6067" class="Bound">X</a> <a id="6363" class="Symbol">(</a><a id="6364" href="foundation.universal-property-truncation.html#6293" class="Bound">g</a> <a id="6366" href="foundation.universal-property-truncation.html#6301" class="Bound">b</a><a id="6367" class="Symbol">)))</a> <a id="6371" class="Symbol">(</a><a id="6372" href="foundation.universal-property-truncation.html#6372" class="Bound">a</a> <a id="6374" class="Symbol">:</a> <a id="6376" href="foundation.universal-property-truncation.html#5743" class="Bound">A</a><a id="6377" class="Symbol">)</a> <a id="6379" class="Symbol">→</a> <a id="6381" href="foundation.universal-property-truncation.html#6296" class="Bound">s</a> <a id="6383" class="Symbol">(</a><a id="6384" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a> <a id="6386" href="foundation.universal-property-truncation.html#6372" class="Bound">a</a><a id="6387" class="Symbol">))</a>
        <a id="6398" class="Symbol">(</a> <a id="6400" href="foundation.universal-property-truncation.html#6065" class="Bound">H</a> <a id="6402" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a><a id="6403" class="Symbol">)</a>
        <a id="6413" class="Symbol">(</a> <a id="6415" href="foundation-core.equivalences.html#12773" class="Function">is-equiv-equiv</a>
          <a id="6440" class="Symbol">(</a> <a id="6442" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html#5106" class="Function">inv-distributive-Π-Σ</a><a id="6462" class="Symbol">)</a>
          <a id="6474" class="Symbol">(</a> <a id="6476" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html#5106" class="Function">inv-distributive-Π-Σ</a><a id="6496" class="Symbol">)</a>
          <a id="6508" class="Symbol">(</a> <a id="6510" href="foundation-core.dependent-pair-types.html#687" class="Function">ind-Σ</a> <a id="6516" class="Symbol">(λ</a> <a id="6519" href="foundation.universal-property-truncation.html#6519" class="Bound">g</a> <a id="6521" href="foundation.universal-property-truncation.html#6521" class="Bound">s</a> <a id="6523" class="Symbol">→</a> <a id="6525" href="foundation-core.identity-types.html#694" class="InductiveConstructor">refl</a><a id="6529" class="Symbol">))</a>
          <a id="6542" class="Symbol">(</a> <a id="6544" href="foundation.universal-property-truncation.html#6065" class="Bound">H</a> <a id="6546" class="Symbol">(</a><a id="6547" href="foundation-core.truncated-types.html#6052" class="Function">Σ-Truncated-Type</a> <a id="6564" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="6566" href="foundation.universal-property-truncation.html#6067" class="Bound">X</a><a id="6567" class="Symbol">)))</a>
        <a id="6579" class="Symbol">(</a> <a id="6581" href="foundation-core.functions.html#309" class="Function">id</a><a id="6583" class="Symbol">)</a>

  <a id="6588" class="Keyword">abstract</a>
    <a id="6601" href="foundation.universal-property-truncation.html#6601" class="Function">is-truncation-dependent-universal-property-truncation</a> <a id="6655" class="Symbol">:</a>
      <a id="6663" class="Symbol">({</a><a id="6665" href="foundation.universal-property-truncation.html#6665" class="Bound">l</a> <a id="6667" class="Symbol">:</a> <a id="6669" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="6674" class="Symbol">}</a> <a id="6676" class="Symbol">→</a> <a id="6678" href="foundation.universal-property-truncation.html#2955" class="Function">dependent-universal-property-truncation</a> <a id="6718" href="foundation.universal-property-truncation.html#6665" class="Bound">l</a> <a id="6720" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="6722" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a><a id="6723" class="Symbol">)</a> <a id="6725" class="Symbol">→</a>
      <a id="6733" class="Symbol">{</a><a id="6734" href="foundation.universal-property-truncation.html#6734" class="Bound">l</a> <a id="6736" class="Symbol">:</a> <a id="6738" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="6743" class="Symbol">}</a> <a id="6745" class="Symbol">→</a> <a id="6747" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="6761" href="foundation.universal-property-truncation.html#6734" class="Bound">l</a> <a id="6763" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="6765" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a>
    <a id="6771" href="foundation.universal-property-truncation.html#6601" class="Function">is-truncation-dependent-universal-property-truncation</a> <a id="6825" href="foundation.universal-property-truncation.html#6825" class="Bound">H</a> <a id="6827" href="foundation.universal-property-truncation.html#6827" class="Bound">X</a> <a id="6829" class="Symbol">=</a>
      <a id="6837" href="foundation.universal-property-truncation.html#6825" class="Bound">H</a> <a id="6839" class="Symbol">(λ</a> <a id="6842" href="foundation.universal-property-truncation.html#6842" class="Bound">b</a> <a id="6844" class="Symbol">→</a> <a id="6846" href="foundation.universal-property-truncation.html#6827" class="Bound">X</a><a id="6847" class="Symbol">)</a>

  <a id="6852" href="foundation.universal-property-truncation.html#6852" class="Function">sec-is-truncation</a> <a id="6870" class="Symbol">:</a>
    <a id="6876" class="Symbol">({</a><a id="6878" href="foundation.universal-property-truncation.html#6878" class="Bound">l</a> <a id="6880" class="Symbol">:</a> <a id="6882" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="6887" class="Symbol">}</a> <a id="6889" class="Symbol">→</a> <a id="6891" href="foundation.universal-property-truncation.html#1986" class="Function">is-truncation</a> <a id="6905" href="foundation.universal-property-truncation.html#6878" class="Bound">l</a> <a id="6907" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="6909" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a><a id="6910" class="Symbol">)</a> <a id="6912" class="Symbol">→</a>
    <a id="6918" class="Symbol">{</a><a id="6919" href="foundation.universal-property-truncation.html#6919" class="Bound">l3</a> <a id="6922" class="Symbol">:</a> <a id="6924" href="Agda.Primitive.html#597" class="Postulate">Level</a><a id="6929" class="Symbol">}</a> <a id="6931" class="Symbol">(</a><a id="6932" href="foundation.universal-property-truncation.html#6932" class="Bound">C</a> <a id="6934" class="Symbol">:</a> <a id="6936" href="foundation-core.truncated-types.html#1651" class="Function">UU-Truncated-Type</a> <a id="6954" href="foundation.universal-property-truncation.html#6919" class="Bound">l3</a> <a id="6957" href="foundation.universal-property-truncation.html#5735" class="Bound">k</a><a id="6958" class="Symbol">)</a>
    <a id="6964" class="Symbol">(</a><a id="6965" href="foundation.universal-property-truncation.html#6965" class="Bound">h</a> <a id="6967" class="Symbol">:</a> <a id="6969" href="foundation.universal-property-truncation.html#5743" class="Bound">A</a> <a id="6971" class="Symbol">→</a> <a id="6973" href="foundation-core.truncated-types.html#1792" class="Function">type-Truncated-Type</a> <a id="6993" href="foundation.universal-property-truncation.html#6932" class="Bound">C</a><a id="6994" class="Symbol">)</a> <a id="6996" class="Symbol">(</a><a id="6997" href="foundation.universal-property-truncation.html#6997" class="Bound">g</a> <a id="6999" class="Symbol">:</a> <a id="7001" href="foundation.truncated-types.html#3516" class="Function">type-hom-Truncated-Type</a> <a id="7025" href="foundation.universal-property-truncation.html#5735" class="Bound">k</a> <a id="7027" href="foundation.universal-property-truncation.html#6932" class="Bound">C</a> <a id="7029" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a><a id="7030" class="Symbol">)</a> <a id="7032" class="Symbol">→</a>
    <a id="7038" href="foundation.universal-property-truncation.html#5786" class="Bound">f</a> <a id="7040" href="foundation-core.homotopies.html#467" class="Function Operator">~</a> <a id="7042" class="Symbol">(</a><a id="7043" href="foundation.universal-property-truncation.html#6997" class="Bound">g</a> <a id="7045" href="foundation-core.functions.html#407" class="Function Operator">∘</a> <a id="7047" href="foundation.universal-property-truncation.html#6965" class="Bound">h</a><a id="7048" class="Symbol">)</a> <a id="7050" class="Symbol">→</a> <a id="7052" href="foundation-core.sections.html#521" class="Function">sec</a> <a id="7056" href="foundation.universal-property-truncation.html#6997" class="Bound">g</a>
  <a id="7060" href="foundation.universal-property-truncation.html#6852" class="Function">sec-is-truncation</a> <a id="7078" href="foundation.universal-property-truncation.html#7078" class="Bound">H</a> <a id="7080" href="foundation.universal-property-truncation.html#7080" class="Bound">C</a> <a id="7082" href="foundation.universal-property-truncation.html#7082" class="Bound">h</a> <a id="7084" href="foundation.universal-property-truncation.html#7084" class="Bound">g</a> <a id="7086" href="foundation.universal-property-truncation.html#7086" class="Bound">K</a> <a id="7088" class="Symbol">=</a>
    <a id="7094" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html#2808" class="Function">map-distributive-Π-Σ</a>
      <a id="7121" class="Symbol">(</a> <a id="7123" href="foundation-core.equivalences.html#4173" class="Function">map-inv-is-equiv</a>
        <a id="7148" class="Symbol">(</a> <a id="7150" href="foundation.universal-property-truncation.html#5841" class="Function">dependent-universal-property-truncation-is-truncation</a> <a id="7204" href="foundation.universal-property-truncation.html#7078" class="Bound">H</a>
          <a id="7216" class="Symbol">(</a> <a id="7218" href="foundation-core.truncated-types.html#6435" class="Function">fib-Truncated-Type</a> <a id="7237" href="foundation.universal-property-truncation.html#7080" class="Bound">C</a> <a id="7239" href="foundation.universal-property-truncation.html#5755" class="Bound">B</a> <a id="7241" href="foundation.universal-property-truncation.html#7084" class="Bound">g</a><a id="7242" class="Symbol">))</a>
        <a id="7253" class="Symbol">(</a> <a id="7255" class="Symbol">λ</a> <a id="7257" href="foundation.universal-property-truncation.html#7257" class="Bound">a</a> <a id="7259" class="Symbol">→</a> <a id="7261" href="foundation-core.dependent-pair-types.html#575" class="InductiveConstructor">pair</a> <a id="7266" class="Symbol">(</a><a id="7267" href="foundation.universal-property-truncation.html#7082" class="Bound">h</a> <a id="7269" href="foundation.universal-property-truncation.html#7257" class="Bound">a</a><a id="7270" class="Symbol">)</a> <a id="7272" class="Symbol">(</a><a id="7273" href="foundation-core.identity-types.html#1552" class="Function">inv</a> <a id="7277" class="Symbol">(</a><a id="7278" href="foundation.universal-property-truncation.html#7086" class="Bound">K</a> <a id="7280" href="foundation.universal-property-truncation.html#7257" class="Bound">a</a><a id="7281" class="Symbol">))))</a>
</pre>
## To do

<pre class="Agda">
<a id="7310" class="Comment">{-

-- Theorem 18.5.2 Condition (iii)

mere-eq-Eq-Rel : {l1 : Level} (A : UU l1) → Eq-Rel l1 A
mere-eq-Eq-Rel A =
  pair
    mere-eq-Prop
    ( pair refl-mere-eq (pair symm-mere-eq trans-mere-eq))

-- Theorem 18.5.2 (iii) implies (i)

reflects-mere-eq :
  {l1 l2 : Level} {A : UU l1} (X : UU-Set l2) (f : A → type-Set X) →
  reflects-Eq-Rel (mere-eq-Eq-Rel A) f
reflects-mere-eq X f {x} {y} r =
  apply-universal-property-trunc-Prop r
    ( Id-Prop X (f x) (f y))
    ( ap f)

reflecting-map-mere-eq :
  {l1 l2 : Level} {A : UU l1} (X : UU-Set l2) (f : A → type-Set X) →
  reflecting-map-Eq-Rel (mere-eq-Eq-Rel A) (type-Set X)
reflecting-map-mere-eq X f = pair f (reflects-mere-eq X f)

abstract
  is-set-truncation-is-set-quotient :
    {l1 l2 l3 : Level} {A : UU l1} (B : UU-Set l2) (f : A → type-Set B) →
    ( {l : Level} →
      is-set-quotient l (mere-eq-Eq-Rel A) B (reflecting-map-mere-eq B f)) →
    is-set-truncation l3 B f
  is-set-truncation-is-set-quotient {A = A} B f H X =
    is-equiv-comp
      ( precomp-Set f X)
      ( pr1)
      ( precomp-Set-Quotient
        ( mere-eq-Eq-Rel A)
        ( B)
        ( reflecting-map-mere-eq B f)
        ( X))
      ( refl-htpy)
      ( H X)
      ( is-equiv-pr1-is-contr
        ( λ h →
          is-proof-irrelevant-is-prop
            ( is-prop-reflects-Eq-Rel (mere-eq-Eq-Rel A) X h)
            ( reflects-mere-eq X h)))

abstract
  is-set-quotient-is-set-truncation :
    {l1 l2 l3 : Level} {A : UU l1} (B : UU-Set l2) (f : A → type-Set B) →
    ( {l : Level} → is-set-truncation l B f) →
    is-set-quotient l3 (mere-eq-Eq-Rel A) B (reflecting-map-mere-eq B f)
  is-set-quotient-is-set-truncation {A = A} B f H X =
    is-equiv-right-factor
      ( precomp-Set f X)
      ( pr1)
      ( precomp-Set-Quotient
        ( mere-eq-Eq-Rel A)
        ( B)
        ( reflecting-map-mere-eq B f)
        ( X))
      ( refl-htpy)
      ( is-equiv-pr1-is-contr
        ( λ h →
          is-proof-irrelevant-is-prop
            ( is-prop-reflects-Eq-Rel (mere-eq-Eq-Rel A) X h)
            ( reflects-mere-eq X h)))
      ( H X)

-- Definition 18.5.3

-- Corollary 18.5.4

reflecting-map-mere-eq-unit-trunc-Set :
  {l : Level} (A : UU l) →
  reflecting-map-Eq-Rel (mere-eq-Eq-Rel A) (type-trunc-Set A)
reflecting-map-mere-eq-unit-trunc-Set A =
  pair unit-trunc-Set (reflects-mere-eq (trunc-Set A) unit-trunc-Set)

abstract
  is-set-quotient-trunc-Set :
    {l1 l2 : Level} (A : UU l1) →
    is-set-quotient l2
      ( mere-eq-Eq-Rel A)
      ( trunc-Set A)
      ( reflecting-map-mere-eq-unit-trunc-Set A)
  is-set-quotient-trunc-Set A =
    is-set-quotient-is-set-truncation
      ( trunc-Set A)
      ( unit-trunc-Set)
      ( λ {l} → is-set-truncation-trunc-Set A)

abstract
  is-surjective-and-effective-unit-trunc-Set :
    {l1 : Level} (A : UU l1) →
    is-surjective-and-effective (mere-eq-Eq-Rel A) unit-trunc-Set
  is-surjective-and-effective-unit-trunc-Set A =
    is-surjective-and-effective-is-set-quotient
      ( mere-eq-Eq-Rel A)
      ( trunc-Set A)
      ( unit-trunc-Set)
      ( reflects-mere-eq (trunc-Set A) unit-trunc-Set)
      ( λ {l} → is-set-quotient-trunc-Set A)

abstract
  is-surjective-unit-trunc-Set :
    {l1 : Level} (A : UU l1) → is-surjective (unit-trunc-Set {A = A})
  is-surjective-unit-trunc-Set A =
    pr1 (is-surjective-and-effective-unit-trunc-Set A)

abstract
  is-effective-unit-trunc-Set :
    {l1 : Level} (A : UU l1) →
    is-effective (mere-eq-Eq-Rel A) (unit-trunc-Set {A = A})
  is-effective-unit-trunc-Set A =
    pr2 (is-surjective-and-effective-unit-trunc-Set A)

abstract
  apply-effectiveness-unit-trunc-Set :
    {l1 : Level} {A : UU l1} {x y : A} →
    Id (unit-trunc-Set x) (unit-trunc-Set y) → mere-eq x y
  apply-effectiveness-unit-trunc-Set {A = A} {x} {y} =
    map-equiv (is-effective-unit-trunc-Set A x y)

abstract
  apply-effectiveness-unit-trunc-Set&#39; :
    {l1 : Level} {A : UU l1} {x y : A} →
    mere-eq x y → Id (unit-trunc-Set x) (unit-trunc-Set y)
  apply-effectiveness-unit-trunc-Set&#39; {A = A} {x} {y} =
    map-inv-equiv (is-effective-unit-trunc-Set A x y)

emb-trunc-Set :
  {l1 : Level} (A : UU l1) → type-trunc-Set A ↪ (A → UU-Prop l1)
emb-trunc-Set A =
  emb-is-surjective-and-effective
    ( mere-eq-Eq-Rel A)
    ( trunc-Set A)
    ( unit-trunc-Set)
    ( is-surjective-and-effective-unit-trunc-Set A)

hom-slice-trunc-Set :
  {l1 : Level} (A : UU l1) →
  hom-slice (mere-eq-Prop {A = A}) (map-emb (emb-trunc-Set A))
hom-slice-trunc-Set A =
  pair
    ( unit-trunc-Set)
    ( triangle-emb-is-surjective-and-effective
      ( mere-eq-Eq-Rel A)
      ( trunc-Set A)
      ( unit-trunc-Set)
      ( is-surjective-and-effective-unit-trunc-Set A))

abstract
  is-image-trunc-Set :
    {l1 l2 : Level} (A : UU l1) →
    is-image l2
      ( mere-eq-Prop {A = A})
      ( emb-trunc-Set A)
      ( hom-slice-trunc-Set A)
  is-image-trunc-Set A =
    is-image-is-surjective-and-effective
      ( mere-eq-Eq-Rel A)
      ( trunc-Set A)
      ( unit-trunc-Set)
      ( is-surjective-and-effective-unit-trunc-Set A)

-- Uniqueness of trunc-Set

module _
  {l1 l2 : Level} {A : UU l1} (B : UU-Set l2) (f : A → type-Set B)
  {h : type-hom-Set B (trunc-Set A)} (H : (h ∘ f) ~ unit-trunc-Set)
  where

  abstract
    is-equiv-is-set-truncation&#39; :
      ({l : Level} → is-set-truncation l B f) → is-equiv h
    is-equiv-is-set-truncation&#39; Sf =
      is-equiv-is-set-truncation-is-set-truncation
        ( B)
        ( f)
        ( trunc-Set A)
        ( unit-trunc-Set)
        ( H)
        ( Sf)
        ( λ {h} → is-set-truncation-trunc-Set A)

  abstract
    is-set-truncation-is-equiv&#39; :
      is-equiv h → ({l : Level} → is-set-truncation l B f)
    is-set-truncation-is-equiv&#39; Eh =
      is-set-truncation-is-equiv-is-set-truncation
        ( B)
        ( f)
        ( trunc-Set A)
        ( unit-trunc-Set)
        ( H)
        ( λ {l} → is-set-truncation-trunc-Set A)
        ( Eh)

module _
  {l1 l2 : Level} {A : UU l1} (B : UU-Set l2) (f : A → type-Set B)
  {h : type-hom-Set (trunc-Set A) B} (H : (h ∘ unit-trunc-Set) ~ f)
  where

  abstract
    is-equiv-is-set-truncation :
      ({l : Level} → is-set-truncation l B f) → is-equiv h
    is-equiv-is-set-truncation Sf =
      is-equiv-is-set-truncation-is-set-truncation
        ( trunc-Set A)
        ( unit-trunc-Set)
        ( B)
        ( f)
        ( H)
        ( λ {l} → is-set-truncation-trunc-Set A)
        ( Sf)

  abstract
    is-set-truncation-is-equiv :
      is-equiv h → ({l : Level} → is-set-truncation l B f)
    is-set-truncation-is-equiv Eh =
      is-set-truncation-is-set-truncation-is-equiv
        ( trunc-Set A)
        ( unit-trunc-Set)
        ( B)
        ( f)
        ( H)
        ( Eh)
        ( λ {l} → is-set-truncation-trunc-Set A)

abstract
  is-equiv-unit-trunc-Set :
    {l : Level} (A : UU-Set l) → is-equiv (unit-trunc-Set {A = type-Set A})
  is-equiv-unit-trunc-Set A =
    is-equiv-is-set-truncation&#39; A id refl-htpy
      ( is-set-truncation-id (is-set-type-Set A))

equiv-unit-trunc-Set :
  {l : Level} (A : UU-Set l) → type-Set A ≃ type-trunc-Set (type-Set A)
equiv-unit-trunc-Set A =
  pair unit-trunc-Set (is-equiv-unit-trunc-Set A)

equiv-unit-trunc-empty-Set : empty ≃ type-trunc-Set empty
equiv-unit-trunc-empty-Set = equiv-unit-trunc-Set empty-Set

abstract
  is-empty-trunc-Set :
    {l : Level} {A : UU l} → is-empty A → is-empty (type-trunc-Set A)
  is-empty-trunc-Set f x = apply-universal-property-trunc-Set x empty-Set f

abstract
  is-empty-is-empty-trunc-Set :
    {l : Level} {A : UU l} → is-empty (type-trunc-Set A) → is-empty A
  is-empty-is-empty-trunc-Set f = f ∘ unit-trunc-Set

equiv-unit-trunc-unit-Set : unit ≃ type-trunc-Set unit
equiv-unit-trunc-unit-Set = equiv-unit-trunc-Set unit-Set

equiv-unit-trunc-ℕ-Set : ℕ ≃ type-trunc-Set ℕ
equiv-unit-trunc-ℕ-Set = equiv-unit-trunc-Set ℕ-Set

equiv-unit-trunc-ℤ-Set : ℤ ≃ type-trunc-Set ℤ
equiv-unit-trunc-ℤ-Set = equiv-unit-trunc-Set ℤ-Set

equiv-unit-trunc-Fin-Set : (k : ℕ) → Fin k ≃ type-trunc-Set (Fin k)
equiv-unit-trunc-Fin-Set k = equiv-unit-trunc-Set (Fin-Set k)

abstract
  is-contr-trunc-Set :
    {l : Level} {A : UU l} → is-contr A → is-contr (type-trunc-Set A)
  is-contr-trunc-Set {l} {A} H =
    is-contr-equiv&#39;
      ( A)
      ( equiv-unit-trunc-Set (pair A (is-set-is-contr H)))
      ( H)

module _
  {l1 l2 : Level} {A : UU l1} (B : UU-Set l2) (f : A → type-Set B)
  (Sf : {l : Level} → is-set-truncation l B f)
  where

  abstract
    uniqueness-trunc-Set :
      is-contr
        ( Σ (type-trunc-Set A ≃ type-Set B)
        ( λ e → (map-equiv e ∘ unit-trunc-Set) ~ f))
    uniqueness-trunc-Set =
      uniqueness-set-truncation (trunc-Set A) unit-trunc-Set B f
        ( λ {l} → is-set-truncation-trunc-Set A)
        ( Sf)

  equiv-uniqueness-trunc-Set : type-trunc-Set A ≃ type-Set B
  equiv-uniqueness-trunc-Set =
    pr1 (center uniqueness-trunc-Set)

  map-equiv-uniqueness-trunc-Set : type-trunc-Set A → type-Set B
  map-equiv-uniqueness-trunc-Set =
    map-equiv equiv-uniqueness-trunc-Set

  triangle-uniqueness-trunc-Set :
    (map-equiv-uniqueness-trunc-Set ∘ unit-trunc-Set) ~ f
  triangle-uniqueness-trunc-Set =
    pr2 (center uniqueness-trunc-Set)

module _
  {l1 l2 : Level} {A : UU l1} (B : UU-Set l2) (f : A → type-Set B)
  (Sf : {l : Level} → is-set-truncation l B f)
  where

  abstract
    uniqueness-trunc-Set&#39; :
      is-contr
        ( Σ ( type-Set B ≃ type-trunc-Set A)
            ( λ e → (map-equiv e ∘ f) ~ unit-trunc-Set))
    uniqueness-trunc-Set&#39; =
      uniqueness-set-truncation B f (trunc-Set A) unit-trunc-Set Sf
        ( λ {l} → is-set-truncation-trunc-Set A)

  equiv-uniqueness-trunc-Set&#39; : type-Set B ≃ type-trunc-Set A
  equiv-uniqueness-trunc-Set&#39; =
    pr1 (center uniqueness-trunc-Set&#39;)

  map-equiv-uniqueness-trunc-Set&#39; : type-Set B → type-trunc-Set A
  map-equiv-uniqueness-trunc-Set&#39; =
    map-equiv equiv-uniqueness-trunc-Set&#39;
  
  triangle-uniqueness-trunc-Set&#39; :
    (map-equiv-uniqueness-trunc-Set&#39; ∘ f) ~ unit-trunc-Set
  triangle-uniqueness-trunc-Set&#39; =
    pr2 (center uniqueness-trunc-Set&#39;)

-- Proposition 18.5.5

module _
  {l1 l2 : Level} {A : UU l1} {B : UU l2} (f : A → B)
  where

  abstract
    unique-map-trunc-Set :
      is-contr
        ( Σ ( type-trunc-Set A → type-trunc-Set B)
            ( λ h → (h ∘ unit-trunc-Set) ~ (unit-trunc-Set ∘ f)))
    unique-map-trunc-Set =
      universal-property-trunc-Set A (trunc-Set B) (unit-trunc-Set ∘ f)

  map-trunc-Set :
    type-trunc-Set A → type-trunc-Set B
  map-trunc-Set =
    pr1 (center unique-map-trunc-Set)

  naturality-trunc-Set :
    (map-trunc-Set ∘ unit-trunc-Set) ~ (unit-trunc-Set ∘ f)
  naturality-trunc-Set =
    pr2 (center unique-map-trunc-Set)

  htpy-map-trunc-Set :
    (h : type-trunc-Set A → type-trunc-Set B) →
    (H : (h ∘ unit-trunc-Set) ~ (unit-trunc-Set ∘ f)) →
    map-trunc-Set ~ h
  htpy-map-trunc-Set h H =
    htpy-eq
      ( ap pr1
        ( eq-is-contr unique-map-trunc-Set
          { pair map-trunc-Set naturality-trunc-Set}
          { pair h H}))

map-id-trunc-Set :
  {l1 : Level} {A : UU l1} → map-trunc-Set (id {A = A}) ~ id
map-id-trunc-Set {l1} {A} =
  htpy-eq
    ( ap pr1
      ( eq-is-contr
        ( universal-property-trunc-Set A (trunc-Set A) unit-trunc-Set)
        { pair (map-trunc-Set id) (naturality-trunc-Set id)}
        { pair id refl-htpy}))

map-comp-trunc-Set :
  {l1 l2 l3 : Level} {A : UU l1} {B : UU l2} {C : UU l3}
  (g : B → C) (f : A → B) →
  map-trunc-Set (g ∘ f) ~ (map-trunc-Set g ∘ map-trunc-Set f)
map-comp-trunc-Set {A = A} {C = C} g f =
  htpy-eq
    ( ap pr1
      ( eq-is-contr
        ( universal-property-trunc-Set
          A
          (trunc-Set C)
          (unit-trunc-Set ∘ (g ∘ f)))
        { pair (map-trunc-Set (g ∘ f)) (naturality-trunc-Set (g ∘ f))}
        { pair ( map-trunc-Set g ∘ map-trunc-Set f)
               ( ( map-trunc-Set g ·l naturality-trunc-Set f) ∙h
                 ( naturality-trunc-Set g ·r f))}))

htpy-trunc-Set :
  {l1 l2 : Level} {A : UU l1} {B : UU l2} {f g : A → B} →
  (f ~ g) → (map-trunc-Set f ~ map-trunc-Set g)
htpy-trunc-Set {B = B} {f = f} {g} H =
  map-inv-is-equiv
    ( dependent-universal-property-trunc-Set
      ( λ x →
        set-Prop
          ( Id-Prop (trunc-Set B) (map-trunc-Set f x) (map-trunc-Set g x))))
    ( λ a →
      ( naturality-trunc-Set f a) ∙
      ( ( ap unit-trunc-Set (H a)) ∙
        ( inv (naturality-trunc-Set g a))))

abstract
  is-equiv-map-trunc-Set :
    {l1 l2 : Level} {A : UU l1} {B : UU l2} {f : A → B} →
    is-equiv f → is-equiv (map-trunc-Set f)
  is-equiv-map-trunc-Set {f = f} H =
    pair
      ( pair
        ( map-trunc-Set (pr1 (pr1 H)))
        ( ( inv-htpy (map-comp-trunc-Set f (pr1 (pr1 H)))) ∙h
          ( ( htpy-trunc-Set (pr2 (pr1 H))) ∙h
            ( map-id-trunc-Set))))
      ( pair
        ( map-trunc-Set (pr1 (pr2 H)))
        ( ( inv-htpy (map-comp-trunc-Set (pr1 (pr2 H)) f)) ∙h
          ( ( htpy-trunc-Set (pr2 (pr2 H))) ∙h
            ( map-id-trunc-Set))))

equiv-trunc-Set :
  {l1 l2 : Level} {A : UU l1} {B : UU l2} →
  (A ≃ B) → (type-trunc-Set A ≃ type-trunc-Set B)
equiv-trunc-Set e =
  pair
    ( map-trunc-Set (map-equiv e))
    ( is-equiv-map-trunc-Set (is-equiv-map-equiv e))

map-equiv-trunc-Set :
  {l1 l2 : Level} {A : UU l1} {B : UU l2} →
  (A ≃ B) → type-trunc-Set A → type-trunc-Set B
map-equiv-trunc-Set e = map-equiv (equiv-trunc-Set e)

--------------------------------------------------------------------------------

module _
  {l1 l2 : Level} (A : UU l1) (B : UU l2)
  where

  abstract
    distributive-trunc-coprod-Set :
      is-contr
        ( Σ ( type-equiv-Set
              ( trunc-Set (coprod A B))
              ( coprod-Set (trunc-Set A) (trunc-Set B)))
            ( λ e →
              ( map-equiv e ∘ unit-trunc-Set) ~
              ( map-coprod unit-trunc-Set unit-trunc-Set)))
    distributive-trunc-coprod-Set =
      uniqueness-trunc-Set
        ( coprod-Set (trunc-Set A) (trunc-Set B))
        ( map-coprod unit-trunc-Set unit-trunc-Set)
        ( λ {l} C →
          is-equiv-right-factor&#39;
            ( ev-inl-inr (λ x → type-Set C))
            ( precomp-Set (map-coprod unit-trunc-Set unit-trunc-Set) C)
            ( universal-property-coprod (type-Set C))
            ( is-equiv-comp&#39;
              ( map-prod
                ( precomp-Set unit-trunc-Set C)
                ( precomp-Set unit-trunc-Set C))
              ( ev-inl-inr (λ x → type-Set C))
              ( universal-property-coprod (type-Set C))
              ( is-equiv-map-prod
                ( precomp-Set unit-trunc-Set C)
                ( precomp-Set unit-trunc-Set C)
                ( is-set-truncation-trunc-Set A C)
                ( is-set-truncation-trunc-Set B C))))

  equiv-distributive-trunc-coprod-Set :
    type-equiv-Set
      ( trunc-Set (coprod A B))
      ( coprod-Set (trunc-Set A) (trunc-Set B))
  equiv-distributive-trunc-coprod-Set =
    pr1 (center distributive-trunc-coprod-Set)

  map-equiv-distributive-trunc-coprod-Set :
    type-hom-Set
      ( trunc-Set (coprod A B))
      ( coprod-Set (trunc-Set A) (trunc-Set B))
  map-equiv-distributive-trunc-coprod-Set =
    map-equiv equiv-distributive-trunc-coprod-Set

  triangle-distributive-trunc-coprod-Set :
    ( map-equiv-distributive-trunc-coprod-Set ∘ unit-trunc-Set) ~
    ( map-coprod unit-trunc-Set unit-trunc-Set)
  triangle-distributive-trunc-coprod-Set =
    pr2 (center distributive-trunc-coprod-Set)

-- Set truncations of Σ-types

module _
  {l1 l2 : Level} (A : UU l1) (B : A → UU l2)
  where

  abstract
    trunc-Σ-Set :
      is-contr
        ( Σ ( type-trunc-Set (Σ A B) ≃
              type-trunc-Set (Σ A (λ x → type-trunc-Set (B x))))
            ( λ e →
              ( map-equiv e ∘ unit-trunc-Set) ~
              ( unit-trunc-Set ∘ tot (λ x → unit-trunc-Set))))
    trunc-Σ-Set =
      uniqueness-trunc-Set
        ( trunc-Set (Σ A (λ x → type-trunc-Set (B x))))
        ( unit-trunc-Set ∘ tot (λ x → unit-trunc-Set))
        ( λ {l} C →
          is-equiv-right-factor&#39;
            ( ev-pair)
            ( precomp-Set (unit-trunc-Set ∘ tot (λ x → unit-trunc-Set)) C)
            ( is-equiv-ev-pair)
            ( is-equiv-htpy-equiv
              ( ( equiv-map-Π
                  ( λ x → equiv-universal-property-trunc-Set (B x) C)) ∘e
                ( ( equiv-ev-pair) ∘e
                  ( equiv-universal-property-trunc-Set
                    ( Σ A (type-trunc-Set ∘ B)) C)))
              ( refl-htpy)))

  equiv-trunc-Σ-Set :
    type-trunc-Set (Σ A B) ≃ type-trunc-Set (Σ A (λ x → type-trunc-Set (B x)))
  equiv-trunc-Σ-Set =
    pr1 (center trunc-Σ-Set)

  map-equiv-trunc-Σ-Set :
    type-trunc-Set (Σ A B) → type-trunc-Set (Σ A (λ x → type-trunc-Set (B x)))
  map-equiv-trunc-Σ-Set =
    map-equiv equiv-trunc-Σ-Set

  square-trunc-Σ-Set :
    ( map-equiv-trunc-Σ-Set ∘ unit-trunc-Set) ~
    ( unit-trunc-Set ∘ tot (λ x → unit-trunc-Set))
  square-trunc-Σ-Set =
    pr2 (center trunc-Σ-Set)

  htpy-map-equiv-trunc-Σ-Set :
    map-trunc-Set (tot (λ x → unit-trunc-Set)) ~ map-equiv-trunc-Σ-Set
  htpy-map-equiv-trunc-Σ-Set =
    htpy-map-trunc-Set
      ( tot (λ x → unit-trunc-Set))
      ( map-equiv-trunc-Σ-Set)
      ( square-trunc-Σ-Set)

  abstract
    is-equiv-map-trunc-tot-unit-trunc-Set :
      is-equiv (map-trunc-Set (tot (λ (x : A) → unit-trunc-Set {A = B x})))
    is-equiv-map-trunc-tot-unit-trunc-Set =
      is-equiv-htpy-equiv
        ( equiv-trunc-Σ-Set)
        ( htpy-map-equiv-trunc-Σ-Set)

-- trunc-Set distributes over products

module _
  {l1 l2 : Level} (A : UU l1) (B : UU l2)
  where

  abstract
    distributive-trunc-prod-Set :
      is-contr
        ( Σ ( type-trunc-Set (A × B) ≃ ( type-trunc-Set A × type-trunc-Set B))
            ( λ e →
              ( map-equiv e ∘ unit-trunc-Set) ~
              ( map-prod unit-trunc-Set unit-trunc-Set)))
    distributive-trunc-prod-Set =
      uniqueness-trunc-Set
        ( prod-Set (trunc-Set A) (trunc-Set B))
        ( map-prod unit-trunc-Set unit-trunc-Set)
        ( λ {l} C →
          is-equiv-right-factor&#39;
            ( ev-pair)
            ( precomp-Set (map-prod unit-trunc-Set unit-trunc-Set) C)
            ( is-equiv-ev-pair)
            ( is-equiv-htpy-equiv
              ( ( equiv-universal-property-trunc-Set A (Π-Set&#39; B (λ y → C))) ∘e
                ( ( equiv-postcomp
                    ( type-trunc-Set A)
                    (equiv-universal-property-trunc-Set B C)) ∘e
                  ( equiv-ev-pair)))
              ( refl-htpy)))

  equiv-distributive-trunc-prod-Set :
    type-trunc-Set (A × B) ≃ ( type-trunc-Set A × type-trunc-Set B)
  equiv-distributive-trunc-prod-Set =
    pr1 (center distributive-trunc-prod-Set)

  map-equiv-distributive-trunc-prod-Set :
    type-trunc-Set (A × B) → type-trunc-Set A × type-trunc-Set B
  map-equiv-distributive-trunc-prod-Set =
    map-equiv equiv-distributive-trunc-prod-Set

  triangle-distributive-trunc-prod-Set :
    ( map-equiv-distributive-trunc-prod-Set ∘ unit-trunc-Set) ~
    ( map-prod unit-trunc-Set unit-trunc-Set)
  triangle-distributive-trunc-prod-Set =
    pr2 (center distributive-trunc-prod-Set)

-- trunc-Set distributes over Π indexed by Fin

abstract
  distributive-trunc-Π-Fin-Set :
    {l : Level} (k : ℕ) (A : Fin k → UU l) →
    is-contr
      ( Σ ( ( type-trunc-Set ((x : Fin k) → A x)) ≃
            ( (x : Fin k) → type-trunc-Set (A x)))
          ( λ e →
            ( map-equiv e ∘ unit-trunc-Set) ~
            ( map-Π (λ x → unit-trunc-Set))))
  distributive-trunc-Π-Fin-Set zero-ℕ A =
    uniqueness-trunc-Set
      ( Π-Set empty-Set (λ x → trunc-Set (A x)))
      ( map-Π (λ x → unit-trunc-Set))
      ( λ {l} B →
        is-equiv-precomp-is-equiv
          ( map-Π (λ x → unit-trunc-Set))
          ( is-equiv-is-contr
            ( map-Π (λ x → unit-trunc-Set))
            ( dependent-universal-property-empty&#39; A)
            ( dependent-universal-property-empty&#39; (type-trunc-Set ∘ A)))
          ( type-Set B))
  distributive-trunc-Π-Fin-Set (succ-ℕ k) A =
    uniqueness-trunc-Set
      ( Π-Set (Fin-Set (succ-ℕ k)) (λ x → trunc-Set (A x)))
      ( map-Π (λ x → unit-trunc-Set))
      ( λ {l} B →
        is-equiv-left-factor&#39;
          ( precomp (map-Π (λ x → unit-trunc-Set)) (type-Set B))
          ( precomp (ev-Maybe {B = type-trunc-Set ∘ A}) (type-Set B))
          ( is-equiv-comp&#39;
            ( precomp ev-Maybe (type-Set B))
            ( precomp
              ( map-prod (map-Π (λ x → unit-trunc-Set)) unit-trunc-Set)
              ( type-Set B))
            ( is-equiv-right-factor&#39;
              ( ev-pair)
              ( precomp
                ( map-prod (map-Π (λ x → unit-trunc-Set)) unit-trunc-Set)
                ( type-Set B))
              ( is-equiv-ev-pair)
              ( is-equiv-htpy-equiv
                ( ( ( pair
                      ( precomp
                        ( (map-Π (λ x → unit-trunc-Set)))
                        ( A (inr star) → type-Set B))
                      ( is-set-truncation-is-equiv
                        ( Π-Set (Fin-Set k) (λ x → trunc-Set (A (inl x))))
                        ( map-Π (λ x → unit-trunc-Set))
                        { map-equiv
                          ( pr1
                            ( center
                              ( distributive-trunc-Π-Fin-Set k (A ∘ inl))))}
                        ( pr2
                          ( center (distributive-trunc-Π-Fin-Set k (A ∘ inl))))
                        ( is-equiv-map-equiv
                          ( pr1
                            ( center
                              ( distributive-trunc-Π-Fin-Set k (A ∘ inl)))))
                        ( Π-Set&#39; (A (inr star)) (λ a → B)))) ∘e
                    ( equiv-postcomp
                      ( (x : Fin k) → type-trunc-Set (A (inl x)))
                      ( equiv-universal-property-trunc-Set
                        ( A (inr star))
                        ( B)))) ∘e
                  ( equiv-ev-pair))
                ( refl-htpy)))
            ( is-equiv-precomp-is-equiv
              ( ev-Maybe)
              ( dependent-universal-property-Maybe)
              ( type-Set B)))
          ( is-equiv-precomp-is-equiv
            ( ev-Maybe)
            ( dependent-universal-property-Maybe)
            ( type-Set B)))

module _
  {l : Level} (k : ℕ) (A : Fin k → UU l)
  where

  equiv-distributive-trunc-Π-Fin-Set :
    type-trunc-Set ((x : Fin k) → A x) ≃ ((x : Fin k) → type-trunc-Set (A x))
  equiv-distributive-trunc-Π-Fin-Set =
    pr1 (center (distributive-trunc-Π-Fin-Set k A))

  map-equiv-distributive-trunc-Π-Fin-Set :
    type-trunc-Set ((x : Fin k) → A x) → ((x : Fin k) → type-trunc-Set (A x))
  map-equiv-distributive-trunc-Π-Fin-Set =
    map-equiv equiv-distributive-trunc-Π-Fin-Set

  triangle-distributive-trunc-Π-Fin-Set :
    ( map-equiv-distributive-trunc-Π-Fin-Set ∘ unit-trunc-Set) ~
    ( map-Π (λ x → unit-trunc-Set))
  triangle-distributive-trunc-Π-Fin-Set =
    pr2 (center (distributive-trunc-Π-Fin-Set k A))

module _
  {l1 l2 : Level} {A : UU l1} (B : A → UU l2)
  where

  abstract
    distributive-trunc-Π-count-Set :
      count A → 
      is-contr
        ( Σ ( ( type-trunc-Set ((x : A) → B x)) ≃
              ( (x : A) → type-trunc-Set (B x)))
            ( λ e →
              ( map-equiv e ∘ unit-trunc-Set) ~
              ( map-Π (λ x → unit-trunc-Set))))
    distributive-trunc-Π-count-Set (pair k e) =
      is-contr-equiv
        ( Σ ( ( type-trunc-Set ((x : A) → B x)) ≃
              ( (x : Fin k) → type-trunc-Set (B (map-equiv e x))))
            ( λ f →
              ( map-equiv f ∘ unit-trunc-Set) ~
              ( map-Π (λ x → unit-trunc-Set) ∘ precomp-Π (map-equiv e) B)))
        ( equiv-Σ
          ( λ f →
            ( map-equiv f ∘ unit-trunc-Set) ~
            ( map-Π (λ x → unit-trunc-Set) ∘ precomp-Π (map-equiv e) B))
          ( equiv-postcomp-equiv
            ( equiv-precomp-Π e (type-trunc-Set ∘ B))
            ( type-trunc-Set ((x : A) → B x)))
          ( λ f →
            equiv-map-Π
              ( λ h →
                ( ( inv-equiv equiv-funext) ∘e
                  ( equiv-precomp-Π e
                    ( λ x → Id ((map-equiv f ∘ unit-trunc-Set) h x)
                    ( map-Π (λ y → unit-trunc-Set) h x)))) ∘e
                ( equiv-funext))))
        ( is-contr-equiv&#39;
          ( Σ ( ( type-trunc-Set ((x : Fin k) → B (map-equiv e x))) ≃
                ( (x : Fin k) → type-trunc-Set (B (map-equiv e x))))
              ( λ f →
                ( map-equiv f ∘ unit-trunc-Set) ~
                ( map-Π (λ x → unit-trunc-Set))))
          ( equiv-Σ
            ( λ f →
              ( map-equiv f ∘ unit-trunc-Set) ~
              ( map-Π (λ x → unit-trunc-Set) ∘ precomp-Π (map-equiv e) B))
            ( equiv-precomp-equiv
              ( equiv-trunc-Set (equiv-precomp-Π e B))
              ( (x : Fin k) → type-trunc-Set (B (map-equiv e x))))
            ( λ f →
              equiv-Π
                ( λ h →
                  Id ( map-equiv f
                       ( map-equiv
                         ( equiv-trunc-Set (equiv-precomp-Π e B))
                         ( unit-trunc-Set h)))
                     ( map-Π (λ x → unit-trunc-Set) (λ x → h (map-equiv e x))))
                ( equiv-Π B e (λ x → id-equiv))
                ( λ h →
                  ( ( inv-equiv equiv-funext) ∘e
                    ( equiv-Π
                      ( λ x →
                        Id ( map-equiv f
                             ( map-equiv-trunc-Set
                               ( equiv-precomp-Π e B)
                               ( unit-trunc-Set
                                 ( map-equiv-Π B e (λ x → id-equiv) h)))
                             ( x))
                           ( unit-trunc-Set
                             ( map-equiv-Π B e
                               ( λ z → id-equiv)
                               ( h)
                               ( map-equiv e x))))
                      ( id-equiv)
                      ( λ x →
                        ( equiv-concat
                          ( ap
                            ( λ t → map-equiv f t x)
                            ( ( naturality-trunc-Set (precomp-Π (map-equiv e) B)
                                ( map-equiv-Π B e (λ _ → id-equiv) h)) ∙
                              ( ap
                                ( unit-trunc-Set)
                                ( eq-htpy
                                  ( compute-map-equiv-Π B e
                                    ( λ _ → id-equiv)
                                    ( h))))))
                          ( unit-trunc-Set
                            ( map-equiv-Π B e
                              ( λ _ → id-equiv)
                              ( h)
                              ( map-equiv e x)))) ∘e
                        ( equiv-concat&#39;
                          ( map-equiv f (unit-trunc-Set h) x)
                          ( ap unit-trunc-Set
                            ( inv
                              ( compute-map-equiv-Π B e
                                ( λ _ → id-equiv)
                                ( h)
                                ( x)))))))) ∘e
                  ( equiv-funext))))
          ( distributive-trunc-Π-Fin-Set k (B ∘ map-equiv e)))

module _
  {l1 l2 : Level} {A : UU l1} (B : A → UU l2) (c : count A)
  where

  equiv-distributive-trunc-Π-count-Set :
    ( type-trunc-Set ((x : A) → B x)) ≃ ((x : A) → type-trunc-Set (B x))
  equiv-distributive-trunc-Π-count-Set =
    pr1 (center (distributive-trunc-Π-count-Set B c))

  map-equiv-distributive-trunc-Π-count-Set :
    ( type-trunc-Set ((x : A) → B x)) → ((x : A) → type-trunc-Set (B x))
  map-equiv-distributive-trunc-Π-count-Set =
    map-equiv equiv-distributive-trunc-Π-count-Set

  triangle-distributive-trunc-Π-count-Set :
    ( map-equiv-distributive-trunc-Π-count-Set ∘ unit-trunc-Set) ~
    ( map-Π (λ x → unit-trunc-Set))
  triangle-distributive-trunc-Π-count-Set =
    pr2 (center (distributive-trunc-Π-count-Set B c))

module _
  {l1 l2 : Level} {A : UU l1} (B : A → UU l2) (H : is-finite A)
  where

  abstract
    distributive-trunc-Π-is-finite-Set :
      is-contr
        ( Σ ( ( type-trunc-Set ((x : A) → B x)) ≃
              ( (x : A) → type-trunc-Set (B x)))
            ( λ e →
              ( map-equiv e ∘ unit-trunc-Set) ~
              ( map-Π (λ x → unit-trunc-Set))))
    distributive-trunc-Π-is-finite-Set =
      apply-universal-property-trunc-Prop H
        ( is-contr-Prop _)
        ( distributive-trunc-Π-count-Set B)

  equiv-distributive-trunc-Π-is-finite-Set :
    ( type-trunc-Set ((x : A) → B x)) ≃ ((x : A) → type-trunc-Set (B x))
  equiv-distributive-trunc-Π-is-finite-Set =
    pr1 (center distributive-trunc-Π-is-finite-Set)

  map-equiv-distributive-trunc-Π-is-finite-Set :
    ( type-trunc-Set ((x : A) → B x)) → ((x : A) → type-trunc-Set (B x))
  map-equiv-distributive-trunc-Π-is-finite-Set =
    map-equiv equiv-distributive-trunc-Π-is-finite-Set

  triangle-distributive-trunc-Π-is-finite-Set :
    ( map-equiv-distributive-trunc-Π-is-finite-Set ∘ unit-trunc-Set) ~
    ( map-Π (λ x → unit-trunc-Set))
  triangle-distributive-trunc-Π-is-finite-Set =
    pr2 (center distributive-trunc-Π-is-finite-Set)
    -}</a>
</pre>