---
name: xamsmath-50-combinatorics
description: Use the xamsmath combinatorics plugin for binomial, multinomial, partition, and counting notation.
license: MIT
compatibility: opencode
metadata:
  package: xamsmath
  topic: combinatorics
---

# xamsmath: Combinatorics Plugin

## When To Use

Use the `combinatorics` plugin for multiset coefficients, Stirling numbers, and
falling or rising factorial notation.

## Required Setup

```latex
\usepackage{xamsmath}
\XAMSMathLoadPlugin{combinatorics}
```

## Commands

### `\multbinom{<n>}{<k>}`

Multiset coefficient, commonly read as combinations with repetition.

```latex
\multbinom{n}{k}
```

### `\Stirling{<n>}{<k>}`

Stirling number of the second kind with brace delimiters.

```latex
\Stirling{n}{k}
```

### `\stirling{<n>}{<k>}`

Stirling number of the first kind with bracket delimiters.

```latex
\stirling{n}{k}
```

### `\fallf{<x>}^{<n>}`

Falling factorial with an underlined exponent. This command is PIE-aware.

```latex
\fallf{x}^{n}
\fallf{x}_{k}^{n}
```

### `\risef{<x>}^{<n>}`

Rising factorial or Pochhammer-style notation with an overlined exponent. This
command is PIE-aware.

```latex
\risef{x}^{n}
\risef{x}_{k}^{n}
```

## Rules

- Put falling and rising factorial order in the superscript after the argument.
- Put any index after the argument as a subscript.
- Use `\Stirling` for second-kind Stirling numbers and `\stirling` for first-kind Stirling numbers.

## Avoid

```latex
x^{\underline{n}}
x^{\overline{n}}
```

Prefer:

```latex
\fallf{x}^{n}
\risef{x}^{n}
```
