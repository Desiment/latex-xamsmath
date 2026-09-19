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

## Delimiter Conventions

Prefer specialized delimiter commands when they exist:

- Use `\abs{...}` for absolute value or modulus when the algebra plugin is
  loaded. See `xamsmath-30-algebra`.
- Use `\set{...}` for set notation and set-builder notation when the
  foundations plugin is loaded. See `xamsmath-20-foundations`.
- Use probability plugin delimiters such as `\P(...)`, `\Law(...)`, `\E[...]`,
  and `\D[...]` for probability notation. See `xamsmath-60-probability`.
- Use upgraded standard operators directly, for example `\sin(...)`,
  `\log[...]`, and `\det{...}`.

Use `\mleft...\mright` when delimiters bound the argument of a function,
operator, or functional expression and no more specific command exists:

```latex
f\mleft(\frac{x}{2}\mright)
T\mleft[\sum_{i=1}^n x_i\mright]
\Phi\mleft(\int_0^1 f(x)\,\dd{x}\mright)
```

Use ordinary `\left...\right` when delimiters express arithmetic grouping or
structural grouping rather than a function/operator argument:

```latex
\left(\frac{a+b}{c+d}\right)^2
\left[\frac{j-1}{m},\frac jm\right)
```

The priority is: specialized command first, then `\mleft...\mright` for
function/operator arguments, then `\left...\right` for arithmetic or structural
grouping.

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
- Use `\mleft...\mright` for function/operator arguments when no specialized
  delimiter command or upgraded operator syntax applies.
- Use `\left...\right` for arithmetic grouping, structural grouping, and
  interval notation.

## Avoid

```latex
\sin\left(\frac{x}{2}\right)
\exp\left(-\frac{x^2}{2}\right)
f\left(\frac{x}{2}\right)
\left|\frac{a}{b}\right|
\{x \in \R \mid x > 0\}
```

Prefer:

```latex
\sin(\frac{x}{2})
\exp(-\frac{x^2}{2})
f\mleft(\frac{x}{2}\mright)
\abs{\frac{a}{b}}
\set{x \in \R | x > 0}
```
