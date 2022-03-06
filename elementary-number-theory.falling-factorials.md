# Falling factorials

<pre class="Agda"><a id="31" class="Symbol">{-#</a> <a id="35" class="Keyword">OPTIONS</a> <a id="43" class="Pragma">--without-K</a> <a id="55" class="Pragma">--exact-split</a> <a id="69" class="Symbol">#-}</a>

<a id="74" class="Keyword">module</a> <a id="81" href="elementary-number-theory.falling-factorials.html" class="Module">elementary-number-theory.falling-factorials</a> <a id="125" class="Keyword">where</a>

<a id="132" class="Keyword">open</a> <a id="137" class="Keyword">import</a> <a id="144" href="elementary-number-theory.multiplication-natural-numbers.html" class="Module">elementary-number-theory.multiplication-natural-numbers</a> <a id="200" class="Keyword">using</a>
  <a id="208" class="Symbol">(</a> <a id="210" href="elementary-number-theory.multiplication-natural-numbers.html#1176" class="Function">mul-ℕ</a><a id="215" class="Symbol">)</a>
<a id="217" class="Keyword">open</a> <a id="222" class="Keyword">import</a> <a id="229" href="elementary-number-theory.natural-numbers.html" class="Module">elementary-number-theory.natural-numbers</a> <a id="270" class="Keyword">using</a> <a id="276" class="Symbol">(</a><a id="277" href="elementary-number-theory.natural-numbers.html#1438" class="Datatype">ℕ</a><a id="278" class="Symbol">;</a> <a id="280" href="elementary-number-theory.natural-numbers.html#1459" class="InductiveConstructor">zero-ℕ</a><a id="286" class="Symbol">;</a> <a id="288" href="elementary-number-theory.natural-numbers.html#1472" class="InductiveConstructor">succ-ℕ</a><a id="294" class="Symbol">)</a>
</pre>
## Idea

The falling factorial (n)_m is the number n(n-1)⋯(n-m+1)

## Definition

<pre class="Agda"><a id="falling-factorial-ℕ"></a><a id="391" href="elementary-number-theory.falling-factorials.html#391" class="Function">falling-factorial-ℕ</a> <a id="411" class="Symbol">:</a> <a id="413" href="elementary-number-theory.natural-numbers.html#1438" class="Datatype">ℕ</a> <a id="415" class="Symbol">→</a> <a id="417" href="elementary-number-theory.natural-numbers.html#1438" class="Datatype">ℕ</a> <a id="419" class="Symbol">→</a> <a id="421" href="elementary-number-theory.natural-numbers.html#1438" class="Datatype">ℕ</a>
<a id="423" href="elementary-number-theory.falling-factorials.html#391" class="Function">falling-factorial-ℕ</a> <a id="443" href="elementary-number-theory.natural-numbers.html#1459" class="InductiveConstructor">zero-ℕ</a> <a id="450" href="elementary-number-theory.natural-numbers.html#1459" class="InductiveConstructor">zero-ℕ</a> <a id="457" class="Symbol">=</a> <a id="459" class="Number">1</a>
<a id="461" href="elementary-number-theory.falling-factorials.html#391" class="Function">falling-factorial-ℕ</a> <a id="481" href="elementary-number-theory.natural-numbers.html#1459" class="InductiveConstructor">zero-ℕ</a> <a id="488" class="Symbol">(</a><a id="489" href="elementary-number-theory.natural-numbers.html#1472" class="InductiveConstructor">succ-ℕ</a> <a id="496" href="elementary-number-theory.falling-factorials.html#496" class="Bound">m</a><a id="497" class="Symbol">)</a> <a id="499" class="Symbol">=</a> <a id="501" class="Number">0</a>
<a id="503" href="elementary-number-theory.falling-factorials.html#391" class="Function">falling-factorial-ℕ</a> <a id="523" class="Symbol">(</a><a id="524" href="elementary-number-theory.natural-numbers.html#1472" class="InductiveConstructor">succ-ℕ</a> <a id="531" href="elementary-number-theory.falling-factorials.html#531" class="Bound">n</a><a id="532" class="Symbol">)</a> <a id="534" href="elementary-number-theory.natural-numbers.html#1459" class="InductiveConstructor">zero-ℕ</a> <a id="541" class="Symbol">=</a> <a id="543" class="Number">1</a>
<a id="545" href="elementary-number-theory.falling-factorials.html#391" class="Function">falling-factorial-ℕ</a> <a id="565" class="Symbol">(</a><a id="566" href="elementary-number-theory.natural-numbers.html#1472" class="InductiveConstructor">succ-ℕ</a> <a id="573" href="elementary-number-theory.falling-factorials.html#573" class="Bound">n</a><a id="574" class="Symbol">)</a> <a id="576" class="Symbol">(</a><a id="577" href="elementary-number-theory.natural-numbers.html#1472" class="InductiveConstructor">succ-ℕ</a> <a id="584" href="elementary-number-theory.falling-factorials.html#584" class="Bound">m</a><a id="585" class="Symbol">)</a> <a id="587" class="Symbol">=</a>
  <a id="591" href="elementary-number-theory.multiplication-natural-numbers.html#1176" class="Function">mul-ℕ</a> <a id="597" class="Symbol">(</a><a id="598" href="elementary-number-theory.natural-numbers.html#1472" class="InductiveConstructor">succ-ℕ</a> <a id="605" href="elementary-number-theory.falling-factorials.html#573" class="Bound">n</a><a id="606" class="Symbol">)</a> <a id="608" class="Symbol">(</a><a id="609" href="elementary-number-theory.falling-factorials.html#391" class="Function">falling-factorial-ℕ</a> <a id="629" href="elementary-number-theory.falling-factorials.html#573" class="Bound">n</a> <a id="631" href="elementary-number-theory.falling-factorials.html#584" class="Bound">m</a><a id="632" class="Symbol">)</a>

<a id="635" class="Comment">{-
Fin-falling-factorial-ℕ :
  (n m : ℕ) → Fin (falling-factorial-ℕ n m) ≃ (Fin m ↪ Fin n)
Fin-falling-factorial-ℕ n m = {!!}
-}</a>

<a id="765" class="Comment">{-
Fin-falling-factorial-ℕ : (n m : ℕ) → Fin (falling-factorial-ℕ n m) ≃ (Fin m ↪ Fin n)
Fin-falling-factorial-ℕ zero-ℕ zero-ℕ =
  equiv-is-contr
    ( is-contr-Fin-one-ℕ)
    ( is-contr-equiv
      ( is-emb id)
      ( left-unit-law-Σ-is-contr
        ( universal-property-empty&#39; empty)
        ( id))
      ( dependent-universal-property-empty&#39;
        ( λ x → (y : empty) → is-equiv (ap id))))
Fin-falling-factorial-ℕ zero-ℕ (succ-ℕ m) =
  equiv-is-empty id (λ f → map-emb f (inr star))
Fin-falling-factorial-ℕ (succ-ℕ n) zero-ℕ =
  equiv-is-contr
    ( is-contr-Fin-one-ℕ)
    ( is-contr-equiv
      ( is-emb ex-falso)
      ( left-unit-law-Σ-is-contr
        ( universal-property-empty&#39; (Fin (succ-ℕ n)))
        ( ex-falso))
      ( dependent-universal-property-empty&#39;
        ( λ x → (y : empty) → is-equiv (ap ex-falso))))
Fin-falling-factorial-ℕ (succ-ℕ n) (succ-ℕ m) =
  ( ( ( right-unit-law-Σ-is-contr
        { B = λ f → is-decidable (fib (map-emb f) (inr star))}
        ( λ f →
          is-proof-irrelevant-is-prop
            ( is-prop-is-decidable
              ( is-prop-map-is-emb (is-emb-map-emb f) (inr star)))
            ( is-decidable-Σ-Fin
              ( λ x →
                has-decidable-equality-Fin (map-emb f x) (inr star))))) ∘e
      ( ( inv-equiv
          ( left-distributive-Σ-coprod
            ( Fin (succ-ℕ m) ↪ Fin (succ-ℕ n))
            ( λ f → fib (map-emb f) (inr star))
            ( λ f → ¬ (fib (map-emb f) (inr star))))) ∘e
        {!!})) ∘e
    ( equiv-coprod (Fin-falling-factorial-ℕ n m) (Fin-falling-factorial-ℕ n (succ-ℕ m)))) ∘e
  ( Fin-add-ℕ (falling-factorial-ℕ n m) (falling-factorial-ℕ n (succ-ℕ m)))
-}</a>
</pre>