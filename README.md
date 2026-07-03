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


AFAIK you need LuaLaTeX to use some features

### Installation Methods

**Method 1: Manual Installation**
```bash
# Copy xamsmath.sty and plugins/ to your LaTeX path
cp xamsmath.sty ~/texmf/tex/latex/xamsmath/
cp plugins/*.tex ~/texmf/tex/latex/xamsmath/plugins/
```

**Method 2: Project Local**
```bash
# Place in your project directory
project/
├── xamsmath.sty
├── plugins/
│   ├── foundations.tex
│   ├── algebra.tex
│   ├── calculus.tex
│   ├── combinatorics.tex
│   └── probability.tex
└── main.tex
```

## ToDo
- [ ] Split examples and move them in examples directory
- [ ] Extend examples and ensure that  each example has code snippet before it (in rendered PDF)
- [ ] Microtypography features: slight operator extension
- [ ] Microtypography features: alignment of under/overbraces
- [ ] Microtypography features: under/overbraces that do not interact with autoscale braces 
- [ ] Microtypography features: improve fcking xfrac package
- [ ] Microtypography features: imporved sizes in sub/supscripts (make proper improvement)
- [ ] Move template macros functionality to seperate project 
- [ ] MnSymbol export features 
- [ ] Add links to all mathematically related packages 

## Version History

- **v0.1-alpha** (2025-10-06): Initial release with core features and plugin system
