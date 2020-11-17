# An Abstract Domain for Certifying Neural Networks

## Neural network robustness

**Given**

Neural network: $f: {R}^m -> {R}^n$

Perturbation region $\mathcal{R}(I_0,\phi)$

**Perturbation Regions**

1. $L_{\infty}(I_0,\epsilon)$: All images I where pixel values in I and $I_0$ differ by at most $\epsilon$.
2. Rotate$(I_0,\epsilon,\alpha,\beta)$:All images I in $L_{\infty}(I_0,\epsilon)$ rotated by $\theta \in \[\alpha,\beta\]$.

**To Prove**

$\forall I \in \mathcal{R}(I_0,\phi),f(I)[c]>f(I)[j]$\\
where c is the correct output and j is any other output.

**Challenges**

The size of $\mathcal{R}(I_0,\phi)$ grows exponentially in the number of pixels:
* cannot compute f(I) for all I separately.

Prior work on verification
* Precise but does not scale:
  * SMT solving \[CAV'17\]
  * input refinement \[USENIX'18\]
  * semidefinite relaxations \[ICLR'18\]
* Scales but imprecise
  * Linear relaxations \[ICML'18\]
  * abstract interpretation \[S & P'18, NIPS'18\]

**This Paper**

A new abstract domain combining floating point Polyhedra with intervals:
* custom transformers for common functions in neural networks sch as affine transformsm ReLU, sigmoid, tanh, and maxpool activations
* scalable and precise analysis

## Inplementation

### DeepPoly

complete and parallelized end-to-end implementation based on ELINA


* First approach to certify robustness under rotation combined with linear interpolation:
  * based on input refinement
  * $\epsilon = 0.001, \alpha = -45\degree, \beta = 65\degree$

> comparation with NIPS'18 and DeepPoly

### Neural network transformations

Affine: $x_j <- v + \sum_{i\in [j-1]} w_i * x_i$

ReLU: $x_j <- max(0,x_i)$

Maxpool: $x_j <- max_{i\in P}x_i$

Sigmoid: $x_j <- \frac{e^{x_i}}{e^{x_i}+1}$

Tanh: $x_j <- tanh(x_i)$

### The Abstract Domain

Shape: associate a lower polyhedral $a_i^{\leq}$ and an upper polyhedral $a_i^{\geq}$ constraint with each $x_i$



Concretization of abstract element a:
$\gamma_n(a) = {x\in R^n | \foralli \in [n], a_i^{\leq} \leq x_i \wedge a_i^{\geq} \geq x_i}$

Domain invariant: store auxiliary concrete lower and upper bounds $l_i,u_i$ for each $x_i$.

 