# Foundation

<pre class="Agda"><a id="23" class="Symbol">{-#</a> <a id="27" class="Keyword">OPTIONS</a> <a id="35" class="Pragma">--without-K</a> <a id="47" class="Pragma">--exact-split</a> <a id="61" class="Symbol">#-}</a>

<a id="66" class="Keyword">module</a> <a id="73" href="foundation.html" class="Module">foundation</a> <a id="84" class="Keyword">where</a>

<a id="91" class="Keyword">open</a> <a id="96" class="Keyword">import</a> <a id="103" href="foundation.0-maps.html" class="Module">foundation.0-maps</a> <a id="121" class="Keyword">public</a>
<a id="128" class="Keyword">open</a> <a id="133" class="Keyword">import</a> <a id="140" href="foundation.1-types.html" class="Module">foundation.1-types</a> <a id="159" class="Keyword">public</a>
<a id="166" class="Keyword">open</a> <a id="171" class="Keyword">import</a> <a id="178" href="foundation.2-types.html" class="Module">foundation.2-types</a> <a id="197" class="Keyword">public</a>
<a id="204" class="Keyword">open</a> <a id="209" class="Keyword">import</a> <a id="216" href="foundation.algebras-polynomial-endofunctors.html" class="Module">foundation.algebras-polynomial-endofunctors</a> <a id="260" class="Keyword">public</a>
<a id="267" class="Keyword">open</a> <a id="272" class="Keyword">import</a> <a id="279" href="foundation.automorphisms.html" class="Module">foundation.automorphisms</a> <a id="304" class="Keyword">public</a>
<a id="311" class="Keyword">open</a> <a id="316" class="Keyword">import</a> <a id="323" href="foundation.axiom-of-choice.html" class="Module">foundation.axiom-of-choice</a> <a id="350" class="Keyword">public</a>
<a id="357" class="Keyword">open</a> <a id="362" class="Keyword">import</a> <a id="369" href="foundation.binary-relations.html" class="Module">foundation.binary-relations</a> <a id="397" class="Keyword">public</a>
<a id="404" class="Keyword">open</a> <a id="409" class="Keyword">import</a> <a id="416" href="foundation.boolean-reflection.html" class="Module">foundation.boolean-reflection</a> <a id="446" class="Keyword">public</a>
<a id="453" class="Keyword">open</a> <a id="458" class="Keyword">import</a> <a id="465" href="foundation.booleans.html" class="Module">foundation.booleans</a> <a id="485" class="Keyword">public</a>
<a id="492" class="Keyword">open</a> <a id="497" class="Keyword">import</a> <a id="504" href="foundation.cantors-diagonal-argument.html" class="Module">foundation.cantors-diagonal-argument</a> <a id="541" class="Keyword">public</a>
<a id="548" class="Keyword">open</a> <a id="553" class="Keyword">import</a> <a id="560" href="foundation.cartesian-product-types.html" class="Module">foundation.cartesian-product-types</a> <a id="595" class="Keyword">public</a>
<a id="602" class="Keyword">open</a> <a id="607" class="Keyword">import</a> <a id="614" href="foundation.choice-of-representatives-equivalence-relation.html" class="Module">foundation.choice-of-representatives-equivalence-relation</a> <a id="672" class="Keyword">public</a>
<a id="679" class="Keyword">open</a> <a id="684" class="Keyword">import</a> <a id="691" href="foundation.coherently-invertible-maps.html" class="Module">foundation.coherently-invertible-maps</a> <a id="729" class="Keyword">public</a>
<a id="736" class="Keyword">open</a> <a id="741" class="Keyword">import</a> <a id="748" href="foundation.commuting-squares.html" class="Module">foundation.commuting-squares</a> <a id="777" class="Keyword">public</a>
<a id="784" class="Keyword">open</a> <a id="789" class="Keyword">import</a> <a id="796" href="foundation.complements.html" class="Module">foundation.complements</a> <a id="819" class="Keyword">public</a>
<a id="826" class="Keyword">open</a> <a id="831" class="Keyword">import</a> <a id="838" href="foundation.conjunction.html" class="Module">foundation.conjunction</a> <a id="861" class="Keyword">public</a>
<a id="868" class="Keyword">open</a> <a id="873" class="Keyword">import</a> <a id="880" href="foundation.connected-types.html" class="Module">foundation.connected-types</a> <a id="907" class="Keyword">public</a>
<a id="914" class="Keyword">open</a> <a id="919" class="Keyword">import</a> <a id="926" href="foundation.connected-components-universes.html" class="Module">foundation.connected-components-universes</a> <a id="968" class="Keyword">public</a>
<a id="975" class="Keyword">open</a> <a id="980" class="Keyword">import</a> <a id="987" href="foundation.connected-components.html" class="Module">foundation.connected-components</a> <a id="1019" class="Keyword">public</a>
<a id="1026" class="Keyword">open</a> <a id="1031" class="Keyword">import</a> <a id="1038" href="foundation.constant-maps.html" class="Module">foundation.constant-maps</a> <a id="1063" class="Keyword">public</a>
<a id="1070" class="Keyword">open</a> <a id="1075" class="Keyword">import</a> <a id="1082" href="foundation.contractible-maps.html" class="Module">foundation.contractible-maps</a> <a id="1111" class="Keyword">public</a>
<a id="1118" class="Keyword">open</a> <a id="1123" class="Keyword">import</a> <a id="1130" href="foundation.contractible-types.html" class="Module">foundation.contractible-types</a> <a id="1160" class="Keyword">public</a>
<a id="1167" class="Keyword">open</a> <a id="1172" class="Keyword">import</a> <a id="1179" href="foundation.coproduct-types.html" class="Module">foundation.coproduct-types</a> <a id="1206" class="Keyword">public</a>
<a id="1213" class="Keyword">open</a> <a id="1218" class="Keyword">import</a> <a id="1225" href="foundation.coslice.html" class="Module">foundation.coslice</a> <a id="1244" class="Keyword">public</a>
<a id="1251" class="Keyword">open</a> <a id="1256" class="Keyword">import</a> <a id="1263" href="foundation.decidable-dependent-function-types.html" class="Module">foundation.decidable-dependent-function-types</a> <a id="1309" class="Keyword">public</a>
<a id="1316" class="Keyword">open</a> <a id="1321" class="Keyword">import</a> <a id="1328" href="foundation.decidable-dependent-pair-types.html" class="Module">foundation.decidable-dependent-pair-types</a> <a id="1370" class="Keyword">public</a>
<a id="1377" class="Keyword">open</a> <a id="1382" class="Keyword">import</a> <a id="1389" href="foundation.decidable-embeddings.html" class="Module">foundation.decidable-embeddings</a> <a id="1421" class="Keyword">public</a>
<a id="1428" class="Keyword">open</a> <a id="1433" class="Keyword">import</a> <a id="1440" href="foundation.decidable-equality.html" class="Module">foundation.decidable-equality</a> <a id="1470" class="Keyword">public</a>
<a id="1477" class="Keyword">open</a> <a id="1482" class="Keyword">import</a> <a id="1489" href="foundation.decidable-maps.html" class="Module">foundation.decidable-maps</a> <a id="1515" class="Keyword">public</a>
<a id="1522" class="Keyword">open</a> <a id="1527" class="Keyword">import</a> <a id="1534" href="foundation.decidable-propositions.html" class="Module">foundation.decidable-propositions</a> <a id="1568" class="Keyword">public</a>
<a id="1575" class="Keyword">open</a> <a id="1580" class="Keyword">import</a> <a id="1587" href="foundation.decidable-subtypes.html" class="Module">foundation.decidable-subtypes</a> <a id="1617" class="Keyword">public</a>
<a id="1624" class="Keyword">open</a> <a id="1629" class="Keyword">import</a> <a id="1636" href="foundation.decidable-types.html" class="Module">foundation.decidable-types</a> <a id="1663" class="Keyword">public</a>
<a id="1670" class="Keyword">open</a> <a id="1675" class="Keyword">import</a> <a id="1682" href="foundation.dependent-pair-types.html" class="Module">foundation.dependent-pair-types</a> <a id="1714" class="Keyword">public</a>
<a id="1721" class="Keyword">open</a> <a id="1726" class="Keyword">import</a> <a id="1733" href="foundation.diagonal-maps-of-types.html" class="Module">foundation.diagonal-maps-of-types</a> <a id="1767" class="Keyword">public</a>
<a id="1774" class="Keyword">open</a> <a id="1779" class="Keyword">import</a> <a id="1786" href="foundation.disjunction.html" class="Module">foundation.disjunction</a> <a id="1809" class="Keyword">public</a>
<a id="1816" class="Keyword">open</a> <a id="1821" class="Keyword">import</a> <a id="1828" href="foundation.distributivity-of-dependent-functions-over-coproduct-types.html" class="Module">foundation.distributivity-of-dependent-functions-over-coproduct-types</a> <a id="1898" class="Keyword">public</a>
<a id="1905" class="Keyword">open</a> <a id="1910" class="Keyword">import</a> <a id="1917" href="foundation.distributivity-of-dependent-functions-over-dependent-pairs.html" class="Module">foundation.distributivity-of-dependent-functions-over-dependent-pairs</a> <a id="1987" class="Keyword">public</a>
<a id="1994" class="Keyword">open</a> <a id="1999" class="Keyword">import</a> <a id="2006" href="foundation.double-negation.html" class="Module">foundation.double-negation</a> <a id="2033" class="Keyword">public</a>
<a id="2040" class="Keyword">open</a> <a id="2045" class="Keyword">import</a> <a id="2052" href="foundation.effective-maps-equivalence-relations.html" class="Module">foundation.effective-maps-equivalence-relations</a> <a id="2100" class="Keyword">public</a>
<a id="2107" class="Keyword">open</a> <a id="2112" class="Keyword">import</a> <a id="2119" href="foundation.elementhood-relation-W-types.html" class="Module">foundation.elementhood-relation-W-types</a> <a id="2159" class="Keyword">public</a>
<a id="2166" class="Keyword">open</a> <a id="2171" class="Keyword">import</a> <a id="2178" href="foundation.embeddings.html" class="Module">foundation.embeddings</a> <a id="2200" class="Keyword">public</a>
<a id="2207" class="Keyword">open</a> <a id="2212" class="Keyword">import</a> <a id="2219" href="foundation.empty-types.html" class="Module">foundation.empty-types</a> <a id="2242" class="Keyword">public</a>
<a id="2249" class="Keyword">open</a> <a id="2254" class="Keyword">import</a> <a id="2261" href="foundation.epimorphisms-with-respect-to-sets.html" class="Module">foundation.epimorphisms-with-respect-to-sets</a> <a id="2306" class="Keyword">public</a>
<a id="2313" class="Keyword">open</a> <a id="2318" class="Keyword">import</a> <a id="2325" href="foundation.equality-cartesian-product-types.html" class="Module">foundation.equality-cartesian-product-types</a> <a id="2369" class="Keyword">public</a>
<a id="2376" class="Keyword">open</a> <a id="2381" class="Keyword">import</a> <a id="2388" href="foundation.equality-coproduct-types.html" class="Module">foundation.equality-coproduct-types</a> <a id="2424" class="Keyword">public</a>
<a id="2431" class="Keyword">open</a> <a id="2436" class="Keyword">import</a> <a id="2443" href="foundation.equality-dependent-function-types.html" class="Module">foundation.equality-dependent-function-types</a> <a id="2488" class="Keyword">public</a>
<a id="2495" class="Keyword">open</a> <a id="2500" class="Keyword">import</a> <a id="2507" href="foundation.equality-dependent-pair-types.html" class="Module">foundation.equality-dependent-pair-types</a> <a id="2548" class="Keyword">public</a>
<a id="2555" class="Keyword">open</a> <a id="2560" class="Keyword">import</a> <a id="2567" href="foundation.equality-fibers-of-maps.html" class="Module">foundation.equality-fibers-of-maps</a> <a id="2602" class="Keyword">public</a>
<a id="2609" class="Keyword">open</a> <a id="2614" class="Keyword">import</a> <a id="2621" href="foundation.equivalence-classes.html" class="Module">foundation.equivalence-classes</a> <a id="2652" class="Keyword">public</a>
<a id="2659" class="Keyword">open</a> <a id="2664" class="Keyword">import</a> <a id="2671" href="foundation.equivalence-induction.html" class="Module">foundation.equivalence-induction</a> <a id="2704" class="Keyword">public</a>
<a id="2711" class="Keyword">open</a> <a id="2716" class="Keyword">import</a> <a id="2723" href="foundation.equivalence-relations.html" class="Module">foundation.equivalence-relations</a> <a id="2756" class="Keyword">public</a>
<a id="2763" class="Keyword">open</a> <a id="2768" class="Keyword">import</a> <a id="2775" href="foundation.equivalences-maybe.html" class="Module">foundation.equivalences-maybe</a> <a id="2805" class="Keyword">public</a>
<a id="2812" class="Keyword">open</a> <a id="2817" class="Keyword">import</a> <a id="2824" href="foundation.equivalences.html" class="Module">foundation.equivalences</a> <a id="2848" class="Keyword">public</a>
<a id="2855" class="Keyword">open</a> <a id="2860" class="Keyword">import</a> <a id="2867" href="foundation.existential-quantification.html" class="Module">foundation.existential-quantification</a> <a id="2905" class="Keyword">public</a>
<a id="2912" class="Keyword">open</a> <a id="2917" class="Keyword">import</a> <a id="2924" href="foundation.extensional-W-types.html" class="Module">foundation.extensional-W-types</a> <a id="2955" class="Keyword">public</a>
<a id="2962" class="Keyword">open</a> <a id="2967" class="Keyword">import</a> <a id="2974" href="foundation.faithful-maps.html" class="Module">foundation.faithful-maps</a> <a id="2999" class="Keyword">public</a>
<a id="3006" class="Keyword">open</a> <a id="3011" class="Keyword">import</a> <a id="3018" href="foundation.fiber-inclusions.html" class="Module">foundation.fiber-inclusions</a> <a id="3046" class="Keyword">public</a>
<a id="3053" class="Keyword">open</a> <a id="3058" class="Keyword">import</a> <a id="3065" href="foundation.fibered-maps.html" class="Module">foundation.fibered-maps</a> <a id="3089" class="Keyword">public</a>
<a id="3096" class="Keyword">open</a> <a id="3101" class="Keyword">import</a> <a id="3108" href="foundation.fibers-of-maps.html" class="Module">foundation.fibers-of-maps</a> <a id="3134" class="Keyword">public</a>
<a id="3141" class="Keyword">open</a> <a id="3146" class="Keyword">import</a> <a id="3153" href="foundation.function-extensionality.html" class="Module">foundation.function-extensionality</a> <a id="3188" class="Keyword">public</a>
<a id="3195" class="Keyword">open</a> <a id="3200" class="Keyword">import</a> <a id="3207" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="3228" class="Keyword">public</a>
<a id="3235" class="Keyword">open</a> <a id="3240" class="Keyword">import</a> <a id="3247" href="foundation.functoriality-cartesian-product-types.html" class="Module">foundation.functoriality-cartesian-product-types</a> <a id="3296" class="Keyword">public</a>
<a id="3303" class="Keyword">open</a> <a id="3308" class="Keyword">import</a> <a id="3315" href="foundation.functoriality-coproduct-types.html" class="Module">foundation.functoriality-coproduct-types</a> <a id="3356" class="Keyword">public</a>
<a id="3363" class="Keyword">open</a> <a id="3368" class="Keyword">import</a> <a id="3375" href="foundation.functoriality-dependent-function-types.html" class="Module">foundation.functoriality-dependent-function-types</a> <a id="3425" class="Keyword">public</a>
<a id="3432" class="Keyword">open</a> <a id="3437" class="Keyword">import</a> <a id="3444" href="foundation.functoriality-dependent-pair-types.html" class="Module">foundation.functoriality-dependent-pair-types</a> <a id="3490" class="Keyword">public</a>
<a id="3497" class="Keyword">open</a> <a id="3502" class="Keyword">import</a> <a id="3509" href="foundation.functoriality-function-types.html" class="Module">foundation.functoriality-function-types</a> <a id="3549" class="Keyword">public</a>
<a id="3556" class="Keyword">open</a> <a id="3561" class="Keyword">import</a> <a id="3568" href="foundation.functoriality-propositional-truncation.html" class="Module">foundation.functoriality-propositional-truncation</a> <a id="3618" class="Keyword">public</a>
<a id="3625" class="Keyword">open</a> <a id="3630" class="Keyword">import</a> <a id="3637" href="foundation.functoriality-set-quotients.html" class="Module">foundation.functoriality-set-quotients</a> <a id="3676" class="Keyword">public</a>
<a id="3683" class="Keyword">open</a> <a id="3688" class="Keyword">import</a> <a id="3695" href="foundation.functoriality-set-truncation.html" class="Module">foundation.functoriality-set-truncation</a>
<a id="3735" class="Keyword">open</a> <a id="3740" class="Keyword">import</a> <a id="3747" href="foundation.functoriality-W-types.html" class="Module">foundation.functoriality-W-types</a> <a id="3780" class="Keyword">public</a>
<a id="3787" class="Keyword">open</a> <a id="3792" class="Keyword">import</a> <a id="3799" href="foundation.fundamental-theorem-of-identity-types.html" class="Module">foundation.fundamental-theorem-of-identity-types</a> <a id="3848" class="Keyword">public</a>
<a id="3855" class="Keyword">open</a> <a id="3860" class="Keyword">import</a> <a id="3867" href="foundation.global-choice.html" class="Module">foundation.global-choice</a> <a id="3892" class="Keyword">public</a>
<a id="3899" class="Keyword">open</a> <a id="3904" class="Keyword">import</a> <a id="3911" href="foundation.homotopies.html" class="Module">foundation.homotopies</a> <a id="3933" class="Keyword">public</a>
<a id="3940" class="Keyword">open</a> <a id="3945" class="Keyword">import</a> <a id="3952" href="foundation.identity-systems.html" class="Module">foundation.identity-systems</a> <a id="3980" class="Keyword">public</a>
<a id="3987" class="Keyword">open</a> <a id="3992" class="Keyword">import</a> <a id="3999" href="foundation.identity-types.html" class="Module">foundation.identity-types</a> <a id="4025" class="Keyword">public</a>
<a id="4032" class="Keyword">open</a> <a id="4037" class="Keyword">import</a> <a id="4044" href="foundation.images.html" class="Module">foundation.images</a> <a id="4062" class="Keyword">public</a>
<a id="4069" class="Keyword">open</a> <a id="4074" class="Keyword">import</a> <a id="4081" href="foundation.impredicative-encodings.html" class="Module">foundation.impredicative-encodings</a> <a id="4116" class="Keyword">public</a>
<a id="4123" class="Keyword">open</a> <a id="4128" class="Keyword">import</a> <a id="4135" href="foundation.indexed-W-types.html" class="Module">foundation.indexed-W-types</a> <a id="4162" class="Keyword">public</a>
<a id="4169" class="Keyword">open</a> <a id="4174" class="Keyword">import</a> <a id="4181" href="foundation.induction-principle-propositional-truncation.html" class="Module">foundation.induction-principle-propositional-truncation</a> <a id="4237" class="Keyword">public</a>
<a id="4244" class="Keyword">open</a> <a id="4249" class="Keyword">import</a> <a id="4256" href="foundation.induction-W-types.html" class="Module">foundation.induction-W-types</a> <a id="4285" class="Keyword">public</a>
<a id="4292" class="Keyword">open</a> <a id="4297" class="Keyword">import</a> <a id="4304" href="foundation.inequality-W-types.html" class="Module">foundation.inequality-W-types</a> <a id="4334" class="Keyword">public</a>
<a id="4341" class="Keyword">open</a> <a id="4346" class="Keyword">import</a> <a id="4353" href="foundation.injective-maps.html" class="Module">foundation.injective-maps</a> <a id="4379" class="Keyword">public</a>
<a id="4386" class="Keyword">open</a> <a id="4391" class="Keyword">import</a> <a id="4398" href="foundation.interchange-law.html" class="Module">foundation.interchange-law</a> <a id="4425" class="Keyword">public</a>
<a id="4432" class="Keyword">open</a> <a id="4437" class="Keyword">import</a> <a id="4444" href="foundation.isolated-points.html" class="Module">foundation.isolated-points</a> <a id="4471" class="Keyword">public</a>
<a id="4478" class="Keyword">open</a> <a id="4483" class="Keyword">import</a> <a id="4490" href="foundation.isomorphisms-of-sets.html" class="Module">foundation.isomorphisms-of-sets</a> <a id="4522" class="Keyword">public</a>
<a id="4529" class="Keyword">open</a> <a id="4534" class="Keyword">import</a> <a id="4541" href="foundation.law-of-excluded-middle.html" class="Module">foundation.law-of-excluded-middle</a> <a id="4575" class="Keyword">public</a>
<a id="4582" class="Keyword">open</a> <a id="4587" class="Keyword">import</a> <a id="4594" href="foundation.lawveres-fixed-point-theorem.html" class="Module">foundation.lawveres-fixed-point-theorem</a> <a id="4634" class="Keyword">public</a>
<a id="4641" class="Keyword">open</a> <a id="4646" class="Keyword">import</a> <a id="4653" href="foundation.lists.html" class="Module">foundation.lists</a> <a id="4670" class="Keyword">public</a>
<a id="4677" class="Keyword">open</a> <a id="4682" class="Keyword">import</a> <a id="4689" href="foundation.locally-small-types.html" class="Module">foundation.locally-small-types</a> <a id="4720" class="Keyword">public</a>
<a id="4727" class="Keyword">open</a> <a id="4732" class="Keyword">import</a> <a id="4739" href="foundation.logical-equivalences.html" class="Module">foundation.logical-equivalences</a> <a id="4771" class="Keyword">public</a>
<a id="4778" class="Keyword">open</a> <a id="4783" class="Keyword">import</a> <a id="4790" href="foundation.maybe.html" class="Module">foundation.maybe</a> <a id="4807" class="Keyword">public</a>
<a id="4814" class="Keyword">open</a> <a id="4819" class="Keyword">import</a> <a id="4826" href="foundation.mere-equality.html" class="Module">foundation.mere-equality</a> <a id="4851" class="Keyword">public</a>
<a id="4858" class="Keyword">open</a> <a id="4863" class="Keyword">import</a> <a id="4870" href="foundation.mere-equivalences.html" class="Module">foundation.mere-equivalences</a> <a id="4899" class="Keyword">public</a>
<a id="4906" class="Keyword">open</a> <a id="4911" class="Keyword">import</a> <a id="4918" href="foundation.monomorphisms.html" class="Module">foundation.monomorphisms</a> <a id="4943" class="Keyword">public</a>
<a id="4950" class="Keyword">open</a> <a id="4955" class="Keyword">import</a> <a id="4962" href="foundation.multisets.html" class="Module">foundation.multisets</a> <a id="4983" class="Keyword">public</a>
<a id="4990" class="Keyword">open</a> <a id="4995" class="Keyword">import</a> <a id="5002" href="foundation.negation.html" class="Module">foundation.negation</a> <a id="5022" class="Keyword">public</a>
<a id="5029" class="Keyword">open</a> <a id="5034" class="Keyword">import</a> <a id="5041" href="foundation.non-contractible-types.html" class="Module">foundation.non-contractible-types</a> <a id="5075" class="Keyword">public</a>
<a id="5082" class="Keyword">open</a> <a id="5087" class="Keyword">import</a> <a id="5094" href="foundation.path-split-maps.html" class="Module">foundation.path-split-maps</a> <a id="5121" class="Keyword">public</a>
<a id="5128" class="Keyword">open</a> <a id="5133" class="Keyword">import</a> <a id="5140" href="foundation.polynomial-endofunctors.html" class="Module">foundation.polynomial-endofunctors</a> <a id="5175" class="Keyword">public</a>
<a id="5182" class="Keyword">open</a> <a id="5187" class="Keyword">import</a> <a id="5194" href="foundation.propositional-extensionality.html" class="Module">foundation.propositional-extensionality</a> <a id="5234" class="Keyword">public</a>
<a id="5241" class="Keyword">open</a> <a id="5246" class="Keyword">import</a> <a id="5253" href="foundation.propositional-maps.html" class="Module">foundation.propositional-maps</a> <a id="5283" class="Keyword">public</a>
<a id="5290" class="Keyword">open</a> <a id="5295" class="Keyword">import</a> <a id="5302" href="foundation.propositional-truncations.html" class="Module">foundation.propositional-truncations</a> <a id="5339" class="Keyword">public</a>
<a id="5346" class="Keyword">open</a> <a id="5351" class="Keyword">import</a> <a id="5358" href="foundation.propositions.html" class="Module">foundation.propositions</a> <a id="5382" class="Keyword">public</a>
<a id="5389" class="Keyword">open</a> <a id="5394" class="Keyword">import</a> <a id="5401" href="foundation.pullbacks.html" class="Module">foundation.pullbacks</a> <a id="5422" class="Keyword">public</a>
<a id="5429" class="Keyword">open</a> <a id="5434" class="Keyword">import</a> <a id="5441" href="foundation.raising-universe-levels.html" class="Module">foundation.raising-universe-levels</a> <a id="5476" class="Keyword">public</a>
<a id="5483" class="Keyword">open</a> <a id="5488" class="Keyword">import</a> <a id="5495" href="foundation.reflecting-maps-equivalence-relations.html" class="Module">foundation.reflecting-maps-equivalence-relations</a> <a id="5544" class="Keyword">public</a>
<a id="5551" class="Keyword">open</a> <a id="5556" class="Keyword">import</a> <a id="5563" href="foundation.replacement.html" class="Module">foundation.replacement</a> <a id="5586" class="Keyword">public</a>
<a id="5593" class="Keyword">open</a> <a id="5598" class="Keyword">import</a> <a id="5605" href="foundation.retractions.html" class="Module">foundation.retractions</a> <a id="5628" class="Keyword">public</a>
<a id="5635" class="Keyword">open</a> <a id="5640" class="Keyword">import</a> <a id="5647" href="foundation.Russells-paradox.html" class="Module">foundation.Russells-paradox</a> <a id="5675" class="Keyword">public</a>
<a id="5682" class="Keyword">open</a> <a id="5687" class="Keyword">import</a> <a id="5694" href="foundation.sections.html" class="Module">foundation.sections</a> <a id="5714" class="Keyword">public</a>
<a id="5721" class="Keyword">open</a> <a id="5726" class="Keyword">import</a> <a id="5733" href="foundation.set-presented-types.html" class="Module">foundation.set-presented-types</a> <a id="5764" class="Keyword">public</a>
<a id="5771" class="Keyword">open</a> <a id="5776" class="Keyword">import</a> <a id="5783" href="foundation.set-truncations.html" class="Module">foundation.set-truncations</a> <a id="5810" class="Keyword">public</a>
<a id="5817" class="Keyword">open</a> <a id="5822" class="Keyword">import</a> <a id="5829" href="foundation.sets.html" class="Module">foundation.sets</a> <a id="5845" class="Keyword">public</a>
<a id="5852" class="Keyword">open</a> <a id="5857" class="Keyword">import</a> <a id="5864" href="foundation.singleton-induction.html" class="Module">foundation.singleton-induction</a> <a id="5895" class="Keyword">public</a>
<a id="5902" class="Keyword">open</a> <a id="5907" class="Keyword">import</a> <a id="5914" href="foundation.slice.html" class="Module">foundation.slice</a> <a id="5931" class="Keyword">public</a>
<a id="5938" class="Keyword">open</a> <a id="5943" class="Keyword">import</a> <a id="5950" href="foundation.small-maps.html" class="Module">foundation.small-maps</a> <a id="5972" class="Keyword">public</a>
<a id="5979" class="Keyword">open</a> <a id="5984" class="Keyword">import</a> <a id="5991" href="foundation.small-multisets.html" class="Module">foundation.small-multisets</a> <a id="6018" class="Keyword">public</a>
<a id="6025" class="Keyword">open</a> <a id="6030" class="Keyword">import</a> <a id="6037" href="foundation.small-types.html" class="Module">foundation.small-types</a> <a id="6060" class="Keyword">public</a>
<a id="6067" class="Keyword">open</a> <a id="6072" class="Keyword">import</a> <a id="6079" href="foundation.small-universes.html" class="Module">foundation.small-universes</a> <a id="6106" class="Keyword">public</a>
<a id="6113" class="Keyword">open</a> <a id="6118" class="Keyword">import</a> <a id="6125" href="foundation.split-surjective-maps.html" class="Module">foundation.split-surjective-maps</a> <a id="6158" class="Keyword">public</a>
<a id="6165" class="Keyword">open</a> <a id="6170" class="Keyword">import</a> <a id="6177" href="foundation.structure-identity-principle.html" class="Module">foundation.structure-identity-principle</a> <a id="6217" class="Keyword">public</a>
<a id="6224" class="Keyword">open</a> <a id="6229" class="Keyword">import</a> <a id="6236" href="foundation.structure.html" class="Module">foundation.structure</a> <a id="6257" class="Keyword">public</a>
<a id="6264" class="Keyword">open</a> <a id="6269" class="Keyword">import</a> <a id="6276" href="foundation.subterminal-types.html" class="Module">foundation.subterminal-types</a> <a id="6305" class="Keyword">public</a>
<a id="6312" class="Keyword">open</a> <a id="6317" class="Keyword">import</a> <a id="6324" href="foundation.subtype-identity-principle.html" class="Module">foundation.subtype-identity-principle</a> <a id="6362" class="Keyword">public</a>
<a id="6369" class="Keyword">open</a> <a id="6374" class="Keyword">import</a> <a id="6381" href="foundation.subtypes.html" class="Module">foundation.subtypes</a> <a id="6401" class="Keyword">public</a>
<a id="6408" class="Keyword">open</a> <a id="6413" class="Keyword">import</a> <a id="6420" href="foundation.subuniverses.html" class="Module">foundation.subuniverses</a> <a id="6444" class="Keyword">public</a>
<a id="6451" class="Keyword">open</a> <a id="6456" class="Keyword">import</a> <a id="6463" href="foundation.surjective-maps.html" class="Module">foundation.surjective-maps</a> <a id="6490" class="Keyword">public</a>
<a id="6497" class="Keyword">open</a> <a id="6502" class="Keyword">import</a> <a id="6509" href="foundation.truncated-maps.html" class="Module">foundation.truncated-maps</a> <a id="6535" class="Keyword">public</a>
<a id="6542" class="Keyword">open</a> <a id="6547" class="Keyword">import</a> <a id="6554" href="foundation.truncated-types.html" class="Module">foundation.truncated-types</a> <a id="6581" class="Keyword">public</a>
<a id="6588" class="Keyword">open</a> <a id="6593" class="Keyword">import</a> <a id="6600" href="foundation.truncation-levels.html" class="Module">foundation.truncation-levels</a> <a id="6629" class="Keyword">public</a>
<a id="6636" class="Keyword">open</a> <a id="6641" class="Keyword">import</a> <a id="6648" href="foundation.type-arithmetic-cartesian-product-types.html" class="Module">foundation.type-arithmetic-cartesian-product-types</a> <a id="6699" class="Keyword">public</a>
<a id="6706" class="Keyword">open</a> <a id="6711" class="Keyword">import</a> <a id="6718" href="foundation.type-arithmetic-coproduct-types.html" class="Module">foundation.type-arithmetic-coproduct-types</a> <a id="6761" class="Keyword">public</a>
<a id="6768" class="Keyword">open</a> <a id="6773" class="Keyword">import</a> <a id="6780" href="foundation.type-arithmetic-dependent-pair-types.html" class="Module">foundation.type-arithmetic-dependent-pair-types</a> <a id="6828" class="Keyword">public</a>
<a id="6835" class="Keyword">open</a> <a id="6840" class="Keyword">import</a> <a id="6847" href="foundation.type-arithmetic-empty-type.html" class="Module">foundation.type-arithmetic-empty-type</a> <a id="6885" class="Keyword">public</a>
<a id="6892" class="Keyword">open</a> <a id="6897" class="Keyword">import</a> <a id="6904" href="foundation.type-arithmetic-unit-type.html" class="Module">foundation.type-arithmetic-unit-type</a> <a id="6941" class="Keyword">public</a>
<a id="6948" class="Keyword">open</a> <a id="6953" class="Keyword">import</a> <a id="6960" href="foundation.uniqueness-image.html" class="Module">foundation.uniqueness-image</a> <a id="6988" class="Keyword">public</a>
<a id="6995" class="Keyword">open</a> <a id="7000" class="Keyword">import</a> <a id="7007" href="foundation.uniqueness-set-quotients.html" class="Module">foundation.uniqueness-set-quotients</a> <a id="7043" class="Keyword">public</a>
<a id="7050" class="Keyword">open</a> <a id="7055" class="Keyword">import</a> <a id="7062" href="foundation.uniqueness-set-truncations.html" class="Module">foundation.uniqueness-set-truncations</a> <a id="7100" class="Keyword">public</a>
<a id="7107" class="Keyword">open</a> <a id="7112" class="Keyword">import</a> <a id="7119" href="foundation.unit-type.html" class="Module">foundation.unit-type</a> <a id="7140" class="Keyword">public</a>
<a id="7147" class="Keyword">open</a> <a id="7152" class="Keyword">import</a> <a id="7159" href="foundation.univalence-implies-function-extensionality.html" class="Module">foundation.univalence-implies-function-extensionality</a> <a id="7213" class="Keyword">public</a>
<a id="7220" class="Keyword">open</a> <a id="7225" class="Keyword">import</a> <a id="7232" href="foundation.univalence.html" class="Module">foundation.univalence</a> <a id="7254" class="Keyword">public</a>
<a id="7261" class="Keyword">open</a> <a id="7266" class="Keyword">import</a> <a id="7273" href="foundation.univalent-type-families.html" class="Module">foundation.univalent-type-families</a> <a id="7308" class="Keyword">public</a>
<a id="7315" class="Keyword">open</a> <a id="7320" class="Keyword">import</a> <a id="7327" href="foundation.universal-property-booleans.html" class="Module">foundation.universal-property-booleans</a> <a id="7366" class="Keyword">public</a>
<a id="7373" class="Keyword">open</a> <a id="7378" class="Keyword">import</a> <a id="7385" href="foundation.universal-property-cartesian-product-types.html" class="Module">foundation.universal-property-cartesian-product-types</a> <a id="7439" class="Keyword">public</a>
<a id="7446" class="Keyword">open</a> <a id="7451" class="Keyword">import</a> <a id="7458" href="foundation.universal-property-coproduct-types.html" class="Module">foundation.universal-property-coproduct-types</a> <a id="7504" class="Keyword">public</a>
<a id="7511" class="Keyword">open</a> <a id="7516" class="Keyword">import</a> <a id="7523" href="foundation.universal-property-dependent-pair-types.html" class="Module">foundation.universal-property-dependent-pair-types</a> <a id="7574" class="Keyword">public</a>
<a id="7581" class="Keyword">open</a> <a id="7586" class="Keyword">import</a> <a id="7593" href="foundation.universal-property-empty-type.html" class="Module">foundation.universal-property-empty-type</a> <a id="7634" class="Keyword">public</a>
<a id="7641" class="Keyword">open</a> <a id="7646" class="Keyword">import</a> <a id="7653" href="foundation.universal-property-fiber-products.html" class="Module">foundation.universal-property-fiber-products</a> <a id="7698" class="Keyword">public</a>
<a id="7705" class="Keyword">open</a> <a id="7710" class="Keyword">import</a> <a id="7717" href="foundation.universal-property-identity-types.html" class="Module">foundation.universal-property-identity-types</a> <a id="7762" class="Keyword">public</a>
<a id="7769" class="Keyword">open</a> <a id="7774" class="Keyword">import</a> <a id="7781" href="foundation.universal-property-image.html" class="Module">foundation.universal-property-image</a> <a id="7817" class="Keyword">public</a>
<a id="7824" class="Keyword">open</a> <a id="7829" class="Keyword">import</a> <a id="7836" href="foundation.universal-property-maybe.html" class="Module">foundation.universal-property-maybe</a> <a id="7872" class="Keyword">public</a>
<a id="7879" class="Keyword">open</a> <a id="7884" class="Keyword">import</a> <a id="7891" href="foundation.universal-property-propositional-truncation-into-sets.html" class="Module">foundation.universal-property-propositional-truncation-into-sets</a> <a id="7956" class="Keyword">public</a>
<a id="7963" class="Keyword">open</a> <a id="7968" class="Keyword">import</a> <a id="7975" href="foundation.universal-property-propositional-truncation.html" class="Module">foundation.universal-property-propositional-truncation</a> <a id="8030" class="Keyword">public</a>
<a id="8037" class="Keyword">open</a> <a id="8042" class="Keyword">import</a> <a id="8049" href="foundation.universal-property-pullbacks.html" class="Module">foundation.universal-property-pullbacks</a> <a id="8089" class="Keyword">public</a>
<a id="8096" class="Keyword">open</a> <a id="8101" class="Keyword">import</a> <a id="8108" href="foundation.universal-property-set-quotients.html" class="Module">foundation.universal-property-set-quotients</a> <a id="8152" class="Keyword">public</a>
<a id="8159" class="Keyword">open</a> <a id="8164" class="Keyword">import</a> <a id="8171" href="foundation.universal-property-set-truncation.html" class="Module">foundation.universal-property-set-truncation</a> <a id="8216" class="Keyword">public</a>
<a id="8223" class="Keyword">open</a> <a id="8228" class="Keyword">import</a> <a id="8235" href="foundation.universal-property-unit-type.html" class="Module">foundation.universal-property-unit-type</a> <a id="8275" class="Keyword">public</a>
<a id="8282" class="Keyword">open</a> <a id="8287" class="Keyword">import</a> <a id="8294" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="8321" class="Keyword">public</a>
<a id="8328" class="Keyword">open</a> <a id="8333" class="Keyword">import</a> <a id="8340" href="foundation.unordered-pairs.html" class="Module">foundation.unordered-pairs</a> <a id="8367" class="Keyword">public</a>
<a id="8374" class="Keyword">open</a> <a id="8379" class="Keyword">import</a> <a id="8386" href="foundation.W-types.html" class="Module">foundation.W-types</a> <a id="8405" class="Keyword">public</a>
<a id="8412" class="Keyword">open</a> <a id="8417" class="Keyword">import</a> <a id="8424" href="foundation.weak-function-extensionality.html" class="Module">foundation.weak-function-extensionality</a> <a id="8464" class="Keyword">public</a>
<a id="8471" class="Keyword">open</a> <a id="8476" class="Keyword">import</a> <a id="8483" href="foundation.weakly-constant-maps.html" class="Module">foundation.weakly-constant-maps</a> <a id="8515" class="Keyword">public</a>
</pre>