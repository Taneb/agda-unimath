# Foundation

<pre class="Agda"><a id="23" class="Symbol">{-#</a> <a id="27" class="Keyword">OPTIONS</a> <a id="35" class="Pragma">--without-K</a> <a id="47" class="Pragma">--exact-split</a> <a id="61" class="Symbol">#-}</a>

<a id="66" class="Keyword">module</a> <a id="73" href="foundation.html" class="Module">foundation</a> <a id="84" class="Keyword">where</a>

<a id="91" class="Keyword">open</a> <a id="96" class="Keyword">import</a> <a id="103" href="foundation.0-maps.html" class="Module">foundation.0-maps</a> <a id="121" class="Keyword">public</a>
<a id="128" class="Keyword">open</a> <a id="133" class="Keyword">import</a> <a id="140" href="foundation.1-types.html" class="Module">foundation.1-types</a> <a id="159" class="Keyword">public</a>
<a id="166" class="Keyword">open</a> <a id="171" class="Keyword">import</a> <a id="178" href="foundation.2-types.html" class="Module">foundation.2-types</a> <a id="197" class="Keyword">public</a>
<a id="204" class="Keyword">open</a> <a id="209" class="Keyword">import</a> <a id="216" href="foundation.algebras-polynomial-endofunctors.html" class="Module">foundation.algebras-polynomial-endofunctors</a> <a id="260" class="Keyword">public</a>
<a id="267" class="Keyword">open</a> <a id="272" class="Keyword">import</a> <a id="279" href="foundation.automorphisms.html" class="Module">foundation.automorphisms</a> <a id="304" class="Keyword">public</a>
<a id="311" class="Keyword">open</a> <a id="316" class="Keyword">import</a> <a id="323" href="foundation.axiom-of-choice.html" class="Module">foundation.axiom-of-choice</a> <a id="350" class="Keyword">public</a>
<a id="357" class="Keyword">open</a> <a id="362" class="Keyword">import</a> <a id="369" href="foundation.binary-embeddings.html" class="Module">foundation.binary-embeddings</a> <a id="398" class="Keyword">public</a>
<a id="405" class="Keyword">open</a> <a id="410" class="Keyword">import</a> <a id="417" href="foundation.binary-equivalences.html" class="Module">foundation.binary-equivalences</a> <a id="448" class="Keyword">public</a>
<a id="455" class="Keyword">open</a> <a id="460" class="Keyword">import</a> <a id="467" href="foundation.binary-relations.html" class="Module">foundation.binary-relations</a> <a id="495" class="Keyword">public</a>
<a id="502" class="Keyword">open</a> <a id="507" class="Keyword">import</a> <a id="514" href="foundation.boolean-reflection.html" class="Module">foundation.boolean-reflection</a> <a id="544" class="Keyword">public</a>
<a id="551" class="Keyword">open</a> <a id="556" class="Keyword">import</a> <a id="563" href="foundation.booleans.html" class="Module">foundation.booleans</a> <a id="583" class="Keyword">public</a>
<a id="590" class="Keyword">open</a> <a id="595" class="Keyword">import</a> <a id="602" href="foundation.cantors-diagonal-argument.html" class="Module">foundation.cantors-diagonal-argument</a> <a id="639" class="Keyword">public</a>
<a id="646" class="Keyword">open</a> <a id="651" class="Keyword">import</a> <a id="658" href="foundation.cartesian-product-types.html" class="Module">foundation.cartesian-product-types</a> <a id="693" class="Keyword">public</a>
<a id="700" class="Keyword">open</a> <a id="705" class="Keyword">import</a> <a id="712" href="foundation.choice-of-representatives-equivalence-relation.html" class="Module">foundation.choice-of-representatives-equivalence-relation</a> <a id="770" class="Keyword">public</a>
<a id="777" class="Keyword">open</a> <a id="782" class="Keyword">import</a> <a id="789" href="foundation.coherently-invertible-maps.html" class="Module">foundation.coherently-invertible-maps</a> <a id="827" class="Keyword">public</a>
<a id="834" class="Keyword">open</a> <a id="839" class="Keyword">import</a> <a id="846" href="foundation.commuting-squares.html" class="Module">foundation.commuting-squares</a> <a id="875" class="Keyword">public</a>
<a id="882" class="Keyword">open</a> <a id="887" class="Keyword">import</a> <a id="894" href="foundation.complements.html" class="Module">foundation.complements</a> <a id="917" class="Keyword">public</a>
<a id="924" class="Keyword">open</a> <a id="929" class="Keyword">import</a> <a id="936" href="foundation.conjunction.html" class="Module">foundation.conjunction</a> <a id="959" class="Keyword">public</a>
<a id="966" class="Keyword">open</a> <a id="971" class="Keyword">import</a> <a id="978" href="foundation.connected-types.html" class="Module">foundation.connected-types</a> <a id="1005" class="Keyword">public</a>
<a id="1012" class="Keyword">open</a> <a id="1017" class="Keyword">import</a> <a id="1024" href="foundation.connected-components-universes.html" class="Module">foundation.connected-components-universes</a> <a id="1066" class="Keyword">public</a>
<a id="1073" class="Keyword">open</a> <a id="1078" class="Keyword">import</a> <a id="1085" href="foundation.connected-components.html" class="Module">foundation.connected-components</a> <a id="1117" class="Keyword">public</a>
<a id="1124" class="Keyword">open</a> <a id="1129" class="Keyword">import</a> <a id="1136" href="foundation.constant-maps.html" class="Module">foundation.constant-maps</a> <a id="1161" class="Keyword">public</a>
<a id="1168" class="Keyword">open</a> <a id="1173" class="Keyword">import</a> <a id="1180" href="foundation.contractible-maps.html" class="Module">foundation.contractible-maps</a> <a id="1209" class="Keyword">public</a>
<a id="1216" class="Keyword">open</a> <a id="1221" class="Keyword">import</a> <a id="1228" href="foundation.contractible-types.html" class="Module">foundation.contractible-types</a> <a id="1258" class="Keyword">public</a>
<a id="1265" class="Keyword">open</a> <a id="1270" class="Keyword">import</a> <a id="1277" href="foundation.coproduct-types.html" class="Module">foundation.coproduct-types</a> <a id="1304" class="Keyword">public</a>
<a id="1311" class="Keyword">open</a> <a id="1316" class="Keyword">import</a> <a id="1323" href="foundation.coslice.html" class="Module">foundation.coslice</a> <a id="1342" class="Keyword">public</a>
<a id="1349" class="Keyword">open</a> <a id="1354" class="Keyword">import</a> <a id="1361" href="foundation.decidable-dependent-function-types.html" class="Module">foundation.decidable-dependent-function-types</a> <a id="1407" class="Keyword">public</a>
<a id="1414" class="Keyword">open</a> <a id="1419" class="Keyword">import</a> <a id="1426" href="foundation.decidable-dependent-pair-types.html" class="Module">foundation.decidable-dependent-pair-types</a> <a id="1468" class="Keyword">public</a>
<a id="1475" class="Keyword">open</a> <a id="1480" class="Keyword">import</a> <a id="1487" href="foundation.decidable-embeddings.html" class="Module">foundation.decidable-embeddings</a> <a id="1519" class="Keyword">public</a>
<a id="1526" class="Keyword">open</a> <a id="1531" class="Keyword">import</a> <a id="1538" href="foundation.decidable-equality.html" class="Module">foundation.decidable-equality</a> <a id="1568" class="Keyword">public</a>
<a id="1575" class="Keyword">open</a> <a id="1580" class="Keyword">import</a> <a id="1587" href="foundation.decidable-maps.html" class="Module">foundation.decidable-maps</a> <a id="1613" class="Keyword">public</a>
<a id="1620" class="Keyword">open</a> <a id="1625" class="Keyword">import</a> <a id="1632" href="foundation.decidable-propositions.html" class="Module">foundation.decidable-propositions</a> <a id="1666" class="Keyword">public</a>
<a id="1673" class="Keyword">open</a> <a id="1678" class="Keyword">import</a> <a id="1685" href="foundation.decidable-subtypes.html" class="Module">foundation.decidable-subtypes</a> <a id="1715" class="Keyword">public</a>
<a id="1722" class="Keyword">open</a> <a id="1727" class="Keyword">import</a> <a id="1734" href="foundation.decidable-types.html" class="Module">foundation.decidable-types</a> <a id="1761" class="Keyword">public</a>
<a id="1768" class="Keyword">open</a> <a id="1773" class="Keyword">import</a> <a id="1780" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="1812" class="Keyword">public</a>
<a id="1819" class="Keyword">open</a> <a id="1824" class="Keyword">import</a> <a id="1831" href="foundation.diagonal-maps-of-types.html" class="Module">foundation.diagonal-maps-of-types</a> <a id="1865" class="Keyword">public</a>
<a id="1872" class="Keyword">open</a> <a id="1877" class="Keyword">import</a> <a id="1884" href="foundation.disjunction.html" class="Module">foundation.disjunction</a> <a id="1907" class="Keyword">public</a>
<a id="1914" class="Keyword">open</a> <a id="1919" class="Keyword">import</a> <a id="1926" href="foundation.distributivity-of-dependent-functions-over-coproduct-types.html" class="Module">foundation.distributivity-of-dependent-functions-over-coproduct-types</a> <a id="1996" class="Keyword">public</a>
<a id="2003" class="Keyword">open</a> <a id="2008" class="Keyword">import</a> <a id="2015" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html" class="Module">foundation.distributivity-of-dependent-functions-over-dependent-pairs</a> <a id="2085" class="Keyword">public</a>
<a id="2092" class="Keyword">open</a> <a id="2097" class="Keyword">import</a> <a id="2104" href="foundation.double-negation.html" class="Module">foundation.double-negation</a> <a id="2131" class="Keyword">public</a>
<a id="2138" class="Keyword">open</a> <a id="2143" class="Keyword">import</a> <a id="2150" href="foundation.effective-maps-equivalence-relations.html" class="Module">foundation.effective-maps-equivalence-relations</a> <a id="2198" class="Keyword">public</a>
<a id="2205" class="Keyword">open</a> <a id="2210" class="Keyword">import</a> <a id="2217" href="foundation.elementhood-relation-w-types.html" class="Module">foundation.elementhood-relation-w-types</a> <a id="2257" class="Keyword">public</a>
<a id="2264" class="Keyword">open</a> <a id="2269" class="Keyword">import</a> <a id="2276" href="foundation.embeddings.html" class="Module">foundation.embeddings</a> <a id="2298" class="Keyword">public</a>
<a id="2305" class="Keyword">open</a> <a id="2310" class="Keyword">import</a> <a id="2317" href="foundation.empty-types.html" class="Module">foundation.empty-types</a> <a id="2340" class="Keyword">public</a>
<a id="2347" class="Keyword">open</a> <a id="2352" class="Keyword">import</a> <a id="2359" href="foundation.epimorphisms-with-respect-to-sets.html" class="Module">foundation.epimorphisms-with-respect-to-sets</a> <a id="2404" class="Keyword">public</a>
<a id="2411" class="Keyword">open</a> <a id="2416" class="Keyword">import</a> <a id="2423" href="foundation.equality-cartesian-product-types.html" class="Module">foundation.equality-cartesian-product-types</a> <a id="2467" class="Keyword">public</a>
<a id="2474" class="Keyword">open</a> <a id="2479" class="Keyword">import</a> <a id="2486" href="foundation.equality-coproduct-types.html" class="Module">foundation.equality-coproduct-types</a> <a id="2522" class="Keyword">public</a>
<a id="2529" class="Keyword">open</a> <a id="2534" class="Keyword">import</a> <a id="2541" href="foundation.equality-dependent-function-types.html" class="Module">foundation.equality-dependent-function-types</a> <a id="2586" class="Keyword">public</a>
<a id="2593" class="Keyword">open</a> <a id="2598" class="Keyword">import</a> <a id="2605" href="foundation.equality-dependent-pair-types.html" class="Module">foundation.equality-dependent-pair-types</a> <a id="2646" class="Keyword">public</a>
<a id="2653" class="Keyword">open</a> <a id="2658" class="Keyword">import</a> <a id="2665" href="foundation.equality-fibers-of-maps.html" class="Module">foundation.equality-fibers-of-maps</a> <a id="2700" class="Keyword">public</a>
<a id="2707" class="Keyword">open</a> <a id="2712" class="Keyword">import</a> <a id="2719" href="foundation.equivalence-classes.html" class="Module">foundation.equivalence-classes</a> <a id="2750" class="Keyword">public</a>
<a id="2757" class="Keyword">open</a> <a id="2762" class="Keyword">import</a> <a id="2769" href="foundation.equivalence-induction.html" class="Module">foundation.equivalence-induction</a> <a id="2802" class="Keyword">public</a>
<a id="2809" class="Keyword">open</a> <a id="2814" class="Keyword">import</a> <a id="2821" href="foundation.equivalence-relations.html" class="Module">foundation.equivalence-relations</a> <a id="2854" class="Keyword">public</a>
<a id="2861" class="Keyword">open</a> <a id="2866" class="Keyword">import</a> <a id="2873" href="foundation.equivalences-maybe.html" class="Module">foundation.equivalences-maybe</a> <a id="2903" class="Keyword">public</a>
<a id="2910" class="Keyword">open</a> <a id="2915" class="Keyword">import</a> <a id="2922" href="foundation.equivalences.html" class="Module">foundation.equivalences</a> <a id="2946" class="Keyword">public</a>
<a id="2953" class="Keyword">open</a> <a id="2958" class="Keyword">import</a> <a id="2965" href="foundation.existential-quantification.html" class="Module">foundation.existential-quantification</a> <a id="3003" class="Keyword">public</a>
<a id="3010" class="Keyword">open</a> <a id="3015" class="Keyword">import</a> <a id="3022" href="foundation.extensional-w-types.html" class="Module">foundation.extensional-w-types</a> <a id="3053" class="Keyword">public</a>
<a id="3060" class="Keyword">open</a> <a id="3065" class="Keyword">import</a> <a id="3072" href="foundation.faithful-maps.html" class="Module">foundation.faithful-maps</a> <a id="3097" class="Keyword">public</a>
<a id="3104" class="Keyword">open</a> <a id="3109" class="Keyword">import</a> <a id="3116" href="foundation.fiber-inclusions.html" class="Module">foundation.fiber-inclusions</a> <a id="3144" class="Keyword">public</a>
<a id="3151" class="Keyword">open</a> <a id="3156" class="Keyword">import</a> <a id="3163" href="foundation.fibered-maps.html" class="Module">foundation.fibered-maps</a> <a id="3187" class="Keyword">public</a>
<a id="3194" class="Keyword">open</a> <a id="3199" class="Keyword">import</a> <a id="3206" href="foundation.fibers-of-maps.html" class="Module">foundation.fibers-of-maps</a> <a id="3232" class="Keyword">public</a>
<a id="3239" class="Keyword">open</a> <a id="3244" class="Keyword">import</a> <a id="3251" href="foundation.function-extensionality.html" class="Module">foundation.function-extensionality</a> <a id="3286" class="Keyword">public</a>
<a id="3293" class="Keyword">open</a> <a id="3298" class="Keyword">import</a> <a id="3305" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="3326" class="Keyword">public</a>
<a id="3333" class="Keyword">open</a> <a id="3338" class="Keyword">import</a> <a id="3345" href="foundation.functoriality-cartesian-product-types.html" class="Module">foundation.functoriality-cartesian-product-types</a> <a id="3394" class="Keyword">public</a>
<a id="3401" class="Keyword">open</a> <a id="3406" class="Keyword">import</a> <a id="3413" href="foundation.functoriality-coproduct-types.html" class="Module">foundation.functoriality-coproduct-types</a> <a id="3454" class="Keyword">public</a>
<a id="3461" class="Keyword">open</a> <a id="3466" class="Keyword">import</a> <a id="3473" href="foundation.functoriality-dependent-function-types.html" class="Module">foundation.functoriality-dependent-function-types</a> <a id="3523" class="Keyword">public</a>
<a id="3530" class="Keyword">open</a> <a id="3535" class="Keyword">import</a> <a id="3542" href="foundation.functoriality-dependent-pair-types.html" class="Module">foundation.functoriality-dependent-pair-types</a> <a id="3588" class="Keyword">public</a>
<a id="3595" class="Keyword">open</a> <a id="3600" class="Keyword">import</a> <a id="3607" href="foundation.functoriality-function-types.html" class="Module">foundation.functoriality-function-types</a> <a id="3647" class="Keyword">public</a>
<a id="3654" class="Keyword">open</a> <a id="3659" class="Keyword">import</a> <a id="3666" href="foundation.functoriality-propositional-truncation.html" class="Module">foundation.functoriality-propositional-truncation</a> <a id="3716" class="Keyword">public</a>
<a id="3723" class="Keyword">open</a> <a id="3728" class="Keyword">import</a> <a id="3735" href="foundation.functoriality-set-quotients.html" class="Module">foundation.functoriality-set-quotients</a> <a id="3774" class="Keyword">public</a>
<a id="3781" class="Keyword">open</a> <a id="3786" class="Keyword">import</a> <a id="3793" href="foundation.functoriality-set-truncation.html" class="Module">foundation.functoriality-set-truncation</a>
<a id="3833" class="Keyword">open</a> <a id="3838" class="Keyword">import</a> <a id="3845" href="foundation.functoriality-w-types.html" class="Module">foundation.functoriality-w-types</a> <a id="3878" class="Keyword">public</a>
<a id="3885" class="Keyword">open</a> <a id="3890" class="Keyword">import</a> <a id="3897" href="foundation.fundamental-theorem-of-identity-types.html" class="Module">foundation.fundamental-theorem-of-identity-types</a> <a id="3946" class="Keyword">public</a>
<a id="3953" class="Keyword">open</a> <a id="3958" class="Keyword">import</a> <a id="3965" href="foundation.global-choice.html" class="Module">foundation.global-choice</a> <a id="3990" class="Keyword">public</a>
<a id="3997" class="Keyword">open</a> <a id="4002" class="Keyword">import</a> <a id="4009" href="foundation.homotopies.html" class="Module">foundation.homotopies</a> <a id="4031" class="Keyword">public</a>
<a id="4038" class="Keyword">open</a> <a id="4043" class="Keyword">import</a> <a id="4050" href="foundation.identity-systems.html" class="Module">foundation.identity-systems</a> <a id="4078" class="Keyword">public</a>
<a id="4085" class="Keyword">open</a> <a id="4090" class="Keyword">import</a> <a id="4097" href="foundation.identity-types.html" class="Module">foundation.identity-types</a> <a id="4123" class="Keyword">public</a>
<a id="4130" class="Keyword">open</a> <a id="4135" class="Keyword">import</a> <a id="4142" href="foundation.images.html" class="Module">foundation.images</a> <a id="4160" class="Keyword">public</a>
<a id="4167" class="Keyword">open</a> <a id="4172" class="Keyword">import</a> <a id="4179" href="foundation.impredicative-encodings.html" class="Module">foundation.impredicative-encodings</a> <a id="4214" class="Keyword">public</a>
<a id="4221" class="Keyword">open</a> <a id="4226" class="Keyword">import</a> <a id="4233" href="foundation.indexed-w-types.html" class="Module">foundation.indexed-w-types</a> <a id="4260" class="Keyword">public</a>
<a id="4267" class="Keyword">open</a> <a id="4272" class="Keyword">import</a> <a id="4279" href="foundation.induction-principle-propositional-truncation.html" class="Module">foundation.induction-principle-propositional-truncation</a> <a id="4335" class="Keyword">public</a>
<a id="4342" class="Keyword">open</a> <a id="4347" class="Keyword">import</a> <a id="4354" href="foundation.induction-w-types.html" class="Module">foundation.induction-w-types</a> <a id="4383" class="Keyword">public</a>
<a id="4390" class="Keyword">open</a> <a id="4395" class="Keyword">import</a> <a id="4402" href="foundation.inequality-w-types.html" class="Module">foundation.inequality-w-types</a> <a id="4432" class="Keyword">public</a>
<a id="4439" class="Keyword">open</a> <a id="4444" class="Keyword">import</a> <a id="4451" href="foundation.injective-maps.html" class="Module">foundation.injective-maps</a> <a id="4477" class="Keyword">public</a>
<a id="4484" class="Keyword">open</a> <a id="4489" class="Keyword">import</a> <a id="4496" href="foundation.interchange-law.html" class="Module">foundation.interchange-law</a> <a id="4523" class="Keyword">public</a>
<a id="4530" class="Keyword">open</a> <a id="4535" class="Keyword">import</a> <a id="4542" href="foundation.involutions.html" class="Module">foundation.involutions</a> <a id="4565" class="Keyword">public</a>
<a id="4572" class="Keyword">open</a> <a id="4577" class="Keyword">import</a> <a id="4584" href="foundation.isolated-points.html" class="Module">foundation.isolated-points</a> <a id="4611" class="Keyword">public</a>
<a id="4618" class="Keyword">open</a> <a id="4623" class="Keyword">import</a> <a id="4630" href="foundation.isomorphisms-of-sets.html" class="Module">foundation.isomorphisms-of-sets</a> <a id="4662" class="Keyword">public</a>
<a id="4669" class="Keyword">open</a> <a id="4674" class="Keyword">import</a> <a id="4681" href="foundation.law-of-excluded-middle.html" class="Module">foundation.law-of-excluded-middle</a> <a id="4715" class="Keyword">public</a>
<a id="4722" class="Keyword">open</a> <a id="4727" class="Keyword">import</a> <a id="4734" href="foundation.lawveres-fixed-point-theorem.html" class="Module">foundation.lawveres-fixed-point-theorem</a> <a id="4774" class="Keyword">public</a>
<a id="4781" class="Keyword">open</a> <a id="4786" class="Keyword">import</a> <a id="4793" href="foundation.locally-small-types.html" class="Module">foundation.locally-small-types</a> <a id="4824" class="Keyword">public</a>
<a id="4831" class="Keyword">open</a> <a id="4836" class="Keyword">import</a> <a id="4843" href="foundation.logical-equivalences.html" class="Module">foundation.logical-equivalences</a> <a id="4875" class="Keyword">public</a>
<a id="4882" class="Keyword">open</a> <a id="4887" class="Keyword">import</a> <a id="4894" href="foundation.maybe.html" class="Module">foundation.maybe</a> <a id="4911" class="Keyword">public</a>
<a id="4918" class="Keyword">open</a> <a id="4923" class="Keyword">import</a> <a id="4930" href="foundation.mere-equality.html" class="Module">foundation.mere-equality</a> <a id="4955" class="Keyword">public</a>
<a id="4962" class="Keyword">open</a> <a id="4967" class="Keyword">import</a> <a id="4974" href="foundation.mere-equivalences.html" class="Module">foundation.mere-equivalences</a> <a id="5003" class="Keyword">public</a>
<a id="5010" class="Keyword">open</a> <a id="5015" class="Keyword">import</a> <a id="5022" href="foundation.monomorphisms.html" class="Module">foundation.monomorphisms</a> <a id="5047" class="Keyword">public</a>
<a id="5054" class="Keyword">open</a> <a id="5059" class="Keyword">import</a> <a id="5066" href="foundation.multisets.html" class="Module">foundation.multisets</a> <a id="5087" class="Keyword">public</a>
<a id="5094" class="Keyword">open</a> <a id="5099" class="Keyword">import</a> <a id="5106" href="foundation.negation.html" class="Module">foundation.negation</a> <a id="5126" class="Keyword">public</a>
<a id="5133" class="Keyword">open</a> <a id="5138" class="Keyword">import</a> <a id="5145" href="foundation.non-contractible-types.html" class="Module">foundation.non-contractible-types</a> <a id="5179" class="Keyword">public</a>
<a id="5186" class="Keyword">open</a> <a id="5191" class="Keyword">import</a> <a id="5198" href="foundation.path-algebra.html" class="Module">foundation.path-algebra</a> <a id="5222" class="Keyword">public</a>
<a id="5229" class="Keyword">open</a> <a id="5234" class="Keyword">import</a> <a id="5241" href="foundation.path-split-maps.html" class="Module">foundation.path-split-maps</a> <a id="5268" class="Keyword">public</a>
<a id="5275" class="Keyword">open</a> <a id="5280" class="Keyword">import</a> <a id="5287" href="foundation.polynomial-endofunctors.html" class="Module">foundation.polynomial-endofunctors</a> <a id="5322" class="Keyword">public</a>
<a id="5329" class="Keyword">open</a> <a id="5334" class="Keyword">import</a> <a id="5341" href="foundation.propositional-extensionality.html" class="Module">foundation.propositional-extensionality</a> <a id="5381" class="Keyword">public</a>
<a id="5388" class="Keyword">open</a> <a id="5393" class="Keyword">import</a> <a id="5400" href="foundation.propositional-maps.html" class="Module">foundation.propositional-maps</a> <a id="5430" class="Keyword">public</a>
<a id="5437" class="Keyword">open</a> <a id="5442" class="Keyword">import</a> <a id="5449" href="foundation.propositional-truncations.html" class="Module">foundation.propositional-truncations</a> <a id="5486" class="Keyword">public</a>
<a id="5493" class="Keyword">open</a> <a id="5498" class="Keyword">import</a> <a id="5505" href="foundation.propositions.html" class="Module">foundation.propositions</a> <a id="5529" class="Keyword">public</a>
<a id="5536" class="Keyword">open</a> <a id="5541" class="Keyword">import</a> <a id="5548" href="foundation.pullbacks.html" class="Module">foundation.pullbacks</a> <a id="5569" class="Keyword">public</a>
<a id="5576" class="Keyword">open</a> <a id="5581" class="Keyword">import</a> <a id="5588" href="foundation.ranks-of-elements-w-types.html" class="Module">foundation.ranks-of-elements-w-types</a> <a id="5625" class="Keyword">public</a>
<a id="5632" class="Keyword">open</a> <a id="5637" class="Keyword">import</a> <a id="5644" href="foundation.raising-universe-levels.html" class="Module">foundation.raising-universe-levels</a> <a id="5679" class="Keyword">public</a>
<a id="5686" class="Keyword">open</a> <a id="5691" class="Keyword">import</a> <a id="5698" href="foundation.reflecting-maps-equivalence-relations.html" class="Module">foundation.reflecting-maps-equivalence-relations</a> <a id="5747" class="Keyword">public</a>
<a id="5754" class="Keyword">open</a> <a id="5759" class="Keyword">import</a> <a id="5766" href="foundation.replacement.html" class="Module">foundation.replacement</a> <a id="5789" class="Keyword">public</a>
<a id="5796" class="Keyword">open</a> <a id="5801" class="Keyword">import</a> <a id="5808" href="foundation.retractions.html" class="Module">foundation.retractions</a> <a id="5831" class="Keyword">public</a>
<a id="5838" class="Keyword">open</a> <a id="5843" class="Keyword">import</a> <a id="5850" href="foundation.russells-paradox.html" class="Module">foundation.russells-paradox</a> <a id="5878" class="Keyword">public</a>
<a id="5885" class="Keyword">open</a> <a id="5890" class="Keyword">import</a> <a id="5897" href="foundation.sections.html" class="Module">foundation.sections</a> <a id="5917" class="Keyword">public</a>
<a id="5924" class="Keyword">open</a> <a id="5929" class="Keyword">import</a> <a id="5936" href="foundation.set-presented-types.html" class="Module">foundation.set-presented-types</a> <a id="5967" class="Keyword">public</a>
<a id="5974" class="Keyword">open</a> <a id="5979" class="Keyword">import</a> <a id="5986" href="foundation.set-truncations.html" class="Module">foundation.set-truncations</a> <a id="6013" class="Keyword">public</a>
<a id="6020" class="Keyword">open</a> <a id="6025" class="Keyword">import</a> <a id="6032" href="foundation.sets.html" class="Module">foundation.sets</a> <a id="6048" class="Keyword">public</a>
<a id="6055" class="Keyword">open</a> <a id="6060" class="Keyword">import</a> <a id="6067" href="foundation.singleton-induction.html" class="Module">foundation.singleton-induction</a> <a id="6098" class="Keyword">public</a>
<a id="6105" class="Keyword">open</a> <a id="6110" class="Keyword">import</a> <a id="6117" href="foundation.slice.html" class="Module">foundation.slice</a> <a id="6134" class="Keyword">public</a>
<a id="6141" class="Keyword">open</a> <a id="6146" class="Keyword">import</a> <a id="6153" href="foundation.small-maps.html" class="Module">foundation.small-maps</a> <a id="6175" class="Keyword">public</a>
<a id="6182" class="Keyword">open</a> <a id="6187" class="Keyword">import</a> <a id="6194" href="foundation.small-multisets.html" class="Module">foundation.small-multisets</a> <a id="6221" class="Keyword">public</a>
<a id="6228" class="Keyword">open</a> <a id="6233" class="Keyword">import</a> <a id="6240" href="foundation.small-types.html" class="Module">foundation.small-types</a> <a id="6263" class="Keyword">public</a>
<a id="6270" class="Keyword">open</a> <a id="6275" class="Keyword">import</a> <a id="6282" href="foundation.small-universes.html" class="Module">foundation.small-universes</a> <a id="6309" class="Keyword">public</a>
<a id="6316" class="Keyword">open</a> <a id="6321" class="Keyword">import</a> <a id="6328" href="foundation.split-surjective-maps.html" class="Module">foundation.split-surjective-maps</a> <a id="6361" class="Keyword">public</a>
<a id="6368" class="Keyword">open</a> <a id="6373" class="Keyword">import</a> <a id="6380" href="foundation.structure-identity-principle.html" class="Module">foundation.structure-identity-principle</a> <a id="6420" class="Keyword">public</a>
<a id="6427" class="Keyword">open</a> <a id="6432" class="Keyword">import</a> <a id="6439" href="foundation.structure.html" class="Module">foundation.structure</a> <a id="6460" class="Keyword">public</a>
<a id="6467" class="Keyword">open</a> <a id="6472" class="Keyword">import</a> <a id="6479" href="foundation.subterminal-types.html" class="Module">foundation.subterminal-types</a> <a id="6508" class="Keyword">public</a>
<a id="6515" class="Keyword">open</a> <a id="6520" class="Keyword">import</a> <a id="6527" href="foundation.subtype-identity-principle.html" class="Module">foundation.subtype-identity-principle</a> <a id="6565" class="Keyword">public</a>
<a id="6572" class="Keyword">open</a> <a id="6577" class="Keyword">import</a> <a id="6584" href="foundation.subtypes.html" class="Module">foundation.subtypes</a> <a id="6604" class="Keyword">public</a>
<a id="6611" class="Keyword">open</a> <a id="6616" class="Keyword">import</a> <a id="6623" href="foundation.subuniverses.html" class="Module">foundation.subuniverses</a> <a id="6647" class="Keyword">public</a>
<a id="6654" class="Keyword">open</a> <a id="6659" class="Keyword">import</a> <a id="6666" href="foundation.surjective-maps.html" class="Module">foundation.surjective-maps</a> <a id="6693" class="Keyword">public</a>
<a id="6700" class="Keyword">open</a> <a id="6705" class="Keyword">import</a> <a id="6712" href="foundation.truncated-maps.html" class="Module">foundation.truncated-maps</a> <a id="6738" class="Keyword">public</a>
<a id="6745" class="Keyword">open</a> <a id="6750" class="Keyword">import</a> <a id="6757" href="foundation.truncated-types.html" class="Module">foundation.truncated-types</a> <a id="6784" class="Keyword">public</a>
<a id="6791" class="Keyword">open</a> <a id="6796" class="Keyword">import</a> <a id="6803" href="foundation.truncation-levels.html" class="Module">foundation.truncation-levels</a> <a id="6832" class="Keyword">public</a>
<a id="6839" class="Keyword">open</a> <a id="6844" class="Keyword">import</a> <a id="6851" href="foundation.type-arithmetic-cartesian-product-types.html" class="Module">foundation.type-arithmetic-cartesian-product-types</a> <a id="6902" class="Keyword">public</a>
<a id="6909" class="Keyword">open</a> <a id="6914" class="Keyword">import</a> <a id="6921" href="foundation.type-arithmetic-coproduct-types.html" class="Module">foundation.type-arithmetic-coproduct-types</a> <a id="6964" class="Keyword">public</a>
<a id="6971" class="Keyword">open</a> <a id="6976" class="Keyword">import</a> <a id="6983" href="foundation.type-arithmetic-dependent-pair-types.html" class="Module">foundation.type-arithmetic-dependent-pair-types</a> <a id="7031" class="Keyword">public</a>
<a id="7038" class="Keyword">open</a> <a id="7043" class="Keyword">import</a> <a id="7050" href="foundation.type-arithmetic-empty-type.html" class="Module">foundation.type-arithmetic-empty-type</a> <a id="7088" class="Keyword">public</a>
<a id="7095" class="Keyword">open</a> <a id="7100" class="Keyword">import</a> <a id="7107" href="foundation.type-arithmetic-unit-type.html" class="Module">foundation.type-arithmetic-unit-type</a> <a id="7144" class="Keyword">public</a>
<a id="7151" class="Keyword">open</a> <a id="7156" class="Keyword">import</a> <a id="7163" href="foundation.uniqueness-image.html" class="Module">foundation.uniqueness-image</a> <a id="7191" class="Keyword">public</a>
<a id="7198" class="Keyword">open</a> <a id="7203" class="Keyword">import</a> <a id="7210" href="foundation.uniqueness-set-quotients.html" class="Module">foundation.uniqueness-set-quotients</a> <a id="7246" class="Keyword">public</a>
<a id="7253" class="Keyword">open</a> <a id="7258" class="Keyword">import</a> <a id="7265" href="foundation.uniqueness-set-truncations.html" class="Module">foundation.uniqueness-set-truncations</a> <a id="7303" class="Keyword">public</a>
<a id="7310" class="Keyword">open</a> <a id="7315" class="Keyword">import</a> <a id="7322" href="foundation.uniqueness-truncation.html" class="Module">foundation.uniqueness-truncation</a> <a id="7355" class="Keyword">public</a>
<a id="7362" class="Keyword">open</a> <a id="7367" class="Keyword">import</a> <a id="7374" href="foundation.unit-type.html" class="Module">foundation.unit-type</a> <a id="7395" class="Keyword">public</a>
<a id="7402" class="Keyword">open</a> <a id="7407" class="Keyword">import</a> <a id="7414" href="foundation.univalence-implies-function-extensionality.html" class="Module">foundation.univalence-implies-function-extensionality</a> <a id="7468" class="Keyword">public</a>
<a id="7475" class="Keyword">open</a> <a id="7480" class="Keyword">import</a> <a id="7487" href="foundation.univalence.html" class="Module">foundation.univalence</a> <a id="7509" class="Keyword">public</a>
<a id="7516" class="Keyword">open</a> <a id="7521" class="Keyword">import</a> <a id="7528" href="foundation.univalent-type-families.html" class="Module">foundation.univalent-type-families</a> <a id="7563" class="Keyword">public</a>
<a id="7570" class="Keyword">open</a> <a id="7575" class="Keyword">import</a> <a id="7582" href="foundation.universal-property-booleans.html" class="Module">foundation.universal-property-booleans</a> <a id="7621" class="Keyword">public</a>
<a id="7628" class="Keyword">open</a> <a id="7633" class="Keyword">import</a> <a id="7640" href="foundation.universal-property-cartesian-product-types.html" class="Module">foundation.universal-property-cartesian-product-types</a> <a id="7694" class="Keyword">public</a>
<a id="7701" class="Keyword">open</a> <a id="7706" class="Keyword">import</a> <a id="7713" href="foundation.universal-property-coproduct-types.html" class="Module">foundation.universal-property-coproduct-types</a> <a id="7759" class="Keyword">public</a>
<a id="7766" class="Keyword">open</a> <a id="7771" class="Keyword">import</a> <a id="7778" href="foundation.universal-property-dependent-pair-types.html" class="Module">foundation.universal-property-dependent-pair-types</a> <a id="7829" class="Keyword">public</a>
<a id="7836" class="Keyword">open</a> <a id="7841" class="Keyword">import</a> <a id="7848" href="foundation.universal-property-empty-type.html" class="Module">foundation.universal-property-empty-type</a> <a id="7889" class="Keyword">public</a>
<a id="7896" class="Keyword">open</a> <a id="7901" class="Keyword">import</a> <a id="7908" href="foundation.universal-property-fiber-products.html" class="Module">foundation.universal-property-fiber-products</a> <a id="7953" class="Keyword">public</a>
<a id="7960" class="Keyword">open</a> <a id="7965" class="Keyword">import</a> <a id="7972" href="foundation.universal-property-identity-types.html" class="Module">foundation.universal-property-identity-types</a> <a id="8017" class="Keyword">public</a>
<a id="8024" class="Keyword">open</a> <a id="8029" class="Keyword">import</a> <a id="8036" href="foundation.universal-property-image.html" class="Module">foundation.universal-property-image</a> <a id="8072" class="Keyword">public</a>
<a id="8079" class="Keyword">open</a> <a id="8084" class="Keyword">import</a> <a id="8091" href="foundation.universal-property-maybe.html" class="Module">foundation.universal-property-maybe</a> <a id="8127" class="Keyword">public</a>
<a id="8134" class="Keyword">open</a> <a id="8139" class="Keyword">import</a> <a id="8146" href="foundation.universal-property-propositional-truncation-into-sets.html" class="Module">foundation.universal-property-propositional-truncation-into-sets</a> <a id="8211" class="Keyword">public</a>
<a id="8218" class="Keyword">open</a> <a id="8223" class="Keyword">import</a> <a id="8230" href="foundation.universal-property-propositional-truncation.html" class="Module">foundation.universal-property-propositional-truncation</a> <a id="8285" class="Keyword">public</a>
<a id="8292" class="Keyword">open</a> <a id="8297" class="Keyword">import</a> <a id="8304" href="foundation.universal-property-pullbacks.html" class="Module">foundation.universal-property-pullbacks</a> <a id="8344" class="Keyword">public</a>
<a id="8351" class="Keyword">open</a> <a id="8356" class="Keyword">import</a> <a id="8363" href="foundation.universal-property-set-quotients.html" class="Module">foundation.universal-property-set-quotients</a> <a id="8407" class="Keyword">public</a>
<a id="8414" class="Keyword">open</a> <a id="8419" class="Keyword">import</a> <a id="8426" href="foundation.universal-property-set-truncation.html" class="Module">foundation.universal-property-set-truncation</a> <a id="8471" class="Keyword">public</a>
<a id="8478" class="Keyword">open</a> <a id="8483" class="Keyword">import</a> <a id="8490" href="foundation.universal-property-truncation.html" class="Module">foundation.universal-property-truncation</a> <a id="8531" class="Keyword">public</a>
<a id="8538" class="Keyword">open</a> <a id="8543" class="Keyword">import</a> <a id="8550" href="foundation.universal-property-unit-type.html" class="Module">foundation.universal-property-unit-type</a> <a id="8590" class="Keyword">public</a>
<a id="8597" class="Keyword">open</a> <a id="8602" class="Keyword">import</a> <a id="8609" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="8636" class="Keyword">public</a>
<a id="8643" class="Keyword">open</a> <a id="8648" class="Keyword">import</a> <a id="8655" href="foundation.unordered-pairs.html" class="Module">foundation.unordered-pairs</a> <a id="8682" class="Keyword">public</a>
<a id="8689" class="Keyword">open</a> <a id="8694" class="Keyword">import</a> <a id="8701" href="foundation.w-types.html" class="Module">foundation.w-types</a> <a id="8720" class="Keyword">public</a>
<a id="8727" class="Keyword">open</a> <a id="8732" class="Keyword">import</a> <a id="8739" href="foundation.weak-function-extensionality.html" class="Module">foundation.weak-function-extensionality</a> <a id="8779" class="Keyword">public</a>
<a id="8786" class="Keyword">open</a> <a id="8791" class="Keyword">import</a> <a id="8798" href="foundation.weakly-constant-maps.html" class="Module">foundation.weakly-constant-maps</a> <a id="8830" class="Keyword">public</a>
</pre>