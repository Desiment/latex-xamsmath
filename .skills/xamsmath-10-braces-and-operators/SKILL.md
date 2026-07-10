---
name: xamsmath-10-braces-and-operators
description: Use xamsmath braces, autosized operators, math fonts, and compact math microtype helpers.
license: MIT
compatibility: opencode
metadata:
  package: xamsmath
  topic: braces-and-operators
---

# xamsmath: Braces, Operators, Fonts, And Microtype

## When To Use

Use this skill when writing documents with `xamsmath` option modules rather than
plugin commands. These commands come from `fonts`, `operators`, `braces`, and
`eqmicrotype`.

## Required Setup

```latex
\usepackage[fonts,operators,braces,eqmicrotype]{xamsmath}
```

or:

```latex
\usepackage[all]{xamsmath}
```

## Fonts Option

### `\mathbx{<symbol>}`

Typesets content with the Boondox double-struck math alphabet.

```latex
\mathbx{1}_A
```

## Operators Option

### `\Proj`

Projection operator.

```latex
\Proj(x)
```

### `\argmax`, `\argmin`

Limit-style optimization operators.

```latex
\argmax_{x \in X} f(x)
\argmin_{x \in X} f(x)
```

### `\loc`, `\const`

Upright local qualifier and generic constant marker.

```latex
L^2_\loc
C = \const
```

## Braces Option

The `braces` option upgrades `\DeclareBracedMathOperator` and many standard
operators so they can accept autosized operands in `[]`, `()`, or `{}`.

Upgraded non-limit operators:

- `\arcsin`, `\arctan`, `\cos`, `\cosh`, `\cot`, `\coth`, `\csc`, `\sec`, `\sin`, `\sinh`, `\tan`, `\tanh`
- `\exp`, `\log`, `\ln`, `\lg`
- `\arg`, `\deg`, `\det`, `\dim`, `\gcd`, `\lcm`, `\ker`, `\im`, `\hom`

Upgraded limit-style operators:

- `\inf`, `\sup`, `\max`, `\min`, `\lin`
- `\injlim`, `\projlim`, `\liminf`, `\limsup`, `\varliminf`, `\varlimsup`, `\varinjlim`, `\varprojlim`

Examples:

```latex
\sin(\frac{x}{2})
\log[\sum_{n=1}^N a_n]
\det{A^{-1}BA}
\limsup_{n \to \infty}(a_n)
\varprojlim{X_i}
```

### `\leftoperatorbrace`, `\rightoperatorbrace`, `\leftoperatorbracket`, `\rightoperatorbracket`

Low-level operator delimiter commands used internally by the braced-operator
implementation. Ordinary documents should normally use upgraded operators
directly.

### `\swapifbranches{<conditional>}{<true branch>}{<false branch>}`

Internal patch helper used to invert `mathtools` paired-delimiter star behavior.
It is exposed by the module but should not be used in ordinary documents.

### `\tmpl_braced_math_operator`

Internal template used by `\DeclareBracedMathOperator` when the `braces` option
is active. Package authors should usually call `\DeclareBracedMathOperator`
instead of instantiating this template directly.

## Eqmicrotype Option

### `\cramped{<math>}`

Typesets math material in a cramped style while preserving the current style
level.

```latex
\cramped{\sum_{i=1}^n x_i}
```

### `\medminus`, `\medplus`

Reduced-size plus and minus operators.

```latex
a \medminus b
a \medplus b
```

### `\pinfty`, `\ninfty`

Compact positive and negative infinity markers.

```latex
x \to \pinfty
x \to \ninfty
```

### `\changemathstyle{<0..7>}`

Low-level style selector used by `\cramped`. Prefer `\cramped` in documents.

## Rules

- With `braces`, do not wrap standard operators in manual `\left...\right` just to size their immediate argument.
- Use ordinary function notation for simple arguments, for example `\sin(x)`.
- Use `\DeclareBracedMathOperator*` for custom limit-style operators.

## Avoid

```latex
\sin\left(\frac{x}{2}\right)
\exp\left(-\frac{x^2}{2}\right)
```

Prefer:

```latex
\sin(\frac{x}{2})
\exp(-\frac{x^2}{2})
```
