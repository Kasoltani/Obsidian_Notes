#ucsc #cse109 

#### Partial Measurements and "Spooky action at a distance"
- Recap:
	- Alice and Bob states for qubits
	-  Alice and Bob Qubit Example

		Alice prepares qubit:  
		$$
		\ket{\psi} = \alpha_0 \ket{0} + \alpha_1 \ket{1}
		$$
		
		Bob prepares qubit:  
		$$
		\ket{\phi} = \beta_0 \ket{0} + \beta_1 \ket{1}
		$$
		
		Joint state (tensor product):  
		$$
		\ket{\psi} \otimes \ket{\phi} = (\alpha_0 \ket{0} + \alpha_1 \ket{1}) \otimes (\beta_0 \ket{0} + \beta_1 \ket{1})
		$$
		$$
		= \alpha_0 \beta_0 \ket{00} + \alpha_0 \beta_1 \ket{01} + \alpha_1 \beta_0 \ket{10} + \alpha_1 \beta_1 \ket{11}
		$$
		
		Vector form:  
		$$
		\begin{bmatrix}
		\alpha_0 \beta_0 \\
		\alpha_0 \beta_1 \\
		\alpha_1 \beta_0 \\
		\alpha_1 \beta_1
		\end{bmatrix}
		$$
		
		# CNOT Gate
		
		CNOT (Controlled-NOT):  
		- Control qubit stays the same.
		- If control is $$\ket{1}$$, the target qubit flips.
		
		Effect on basis states:  
		$$
		\ket{00} \rightarrow \ket{00} \\
		\ket{01} \rightarrow \ket{01} \\
		\ket{10} \rightarrow \ket{11} \\
		\ket{11} \rightarrow \ket{10}
		$$
		
		# SWAP Gate
		
		SWAP gate:  
		- Swaps the two qubits.
		
		Effect on basis states:  
		$$
		\ket{00} \rightarrow \ket{00} \\
		\ket{01} \rightarrow \ket{10} \\
		\ket{10} \rightarrow \ket{01} \\
		\ket{11} \rightarrow \ket{11}
		$$

#### Applying CNOT, SWAP, then Unitary Operations
- Initial joint state:  
	$$
	\ket{\psi} \otimes \ket{\phi}
	$$
	After CNOT gate:  
	$$
	\text{CNOT} \big( \ket{\psi} \otimes \ket{\phi} \big)
	$$
	After SWAP gate:  
	$$
	\text{SWAP} \big( \text{CNOT} \big( \ket{\psi} \otimes \ket{\phi} \big) \big)
	$$
	Call this resulting state $$\ket{\nu}$$
	$$
	\ket{\nu} = \text{SWAP} \big( \text{CNOT} \big( \ket{\psi} \otimes \ket{\phi} \big) \big)
	$$
	Now, apply unitary operations:
	- Bob applies $$U$$ to his qubit.
	- Alice applies $$V$$ to her qubit.
	The final state becomes:  
	$$
	(V \otimes U) \ket{\nu}
	$$

- important phrase "extend by linearity"
- what about measurement: they are $\textbf{NOT}$ just a linear transformation

# Joint State and Alice's Measurement Probability

Joint state:  
$|\Psi\rangle = a_{00} |00\rangle + a_{01} |01\rangle + a_{10} |10\rangle + a_{11} |11\rangle$

First qubit belongs to Alice, second to Bob.

If Alice measures her qubit to be $|0\rangle$, the probability is:  
$\text{P}(0) = |a_{00}|^2 + |a_{01}|^2$

**Explanation:**  
We sum the squared amplitudes of all terms where Alice's qubit is $|0\rangle$ (first index is 0). So we include both $a_{00}$ and $a_{01}$.

After measurement result $|0\rangle$, the state collapses to:  
$|\Psi'\rangle = \frac{1}{\sqrt{\text{P}(0)}} \left( a_{00} |00\rangle + a_{01} |01\rangle \right)$

If we know $p_0$ we can find the probability of 1 with $1-p_0$ 

- NOT IMPORTANT FOR TESTS BUT GOOD FOR TEXTBOOK: 
	- Mixed states - "classical" probability distributions over "pure" quantum states

# Measurement of Alice's Qubit with Outer Product Form

Joint state:  
$|\Psi\rangle = a_{00} |00\rangle + a_{01} |01\rangle + a_{10} |10\rangle + a_{11} |11\rangle$

First qubit = Alice, second = Bob.

---

**If Alice measures $|0\rangle$:**

Probability:  
$P(0) = |a_{00}|^2 + |a_{01}|^2$

Post-measurement state:  
$|\Psi_0\rangle = |0\rangle \otimes \left( \frac{a_{00}}{\sqrt{P(0)}} |0\rangle + \frac{a_{01}}{\sqrt{P(0)}} |1\rangle \right)$

---

**If Alice measures $|1\rangle$:**

Probability:  
$P(1) = |a_{10}|^2 + |a_{11}|^2$

Post-measurement state:  
$|\Psi_1\rangle = |1\rangle \otimes \left( \frac{a_{10}}{\sqrt{P(1)}} |0\rangle + \frac{a_{11}}{\sqrt{P(1)}} |1\rangle \right)$

Now bobs photon goes into 1 qubit measuring device
# Bob's State After Alice's Measurement

Given joint state:  
$|\Psi\rangle = a_{00} |00\rangle + a_{01} |01\rangle + a_{10} |10\rangle + a_{11} |11\rangle$

---

**If Alice measures $|0\rangle$:**

Probability:  
$P(0) = |a_{00}|^2 + |a_{01}|^2$

Bob’s post-measurement state:  
$\displaystyle |\phi_0\rangle = \frac{a_{00}}{\sqrt{P(0)}} |0\rangle + \frac{a_{01}}{\sqrt{P(0)}} |1\rangle$

---

**If Alice measures $|1\rangle$:**

Probability:  
$P(1) = |a_{10}|^2 + |a_{11}|^2$

Bob’s post-measurement state:  
$\displaystyle |\phi_1\rangle = \frac{a_{10}}{\sqrt{P(1)}} |0\rangle + \frac{a_{11}}{\sqrt{P(1)}} |1\rangle$

# Why $a_{00} / |a_{00}| \, |0\rangle |0\rangle$ Appears

If the joint state is:
$|\Psi\rangle = a_{00} |00\rangle + a_{01} |01\rangle + a_{10} |10\rangle + a_{11} |11\rangle$

Then suppose all other amplitudes are zero or Alice’s measurement collapses to a specific component — say, only $a_{00}$ survives.

The state becomes:  
$|\Psi'\rangle = \frac{1}{|a_{00}|} a_{00} |00\rangle = \frac{a_{00}}{|a_{00}|} |00\rangle$

Here, $a_{00}/|a_{00}|$ is a **global phase** (a complex number of magnitude 1), which doesn't affect measurement outcomes.

**So:** the professor is emphasizing that **if only $a_{00}$ remains**, then the state is **$|0\rangle \otimes |0\rangle$ up to a global phase**, written as $a_{00}/|a_{00}| \, |00\rangle$.


#### Partial Measurement (Quantum Mechanics Law #6)
# Qutrit Measurement Collapse (Law #6)

Alice and Bob share a joint qutrit state:
$$
|\Psi\rangle = \sum_{i,j=0}^{2} a_{ij} \, |i\rangle \otimes |j\rangle
$$

That is:
$$
|\Psi\rangle = a_{00}|00\rangle + a_{01}|01\rangle + \dots + a_{22}|22\rangle
$$

Suppose Bob measures his qutrit and gets outcome $|1\rangle$.

The state collapses to only those components where Bob’s side is $|1\rangle$:
$$
|\Psi'\rangle = \frac{1}{\sqrt{P(1)}} \left( a_{01}|01\rangle + a_{11}|11\rangle + a_{21}|21\rangle \right)
$$

Where the probability of getting result $1$ is:
$$
P(1) = |a_{01}|^2 + |a_{11}|^2 + |a_{21}|^2
$$
Then the state collapses to:
$$
|\Psi'\rangle = \frac{1}{\sqrt{q_1}} \left( a_{01}|01\rangle + a_{11}|11\rangle + a_{21}|21\rangle \right)
$$
This is **Law #6**: measurement causes collapse to a normalized subspace consistent with the observed outcome.

# 3-Qubit State: Measuring First Two Qubits as $|00\rangle$

Start with:
$$
|\Psi\rangle = a_{000}|000\rangle + a_{001}|001\rangle + a_{010}|010\rangle + a_{011}|011\rangle \\
\phantom{|\Psi\rangle = } + a_{100}|100\rangle + a_{101}|101\rangle + a_{110}|110\rangle + a_{111}|111\rangle
$$

Now measure the **first two qubits**, and the outcome is $|00\rangle$.

Only the $|000\rangle$ and $|001\rangle$ terms survive. Let:
$$
p_{00} = |a_{000}|^2 + |a_{001}|^2
$$

Then the post-measurement (normalized) state is:
$$
|\Psi'\rangle = \frac{1}{\sqrt{p_{00}}} \left( a_{000}|000\rangle + a_{001}|001\rangle \right)
$$

This is the system collapsed to the subspace where the first two qubits are $|00\rangle$, and the third qubit is left in a superposition.


# Alice and Bob Prepare an EPR Pair

Alice and Bob prepare the entangled Bell state:
$$
|\Phi^+\rangle = \frac{1}{\sqrt{2}} \left( |00\rangle + |11\rangle \right)
$$

This is called an **EPR pair**. It means:
- If Alice measures $|0\rangle$, Bob will also get $|0\rangle$
- If Alice measures $|1\rangle$, Bob will also get $|1\rangle$
- Neither qubit has a definite value until measurement — but outcomes are always correlated

Alice holds the first qubit, Bob holds the second.

Alice now goes to the moon and measures her qubit.
- 50% percent chance of 0 and 50% chance of 1.
Bobs state will instantaneously collapse to 0 or 1 depending on what alice measures.

#### What if Alice measures in some other basis?
- example: the $\ket+$ $\ket-$
- Two ways to do this
- 1. Rewrite state in that basis, use "usual rule"
- 2. simulate a unitary or standard basis measurements
-------------------------------------------
# EPR with Hadamard–Measurement–Hadamard on Alice

Start in the EPR pair:  
$$
|\Phi^+\rangle = \frac{1}{\sqrt{2}} \left( |00\rangle + |11\rangle \right)
$$

---

**1. Apply Hadamard to Alice’s qubit** (only the first qubit):

Use:  
$H|0\rangle = \frac{1}{\sqrt{2}} (|0\rangle + |1\rangle)$  
$H|1\rangle = \frac{1}{\sqrt{2}} (|0\rangle - |1\rangle)$

So:  
$$
(H \otimes I) |\Phi^+\rangle = \frac{1}{\sqrt{2}} \left( H|0\rangle \otimes |0\rangle + H|1\rangle \otimes |1\rangle \right)
$$

Substitute:  
$$
= \frac{1}{\sqrt{2}} \left( \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \otimes |0\rangle + \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle) \otimes |1\rangle \right)
$$

Simplify:  
$$
= \frac{1}{2} \left( |00\rangle + |10\rangle + |01\rangle - |11\rangle \right)
$$

---

**2. Measure Alice in standard basis** ($|0\rangle$, $|1\rangle$)

- If result is $|0\rangle$:  
  Surviving terms: $|00\rangle + |01\rangle$  
  Normalize:  
  $|\psi_0\rangle = \frac{1}{\sqrt{2}} \left( |00\rangle + |01\rangle \right)$

- If result is $|1\rangle$:  
  Surviving terms: $|10\rangle - |11\rangle$  
  Normalize:  
  $|\psi_1\rangle = \frac{1}{\sqrt{2}} \left( |10\rangle - |11\rangle \right)$

---

**3. Apply Hadamard again to Alice’s qubit**

Use:  
$H|0\rangle = \frac{1}{\sqrt{2}} (|0\rangle + |1\rangle)$  
$H|1\rangle = \frac{1}{\sqrt{2}} (|0\rangle - |1\rangle)$

---

If Alice measured $|0\rangle$:
$$
|\psi_0\rangle = \frac{1}{\sqrt{2}} (|00\rangle + |01\rangle) \\
\Rightarrow (H \otimes I)|\psi_0\rangle = \frac{1}{\sqrt{2}} \left( H|0\rangle \otimes |0\rangle + H|0\rangle \otimes |1\rangle \right) \\
= \frac{1}{\sqrt{2}} \left( \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \otimes |0\rangle + \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \otimes |1\rangle \right) \\
= \frac{1}{2} \left( |00\rangle + |01\rangle + |10\rangle + |11\rangle \right)
$$

If Alice measured $|1\rangle$:
$$
|\psi_1\rangle = \frac{1}{\sqrt{2}} (|10\rangle - |11\rangle) \\
\Rightarrow (H \otimes I)|\psi_1\rangle = \frac{1}{\sqrt{2}} \left( H|1\rangle \otimes |0\rangle - H|1\rangle \otimes |1\rangle \right) \\
= \frac{1}{\sqrt{2}} \left( \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle) \otimes |0\rangle - \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle) \otimes |1\rangle \right) \\
= \frac{1}{2} \left( |00\rangle - |01\rangle - |10\rangle + |11\rangle \right)
$$
