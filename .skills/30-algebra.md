# xamsmath: Algebra Plugin

## When To Use

Use the `algebra` plugin for complex numbers, number systems, linear algebra,
vector notation, matrix operators, floors/ceilings, and divisibility notation.

## Required Setup

```latex
\usepackage[all]{xamsmath}
\XAMSMathLoadPlugin{algebra}
```

## Complex Number Commands

- `\conj{<expr>}`: complex conjugate by overline.
- `\Re`: real-part operator.
- `\Im`: imaginary-part operator.
- `\abs{<expr>}`: absolute value or modulus delimiter.

```latex
\conj{z}
\Re(z)
\Im(z)
\abs{z}
\abs{\frac{a}{b}}
```

## Number System Commands

- `\N`: natural numbers.
- `\Z`: integers.
- `\Q`: rational numbers.
- `\R`: real numbers.
- `\C`: complex numbers.
- `\H`: quaternions.
- `\bbstruct{<letter>}`: low-level helper that renders a blackboard-bold structure letter. Prefer the predefined number-system commands in documents.

```latex
n \in \N
z \in \Z
q \in \Q
x \in \R
z \in \C
h \in \H
\bbstruct{K}
```

## Linear Algebra Delimiters

- `\norm{<expr>}`: norm delimiter. Empty argument prints a centered placeholder dot.
- `\spr{<left>}{<right>}`: scalar product delimiter.
- `\cpr{<left>}{<right>}`: bracketed product delimiter.

```latex
\norm{v}
\norm{}
\spr{u}{v}
\spr{}{}
\cpr{u}{v}
\cpr{}{}
```

## Vector Commands

The plugin renews `\vec` to use `esvect` arrows and generates vector shorthand
commands.

Generated shorthands:

- `\va`, `\vb`, `\vc`, `\vd`, `\ve`, `\vf`, `\vg`, `\vh`
- `\vk`, `\vl`, `\vm`, `\vn`, `\vo`, `\vp`, `\vq`, `\vr`, `\vs`, `\vt`, `\vu`, `\vv`, `\vw`, `\vx`, `\vy`, `\vz`
- `\vi`: vector dotless i.
- `\vj`: vector dotless j.

Examples:

```latex
\vec{x}
\va + \vb
\vi + \vj + \vk
```

## Matrix Operators

- `\tr`: trace.
- `\rk`: rank.
- `\perm`: permanent.

```latex
\tr(A)
\rk(A)
\perm(A)
```

## Number Theory Commands

- `\ceil{<expr>}`: ceiling delimiter.
- `\floor{<expr>}`: floor delimiter.
- `\divby`: Russian divisibility relation.
- `\bydiv`: international vertical-bar divisibility relation.
- `\notdivby`: negated Russian divisibility relation.
- `\notbydiv`: negated international divisibility relation.

```latex
\ceil{x/2}
\floor{x/2}
a \divby b
a \bydiv b
a \notdivby b
a \notbydiv b
```

## Rules

- Use `\abs{...}` instead of manual `\left|...\right|` for absolute value.
- Use `\norm{...}`, `\spr{...}{...}`, and `\cpr{...}{...}` for consistent linear algebra notation.
- Use generated vector shorthands only after loading the algebra plugin.

## Avoid

```latex
\left|\frac{a}{b}\right|
\left\|v\right\|
```

Prefer:

```latex
\abs{\frac{a}{b}}
\norm{v}
```
