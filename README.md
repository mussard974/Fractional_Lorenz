# FractionalLorenz

`FractionalLorenz` is a Python package for computing **relative** and **absolute Lorenz curves** of arbitrary integer and fractional order together with their associated inequality indices.

The package implements the recursive Lorenz families and the fractional interpolation introduced in the accompanying paper.

---

# Installation

Clone the repository

```bash
git clone https://github.com/your_username/FractionalLorenz.git
```

or simply copy `FractionalLorenz.py` into your project.

## Dependencies

- numpy
- scipy
- matplotlib
- pandas (optional, for data handling)

---

# Relative and Absolute Lorenz Curves

The package computes both the **relative** and **absolute** Lorenz families.

## Relative Lorenz curves

```python
from FractionalLorenz import FractionalLorenz

L = FractionalLorenz()

L.fit(
    y,
    weight=weights,
    dominance_param=1,
    kind="relative"
)

L.graph()
```

The argument

```python
kind="relative"
```

computes the family

\[
LR_1,\;LR_2,\;LR_3,\;\ldots
\]

---

## Absolute Lorenz curves

Simply replace

```python
kind="relative"
```

by

```python
kind="absolute"
```

```python
L.fit(
    y,
    weight=weights,
    dominance_param=1,
    kind="absolute"
)

L.graph()
```

which computes

\[
LA_1,\;LA_2,\;LA_3,\;\ldots
\]

---

# Fractional Lorenz Curves

Fractional orders are obtained by specifying

```python
fractional_param
```

For example,

```python
L.fit(
    y,
    weight=weights,
    dominance_param=1,
    fractional_param=0.4,
    kind="relative"
)
```

computes

\[
LR_{1.4}.
\]

Likewise,

```python
L.fit(
    y,
    weight=weights,
    dominance_param=2,
    fractional_param=0.8,
    kind="absolute"
)
```

computes

\[
LA_{2.8}.
\]

---

# Inequality Indices

The associated inequality coefficient is obtained with

```python
L.inequality_index()
```

For example,

```python
L.fit(
    y,
    weight=weights,
    dominance_param=1,
    kind="relative"
)

gini = L.inequality_index()
```

returns the ordinary **relative Gini coefficient**.

Similarly,

```python
L.fit(
    y,
    weight=weights,
    dominance_param=1,
    kind="absolute"
)

gini_absolute = L.inequality_index()
```

returns the ordinary **absolute Gini coefficient**.

Higher and fractional orders are obtained by modifying

```python
dominance_param
```

and

```python
fractional_param
```

respectively.

> **Note.**
>
> The user indexing follows the Lorenz curve order:
>
> - `dominance_param = 1` corresponds to the ordinary Gini coefficient;
> - `dominance_param = 2` corresponds to the second-order Gini family;
> - `dominance_param = 3` corresponds to the third-order Gini family;
> - etc.

---

# Minimal Fractional Order

The package provides a routine for determining the smallest fractional order for which two Lorenz curves no longer cross.

```python
FractionalLorenz.minimal_fractional_order(
    y,
    weight1,
    weight2,
    kind="relative"
)
```

The routine searches

\[
1,\;1.1,\;1.2,\;\ldots,\;1.9,\;2,\;2.1,\;\ldots
\]

until no crossing remains on the interval

\[
[0.01,\;0.99].
\]

---

# Examples

## Relative Lorenz curve (order 1)

![Relative Lorenz curve](LR1.png)

---

## Absolute Lorenz curve (order 1)

![Absolute Lorenz curve](LA1.png)

---

## Fractional relative Lorenz curve

Example for the fractional order \(1+c\).

![Fractional Relative Lorenz curve](LR1-1.png)

---

## Fractional absolute Lorenz curve

Example for the fractional order \(1+c\).

![Fractional Absolute Lorenz curve](LA1-1.png)

---

# References

If you use this package in academic work, please cite the accompanying paper introducing the fractional Lorenz families and their associated inequality measures.
