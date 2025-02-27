---
title: Formalisation of the Symmetry Book
---

```agda
{-# OPTIONS --without-K --exact-split --allow-unsolved-metas #-}

module order-theory.preorders where

open import univalent-foundations public
```

## Preorders

```agda
Preorder : (l1 l2 : Level) → UU (lsuc l1 ⊔ lsuc l2)
Preorder l1 l2 =
  Σ ( UU l1)
    ( λ X →
      Σ ( X → X → UU-Prop l2)
        ( λ R →
          ( (x : X) → type-Prop (R x x)) ×
          ( (x y z : X) →
            type-Prop (R y z) → type-Prop (R x y) → type-Prop (R x z))))

module _
  {l1 l2 : Level} (X : Preorder l1 l2)
  where

  element-Preorder : UU l1
  element-Preorder = pr1 X

  leq-preorder-Prop : (x y : element-Preorder) → UU-Prop l2
  leq-preorder-Prop = pr1 (pr2 X)

  leq-Preorder : (x y : element-Preorder) → UU l2
  leq-Preorder x y = type-Prop (leq-preorder-Prop x y)

  is-prop-leq-Preorder : (x y : element-Preorder) → is-prop (leq-Preorder x y)
  is-prop-leq-Preorder x y = is-prop-type-Prop (leq-preorder-Prop x y)

  refl-leq-Preorder : (x : element-Preorder) → leq-Preorder x x
  refl-leq-Preorder = pr1 (pr2 (pr2 X))

  transitive-leq-Preorder :
    (x y z : element-Preorder) →
    leq-Preorder y z → leq-Preorder x y → leq-Preorder x z
  transitive-leq-Preorder = pr2 (pr2 (pr2 X))

  incident-preorder-Prop : (x y : element-Preorder) → UU-Prop l2
  incident-preorder-Prop x y =
    disj-Prop (leq-preorder-Prop x y) (leq-preorder-Prop y x)

  incident-Preorder : (x y : element-Preorder) → UU l2
  incident-Preorder x y = type-Prop (incident-preorder-Prop x y)

  is-prop-incident-Preorder :
    (x y : element-Preorder) → is-prop (incident-Preorder x y)
  is-prop-incident-Preorder x y = is-prop-type-Prop (incident-preorder-Prop x y)

  is-total-preorder-Prop : UU-Prop (l1 ⊔ l2)
  is-total-preorder-Prop =
    Π-Prop element-Preorder
      ( λ x → Π-Prop element-Preorder (λ y → incident-preorder-Prop x y))

  is-total-Preorder : UU (l1 ⊔ l2)
  is-total-Preorder = type-Prop is-total-preorder-Prop

  is-prop-is-total-Preorder : is-prop is-total-Preorder
  is-prop-is-total-Preorder = is-prop-type-Prop is-total-preorder-Prop
```

### Least and largest elements in preorders

```
module _
  {l1 l2 : Level} (X : Preorder l1 l2)
  where

  is-least-element-preorder-Prop : element-Preorder X → UU-Prop (l1 ⊔ l2)
  is-least-element-preorder-Prop x =
    Π-Prop (element-Preorder X) (leq-preorder-Prop X x)

  is-least-element-Preorder : element-Preorder X → UU (l1 ⊔ l2)
  is-least-element-Preorder x = type-Prop (is-least-element-preorder-Prop x)

  is-prop-is-least-element-Preorder :
    (x : element-Preorder X) → is-prop (is-least-element-Preorder x)
  is-prop-is-least-element-Preorder x =
    is-prop-type-Prop (is-least-element-preorder-Prop x)

  least-element-Preorder : UU (l1 ⊔ l2)
  least-element-Preorder = Σ (element-Preorder X) is-least-element-Preorder

  is-largest-element-preorder-Prop : element-Preorder X → UU-Prop (l1 ⊔ l2)
  is-largest-element-preorder-Prop x =
    Π-Prop (element-Preorder X) (λ y → leq-preorder-Prop X y x)

  is-largest-element-Preorder : element-Preorder X → UU (l1 ⊔ l2)
  is-largest-element-Preorder x = type-Prop (is-largest-element-preorder-Prop x)

  is-prop-is-largest-element-Preorder :
    (x : element-Preorder X) → is-prop (is-largest-element-Preorder x)
  is-prop-is-largest-element-Preorder x =
    is-prop-type-Prop (is-largest-element-preorder-Prop x)

  largest-element-Preorder : UU (l1 ⊔ l2)
  largest-element-Preorder = Σ (element-Preorder X) is-largest-element-Preorder
```

### Sub-preorders

```agda

module _
  {l1 l2 l3 : Level} (X : Preorder l1 l2) (S : element-Preorder X → UU-Prop l3)
  where

  element-sub-Preorder : UU (l1 ⊔ l3)
  element-sub-Preorder = type-subtype S

  eq-element-sub-Preorder :
    (x y : element-sub-Preorder) → Id (pr1 x) (pr1 y) → Id x y
  eq-element-sub-Preorder x y = eq-subtype S

  leq-sub-preorder-Prop : (x y : element-sub-Preorder) → UU-Prop l2
  leq-sub-preorder-Prop x y = leq-preorder-Prop X (pr1 x) (pr1 y)

  leq-sub-Preorder : (x y : element-sub-Preorder) → UU l2
  leq-sub-Preorder x y = type-Prop (leq-sub-preorder-Prop x y)

  is-prop-leq-sub-Preorder :
    (x y : element-sub-Preorder) → is-prop (leq-sub-Preorder x y)
  is-prop-leq-sub-Preorder x y =
    is-prop-type-Prop (leq-sub-preorder-Prop x y)

  refl-leq-sub-Preorder : (x : element-sub-Preorder) → leq-sub-Preorder x x
  refl-leq-sub-Preorder x = refl-leq-Preorder X (pr1 x)

  transitive-leq-sub-Preorder :
    (x y z : element-sub-Preorder) →
    leq-sub-Preorder y z → leq-sub-Preorder x y → leq-sub-Preorder x z
  transitive-leq-sub-Preorder x y z =
    transitive-leq-Preorder X (pr1 x) (pr1 y) (pr1 z)

  sub-Preorder : Preorder (l1 ⊔ l3) l2
  pr1 sub-Preorder = element-sub-Preorder
  pr1 (pr2 sub-Preorder) = leq-sub-preorder-Prop
  pr1 (pr2 (pr2 sub-Preorder)) = refl-leq-sub-Preorder
  pr2 (pr2 (pr2 sub-Preorder)) = transitive-leq-sub-Preorder
```

### Decidable sub-preorders

```agda

module _
  {l1 l2 l3 : Level} (X : Preorder l1 l2)
  (S : element-Preorder X → decidable-Prop l3)
  where

  element-decidable-sub-Preorder : UU (l1 ⊔ l3)
  element-decidable-sub-Preorder =
    element-sub-Preorder X (subtype-decidable-subtype S)

  eq-element-decidable-sub-Preorder :
    (x y : element-decidable-sub-Preorder) → Id (pr1 x) (pr1 y) → Id x y
  eq-element-decidable-sub-Preorder =
    eq-element-sub-Preorder X (subtype-decidable-subtype S)

  leq-decidable-sub-preorder-Prop :
    (x y : element-decidable-sub-Preorder) → UU-Prop l2
  leq-decidable-sub-preorder-Prop =
    leq-sub-preorder-Prop X (subtype-decidable-subtype S)

  leq-decidable-sub-Preorder : (x y : element-decidable-sub-Preorder) → UU l2
  leq-decidable-sub-Preorder =
    leq-sub-Preorder X (subtype-decidable-subtype S)

  is-prop-leq-decidable-sub-Preorder :
    (x y : element-decidable-sub-Preorder) →
    is-prop (leq-decidable-sub-Preorder x y)
  is-prop-leq-decidable-sub-Preorder =
    is-prop-leq-sub-Preorder X (subtype-decidable-subtype S)

  refl-leq-decidable-sub-Preorder :
    (x : element-decidable-sub-Preorder) → leq-decidable-sub-Preorder x x
  refl-leq-decidable-sub-Preorder =
    refl-leq-sub-Preorder X (subtype-decidable-subtype S)

  transitive-leq-decidable-sub-Preorder :
    (x y z : element-decidable-sub-Preorder) →
    leq-decidable-sub-Preorder y z → leq-decidable-sub-Preorder x y →
    leq-decidable-sub-Preorder x z
  transitive-leq-decidable-sub-Preorder =
    transitive-leq-sub-Preorder X (subtype-decidable-subtype S)

  decidable-sub-Preorder : Preorder (l1 ⊔ l3) l2
  decidable-sub-Preorder = sub-Preorder X (subtype-decidable-subtype S)
```

### Inclusion of sub-preorders

```agda
module _
  {l1 l2 : Level} (X : Preorder l1 l2)
  where

  module _
    {l3 l4 : Level} (S : element-Preorder X → UU-Prop l3)
    (T : element-Preorder X → UU-Prop l4)
    where
    
    inclusion-sub-preorder-Prop : UU-Prop (l1 ⊔ l3 ⊔ l4)
    inclusion-sub-preorder-Prop =
      Π-Prop (element-Preorder X) (λ x → hom-Prop (S x) (T x))

    inclusion-sub-Preorder : UU (l1 ⊔ l3 ⊔ l4)
    inclusion-sub-Preorder = type-Prop inclusion-sub-preorder-Prop

    is-prop-inclusion-sub-Preorder : is-prop inclusion-sub-Preorder
    is-prop-inclusion-sub-Preorder =
      is-prop-type-Prop inclusion-sub-preorder-Prop

  refl-inclusion-sub-Preorder :
    {l3 : Level} (S : element-Preorder X → UU-Prop l3) →
    inclusion-sub-Preorder S S
  refl-inclusion-sub-Preorder S x = id

  transitive-inclusion-sub-Preorder :
    {l3 l4 l5 : Level} (S : element-Preorder X → UU-Prop l3)
    (T : element-Preorder X → UU-Prop l4)
    (U : element-Preorder X → UU-Prop l5) →
    inclusion-sub-Preorder T U → inclusion-sub-Preorder S T →
    inclusion-sub-Preorder S U
  transitive-inclusion-sub-Preorder S T U g f x = (g x) ∘ (f x)

  Sub-Preorder : (l : Level) → Preorder (l1 ⊔ lsuc l) (l1 ⊔ l)
  pr1 (Sub-Preorder l) = element-Preorder X → UU-Prop l
  pr1 (pr2 (Sub-Preorder l)) = inclusion-sub-preorder-Prop
  pr1 (pr2 (pr2 (Sub-Preorder l))) = refl-inclusion-sub-Preorder
  pr2 (pr2 (pr2 (Sub-Preorder l))) = transitive-inclusion-sub-Preorder

```

### Chains in preorders

```agda
module _
  {l1 l2 : Level} (X : Preorder l1 l2)
  where

  is-chain-sub-preorder-Prop :
    {l3 : Level} (S : element-Preorder X → UU-Prop l3) → UU-Prop (l1 ⊔ l2 ⊔ l3)
  is-chain-sub-preorder-Prop S = is-total-preorder-Prop (sub-Preorder X S)

  is-chain-sub-Preorder :
    {l3 : Level} (S : element-Preorder X → UU-Prop l3) → UU (l1 ⊔ l2 ⊔ l3)
  is-chain-sub-Preorder S = type-Prop (is-chain-sub-preorder-Prop S)

  is-prop-is-chain-sub-Preorder :
    {l3 : Level} (S : element-Preorder X → UU-Prop l3) →
    is-prop (is-chain-sub-Preorder S)
  is-prop-is-chain-sub-Preorder S =
    is-prop-type-Prop (is-chain-sub-preorder-Prop S)

chain-Preorder :
  {l1 l2 : Level} (l : Level) (X : Preorder l1 l2) → UU (l1 ⊔ l2 ⊔ lsuc l)
chain-Preorder l X =
  Σ (element-Preorder X → UU-Prop l) (is-chain-sub-Preorder X)

module _
  {l1 l2 l3 : Level} (X : Preorder l1 l2) (C : chain-Preorder l3 X)
  where

  sub-preorder-chain-Preorder : element-Preorder X → UU-Prop l3
  sub-preorder-chain-Preorder = pr1 C

  element-chain-Preorder : UU (l1 ⊔ l3)
  element-chain-Preorder = type-subtype sub-preorder-chain-Preorder

module _
  {l1 l2 : Level} (X : Preorder l1 l2)
  where
  
  inclusion-chain-preorder-Prop :
    {l3 l4 : Level} → chain-Preorder l3 X → chain-Preorder l4 X →
    UU-Prop (l1 ⊔ l3 ⊔ l4)
  inclusion-chain-preorder-Prop C D =
    inclusion-sub-preorder-Prop X
      ( sub-preorder-chain-Preorder X C)
      ( sub-preorder-chain-Preorder X D)

  inclusion-chain-Preorder :
    {l3 l4 : Level} → chain-Preorder l3 X → chain-Preorder l4 X →
    UU (l1 ⊔ l3 ⊔ l4)
  inclusion-chain-Preorder C D = type-Prop (inclusion-chain-preorder-Prop C D)

  is-prop-inclusion-chain-Preorder :
    {l3 l4 : Level} (C : chain-Preorder l3 X) (D : chain-Preorder l4 X) →
    is-prop (inclusion-chain-Preorder C D)
  is-prop-inclusion-chain-Preorder C D =
    is-prop-type-Prop (inclusion-chain-preorder-Prop C D)
```

### Maximal chains in preorders

```agda

module _
  {l1 l2 : Level} (X : Preorder l1 l2)
  where
  
  is-maximal-chain-preorder-Prop :
    {l3 : Level} → chain-Preorder l3 X → UU-Prop (l1 ⊔ l2 ⊔ lsuc l3)
  is-maximal-chain-preorder-Prop {l3} C =
    Π-Prop (chain-Preorder l3 X) (inclusion-chain-preorder-Prop X C)

  is-maximal-chain-Preorder :
    {l3 : Level} → chain-Preorder l3 X → UU (l1 ⊔ l2 ⊔ lsuc l3)
  is-maximal-chain-Preorder C = type-Prop (is-maximal-chain-preorder-Prop C)

  is-prop-is-maximal-chain-Preorder :
    {l3 : Level} (C : chain-Preorder l3 X) →
    is-prop (is-maximal-chain-Preorder C)
  is-prop-is-maximal-chain-Preorder C =
    is-prop-type-Prop (is-maximal-chain-preorder-Prop C)

maximal-chain-Preorder :
  {l1 l2 : Level} (l3 : Level) (X : Preorder l1 l2) → UU (l1 ⊔ l2 ⊔ lsuc l3)
maximal-chain-Preorder l3 X =
  Σ (chain-Preorder l3 X) (is-maximal-chain-Preorder X)

module _
  {l1 l2 l3 : Level} (X : Preorder l1 l2) (C : maximal-chain-Preorder l3 X)
  where

  chain-maximal-chain-Preorder : chain-Preorder l3 X
  chain-maximal-chain-Preorder = pr1 C

  is-maximal-chain-maximal-chain-Preorder :
    is-maximal-chain-Preorder X chain-maximal-chain-Preorder
  is-maximal-chain-maximal-chain-Preorder = pr2 C

  element-maximal-chain-Preorder : UU (l1 ⊔ l3)
  element-maximal-chain-Preorder =
    element-chain-Preorder X chain-maximal-chain-Preorder
```
