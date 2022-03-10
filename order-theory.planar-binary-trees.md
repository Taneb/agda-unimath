# Planar binary trees

<pre class="Agda"><a id="32" class="Symbol">{-#</a> <a id="36" class="Keyword">OPTIONS</a> <a id="44" class="Pragma">--without-K</a> <a id="56" class="Pragma">--exact-split</a> <a id="70" class="Symbol">#-}</a>

<a id="75" class="Keyword">module</a> <a id="82" href="order-theory.planar-binary-trees.html" class="Module">order-theory.planar-binary-trees</a> <a id="115" class="Keyword">where</a>

<a id="122" class="Keyword">open</a> <a id="127" class="Keyword">import</a> <a id="134" href="foundation.booleans.html" class="Module">foundation.booleans</a> <a id="154" class="Keyword">using</a> <a id="160" class="Symbol">(</a><a id="161" href="foundation.booleans.html#1074" class="Datatype">bool</a><a id="165" class="Symbol">;</a> <a id="167" href="foundation.booleans.html#1103" class="InductiveConstructor">false</a><a id="172" class="Symbol">;</a> <a id="174" href="foundation.booleans.html#1098" class="InductiveConstructor">true</a><a id="178" class="Symbol">)</a>
<a id="180" class="Keyword">open</a> <a id="185" class="Keyword">import</a> <a id="192" href="foundation.empty-types.html" class="Module">foundation.empty-types</a> <a id="215" class="Keyword">using</a> <a id="221" class="Symbol">(</a><a id="222" href="foundation-core.empty-types.html#1047" class="Datatype">empty</a><a id="227" class="Symbol">)</a>
<a id="229" class="Keyword">open</a> <a id="234" class="Keyword">import</a> <a id="241" href="foundation.functions.html" class="Module">foundation.functions</a> <a id="262" class="Keyword">using</a> <a id="268" class="Symbol">(</a><a id="269" href="foundation-core.functions.html#309" class="Function">id</a><a id="271" class="Symbol">)</a>
<a id="273" class="Keyword">open</a> <a id="278" class="Keyword">import</a> <a id="285" href="foundation.universe-levels.html" class="Module">foundation.universe-levels</a> <a id="312" class="Keyword">using</a> <a id="318" class="Symbol">(</a><a id="319" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a><a id="321" class="Symbol">;</a> <a id="323" href="Agda.Primitive.html#764" class="Primitive">lzero</a><a id="328" class="Symbol">)</a>
<a id="330" class="Keyword">open</a> <a id="335" class="Keyword">import</a> <a id="342" href="foundation.w-types.html" class="Module">foundation.w-types</a> <a id="361" class="Keyword">using</a> <a id="367" class="Symbol">(</a><a id="368" href="foundation.w-types.html#2315" class="Datatype">𝕎</a><a id="369" class="Symbol">;</a> <a id="371" href="foundation.w-types.html#2926" class="Function">constant-𝕎</a><a id="381" class="Symbol">;</a> <a id="383" href="foundation.w-types.html#2384" class="InductiveConstructor">tree-𝕎</a><a id="389" class="Symbol">)</a>
</pre>
## Idea

A planar binary tree is a binary tree in which the branchings are labelled by the booleans. The idea is that at any branching point in a planar binary tree, we know which branch goes to the left and which branch goes to the right.

Planar binary trees are commonly called binary trees, but in univalent mathematics it makes sense to recognize that the branching points in a binary tree should not record which branch goes left and which branch goes right.

## Definitions

### The inductive definition of the type of planar binary trees

<pre class="Agda"><a id="951" class="Keyword">data</a> <a id="Planar-Bin-Tree"></a><a id="956" href="order-theory.planar-binary-trees.html#956" class="Datatype">Planar-Bin-Tree</a> <a id="972" class="Symbol">:</a> <a id="974" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="977" href="Agda.Primitive.html#764" class="Primitive">lzero</a> <a id="983" class="Keyword">where</a>
  <a id="Planar-Bin-Tree.root-PBT"></a><a id="991" href="order-theory.planar-binary-trees.html#991" class="InductiveConstructor">root-PBT</a> <a id="1000" class="Symbol">:</a> <a id="1002" href="order-theory.planar-binary-trees.html#956" class="Datatype">Planar-Bin-Tree</a>
  <a id="Planar-Bin-Tree.join-PBT"></a><a id="1020" href="order-theory.planar-binary-trees.html#1020" class="InductiveConstructor">join-PBT</a> <a id="1029" class="Symbol">:</a> <a id="1031" class="Symbol">(</a><a id="1032" href="order-theory.planar-binary-trees.html#1032" class="Bound">x</a> <a id="1034" href="order-theory.planar-binary-trees.html#1034" class="Bound">y</a> <a id="1036" class="Symbol">:</a> <a id="1038" href="order-theory.planar-binary-trees.html#956" class="Datatype">Planar-Bin-Tree</a><a id="1053" class="Symbol">)</a> <a id="1055" class="Symbol">→</a> <a id="1057" href="order-theory.planar-binary-trees.html#956" class="Datatype">Planar-Bin-Tree</a>
</pre>
### The definition of the type of planar binary trees as a W-type

<pre class="Agda"><a id="PBT-𝕎"></a><a id="1153" href="order-theory.planar-binary-trees.html#1153" class="Function">PBT-𝕎</a> <a id="1159" class="Symbol">:</a> <a id="1161" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1164" href="Agda.Primitive.html#764" class="Primitive">lzero</a>
<a id="1170" href="order-theory.planar-binary-trees.html#1153" class="Function">PBT-𝕎</a> <a id="1176" class="Symbol">=</a> <a id="1178" href="foundation.w-types.html#2315" class="Datatype">𝕎</a> <a id="1180" href="foundation.booleans.html#1074" class="Datatype">bool</a> <a id="1185" href="order-theory.planar-binary-trees.html#1197" class="Function">P</a>
  <a id="1189" class="Keyword">where</a>
  <a id="1197" href="order-theory.planar-binary-trees.html#1197" class="Function">P</a> <a id="1199" class="Symbol">:</a> <a id="1201" href="foundation.booleans.html#1074" class="Datatype">bool</a> <a id="1206" class="Symbol">→</a> <a id="1208" href="foundation-core.universe-levels.html#222" class="Primitive">UU</a> <a id="1211" href="Agda.Primitive.html#764" class="Primitive">lzero</a>
  <a id="1219" href="order-theory.planar-binary-trees.html#1197" class="Function">P</a> <a id="1221" href="foundation.booleans.html#1098" class="InductiveConstructor">true</a> <a id="1226" class="Symbol">=</a> <a id="1228" href="foundation.booleans.html#1074" class="Datatype">bool</a>
  <a id="1235" href="order-theory.planar-binary-trees.html#1197" class="Function">P</a> <a id="1237" href="foundation.booleans.html#1103" class="InductiveConstructor">false</a> <a id="1243" class="Symbol">=</a> <a id="1245" href="foundation-core.empty-types.html#1047" class="Datatype">empty</a>

<a id="root-PBT-𝕎"></a><a id="1252" href="order-theory.planar-binary-trees.html#1252" class="Function">root-PBT-𝕎</a> <a id="1263" class="Symbol">:</a> <a id="1265" href="order-theory.planar-binary-trees.html#1153" class="Function">PBT-𝕎</a>
<a id="1271" href="order-theory.planar-binary-trees.html#1252" class="Function">root-PBT-𝕎</a> <a id="1282" class="Symbol">=</a> <a id="1284" href="foundation.w-types.html#2926" class="Function">constant-𝕎</a> <a id="1295" href="foundation.booleans.html#1103" class="InductiveConstructor">false</a> <a id="1301" href="foundation-core.functions.html#309" class="Function">id</a>

<a id="join-PBT-𝕎"></a><a id="1305" href="order-theory.planar-binary-trees.html#1305" class="Function">join-PBT-𝕎</a> <a id="1316" class="Symbol">:</a> <a id="1318" class="Symbol">(</a><a id="1319" href="order-theory.planar-binary-trees.html#1319" class="Bound">x</a> <a id="1321" href="order-theory.planar-binary-trees.html#1321" class="Bound">y</a> <a id="1323" class="Symbol">:</a> <a id="1325" href="order-theory.planar-binary-trees.html#1153" class="Function">PBT-𝕎</a><a id="1330" class="Symbol">)</a> <a id="1332" class="Symbol">→</a> <a id="1334" href="order-theory.planar-binary-trees.html#1153" class="Function">PBT-𝕎</a>
<a id="1340" href="order-theory.planar-binary-trees.html#1305" class="Function">join-PBT-𝕎</a> <a id="1351" href="order-theory.planar-binary-trees.html#1351" class="Bound">x</a> <a id="1353" href="order-theory.planar-binary-trees.html#1353" class="Bound">y</a> <a id="1355" class="Symbol">=</a> <a id="1357" href="foundation.w-types.html#2384" class="InductiveConstructor">tree-𝕎</a> <a id="1364" href="foundation.booleans.html#1098" class="InductiveConstructor">true</a> <a id="1369" href="order-theory.planar-binary-trees.html#1381" class="Function">α</a>
  <a id="1373" class="Keyword">where</a>
  <a id="1381" href="order-theory.planar-binary-trees.html#1381" class="Function">α</a> <a id="1383" class="Symbol">:</a> <a id="1385" href="foundation.booleans.html#1074" class="Datatype">bool</a> <a id="1390" class="Symbol">→</a> <a id="1392" href="order-theory.planar-binary-trees.html#1153" class="Function">PBT-𝕎</a>
  <a id="1400" href="order-theory.planar-binary-trees.html#1381" class="Function">α</a> <a id="1402" href="foundation.booleans.html#1098" class="InductiveConstructor">true</a> <a id="1407" class="Symbol">=</a> <a id="1409" href="order-theory.planar-binary-trees.html#1351" class="Bound">x</a>
  <a id="1413" href="order-theory.planar-binary-trees.html#1381" class="Function">α</a> <a id="1415" href="foundation.booleans.html#1103" class="InductiveConstructor">false</a> <a id="1421" class="Symbol">=</a> <a id="1423" href="order-theory.planar-binary-trees.html#1353" class="Bound">y</a>
</pre>
## Properties

### The types `Planar-Bin-Tree` and `PBT-𝕎` are equivalent

<pre class="Agda"><a id="1513" class="Comment">{-
Planar-Bin-Tree-PBT-𝕎 : PBT-𝕎 → Planar-Bin-Tree
Planar-Bin-Tree-PBT-𝕎 (tree-𝕎 true α) =
  join-PBT
    ( Planar-Bin-Tree-PBT-𝕎 (α true))
    ( Planar-Bin-Tree-PBT-𝕎 (α false))
Planar-Bin-Tree-PBT-𝕎 (tree-𝕎 false α) = {!!}
-}</a>
</pre>