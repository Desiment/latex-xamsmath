# xamsmath - Enhanced Mathematical Typesetting for LaTeX

[![LaTeX](https://img.shields.io/badge/LaTeX-3-blue.svg)](https://www.latex-project.org/)

## Overview

`xamsmath` is a comprehensive LaTeX package that extends the standard `amsmath` package with modern LaTeX3 features and enhanced mathematical notation capabilities. It provides advanced typesetting facilities while maintaining full backward compatibility with existing mathematical code.

## Installation

### Requirements
- LaTeX2e with LaTeX3 support
- `amsmath`, `amsfonts`, `amssymb` packages
- `mathtools` for enhanced mathematical typesetting
- `mathcommand` for PIE notation handling

> Some features require LuaLaTeX.

### Installation Methods

**Method 1: Git Submodule**
```bash
cd your-project/
git submodule add https://github.com/anomalyco/xamsmath.git
```

**Method 2: texmf Tree (Global)**
```bash
# Clone or download the repository into your local texmf tree
git clone https://github.com/anomalyco/xamsmath.git ~/texmf/tex/latex/xamsmath/
```

**Method 3: Manual Installation**
```bash
# Copy xamsmath.sty, code/, and plugins/ to your LaTeX path
cp xamsmath.sty ~/texmf/tex/latex/xamsmath/
cp -r code ~/texmf/tex/latex/xamsmath/
cp plugins/*.tex ~/texmf/tex/latex/xamsmath/plugins/
```

**Method 4: Project Local**
```
your-project/
├── xamsmath.sty
├── code/
│   ├── xamsmath.core.code.tex
│   ├── xamsmath.braces.code.tex
│   ├── xamsmath.eqmicrotype.code.tex
│   ├── xamsmath.fonts.code.tex
│   ├── xamsmath.operators.code.tex
│   └── xamsmath.symbols.code.tex
├── plugins/
│   ├── xamsmath.plugin.foundations.tex
│   ├── xamsmath.plugin.algebra.tex
│   ├── xamsmath.plugin.calculus.tex
│   ├── xamsmath.plugin.combinatorics.tex
│   └── xamsmath.plugin.probability.tex
├── examples/
│   ├── example.tex
│   ├── latexmkrc
│   └── .build/
└── main.tex
```

## ToDo
- [x] Split examples and move them in examples directory
- [x] Extend examples and ensure that each example has code snippet before it (in rendered PDF)
- [ ] Microtypography features: slight operator extension
- [ ] Microtypography features: alignment of under/overbraces
- [ ] Microtypography features: under/overbraces that do not interact with autoscale braces 
- [ ] Microtypography features: improve fcking xfrac package
- [ ] Microtypography features: imporved sizes in sub/supscripts (make proper improvement)
- [ ] Move template macros functionality to seperate project 
- [ ] MnSymbol export features 
- [ ] Add links to all mathematically related packages 

## Version History

- **v0.2-alpha** (2026-01-01): Restructured codebase into modular `code/` directory; reworked all plugins with extended notation support; added braces, eqmicrotype, fonts, and operators modules; improved installation documentation.
- **v0.1-alpha** (2025-10-06): Initial release with core features and plugin system
