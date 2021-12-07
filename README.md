# Formal Verification of Real-Interval Operators

We formalize operators in a real-interval arithmetic (RIA) that are designed to be an abstraction of floating-point arithmetic (FPA) operators.

This repository aims to provide a correctness proof, which addresses the following properties:

- **Soundness of RIA four arithmetic operators.**
    - We consider addition, subtraction, multiplication and division.
    - Each operator is given two intervals as arguments that enclose FP numbers (that can be special values, i.e. infinities and NaN).
    - We verify that "*a resulting interval properly enclose the corresponding FP computation results*."
- **Correctness of RIA comparison operators.**
    - We consider two interval extensions, *weak* and *strong*, of comparison operators.
        - Weak extensions are used for unsat checking of FPA logic formulas.
        - Strong extensions are used for sat checking.
    - We only consider comparisons between intervals or between an interval and zero.
    - We verify the following:
        - Lemmas `*_n_unsat`: "*If the weak extension is unsat, then so is the original literal*."
        - "*If the strong extension is sat with intervals that contain FP numbers, then so is the original literal*."
            - We in fact verify the contraposition:
            - Lemmas `*_p_sat`: "*If a literal is unsat, then, for any intervals that contain an FP number, the strong extension is unsat*."

<br />

Reference:

D. Ishii, T. Tomita and T. Aoki: Approximate Translation from Floating-Point to Real-Interval Arithmetic, [arXiv:2112.02804](http://arxiv.org/abs/2112.02804), 2021. 


## Used Tools

- [Why3 1.3.1](http://why3.lri.fr)
- [Alt-Ergo 2.2.0](https://alt-ergo.ocamlpro.com)
- [Coq 8.11.2](https://coq.inria.fr) (w/ [Flocq 3.4.2](https://flocq.gitlabpages.inria.fr))


## Why3 Modules

- `rint.RealInterval`
    - The soundness of the downward/upward rounding operators are not proved with Why3 (the first item in the result). Instead, it is confirmed manually.
- Four arithmetic operators:
    - `rint.Addition`
    - `rint.Subtraction`
    - `rint.Multiplication`
    - `rint.Division`
- Comparison operators: `rint.Comparison`
- Modules that contain auxiliary lemmas (taken from [https://dsksh.github.io/vint-jcam2020.zip](https://dsksh.github.io/vint-jcam2020.zip)):
    - `rineq.RmultLeCompat`
    - `rineq.Rinv`
    - `rineq.RdivLeCompat`


## Verification Result

Used machine: MacBook Pro w/ 2GHz Intel Core i5 and 16GB RAM.

<image src="images/rint_add.png" width="540" />
<image src="images/rint_sub.png" width="540" />
<image src="images/rint_mul.png" width="540" />
<image src="images/rint_div.png" width="540" />
<image src="images/rint_comp.png" width="540" />

<!-- EOF -->
