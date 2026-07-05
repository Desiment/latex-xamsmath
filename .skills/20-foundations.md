# xamsmath: Foundations Plugin

## When To Use

Use the `foundations` plugin for logic, set theory, relations, mappings, and
topology notation.

## Required Setup

```latex
\usepackage[all]{xamsmath}
\XAMSMathLoadPlugin{foundations}
```

If using `\ind`, load the `fonts` option because it uses `\mathbx`.

## Logic Commands

- `\lor`: logical disjunction.
- `\land`: logical conjunction.
- `\lnot`: logical negation.
- `\limp`: implication arrow.
- `\liff`: equivalence arrow.
- `\nec`: modal necessity.
- `\poss`: modal possibility.

Examples:

```latex
p \land q
p \lor q
\lnot p
p \limp q
p \liff q
\nec p
\poss p
```

## Set Theory Commands

### `\set{<body>}`

Autosized set delimiters. Use one plain vertical bar for set-builder notation.

```latex
\set{1,2,3}
\set{x \in \R | x > 0}
\set[\Big]{x | x^2 > 1}
```

### Set operators and relation helpers

- `\card`: cardinality operator.
- `\powerset`: power-set operator.
- `\dom`: domain operator.
- `\cod`: codomain operator.
- `\ran`: range operator.
- `\field`: field of a relation.
- `\id`: identity map operator.
- `\ind`: indicator-function operator.
- `\symdiff`: symmetric difference binary operator.
- `\complement{<set>}`: complement by overline.

Examples:

```latex
\card(A)
\powerset(X)
\dom(f), \cod(f), \ran(f)
\field(R)
\id_X
\ind_A(x)
A \symdiff B
\complement{A}
```

## Mapping Commands

- `\injto`: injective mapping arrow.
- `\surto`: surjective mapping arrow.
- `\bijto`: bijective mapping arrow.

```latex
f: X \injto Y
g: X \surto Y
h: X \bijto Y
```

## Topology Commands

- `\Cl`: closure operator.
- `\Fr`: frontier or boundary operator.
- `\Int`: interior operator.
- `\Out`: exterior operator.
- `\Hom`: Hom-set or homology notation operator.
- `\Borel`: Borel sigma-algebra symbol.

```latex
\Cl(A)
\Fr(A)
\Int(A)
\Out(A)
\Hom(X,Y)
\Borel(X)
```

## Rules

- Use `\set{... | ...}` for set-builder notation; do not use a colon.
- Do not use `\middle|` inside `\set`.
- Use `\injto`, `\surto`, and `\bijto` in mapping type annotations.

## Avoid

```latex
\set{x \in \R : x > 0}
\set{x \in \R \middle| x > 0}
```

Prefer:

```latex
\set{x \in \R | x > 0}
```
