# Univalent mathematics in Agda

[![CI](https://github.com/UniMath/agda-unimath/actions/workflows/ci.yaml/badge.svg)](https://github.com/UniMath/agda-unimath/actions/workflows/ci.yaml) [![pages-build-deployment](https://github.com/UniMath/agda-unimath/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/UniMath/agda-unimath/actions/workflows/pages/pages-build-deployment)

This repository is for a formalisation project for univalent mathematics in Agda. Our goal is to formalize an extensive curriculum of mathematics from the univalent point of view. Furthermore, we think libraries of formalized mathematics could be useful, informative resources for mathematicians. The `agda-unimath` library is designed to work towards this goal. We warmly welcome any contributions. If you would like to contribute, please join the `#unimath` stream of the Agda community chat at

[![Agda on Zulip](https://img.shields.io/badge/zulip-join_chat-brightgreen.svg)](https://agda.zulipchat.com)

This library is based on the formalisation of the [Introduction to Homotopy Type Theory](https://github.com/HoTT-Intro/Agda) book by Egbert Rijke.

The library is built in Agda 2.6.2. It can be compiled by running `make check` from the main folder.

## Design of the library

### Structure of the library

1. The source code of the formalisation can be found in the folder `src`.
2. The library is organized by mathematical subject, with one folder per mathemtical subject. For each folder there is also an Agda file of the same name, which lists the files in that folder by importing them publicly.
3. The `agda-unimath` library has the goal to be an informative resource of formalised mathematics. We therefore formalise in literate agda, using markdown. We think of the files in the formalisation as pages of a wiki on mathematics.
4. The files focus sharply on one topic. Typically, a file begins by introducing one new concept, possibly in several equivalent ways, and develop the most basic properties thereof. Alternatively, a file could have the goal to prove an important theorem, and derive immediate corollaries thereof.

### Style conventions for files

1. File names are descriptive of the concept it introduces, or the main theorem it proves. The file names could be considered indexing terms, with the list of files functioning much like the index in the back of a book. Usually, file names consist of a noun or a noun phrase. File names should be natural, sufficiently precise, concise, and consistent with those of related files. 
2. File names are entirely in lower case, with words separated by hyphens. Words in file names should not be abbreviated unless the abbreviated term is a widely accepted mathematical term, e.g., `poset`.
3. Files that are part of the formalisation should be in literate agda using markdown. They should have the file extension `.lagda.md`.
4. Every file should begin with a markdown header of level `#`.
5. Immediately after the header there should be a block of agda code which loads the options, declares the present module, and performs all the imports. In particular, there should be no further imports later on in the file.
6. The rest of the files is devided into sections, subsections and possibly subsubsections. Each section should have a markdown header of level `##`, and the title of each header should be generic, such as `Idea`, `Definition`, `Example`, `Properties`, and so on. 
7. The subsections should have a markdown header of level `###` and they should concisely describe the content of the block of code that follows.

Ideally the first section of a file explains the idea, then proceeds to give the main definition that is the focus of the current file, then proceeds possibly with examples and by deriving basic properties of the defined concept. We suggest to follow the following template:

```md
# Title

[ options
  module declaration
  imports]

## Idea

( Informal description of the idea)

## Definition

[ formalization of the definition and immediately related structure]

## Examples

### X is an example

( informal explanation)

[ formalization that X is an example]

### Y is an example

( informal explanation)

[ formalization that Y is an example]

## Properties

### Concise descrition of property 1

( informal explanation)

[ formalization of property 1]

### Concise description of property 2

( informal explanation)

[ formalization of property 2]
```

### Library conventions

* This style guide is here to improve the readability of the code. If an item
  in this guide causes suboptimal readability of the code if applied, please
  notify us and we will try to improve this guide, and possibly our code.
* The library uses a standard line length of 80 characters.
* All module headers and standard term definitions should have a single empty line before and after them.
* The library uses Lisp style parentheses, and indent arguments of functions if they are on their own line.
* The library is universe polymorphic. Whenever a type or type family is assumed, it is assigned its own universe level.

#### Names

The naming convention in this library is such that the name of a construction closely matches the type of the construction. For example, the proof that the successor function on the integers is an equivalence has type `is-equiv succ-ℤ`. The name of the proof that the successor function on the integers is an equivalence is therefore `is-equiv-succ-ℤ`. Notice that most names are fully lowercase, and words are separated by hyphens. 

Names may also refer to types of the hypotheses used in the construction. Since the first objective of a name is to describe the type of the constructed term, the description of the hypotheses comes after the description of the conclusion in a name. For example, the term `is-equiv-is-contr-map` is a function of type `is-contr-map f → is-equiv f`, where `f` is a function already assumed. This convention has the advantage that if we have `H : is-contr-map f`, then the term `is-equiv-is-contr-map H` contains the description `is-contr-map` closest to the variable `H` of which it is a description.

Our naming conventions are not to ensure the shortest possible names, and neither to ensure the least amount of typing by the implementers of the library, but to display as accurately as possible what concepts are applied, and hence improve the readability.

* We do not use name space overloading. Unique names should be given to each construction.
* Names should describe in words the concept of its construction.
* As a rule of thumb, names should be entirely lower case, with words separated by hyphens.
* Names describe the object that is constructed first. For some theorems, the later part of a name contains descriptions of the hypotheses.
* Names never refer to variables.
* Important concepts can be capitalized. Usually, capitalized concepts form categories. Examples include `UU`, `Prop`, `Set`, `Semigroup`, `Monoid`, `Group`, `Preorder`, `Poset`, `Precat`, `Cat`, `Graph`, `Undirected-Graph`.
* The capitalized part of a name only appears at the end of the name.
* Unicode symbols are used sparingly, and only in accordance with established mathematical practice.
* Abbreviations are used sparingly, as they also impare the readability of the code.
* If a symbol is not available, the concept is described in words or abbreviated words. For example, the equality symbol = is not available to the user to assert an equality. Hence, we write Id x y to assert equality, referring to the identity type, and we do not use a new symbol.
* Readability of the code has a high priority. Therefore we try to aviod subtly different variations of the same symbol.

#### Indentation

* The contents of a top-level module should have zero indentation.
* Every subsequent nested scope should then be indented by an additional two spaces.
* If the variables of a module do not fit on a line, start the variable declarations on a new line, with an indentation of two spaces.
* If the name of a construction does not fit on a single line with its type declaration, then we start the type declaration on a new line, with an indentation of two additional spaces. If the type specification of a construction then still does not fit on a single line of 80 characters, we start new lines in the type declaration using the same indentation level.
* Function arrows at line breaks should always go at the end of the line rather than the beginning of the next line.

#### Modules

* As a rule of thumb, there should only be one named module per file.
* There should always be a single blank line after a module declaration.
* Using anonymous modules is encouraged to group constructions by topic, introducing the common arguments of those constructions as parameters.
* Otherwise, they should be spread out over multiple lines, each indented by two spaces. If they can be grouped logically by line, then it is fine to do so. Otherwise, a line each is probably clearest. The `where` keyword should be placed on an additional line of code at the end. For example:
  
  ```agda
  module Relation.Binary.Reasoning.Base.Single
    {a ℓ} {A : Set a} (_∼_ : Rel A ℓ)
    (refl : Reflexive _∼_) (trans : Transitive _∼_)
    where
  ```
  
#### Layout of `where` blocks

* `where` blocks are preferred rather than the `let` construction.
* `where` blocks should be indented by two spaces and their contents should be aligned with the `where`.
* The `where` keyword should be placed on the line below the main proof, indented by two spaces.
* Types should be provided for each of the terms, and all terms should be on lines after the `where`, e.g.
  ```agda
  statement : Statement
  statement = proof
    where
    proof : Proof
    proof = some-very-long-proof
  ```

#### Functions

* We do not align the arguments or the equality symbol in a function definition.
* If an argument is unused in a function definition, an underscore may be used.
* If a clause of a construction does not fit on the same line as the name and variable declaration, we start the definition on a new line with two spaces of additional indentation

#### Types

* Function arguments should be implicit if they can "almost always" be inferred within proofs. It is often harder for Agda to infer an argument in a type declaration, but we prioritize usage in proofs in our decision to make an argument implicit.
* If there are lots of implicit arguments that are common to a collection of proofs they should be extracted by using an anonymous module.
* The library doesn't use variables at the moment. All variables are declared either as parameters of an anonymous module or in the type declaration of a construction.

### Coding sample

#### Characterizing identity types

Identity types are characterized using `fundamental-theorem-id`, which can be found in `foundations.11-fundamental-theorem`. This theorem uses an implicit family `B` over a type `a`. The user must provide four arguments:

1. The base element `a:A`.
2. An element of type `B a`.
3. A proof that `Σ A B` is contractible.
4. A family of maps `(x : A) → Id a x → B x`.

The characterization of an identity type therefore revolves around the proof of contractibility of a total space. In order to give proofs of contractibility efficiently, the following theorems are often used:

1. `is-contr-equiv` and `is-contr-equiv'`. These are used to show that the asserted type is equivalent to a contractible type and therefore contractible. The `'` just switches the direction of the equivalence, so that it doesn't have to be manually inverted.
2. The structure identity principle `is-contr-total-Eq-structure`.
3. The substructure identity principle `is-contr-total-Eq-substructure`.
4. The identity principle for Π-types `is-contr-total-Eq-Π`.

A typical example is the characterization of the identity type of the type of equivalences:

```agda
  htpy-equiv : A ≃ B → A ≃ B → UU (l1 ⊔ l2)
  htpy-equiv e e' = (map-equiv e) ~ (map-equiv e')

  refl-htpy-equiv : (e : A ≃ B) → htpy-equiv e e
  refl-htpy-equiv e = refl-htpy

  htpy-eq-equiv : {e e' : A ≃ B} (p : Id e e') → htpy-equiv e e'
  htpy-eq-equiv {e = e} {.e} refl =
    refl-htpy-equiv e

  abstract
    is-contr-total-htpy-equiv :
      (e : A ≃ B) → is-contr (Σ (A ≃ B) (λ e' → htpy-equiv e e'))
    is-contr-total-htpy-equiv (pair f is-equiv-f) =
      is-contr-total-Eq-substructure
        ( is-contr-total-htpy f)
        ( is-subtype-is-equiv)
        ( f)
        ( refl-htpy)
        ( is-equiv-f)

  is-equiv-htpy-eq-equiv :
    (e e' : A ≃ B) → is-equiv (htpy-eq-equiv {e = e} {e'})
  is-equiv-htpy-eq-equiv e =
    fundamental-theorem-id e
      ( refl-htpy-equiv e)
      ( is-contr-total-htpy-equiv e)
      ( λ e' → htpy-eq-equiv {e = e} {e'})

  equiv-htpy-eq-equiv :
    (e e' : A ≃ B) → Id e e' ≃ (htpy-equiv e e')
  pr1 (equiv-htpy-eq-equiv e e') = htpy-eq-equiv
  pr2 (equiv-htpy-eq-equiv e e') = is-equiv-htpy-eq-equiv e e'

  eq-htpy-equiv : {e e' : A ≃ B} → ( htpy-equiv e e') → Id e e'
  eq-htpy-equiv {e = e} {e'} = map-inv-is-equiv (is-equiv-htpy-eq-equiv e e')
```
