#ucsc #cse109 

#### No-Cloning, Teleportation
- There is no physical device that does the following:
	|ψ⟩ ───► [  MACHINE  ] ───► |ψ⟩ ⊗ |ψ⟩

- What we can do:
	- Input:  |0⟩

	   [  MACHINE  ]

		Output: |0⟩    |0⟩
	- basically if we are passing in a qubit that we already know then we can match that
	- no cloning - unlearnability of a qubit just from one copy

#### What about CNOT
We begin with two qubits:

- Qubit A (arbitrary state): $\ket{\psi} = \alpha\ket{0} + \beta\ket{1}$
- Qubit B (initialized): $\ket{0}$

**Initial state:**

$$
\ket{\psi} \otimes \ket{0} = \alpha\ket{00} + \beta\ket{10}
$$

A **CNOT gate** is applied with:

- Control qubit: the first qubit (in state $\ket{\psi}$)
- Target qubit: the second qubit (in state $\ket{0}$)

CNOT flips the target **only if** the control is $\ket{1}$.

**After CNOT:**

$$
\alpha\ket{00} + \beta\ket{11}
$$

This is now an **entangled state** between the two qubits.
## No-Cloning Theorem — Simple Proof

**Claim:** It is impossible to build a universal quantum cloning machine that can copy an *arbitrary* unknown quantum state.

### Setup

Suppose such a machine **exists**. It would be a unitary operator $U$ such that:

$$
U(\ket{\psi} \otimes \ket{0}) = \ket{\psi} \otimes \ket{\psi}
$$

for **any** state $\ket{\psi}$.

Let’s choose two arbitrary normalized states:

$$
\ket{\psi} = \alpha\ket{0} + \beta\ket{1}, \quad \ket{\phi} = \gamma\ket{0} + \delta\ket{1}
$$

Assume $U$ can clone both:

$$
U(\ket{\psi} \otimes \ket{0}) = \ket{\psi} \otimes \ket{\psi} \\
U(\ket{\phi} \otimes \ket{0}) = \ket{\phi} \otimes \ket{\phi}
$$

### Inner product preservation (unitary property)

Since $U$ is unitary, it must preserve inner products:

$$
\braket{\psi|\phi} = \text{original inner product} \\
\Rightarrow \braket{\psi|\phi} = \braket{\psi|\phi}^2 = \text{after cloning}
$$

But this implies:

$$
\braket{\psi|\phi} = \braket{\psi|\phi}^2 \Rightarrow x = x^2 \Rightarrow x(x - 1) = 0
$$

So either:
- $\braket{\psi|\phi} = 0$ (states are orthogonal), or
- $\braket{\psi|\phi} = 1$ (states are identical)

Thus, **cloning only works if the states are either the same or orthogonal**.

### Conclusion

There is no unitary operator that can clone *all* possible states.  
$\Rightarrow$ **Cloning arbitrary unknown quantum states is impossible.**

#### Quantum Teleportation
- "teleport" 1 qubit with 2 bits of classical info

## Modified Quantum Teleportation — CNOT then $+/-$ Measurement

### Setup

- Alice has: $\ket{\psi} = \alpha\ket{0} + \beta\ket{1}$
- Bob has: $\ket{0}$
- Initial state:

$$
\ket{\psi} \otimes \ket{0} = \alpha\ket{00} + \beta\ket{10}
$$

### Step 1: Apply CNOT (Alice is control, Bob is target)

CNOT flips Bob's qubit if Alice's is $\ket{1}$.

- $\alpha\ket{00} \to \alpha\ket{00}$
- $\beta\ket{10} \to \beta\ket{11}$

So the state becomes:

$$
\ket{\Psi} = \alpha\ket{00} + \beta\ket{11}
$$

### Step 2: Alice measures her qubit in the $\{\ket{+}, \ket{-}\}$ basis

Recall:

- $\ket{+} = \frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$
- $\ket{-} = \frac{1}{\sqrt{2}}(\ket{0} - \ket{1})$

We want to rewrite the state $\alpha\ket{00} + \beta\ket{11}$ in the $\{\ket{+}, \ket{-}\}$ basis for **Alice's qubit**.

Use:
- $\ket{0} = \frac{1}{\sqrt{2}}(\ket{+} + \ket{-})$
- $\ket{1} = \frac{1}{\sqrt{2}}(\ket{+} - \ket{-})$

Substitute into the state:

$$
\alpha\ket{0}\ket{0} + \beta\ket{1}\ket{1}
= \alpha \cdot \frac{1}{\sqrt{2}}(\ket{+} + \ket{-})\ket{0}
+ \beta \cdot \frac{1}{\sqrt{2}}(\ket{+} - \ket{-})\ket{1}
$$

Group terms:

$$
= \frac{1}{\sqrt{2}} \left[ \ket{+}(\alpha\ket{0} + \beta\ket{1}) + \ket{-}(\alpha\ket{0} - \beta\ket{1}) \right]
$$

### Step 3: Measurement Outcome

Now Alice measures in the $\{\ket{+}, \ket{-}\}$ basis. There are two possible outcomes:

#### If Alice measures $\ket{+}$:
Bob's qubit collapses to:

$$
\alpha\ket{0} + \beta\ket{1} = \ket{\psi}
$$

#### If Alice measures $\ket{-}$:
Bob's qubit collapses to:

$$
\alpha\ket{0} - \beta\ket{1} = Z\ket{\psi}
$$

### Conclusion

Alice can send 1 classical bit to Bob:

- If outcome was $\ket{+}$, Bob has $\ket{\psi}$
- If outcome was $\ket{-}$, Bob has $Z\ket{\psi}$ and applies the Pauli $Z$ gate to recover $\ket{\psi}$

Quantum state successfully teleported up to a known unitary!

## Quantum Teleportation — CNOT Step with EPR Pair

### Setup

- Alice has two qubits:
  - Qubit 1: $\ket{\psi} = \alpha\ket{0} + \beta\ket{1}$
  - Qubit 2: her half of an EPR pair
- Bob has:
  - Qubit 3: the other half of the EPR pair

The EPR pair is:

$$
\ket{\Phi^+}_{23} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11})
$$

The full 3-qubit initial state:

$$
\ket{\psi}_1 \otimes \ket{\Phi^+}_{23}
= (\alpha\ket{0}_1 + \beta\ket{1}_1) \otimes \frac{1}{\sqrt{2}}(\ket{00}_{23} + \ket{11}_{23})
$$

Distribute the tensor product:

$$
= \frac{1}{\sqrt{2}} \left(
\alpha\ket{0}_1\ket{00}_{23} + \alpha\ket{0}_1\ket{11}_{23}
+ \beta\ket{1}_1\ket{00}_{23} + \beta\ket{1}_1\ket{11}_{23}
\right)
$$

Simplify:

$$
= \frac{1}{\sqrt{2}} \left(
\alpha\ket{000} + \alpha\ket{011} + \beta\ket{100} + \beta\ket{111}
\right)
$$

### Step: Apply CNOT (Alice's qubit 1 is control, her EPR qubit 2 is target)

CNOT acts on qubits 1 and 2:

- $\ket{00} \to \ket{00}$
- $\ket{01} \to \ket{01}$
- $\ket{10} \to \ket{11}$
- $\ket{11} \to \ket{10}$

Apply to each term:

$$
\alpha\ket{000} \to \alpha\ket{000} \\
\alpha\ket{011} \to \alpha\ket{011} \\
\beta\ket{100} \to \beta\ket{110} \\
\beta\ket{111} \to \beta\ket{101}
$$

Final state after CNOT:

$$
\ket{\Psi}_{123} =
\frac{1}{\sqrt{2}} \left(
\alpha\ket{000} + \alpha\ket{011}
+ \beta\ket{110} + \beta\ket{101}
\right)
$$

This state is now entangled and ready for the **Hadamard gate** on qubit 1 and measurement.

basically 1 entangled bit with 2 classical bits is enough info to describe the state of a qubit

