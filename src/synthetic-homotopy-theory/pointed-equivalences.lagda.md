# Pointed equivalences

```agda
{-# OPTIONS --without-K --exact-split #-}

module synthetic-homotopy-theory.pointed-equivalences where

open import foundation.contractible-maps using (is-contr-map-is-equiv)
open import foundation.contractible-types using
  ( is-contr; is-contr-equiv; is-contr-prod; center; eq-is-contr)
open import foundation.cartesian-product-types using (_×_)
open import foundation.dependent-pair-types using (Σ; pair; pr1; pr2)
open import foundation.equivalences using
  ( is-equiv; is-contr-sec-is-equiv; map-inv-is-equiv; issec-map-inv-is-equiv;
    _∘e_; is-emb-is-equiv; is-contr-retr-is-equiv; isretr-map-inv-is-equiv;
    is-equiv-comp'; _≃_; is-property-is-equiv; map-equiv; id-equiv;
    map-inv-equiv; is-equiv-has-inverse)
open import foundation.fibers-of-maps using (fib)
open import foundation.function-extensionality using (htpy-eq)
open import foundation.functions using (_∘_; id)
open import foundation.functoriality-dependent-pair-types using (equiv-tot)
open import foundation.homotopies using (_~_)
open import foundation.identity-types using
  ( Id; refl; ap; inv; _∙_; equiv-con-inv; equiv-inv; equiv-concat'; right-unit;
    is-equiv-concat; is-equiv-concat')
open import foundation.propositions using
  ( is-prop; is-prop-is-proof-irrelevant; is-equiv-is-prop)
open import foundation.structure-identity-principle using
  ( is-contr-total-Eq-structure; extensionality-Σ)
open import foundation.type-arithmetic-dependent-pair-types using
  ( equiv-right-swap-Σ)
open import foundation.univalence using (equiv-univalence)
open import foundation.universe-levels using (Level; UU; _⊔_)

open import synthetic-homotopy-theory.pointed-homotopies using
  ( htpy-pointed-map; extensionality-pointed-map; eq-htpy-pointed-map;
    concat-htpy-pointed-map; assoc-comp-pointed-map;
    left-whisker-htpy-pointed-map; right-unit-law-comp-pointed-map;
    left-unit-law-comp-pointed-map; inv-assoc-comp-pointed-map;
    right-whisker-htpy-pointed-map)
open import synthetic-homotopy-theory.pointed-maps using
  ( _→*_; comp-pointed-map; id-pointed-map; map-pointed-map;
    preserves-point-map-pointed-map; precomp-pointed-map)
open import synthetic-homotopy-theory.pointed-types using
  ( Pointed-Type; type-Pointed-Type; pt-Pointed-Type)
```

## Idea

A pointed equivalence is an equivalence in the category of pointed spaces. Equivalently, a pointed equivalence is a pointed map of which the underlying function is an equivalence.

## Definition

```agda
module _
  {l1 l2 : Level} (A : Pointed-Type l1) (B : Pointed-Type l2) (f : A →* B)
  where

  sec-pointed-map : UU (l1 ⊔ l2)
  sec-pointed-map =
    Σ ( B →* A)
      ( λ g →
        htpy-pointed-map B B
          ( comp-pointed-map B A B f g)
          ( id-pointed-map))

  retr-pointed-map : UU (l1 ⊔ l2)
  retr-pointed-map =
    Σ ( B →* A)
      ( λ g →
        htpy-pointed-map A A
          ( comp-pointed-map A B A g f)
          ( id-pointed-map))

  is-iso-pointed-map : UU (l1 ⊔ l2)
  is-iso-pointed-map = sec-pointed-map × retr-pointed-map

  is-equiv-pointed-map : UU (l1 ⊔ l2)
  is-equiv-pointed-map = is-equiv (map-pointed-map A B f)

  is-contr-sec-is-equiv-pointed-map :
    is-equiv-pointed-map → is-contr sec-pointed-map
  is-contr-sec-is-equiv-pointed-map H =
    is-contr-total-Eq-structure
      ( λ g p (G : (map-pointed-map A B f ∘ g) ~ id) →
          Id { A = Id { A = type-Pointed-Type B}
                      ( map-pointed-map A B f (g (pt-Pointed-Type B)))
                      ( pt-Pointed-Type B)}
             ( G (pt-Pointed-Type B))
             ( ( ( ap (map-pointed-map A B f) p) ∙
                 ( preserves-point-map-pointed-map A B f)) ∙
               ( refl)))
      ( is-contr-sec-is-equiv H)
      ( pair (map-inv-is-equiv H) (issec-map-inv-is-equiv H))
      ( is-contr-equiv
        ( fib
          ( ap (map-pointed-map A B f))
          ( ( issec-map-inv-is-equiv H (pt-Pointed-Type B)) ∙
            ( inv (preserves-point-map-pointed-map A B f))))
        ( equiv-tot
          ( λ p →
            ( ( equiv-con-inv
                ( ap (map-pointed-map A B f) p)
                ( preserves-point-map-pointed-map A B f)
                ( issec-map-inv-is-equiv H (pt-Pointed-Type B))) ∘e
              ( equiv-inv
                ( issec-map-inv-is-equiv H (pt-Pointed-Type B))
                ( ( ap (map-pointed-map A B f) p) ∙
                  ( preserves-point-map-pointed-map A B f)))) ∘e
            ( equiv-concat'
              ( issec-map-inv-is-equiv H (pt-Pointed-Type B))
              ( right-unit))))
        ( is-contr-map-is-equiv
          ( is-emb-is-equiv H
            ( map-inv-is-equiv H (pt-Pointed-Type B))
            ( pt-Pointed-Type A))
          ( ( issec-map-inv-is-equiv H (pt-Pointed-Type B)) ∙
            ( inv (preserves-point-map-pointed-map A B f)))))

  is-contr-retr-is-equiv-pointed-map :
    is-equiv-pointed-map → is-contr retr-pointed-map
  is-contr-retr-is-equiv-pointed-map H =
    is-contr-total-Eq-structure
      ( λ g p (G : (g ∘ map-pointed-map A B f) ~ id) →
        Id {A = Id { A = type-Pointed-Type A}
                   ( g (map-pointed-map A B f (pt-Pointed-Type A)))
                   ( pt-Pointed-Type A)}
           ( G (pt-Pointed-Type A))
           ( ( ( ap g (preserves-point-map-pointed-map A B f)) ∙
               ( p)) ∙
             ( refl)))
      ( is-contr-retr-is-equiv H)
      ( pair (map-inv-is-equiv H) (isretr-map-inv-is-equiv H))
      ( is-contr-equiv
        ( fib
          ( λ p →
            ( ( ap
                ( map-inv-is-equiv H)
                ( preserves-point-map-pointed-map A B f)) ∙
              ( p)) ∙
            ( refl))
          ( isretr-map-inv-is-equiv H (pt-Pointed-Type A)))
        ( equiv-tot (λ p → equiv-inv _ _))
        ( is-contr-map-is-equiv
          ( is-equiv-comp'
            ( λ q → q ∙ refl)
            ( λ p →
              ( ap
                ( map-inv-is-equiv H)
                ( preserves-point-map-pointed-map A B f)) ∙
              ( p))
            ( is-equiv-concat
              ( ap
                ( map-inv-is-equiv H)
                ( preserves-point-map-pointed-map A B f))
              ( pt-Pointed-Type A))
            ( is-equiv-concat'
              ( map-inv-is-equiv H (map-pointed-map A B f (pt-Pointed-Type A)))
              ( refl)))
          ( isretr-map-inv-is-equiv H (pt-Pointed-Type A))))

  is-contr-is-iso-is-equiv-pointed-map :
    is-equiv-pointed-map → is-contr is-iso-pointed-map
  is-contr-is-iso-is-equiv-pointed-map H =
    is-contr-prod
      ( is-contr-sec-is-equiv-pointed-map H)
      ( is-contr-retr-is-equiv-pointed-map H)

  is-iso-is-equiv-pointed-map :
    is-equiv-pointed-map → is-iso-pointed-map
  is-iso-is-equiv-pointed-map H =
    center (is-contr-is-iso-is-equiv-pointed-map H)

  is-equiv-is-iso-pointed-map :
    is-iso-pointed-map → is-equiv-pointed-map
  is-equiv-is-iso-pointed-map H =
    pair
      ( pair
        ( pr1 (pr1 (pr1 H)))
        ( pr1 (pr2 (pr1 H))))
      ( pair
        ( pr1 (pr1 (pr2 H)))
        ( pr1 (pr2 (pr2 H))))

  is-prop-is-iso-pointed-map : is-prop is-iso-pointed-map
  is-prop-is-iso-pointed-map =
    is-prop-is-proof-irrelevant
      ( λ H →
        is-contr-is-iso-is-equiv-pointed-map (is-equiv-is-iso-pointed-map H))

  equiv-is-iso-is-equiv-pointed-map : is-equiv-pointed-map ≃ is-iso-pointed-map
  equiv-is-iso-is-equiv-pointed-map =
    pair
      ( is-iso-is-equiv-pointed-map)
      ( is-equiv-is-prop
        ( is-property-is-equiv (map-pointed-map A B f))
        ( is-prop-is-iso-pointed-map)
        ( is-equiv-is-iso-pointed-map))

_≃*_ :
  {l1 l2 : Level} (A : Pointed-Type l1) (B : Pointed-Type l2) → UU (l1 ⊔ l2)
A ≃* B =
  Σ ( type-Pointed-Type A ≃ type-Pointed-Type B)
    ( λ e → Id (map-equiv e (pt-Pointed-Type A)) (pt-Pointed-Type B))

compute-pointed-equiv :
  {l1 l2 : Level} (A : Pointed-Type l1) (B : Pointed-Type l2) →
  (A ≃* B) ≃ Σ (A →* B) (is-equiv-pointed-map A B)
compute-pointed-equiv A B = equiv-right-swap-Σ

module _
  {l1 l2 : Level} (A : Pointed-Type l1) (B : Pointed-Type l2) (e : A ≃* B)
  where

  equiv-pointed-equiv : type-Pointed-Type A ≃ type-Pointed-Type B
  equiv-pointed-equiv = pr1 e

  map-equiv-pointed-equiv : type-Pointed-Type A → type-Pointed-Type B
  map-equiv-pointed-equiv = map-equiv equiv-pointed-equiv

  preserves-point-equiv-pointed-equiv :
    Id (map-equiv-pointed-equiv (pt-Pointed-Type A)) (pt-Pointed-Type B)
  preserves-point-equiv-pointed-equiv = pr2 e

  pointed-map-pointed-equiv : A →* B
  pointed-map-pointed-equiv =
    pair map-equiv-pointed-equiv preserves-point-equiv-pointed-equiv

-- We characterize the identity type of the universe of pointed types

module _
  {l1 : Level} (A : Pointed-Type l1)
  where
  
  extensionality-Pointed-Type : (B : Pointed-Type l1) → Id A B ≃ (A ≃* B)
  extensionality-Pointed-Type =
    extensionality-Σ
      ( λ b e → Id (map-equiv e (pt-Pointed-Type A)) b)
      ( id-equiv)
      ( refl)
      ( λ B → equiv-univalence)
      ( λ a → id-equiv)

  eq-pointed-equiv : (B : Pointed-Type l1) → A ≃* B → Id A B
  eq-pointed-equiv B = map-inv-equiv (extensionality-Pointed-Type B)

-- Precomposing by pointed equivalences

module _
  {l1 l2 : Level} (A : Pointed-Type l1) (B : Pointed-Type l2) (f : A →* B)
  where

  is-equiv-is-equiv-precomp-pointed-map :
    ( {l : Level} (C : Pointed-Type l) →
      is-equiv (precomp-pointed-map A B C f)) →
    is-equiv-pointed-map A B f
  is-equiv-is-equiv-precomp-pointed-map H =
    is-equiv-has-inverse
      ( map-pointed-map B A g)
      ( htpy-eq
        ( ap pr1
          ( ap pr1
            ( eq-is-contr
              ( is-contr-map-is-equiv (H B) f)
              { pair
                ( comp-pointed-map B A B f g)
                ( eq-htpy-pointed-map A B
                  ( comp-pointed-map A B B
                    ( comp-pointed-map B A B f g)
                    ( f))
                  ( f)
                  ( concat-htpy-pointed-map A B
                    ( comp-pointed-map A B B
                      ( comp-pointed-map B A B f g)
                      ( f))
                    ( comp-pointed-map A A B f
                      ( comp-pointed-map A B A g f))
                    ( f)
                    ( assoc-comp-pointed-map A B A B f g f)
                    ( concat-htpy-pointed-map A B
                      ( comp-pointed-map A A B f
                        ( comp-pointed-map A B A g f))
                      ( comp-pointed-map A A B f id-pointed-map)
                      ( f)
                      ( left-whisker-htpy-pointed-map A A B f
                        ( comp-pointed-map A B A g f)
                        ( id-pointed-map)
                        ( G))
                      ( right-unit-law-comp-pointed-map A B f))))}
              { pair
                ( id-pointed-map)
                ( eq-htpy-pointed-map A B
                  ( comp-pointed-map A B B id-pointed-map f)
                  ( f)
                  ( left-unit-law-comp-pointed-map A B f))}))))
      ( pr1 G)
    where
    g : B →* A
    g = pr1 (center (is-contr-map-is-equiv (H A) id-pointed-map))
    G : htpy-pointed-map A A (comp-pointed-map A B A g f) id-pointed-map
    G = map-equiv
          ( extensionality-pointed-map A A
            ( comp-pointed-map A B A g f)
              id-pointed-map)
        ( pr2 (center (is-contr-map-is-equiv (H A) id-pointed-map)))

  is-equiv-precomp-is-equiv-pointed-map :
    is-equiv-pointed-map A B f →
    {l : Level} → (C : Pointed-Type l) → is-equiv (precomp-pointed-map A B C f)
  is-equiv-precomp-is-equiv-pointed-map E C =
    pair
      ( pair
        ( precomp-pointed-map B A C h)
        ( λ k →
          eq-htpy-pointed-map A C
            ( comp-pointed-map A B C (comp-pointed-map B A C k h) f)
            ( k)
            ( concat-htpy-pointed-map A C
              ( comp-pointed-map A B C (comp-pointed-map B A C k h) f)
              ( comp-pointed-map A A C k (comp-pointed-map A B A h f))
              ( k)
              ( assoc-comp-pointed-map A B A C k h f)
              ( concat-htpy-pointed-map A C
                ( comp-pointed-map A A C k (comp-pointed-map A B A h f))
                ( comp-pointed-map A A C k id-pointed-map)
                ( k)
                ( left-whisker-htpy-pointed-map A A C k
                  ( comp-pointed-map A B A h f)
                  ( id-pointed-map)
                  ( H))
                ( right-unit-law-comp-pointed-map A C k)))))
      ( pair
        ( precomp-pointed-map B A C g)
        ( λ k →
          eq-htpy-pointed-map B C
            ( comp-pointed-map B A C (comp-pointed-map A B C k f) g)
            ( k)
            ( concat-htpy-pointed-map B C
              ( comp-pointed-map B A C (comp-pointed-map A B C k f) g)
              ( comp-pointed-map B B C k (comp-pointed-map B A B f g))
              ( k)
              ( assoc-comp-pointed-map B A B C k f g)
              ( concat-htpy-pointed-map B C
                ( comp-pointed-map B B C k (comp-pointed-map B A B f g))
                ( comp-pointed-map B B C k id-pointed-map)
                ( k)
                ( left-whisker-htpy-pointed-map B B C k
                  ( comp-pointed-map B A B f g)
                  ( id-pointed-map)
                  ( G))
                ( right-unit-law-comp-pointed-map B C k)))))
    where
    I : is-iso-pointed-map A B f
    I = is-iso-is-equiv-pointed-map A B f E
    g : B →* A
    g = pr1 (pr1 I)
    G : htpy-pointed-map B B (comp-pointed-map B A B f g) id-pointed-map
    G = pr2 (pr1 I)
    h : B →* A
    h = pr1 (pr2 I)
    H : htpy-pointed-map A A (comp-pointed-map A B A h f) id-pointed-map
    H = pr2 (pr2 I)

-- Postcomposing by pointed equivalences

module _
  {l1 l2 : Level} (A : Pointed-Type l1) (B : Pointed-Type l2) (f : A →* B)
  where

  is-equiv-is-equiv-comp-pointed-map :
    ({l : Level} (X : Pointed-Type l) → is-equiv (comp-pointed-map X A B f)) →
    is-equiv-pointed-map A B f
  is-equiv-is-equiv-comp-pointed-map H =
    is-equiv-has-inverse
      ( map-pointed-map B A g)
      ( pr1 G)
      ( htpy-eq
        ( ap pr1
          ( ap pr1
            ( eq-is-contr
              ( is-contr-map-is-equiv (H A) f)
                { pair
                  ( comp-pointed-map A B A g f)
                  ( eq-htpy-pointed-map A B
                    ( comp-pointed-map A A B f (comp-pointed-map A B A g f))
                    ( f)
                    ( concat-htpy-pointed-map A B
                      ( comp-pointed-map A A B f (comp-pointed-map A B A g f))
                      ( comp-pointed-map A B B (comp-pointed-map B A B f g) f)
                      ( f)
                      ( inv-assoc-comp-pointed-map A B A B f g f)
                      ( concat-htpy-pointed-map A B
                        ( comp-pointed-map A B B (comp-pointed-map B A B f g) f)
                        ( comp-pointed-map A B B id-pointed-map f)
                        ( f)
                        ( right-whisker-htpy-pointed-map A B B
                          ( comp-pointed-map B A B f g)
                          ( id-pointed-map)
                          ( G)
                          ( f))
                        ( left-unit-law-comp-pointed-map A B f))))}
                { pair
                  ( id-pointed-map)
                  ( eq-htpy-pointed-map A B
                    ( comp-pointed-map A A B f id-pointed-map)
                    ( f)
                    ( right-unit-law-comp-pointed-map A B f))}))))
    where
    g : B →* A
    g = pr1 (center (is-contr-map-is-equiv (H B) id-pointed-map))
    G : htpy-pointed-map B B (comp-pointed-map B A B f g) id-pointed-map
    G = map-equiv
          ( extensionality-pointed-map B B
            ( comp-pointed-map B A B f g)
              id-pointed-map)
        ( pr2 (center (is-contr-map-is-equiv (H B) id-pointed-map)))

  is-equiv-comp-is-equiv-pointed-map :
    is-equiv-pointed-map A B f →
    {l : Level} (X : Pointed-Type l) → is-equiv (comp-pointed-map X A B f)
  is-equiv-comp-is-equiv-pointed-map E X =
    pair
      ( pair
        ( comp-pointed-map X B A g)
        ( λ k →
          eq-htpy-pointed-map X B
            ( comp-pointed-map X A B f (comp-pointed-map X B A g k))
            ( k)
            ( concat-htpy-pointed-map X B
              ( comp-pointed-map X A B f (comp-pointed-map X B A g k))
              ( comp-pointed-map X B B (comp-pointed-map B A B f g) k)
              ( k)
              ( inv-assoc-comp-pointed-map X B A B f g k)
              ( concat-htpy-pointed-map X B
                ( comp-pointed-map X B B (comp-pointed-map B A B f g) k)
                ( comp-pointed-map X B B id-pointed-map k)
                ( k)
                ( right-whisker-htpy-pointed-map X B B
                  ( comp-pointed-map B A B f g)
                  ( id-pointed-map)
                  ( G)
                  ( k))
                ( left-unit-law-comp-pointed-map X B k)))))
      ( pair
        ( comp-pointed-map X B A h)
        ( λ k →
          eq-htpy-pointed-map X A
            ( comp-pointed-map X B A h (comp-pointed-map X A B f k))
            ( k)
            ( concat-htpy-pointed-map X A
              ( comp-pointed-map X B A h (comp-pointed-map X A B f k))
              ( comp-pointed-map X A A (comp-pointed-map A B A h f) k)
              ( k)
              ( inv-assoc-comp-pointed-map X A B A h f k)
              ( concat-htpy-pointed-map X A
                ( comp-pointed-map X A A (comp-pointed-map A B A h f) k)
                ( comp-pointed-map X A A id-pointed-map k)
                ( k)
                ( right-whisker-htpy-pointed-map X A A
                  ( comp-pointed-map A B A h f)
                  ( id-pointed-map)
                  ( H)
                  ( k))
                ( left-unit-law-comp-pointed-map X A k)))))
    where
    I : is-iso-pointed-map A B f
    I = is-iso-is-equiv-pointed-map A B f E
    g : B →* A
    g = pr1 (pr1 I)
    G : htpy-pointed-map B B (comp-pointed-map B A B f g) id-pointed-map
    G = pr2 (pr1 I)
    h : B →* A
    h = pr1 (pr2 I)
    H : htpy-pointed-map A A (comp-pointed-map A B A h f) id-pointed-map
    H = pr2 (pr2 I)
```
