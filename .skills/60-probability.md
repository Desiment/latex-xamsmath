# xamsmath: Probability Plugin

## When To Use

Use the `probability` plugin for probability measures, laws, expectations,
moments, covariance, distributions, and common stochastic-process text.

## Required Setup

```latex
\usepackage[all]{xamsmath}
\XAMSMathLoadPlugin{probability}
```

## Split Delimiter Helpers

These are implemented helper commands and can be useful when authoring related
notation.

- `\BracesSplit{<left>}{<right>}`: parenthesized split delimiter.
- `\BraketSplit{<left>}{<right>}`: bracketed split delimiter.

```latex
\BracesSplit{A}{B}
\BraketSplit{X}{Y}
```

## Functional Authoring Helpers

- `\ConditionalFunctional{<cmd>}{<head>}`: defines a PIE-aware probability-like command using parentheses.
- `\ConditionalFunctionalOperator{<cmd>}{<head>}`: defines a PIE-aware expectation-like command using brackets.

```latex
\ConditionalFunctional{\Qprob}{\mathbb{Q}}
\Qprob(A | B)

\ConditionalFunctionalOperator{\M}{\mathbb{M}}
\M[X | Y]
```

## Probability And Law Commands

- `\P(<event>)`: probability measure.
- `\P(<event> | <condition>)`: conditional probability.
- `\Law(<variable>)`: law or distribution.
- `\Law(<variable> | <condition>)`: conditional law.

These commands are PIE-aware, so indices and exponents come before the
parenthesized argument.

```latex
\P(A)
\P(A | B)
\P_X(A | B)
\P^2(A)
\Law(X)
\Law(X | Y)
```

## Expectation And Moment Commands

- `\E[<expr>]`: expectation.
- `\D[<expr>]`: variance or dispersion notation.
- `\std[<expr>]`: standard deviation.
- `\mad[<expr>]`: mean absolute deviation.
- `\Skew[<expr>]`: skewness.
- `\Kurt[<expr>]`: kurtosis.

All are PIE-aware and support one plain vertical bar for conditioning.

```latex
\E[X]
\E[X | Y]
\E_{\P}[X | Y]
\E^2[X]
\D[X]
\std[X]
\mad[X]
\Skew[X]
\Kurt[X]
```

## Covariance

- `\covbraces{<left>}{<right>}`: parenthesized two-argument delimiter used by `\Cov`.
- `\Cov{<left>}{<right>}`: covariance.

```latex
\covbraces{X}{Y}
\Cov{X}{Y}
\Cov{\sum_{i=1}^n X_i}{Z}
```

## Distribution Commands

Implemented distribution commands:

- `\Uniform`: uniform distribution symbol.
- `\Normal`: normal distribution symbol.
- `\Poiss`: Poisson distribution name.
- `\Exp`: exponential distribution name.

```latex
X \sim \Uniform(a,b)
X \sim \Normal(\mu,\sigma^2)
X \sim \Poiss(\lambda)
X \sim \Exp(\lambda)
```

## Stochastic Process Text

- `\cadlag`: text form of cadlag.

```latex
The process has \cadlag{} paths.
```

## Rules

- Use a plain vertical bar `|` inside `\P(...)`, `\Law(...)`, `\E[...]`, `\D[...]`, `\std[...]`, `\mad[...]`, `\Skew[...]`, and `\Kurt[...]`.
- Do not use `\middle|` inside probability plugin commands.
- Put indices and exponents before parentheses or brackets: `\E_{\P}^2[X]`.
- Use only implemented distribution commands listed above.

## Avoid

```latex
\E[X \middle| Y]
\E[X]_{\P}
\P(A)_{X}
\Bern(p)
\Bin(n,p)
\Mult(n,p_1,\dots,p_k)
```

Prefer:

```latex
\E[X | Y]
\E_{\P}[X]
\P_X(A)
```

`\Bern`, `\Bin`, and `\Mult` are not currently implemented by this package.
