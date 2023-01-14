---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

--

![bg left:40% 80%](https://marp.app/assets/marp.svg)

# **Marp**

Markdown Presentation Ecosystem

https://marp.app/

# **Python Code Quality**

## **Static Analysis**

The errors you can discover without running the code.

Formatting

Code Quality

Security

Type checking

## **Dynamic Analysis**

The errors you can discover by running the code.

Unit tests.

Integration tests.

We will not be discussing dynamic analysis. It is a big topic.

## **Static Analysis Tools - Formatting**

Note all these tools were suggested by copilot.

### **pylint**

A sophisticated static analysis tool for Python. 

[pylint docs](https://pylint.pycqa.org/en/latest/)

Rules are configurable, so you can turn off the ones you don't like, or add your own.

"Pylint analyses your code without actually running it. It checks for errors, enforces a coding standard, looks for code smells, and can make suggestions about how the code could be refactored. Pylint can infer actual values from your code using its internal code representation (astroid). If your code is import logging as argparse, Pylint will know that argparse.error(...) is in fact a logging call and not an argparse call."

### **flake8**

A wrapper around a bunch of other tools.

[flake8 docs](https://flake8.pycqa.org/en/latest/)

```
F401 module imported but unused
```

### **black**

Python code formatter.

The blog posts describing how it was developed are interesting.
The author said it was the hardest program they could imagine writing.

[black github](https://github.com/psf/black)

[black docs](https://black.readthedocs.io/en/stable/)

There is a link from the page above to an online app for trying it out.

[demo - link is ephemeral](https://black.vercel.app/?version=stable&state=_Td6WFoAAATm1rRGAgAhARYAAAB0L-Wj4ARsAnNdAD2IimZxl1N_WlkPinBFoXIfdFTaTVkGVeHShArYj9yPlDvwBA7LhGo8BvRQqDilPtgsfdKl-ha7EFp0Ma6lY_06IceKiVsJ3BpoICJM9wU1VJLD7l3qd5xTmo78LqThf9uibGWcWCD16LBOn0JK8rhhx_Gf2ClySDJtvm7zQJ1Z-Ipmv9D7I_zhjztfi2UTVsJp7917XToHBm2EoNZqyE8homtGskFIiif5EZthHQvvOj8S2gJx8_t_UpWp1ScpIsD_Xq83LX-B956I_EBIeNoGwZZPFC5zAIoMeiaC1jU-sdOHVucLJM_x-jkzMvK8Utdfvp9MMvKyTfb_BZoe0-FAc2ZVlXEpwYgJVAGdCXv3lQT4bpTXyBwDrDVrUeJDivSSwOvT8tlnuMrXoD1Sk2NZB5SHyNmZsfyAEqLALbUnhkX8hbt5U2yNQRDf1LQhuUIOii6k6H9wnDNRnBiQHUfzKfW1CLiThnuVFjlCxQhJ60u67n3EK38XxHkQdOocJXpBNO51E4-f9z2hj0EDTu_ScuqOiC9cI8qJ4grSZIOnnQLv9WPvmCzx5zib3JacesIxMVvZNQiljq_gL7udm1yeXQjENOrBWbfBEkv1P4izWeAysoJgZUhtZFwKFdoCGt2TXe3xQ-wVZFS5KoMPhGFDZGPKzpK15caQOnWobOHLKaL8eFA-qI44qZrMQ7sSLn04bYeenNR2Vxz7hvK0lJhkgKrpVfUnZrtF-e-ubeeUCThWus4jZbKlFBe2Kroz90Elij_UZBMFCcFo0CfIx5mGlrINrTJLhERszRMMDd39XsBDzpZIYV4TcG7HoMS_IF8aMAAAxI-5uTWXbUQAAY8F7QgAAP01Vc6xxGf7AgAAAAAEWVo=)


## **Static Analysis Tools - Code Quality**

### **isort**

A tool to sort imports.

[isort docs](https://pycqa.github.io/isort/)

Why would you want to do this?

A messy set of imports can make it hard to see what is being used. 

It especially makes it hard to see if you've missed or duplicated an import.


### **pydocstyle**

A tool for checking compliance with Python docstring conventions.

[pydocstyle docs](https://www.pydocstyle.org/en/stable/)

```
D100 	Missing docstring in public module

D101 	Missing docstring in public class
```

### **pycodestyle**

[error codes](https://pycodestyle.pycqa.org/en/latest/intro.html#error-codes)

```
W391 	blank line at end of file
```

### **pyflakes**

The simplest static analysis tool for Python.

Pick this for speed, not thoroughness.

[pyflakes docs](https://pypi.org/project/pyflakes/)

### **pyroma**

Note: I had never heard of this one before copilot suggested it.

This tool checks that your package is ready to be uploaded to PyPI.

[pyroma docs](https://pypi.org/project/pyroma/)

### **vulture**

Finds unused code.

[vulture docs](https://pypi.org/project/vulture/)

Note: I also hadn't head of this one before copilot suggested it.

## **Static Analysis Tools - Security**

### **bandit**

Security issue checker for Python.

[bandit docs](https://bandit.readthedocs.io/en/latest/)

This looks like more of a framework than a complete solution. You still need to have examples of vulnerabilities to compare against. 

The documentation is worth reading to learn more about Python security.

### **safety**

Another security issue checker for Python.

[safety docs](https://pyup.io/safety/)

"By default it uses the open Python vulnerability database Safety DB, which is licensed for non-commercial use only."

[Safety DB](https://github.com/pyupio/safety-db)

## **Static Analysis Tools - Type Checking**

### **mypy**

Static type checker for Python.

[code](https://github.com/python/mypy)

What is type checking?

It's a way of checking that the types of variables are what you expect them to be.

#### mypy examples

```python
An example of a type error:

```python
def add(a, b):
    return a + b

add(1, 2)
add(1, '2')
```

2 is an int, '2' is a string. The second call to add will fail.

Mypy needs type annotations to work.

```python
def add(a: int, b: int) -> int:
    return a + b
```

[type hints cheat sheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)

### **pyre**

Fast type checking for Python.

[pyre docs](https://pyre-check.org/)

"Follows the typing standards introduced in PEPs [484 - Type Hints](https://peps.python.org/pep-0484/), [526 - Syntax for Variable Annotations](https://peps.python.org/pep-0526/), [612 - Parameter Specification Variables](https://peps.python.org/pep-0612/), and is being actively developed and constantly improved."


### **pytype**

Inference based type checker for Python.

[pytype docs](https://google.github.io/pytype/)

"Pytype is a static type analyzer for Python code. It infers types for your code, finds bugs, and understands Python’s runtime behavior."

### **pyright**

Static type checker for Python from Microsoft.

Designed for speed.

[pyright code](https://github.com/microsoft/pyright)

