# Contractible types

```agda
{-# OPTIONS --without-K --exact-split #-}

module foundation-core.contractible-types where

open import foundation-core.cartesian-product-types using (_×_)
open import foundation-core.dependent-pair-types using (Σ; pair; pr1; pr2)
open import foundation-core.equality-cartesian-product-types using (eq-pair)
open import foundation-core.equality-dependent-pair-types using (eq-pair-Σ)
open import foundation-core.equivalences using
  ( is-equiv; map-inv-is-equiv; isretr-map-inv-is-equiv; _≃_;
    is-equiv-map-inv-is-equiv; is-equiv-has-inverse)
open import foundation-core.identity-types using
  ( Id; refl; inv; _∙_; left-inv; ap; eq-transpose-tr)
open import foundation-core.retractions using (_retract-of_)
open import foundation-core.universe-levels using (Level; UU)
```

## Idea

Contractible types are types that have, up to identification, exactly one element.

## Definition

```agda
is-contr :
  {l : Level} → UU l → UU l
is-contr A = Σ A (λ a → (x : A) → Id a x)

abstract
  center :
    {l : Level} {A : UU l} → is-contr A → A
  center (pair c is-contr-A) = c
  
eq-is-contr' :
  {l : Level} {A : UU l} → is-contr A → (x y : A) → Id x y
eq-is-contr' (pair c C) x y = (inv (C x)) ∙ (C y)

eq-is-contr :
  {l : Level} {A : UU l} → is-contr A → {x y : A} → Id x y
eq-is-contr C {x} {y} = eq-is-contr' C x y

abstract
  contraction :
    {l : Level} {A : UU l} (is-contr-A : is-contr A) →
    (x : A) → Id (center is-contr-A) x
  contraction C x = eq-is-contr C
  
  coh-contraction :
    {l : Level} {A : UU l} (is-contr-A : is-contr A) →
    Id (contraction is-contr-A (center is-contr-A)) refl
  coh-contraction (pair c C) = left-inv (C c)
```

## Examples

### The total space of the identity type based at a point is contractible

We prove two cases of this fact: the first keeping the left-hand side fixed, and the second keeping the right-hand side fixed.

```agda
module _
  {l : Level} {A : UU l}
  where

  abstract
    is-contr-total-path : (a : A) → is-contr (Σ A (λ x → Id a x))
    pr1 (pr1 (is-contr-total-path a)) = a
    pr2 (pr1 (is-contr-total-path a)) = refl
    pr2 (is-contr-total-path a) (pair .a refl) = refl

  abstract
    is-contr-total-path' : (a : A) → is-contr (Σ A (λ x → Id x a))
    pr1 (pr1 (is-contr-total-path' a)) = a
    pr2 (pr1 (is-contr-total-path' a)) = refl
    pr2 (is-contr-total-path' a) (pair .a refl) = refl
```

## Properties

### Retracts of contractible types are contractible

```agda
module _
  {l1 l2 : Level} {A : UU l1} (B : UU l2)
  where

  abstract
    is-contr-retract-of : A retract-of B → is-contr B → is-contr A
    pr1 (is-contr-retract-of (pair i (pair r isretr)) H) = r (center H)
    pr2 (is-contr-retract-of (pair i (pair r isretr)) H) x =
      ap r (contraction H (i x)) ∙ (isretr x)
```

### Contractible types are closed under equivalences

```agda
module _
  {l1 l2 : Level} {A : UU l1} (B : UU l2)
  where
  
  abstract
    is-contr-is-equiv :
      (f : A → B) → is-equiv f → is-contr B → is-contr A
    pr1 (is-contr-is-equiv f H (pair b K)) = map-inv-is-equiv H b
    pr2 (is-contr-is-equiv f H (pair b K)) x =
      ( ap (map-inv-is-equiv H) (K (f x))) ∙
      ( isretr-map-inv-is-equiv H x)
    
  abstract
    is-contr-equiv : (e : A ≃ B) → is-contr B → is-contr A
    is-contr-equiv (pair e is-equiv-e) is-contr-B =
      is-contr-is-equiv e is-equiv-e is-contr-B

module _
  {l1 l2 : Level} (A : UU l1) {B : UU l2}
  where

  abstract
    is-contr-is-equiv' :
      (f : A → B) → is-equiv f → is-contr A → is-contr B
    is-contr-is-equiv' f is-equiv-f is-contr-A =
      is-contr-is-equiv A
        ( map-inv-is-equiv is-equiv-f)
        ( is-equiv-map-inv-is-equiv is-equiv-f)
        ( is-contr-A)

  abstract
    is-contr-equiv' : (e : A ≃ B) → is-contr A → is-contr B
    is-contr-equiv' (pair e is-equiv-e) is-contr-A =
      is-contr-is-equiv' e is-equiv-e is-contr-A

module _
  {l1 l2 : Level} {A : UU l1} {B : UU l2}
  where

  abstract
    is-equiv-is-contr :
      (f : A → B) → is-contr A → is-contr B → is-equiv f
    is-equiv-is-contr f is-contr-A is-contr-B =
      is-equiv-has-inverse
        ( λ y → center is-contr-A)
        ( λ y → eq-is-contr is-contr-B)
        ( contraction is-contr-A)

  equiv-is-contr : is-contr A → is-contr B → A ≃ B
  pr1 (equiv-is-contr is-contr-A is-contr-B) a = center is-contr-B
  pr2 (equiv-is-contr is-contr-A is-contr-B) =
    is-equiv-is-contr _ is-contr-A is-contr-B
```

### Contractibility of cartesian product types

Given two types `A` and `B`, the following are equivalent:
1. The type `A × B` is contractible.
2. Both `A` and `B` are contractible.

```agda
module _
  {l1 l2 : Level} (A : UU l1) (B : UU l2)
  where

  abstract
    is-contr-left-factor-prod : is-contr (A × B) → is-contr A
    is-contr-left-factor-prod is-contr-AB =
      is-contr-retract-of
        ( A × B)
        ( pair
          ( λ x → pair x (pr2 (center is-contr-AB)))
          ( pair pr1 (λ x → refl)))
        ( is-contr-AB)

module _
  {l1 l2 : Level} (A : UU l1) (B : UU l2)
  where

  abstract
    is-contr-right-factor-prod : is-contr (A × B) → is-contr B
    is-contr-right-factor-prod is-contr-AB =
      is-contr-retract-of
        ( A × B)
        ( pair
          ( pair (pr1 (center is-contr-AB)))
          ( pair pr2 (λ x → refl))           )
        ( is-contr-AB)

module _
  {l1 l2 : Level} {A : UU l1} {B : UU l2}
  where
  
  abstract
    is-contr-prod : is-contr A → is-contr B → is-contr (A × B)
    pr1 (pr1 (is-contr-prod (pair a C) (pair b D))) = a
    pr2 (pr1 (is-contr-prod (pair a C) (pair b D))) = b
    pr2 (is-contr-prod (pair a C) (pair b D)) (pair x y) = eq-pair (C x) (D y)
```

### Contractibility of Σ-types

```agda
module _
  {l1 l2 : Level} {A : UU l1} {B : A → UU l2}
  where

  abstract
    is-contr-Σ' :
      is-contr A → ((x : A) → is-contr (B x)) → is-contr (Σ A B)
    pr1 (pr1 (is-contr-Σ' (pair a H) is-contr-B)) = a
    pr2 (pr1 (is-contr-Σ' (pair a H) is-contr-B)) = center (is-contr-B a)
    pr2 (is-contr-Σ' (pair a H) is-contr-B) (pair x y) =
      eq-pair-Σ
        ( inv (inv (H x)))
        ( eq-transpose-tr (inv (H x)) (eq-is-contr (is-contr-B a)))

  abstract
    is-contr-Σ :
      (C : is-contr A) (a : A) → is-contr (B a) → is-contr (Σ A B)
    pr1 (pr1 (is-contr-Σ H a K)) = a
    pr2 (pr1 (is-contr-Σ H a K)) = center K
    pr2 (is-contr-Σ H a K) (pair x y) =
      eq-pair-Σ
        ( inv (eq-is-contr H))
        ( eq-transpose-tr (eq-is-contr H) (eq-is-contr K))
```

### Contractible types are propositions

```agda
is-prop-is-contr :
  {l : Level} {A : UU l} → is-contr A → (x y : A) → is-contr (Id x y)
pr1 (is-prop-is-contr H x y) = eq-is-contr H
pr2 (is-prop-is-contr H x .x) refl = left-inv (pr2 H x)
```
