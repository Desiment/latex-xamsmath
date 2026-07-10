---
name: xamsmath-05-authoring-helpers
description: Use xamsmath package-authoring helper commands for declaring aliases, paired delimiters, and operators.
license: MIT
compatibility: opencode
metadata:
  package: xamsmath
  topic: authoring-helpers
---

# xamsmath: Authoring Helpers

## When To Use

Use these helpers when defining new mathematical notation inside a document,
plugin, or package module. They are not usually needed for ordinary math writing,
but they are part of the implemented public authoring API.

## Required Setup

```latex
\usepackage{xamsmath}
```

## Commands

### `\piefication{<command>}`

Wraps an existing command so it absorbs trailing prime, index, and exponent
syntax using `mathcommand` PIE parsing.

```latex
\newmathcommand{\Foo}{\mathcal{F}}
\piefication{\Foo}
\Foo'_i^2
```

### `\DeclarePairedSplitDelimiter{<cmd>}{<left>}{<right>}`

Declares a paired delimiter command that optionally splits its argument at one
top-level vertical bar `|`.

```latex
\DeclarePairedSplitDelimiter{\set}{\{}{\}}
\set{x \in \R | x > 0}
\set{1,2,3}
\set[\Big]{x | x^2 > 1}
```

Generated command syntax:

```latex
\cmd{body}
\cmd{left | right}
\cmd[\big]{body}
\cmd[\Big]{left | right}
```

### `\NewTemplateCommand<cmd><template params>{runtime params}{replacement}`

Defines a reusable command template. The template parameter signature is written
inside angle brackets.

```latex
\NewTemplateCommand\tmpl_example<mm>{m}{#1 #3 #2}
```

### `\TemplateInstance{<cmd>}{<template>}<values>`

Creates a zero-argument command by partially applying a template.

```latex
\TemplateInstance\foo\tmpl_example<a,b>
```

### `\TemplateInstancePIE{<cmd>}{<template>}<values>`

Creates a template instance and wraps it with `\piefication`.

```latex
\TemplateInstancePIE\Foo\tmpl_example<a,b>
\Foo_i^2
```

### `\DeclareBracedMathOperator{<cmd>}{<name>}`

Declares an operator. Without the `braces` option, this is an AMS-style fallback.
With the `braces` option, it creates a PIE-aware operator that can take optional
bracketed, parenthesized, or braced operands.

```latex
\DeclareBracedMathOperator{\rank}{rank}
\DeclareBracedMathOperator*{\argmax}{argmax}

\rank(A)
\rank_i^2[A]
\argmax_{x \in X} f(x)
```

## Rules

- Use one top-level `|` in split delimiter arguments.
- Do not use `\middle|` inside commands declared with `\DeclarePairedSplitDelimiter`.
- Use `\TemplateInstancePIE` when the resulting command should accept primes, subscripts, and superscripts.
- Use starred `\DeclareBracedMathOperator*` for limit-style operators.

## Avoid

```latex
\set{x \in \R : x > 0}
\set{x \in \R \middle| x > 0}
```

Use the plain vertical bar convention:

```latex
\set{x \in \R | x > 0}
```
