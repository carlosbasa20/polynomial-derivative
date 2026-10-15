<div align="center">

# 📐 Polynomial Derivative

**A Jupyter notebook that takes a simple polynomial as text and returns its derivative.**

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Dependencies](https://img.shields.io/badge/dependencies-standard%20library%20only-brightgreen)
![Built with Claude Code](https://img.shields.io/badge/Built%20with-Claude%20Code-D97757?logo=anthropic&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-blue)

</div>

```text
f(x)  = 3x^4 - 2x^2 + 5x - 7
f'(x) = 12x^3 - 4x + 5
```

---

## 🤖 Built with Claude Code

> [!NOTE]
> This project was built together with **[Claude Code](https://claude.com/claude-code)**, Anthropic's AI coding agent.
> Its purpose is to show that Claude can be used effectively for this kind of task, and that **I already know how to use this tool** in a real workflow.

| What I did | What Claude did |
| --- | --- |
| Described the goal in plain language | Proposed the design and wrote the code |
| Reviewed and validated the solution | Wrote tests and ran the notebook to check it |
| Decided requirements, language and publishing | Wrote the documentation and published the repository |

AI-assisted development lets me deliver working, tested and documented software **faster**, while keeping control over the decisions and the quality of the result.

---

## ✨ Features

- Parses polynomials written as plain text: `3x^4 - 2x^2 + 5x - 7`
- Differentiates them with the **power rule**: $\frac{d}{dx}(a\,x^n) = n\,a\,x^{n-1}$
- Accepts integer and decimal coefficients (`2.5x^3`), spaces, `*` and `**` (`3*x**2 + 1`)
- Combines like terms automatically (`4x^2 + 3x^2` → `7x^2`)
- Uses exact arithmetic (`fractions.Fraction`), so `0.1x^3` becomes `0.3x^2`, not `0.30000000000000004x^2`
- Gives clear error messages for invalid input (`3x^`, `3y^2`, `x^-2`, …)
- Includes built-in tests and an interactive cell

## 📦 Requirements

| Requirement | Version | Notes |
| --- | --- | --- |
| Python | 3.10+ | Uses `dict[int, Fraction]` type hints |
| Jupyter | any recent | Only needed to open the notebook (`notebook`, `jupyterlab` or VS Code) |

The code itself uses **only the Python standard library** (`re`, `fractions`), so there is nothing else to install.

## 🚀 Getting started

```bash
git clone https://github.com/carlosbasa20/polynomial-derivative.git
cd polynomial-derivative
python -m venv .venv
```

Activate the virtual environment:

```bash
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate
```

Install Jupyter and open the notebook:

```bash
pip install -r requirements.txt
jupyter notebook polynomial_derivative.ipynb
```

> [!TIP]
> You can also open `polynomial_derivative.ipynb` directly in **VS Code** with the Jupyter extension, without installing anything else.

## 🧮 Usage

Run all the cells in order (**Run → Run All Cells**). The last cell asks for a polynomial:

```text
Enter a polynomial (e.g. 3x^4 - 2x^2 + 5x - 7): -2x^3 + 0.5x^2 - 4x + 9
f(x)  = -2x^3 + 0.5x^2 - 4x + 9
f'(x) = -6x^2 + x - 4
```

You can also call the functions directly from any cell:

```python
differentiate_polynomial("x^3 + x")    # '3x^2 + 1'
parse_polynomial("3x^2 - 5x + 1")      # {2: 3, 1: -5, 0: 1}
```

### Input format

| Input | Meaning | Derivative |
| --- | --- | --- |
| `3x^4 - 2x^2 + 5x - 7` | Standard form | `12x^3 - 4x + 5` |
| `-x^5 + 4x^2 - x` | Implicit coefficient of 1 | `-5x^4 + 8x - 1` |
| `2.5x^3 - 0.5x` | Decimal coefficients | `7.5x^2 - 0.5` |
| `3*x**2 + 1` | Python-style operators | `6x` |
| `4x^2 + 3x^2 - x` | Like terms are combined | `14x - 1` |
| `7` | Constant | `0` |

**Not supported:** negative or fractional exponents, variables other than `x`, parentheses, and products of polynomials.

## 🔍 How it works

The notebook is split into three small functions:

1. **`parse_polynomial(text)`** turns the text into a dictionary `{exponent: coefficient}` using a regular expression per term.
2. **`differentiate(coefficients)`** applies the power rule: each `a·x^n` becomes `(n·a)·x^(n-1)`, and constants disappear.
3. **`polynomial_to_text(coefficients)`** converts the dictionary back into readable text, sorted from highest to lowest exponent.

`differentiate_polynomial(text)` chains the three together.

## 📁 Project structure

```text
polynomial-derivative/
├── polynomial_derivative.ipynb   # Notebook: code, examples, tests and interactive cell
├── requirements.txt              # Jupyter (the code itself has no dependencies)
├── LICENSE                       # MIT
└── README.md
```

## ✅ Tests

Section 5 of the notebook checks 10 derivatives and 6 invalid inputs with `assert`. If it runs without errors, it prints:

```text
All tests passed (10 derivatives and 6 invalid inputs).
```

## 📄 License

Released under the [MIT License](LICENSE).

---

<div align="center">

Made by **Carlos Eduardo Barriga Salmeron** with the help of [Claude Code](https://claude.com/claude-code) 🤖

</div>
