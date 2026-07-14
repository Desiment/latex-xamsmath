---
name: xamsmath-00-loading-options
description: Load xamsmath with the right package options and built-in plugins for mathematical documents.
license: MIT
compatibility: opencode
metadata:
  package: xamsmath
  topic: loading-options
---

# xamsmath: Loading And Options

## When To Use

Use `xamsmath` when writing mathematical documents that need extended AMS-style
notation, autosized operator arguments, paired delimiters, derivative helpers,
probability notation, or package-local mathematical plugins.

## Required Setup

Basic loading:

```latex
\usepackage{xamsmath}
```

Load all built-in option modules:

```latex
\usepackage[all]{xamsmath}
```

Load selected option modules:

```latex
\usepackage[fonts,operators,braces,eqmicrotype]{xamsmath}
```

Load plugins after the package:

```latex
\XAMSMathLoadPlugin{foundations}
\XAMSMathLoadPlugin{algebra}
\XAMSMathLoadPlugin{calculus}
\XAMSMathLoadPlugin{combinatorics}
\XAMSMathLoadPlugin{probability}
```

## Package Options

- `unicodemath`: loads `unicode-math` instead of `amsfonts` and `amssymb`.
- `fonts`: loads extra math font dependencies and defines `\mathbx`.
- `symbols`: reserved stable extension point; currently defines no user command.
- `operators`: defines `\Proj`, `\argmax`, `\argmin`, `\loc`, and `\const`.
- `braces`: upgrades braced operator behavior and many standard math operators.
- `eqmicrotype`: defines compact math-style helpers and small sign symbols.
- `all`: enables `fonts`, `symbols`, `operators`, `braces`, and `eqmicrotype`.

## Public Loading Command

### `\XAMSMathLoadPlugin{<plugin>}`

Loads a plugin file from `plugins/xamsmath.plugin.<plugin>.tex`.

Implemented plugin names:

- `foundations`
- `algebra`
- `calculus`
- `combinatorics`
- `probability`

Example:

```latex
\usepackage[all]{xamsmath}
\XAMSMathLoadPlugin{algebra}
\XAMSMathLoadPlugin{probability}
```

## Rules

- Use `\XAMSMathLoadPlugin` only after `\usepackage{xamsmath}`.
- Use `[all]` for documents that need most package features.
- Use focused options for minimal documents.
- The `unicodemath` option replaces `amsfonts` and `amssymb` with `unicode-math`. It is not included in `all`.
- When `unicodemath` is active, the `fonts` option skips `upgreek` and `eucal` since `unicode-math` provides Greek letters natively.
- The `braces` option changes behavior of many standard operators such as `\sin`, `\log`, `\det`, and `\lim`.
- Some plugin commands depend on option-defined commands. For example, `foundations` command `\ind` uses `\mathbx`, so load `fonts` before using it.

## Example

```latex
\documentclass{article}
\usepackage[all]{xamsmath}
\XAMSMathLoadPlugin{foundations}
\XAMSMathLoadPlugin{algebra}
\XAMSMathLoadPlugin{calculus}
\XAMSMathLoadPlugin{probability}

\begin{document}
\[
  \E[X | X \in \set{x \in \R | x > 0}] = \int_0^\infty x f(x) \dif x
\]
\end{document}
```

## Avoid

```latex
\XAMSMathLoadPlugin{algebra}
\usepackage{xamsmath}
```

Load the package first, then plugins.
