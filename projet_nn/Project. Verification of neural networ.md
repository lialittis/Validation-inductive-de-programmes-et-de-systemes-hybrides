# Project. Verification of neural networks

A fundanmental challenge : to ensure the sagety of these learning enabled systems.

In particular, neural networks are often vulnerable to small disturbances, which may lead to incorrect decisions. To address this challenge and prove that a network is free of adversarial examples (usually, in a region around a given input), recent work has started investigation the use o fverification. Current verifiers can be broadly classified as either complete or incomplete.

Complete verifiers are exact, e.e., if the verifier fails to certify a network then the network is non-robust (and vice-versa). => They are mostly based on Mixed Intefer Linear Programming(MILP). Although precise, these can only handle networks with a small number of layers and neurons.

Incomplete verifers usually employ overapproximation methods and hence they are sound but may fail to prove robustness even if it holds. In this
second class of methods, an approach has been recently proposed , allowing to prove by abstract interpretation, the robustness to disturbances for neural networks of realistic size.

Variations were then proposed to improve accuracy or more generally the tradeoff between accuracy and speed. These approaches are based on the abstract domains of zonotopes and polyhedra, with different variations for the abstraction of the activation functions.

## Objectives of the project

The project's objectives are to discuss and possibly experiment existing abstractions, and maybe propose some variations of your own. Implementation is optional. A complementary goal is to extend such analyzes to broader classes of neural networks, such as recurrent networks.

## Expected work

### Bibliographical study

Your project can consist solely on a bibliographic study of the state of the art on neural network verication. In that case, I expect a wide overview of the state of the art (meaning wider than the references I provide here), and some more in-depth discussion of one or two specic papers that you found interesting.



### Proposing and experimenting / discussing new abstractions


### Implementation