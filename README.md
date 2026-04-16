# 📐 Applied Numerical Methods (ANM)

> A clean, interactive Python implementation of core numerical methods — built for students and learners of Applied Mathematics / Numerical Analysis courses.

---

## 📖 Overview

This repository contains well-structured, console-based Python implementations of fundamental numerical methods commonly taught in engineering and mathematics curricula. Each method is self-contained with detailed iteration tables, multiple stopping criteria, divergence detection, and formatted result summaries — making it ideal for both learning and academic lab work.

---

## 🧮 Methods Implemented

### 1. 🔀 Bisection Method
Finds the root of `f(x) = 0` by repeatedly halving a bracketed interval `[a, b]`.

- Requires `f(a)` and `f(b)` to have **opposite signs**
- Guaranteed convergence (if the bracket is valid)
- Stopping criteria: interval width `|b - a|`, function value `|f(c)|`, or both

### 2. 🔁 Fixed Point Iteration
Solves `f(x) = 0` by rewriting it as `x = g(x)` and iterating `x_(n+1) = g(x_n)`.

- Convergence requires `|g'(x)| < 1` near the root
- Built-in divergence detection (`|x| > 1e10`)
- Stopping criteria: absolute error, relative error, `|f(x)|`, or both

### 3. 📉 Secant Method
Finds the root of `f(x) = 0` using two initial guesses — **no derivative needed**.

- Superlinear convergence order (~1.618)
- Handles near-zero denominator gracefully
- Stopping criteria: absolute error, relative error, `|f(x)|`, or both

### 4. 📊 Newton's Interpolation (Forward & Backward)
Estimates the value of a function at a new point using a table of known data points.

- Builds and displays the **finite difference table**
- **Forward interpolation** — best when `x` is near the start of the table
- **Backward interpolation** — best when `x` is near the end of the table
- Auto-suggests the appropriate method based on `x`'s position
- Validates that input data is **equally spaced**

---

## 🚀 Getting Started

### Prerequisites

- Python 3.6 or higher
- No external libraries required (uses only the built-in `math` module)

### Run

```bash
python anm.py
```

Each method prompts you interactively for inputs (bounds, tolerance, initial guesses, data points, etc.).

---

## 🛠️ Customising the Function

To solve a different equation, open `anm.py` and edit the `f(x)` function inside the relevant method section:

```python
def f(x):
    return x**3 - x - 2      # ← change this to your equation
```

For **Fixed Point Iteration**, also edit `g(x)`:

```python
def g(x):
    return (x + 2) ** (1/3)  # ← rearranged form: f(x)=0 → x = g(x)
```

**Example equations you can try:**

| Equation `f(x) = 0`   | `g(x)` for Fixed Point     |
|-----------------------|----------------------------|
| `x³ - x - 2`         | `(x + 2) ** (1/3)`         |
| `cos(x) - x`         | `math.cos(x)`              |
| `x² - 2`             | `2 / x`                    |
| `e^x - 3x`           | `math.exp(x) / 3`          |
| `x³ - 4x + 1`        | `(x**3 + 1) / 4`           |

---

## 🖥️ Sample Output

```
══════════════════════════════════════════════════════════════════════════
  BISECTION METHOD
══════════════════════════════════════════════════════════════════════════
  Interval  : [1, 2]        f(a): -2.000000    f(b): 4.000000
  Tolerance : 0.001         Criterion: interval
──────────────────────────────────────────────────────────────────────────
Iter          a             b       c=(a+b)/2        f(a)        f(c)
   1   1.000000      2.000000      1.50000000   -2.000000    0.875000
   2   1.000000      1.500000      1.25000000   -2.000000   -1.296875
  ...

  ╔══════════════════════════════════════╗
  ║  Approximate Root  : 1.52137756      ║
  ║  f(root)           : 1.91e-04        ║
  ║  Iterations used   : 11              ║
  ╚══════════════════════════════════════╝
```

---

## 📂 File Structure

```
anm.py
│
├── Bisection Method
│   ├── f(x)            — equation to solve
│   ├── bisection()     — core algorithm
│   └── main()          — interactive CLI
│
├── Fixed Point Iteration
│   ├── f(x), g(x)      — original and rearranged equations
│   ├── fixed_point_iteration()
│   └── main()
│
├── Secant Method
│   ├── f(x)
│   ├── secant()
│   └── main()
│
└── Newton's Interpolation
    ├── build_difference_table()
    ├── print_difference_table()
    ├── newton_forward()
    ├── newton_backward()
    ├── validate_equal_spacing()
    └── main()
```

---

## 📚 Topics Covered

- Root Finding Methods (Bracketing & Open)
- Convergence criteria and error analysis
- Finite Difference Tables
- Polynomial Interpolation

---

## 👤 Author

Developed as part of an **Applied Numerical Methods** course.
Originally created in [Google Colab](https://colab.research.google.com/).

---

 📄 License

This project is open for educational use. Feel free to fork, modify, and build upon it.
