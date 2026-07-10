---
name: xamsmath-40-calculus
description: Use the xamsmath calculus plugin for derivatives, integrals, differentials, and calculus notation.
license: MIT
compatibility: opencode
metadata:
  package: xamsmath
  topic: calculus
---

# xamsmath: Calculus Plugin

## When To Use

Use the `calculus` plugin for interval notation, differentials, derivative
fractions, and vector calculus operators.

## Required Setup

```latex
\usepackage[all]{xamsmath}
\XAMSMathLoadPlugin{calculus}
```

The plugin provides a fallback `\sfrac` if the `eqmicrotype` option did not load
`xfrac`.

## Common Calculus Commands

- `\interval{<left>}{<right>}`: angle-bracket interval with semicolon separator.
- `\sign`: signum operator.
- `\supp`: support operator.
- `\dif`: upright differential `d` with integral spacing.
- `\Dif`: uppercase differential operator.
- `\sfrac{<num>}{<den>}`: small fraction when available, regular fraction fallback otherwise.

```latex
\interval{a}{b}
\sign(x)
\supp(f)
\int_a^b f(x) \dif x
\Dif f
\sfrac{dy}{dx}
```

## Ordinary Derivatives

- `\od{<expr>}{<var>}`: ordinary derivative using `\frac`.
- `\lod{<expr>}{<var>}`: ordinary derivative using `\sfrac`.
- `\tod{<expr>}{<var>}`: ordinary derivative using `\tfrac`.
- `\dod{<expr>}{<var>}`: ordinary derivative using `\dfrac`.

These commands are PIE-aware: superscripts specify derivative order and
subscripts specify evaluation suffixes.

```latex
\od{y}{x}
\od^2{y}{x}
\od^2_{x=0}{y}{x}
\lod{y}{x}
\tod{y}{x}
\dod{y}{x}
```

### `\tmpl_derivative_frac`

Internal derivative template used to define `\od`, `\lod`, `\tod`, `\dod`,
`\pd`, `\lpd`, `\tpd`, and `\dpd`. Package authors should usually use the
public derivative commands rather than this template directly.

## Partial Derivatives

- `\pd{<expr>}{<var>}`: partial derivative using `\frac`.
- `\lpd{<expr>}{<var>}`: partial derivative using `\sfrac`.
- `\tpd{<expr>}{<var>}`: partial derivative using `\tfrac`.
- `\dpd{<expr>}{<var>}`: partial derivative using `\dfrac`.

```latex
\pd{u}{t}
\pd^2{u}{x \partial y}
\lpd{u}{t}
\tpd{u}{t}
\dpd{u}{t}
```

## Vector Calculus Operators

- `\grad`: gradient operator.
- `\rot`: rotation or curl operator.
- `\div`: divergence operator. This replaces TeX's division-symbol command.

```latex
\grad f
\grad(f)
\rot \vec{F}
\div \vec{F}
```

## Rules

- Use `\dif` in integrals: `\int f(x) \dif x`.
- Put derivative orders and evaluation suffixes before derivative arguments: `\od^2_{x=0}{y}{x}`.
- Do not place primes before derivative commands; the implementation rejects primes.
- Use `\pd^2{u}{x \partial y}` for mixed partials.

## Avoid

```latex
\frac{dy}{dx}
\od{y}{x}^2
\od'{y}{x}
```

Prefer:

```latex
\od{y}{x}
\od^2{y}{x}
```
