#ucsc #cse109 

### Multi-qubit systems
- $\dim 4$ quantum system 
The state  $\ket\psi$ can also be written as a column vector in $\mathbb{C}^4$:
$$
\ket{\psi} = 
\begin{bmatrix}
\frac{1}{2} \\
\frac{i}{2} \\
\frac{-1}{2} \\
\frac{i}{2}
\end{bmatrix}, \quad
\text{with } \braket{\psi|\psi} = 1
$$
- most common way to implement this is 2 2-dimensional quantum systems = 2 qubits
- $$
\ket{\psi} = a_{00} \ket{00} + a_{01} \ket{01} + a_{10} \ket{10} + a_{11} \ket{11}
$$

$$
\ket{00} =
\begin{bmatrix}
1 \\
0 \\
0 \\
0
\end{bmatrix}, \quad
\ket{01} =
\begin{bmatrix}
0 \\
1 \\
0 \\
0
\end{bmatrix}, \quad
\ket{10} =
\begin{bmatrix}
0 \\
0 \\
1 \\
0
\end{bmatrix}, \quad
\ket{11} =
\begin{bmatrix}
0 \\
0 \\
0 \\
1
\end{bmatrix}
$$
#### Q1: What is the joint 4 dim state?
#### Q2: If bob applies unitary U to his qubit, what is the new 4 dim state?
#### Q3: Alice measures her qubit, what happens?

$$
\ket{\psi}_{\text{Alice}} = \alpha_0 \ket{0} + \alpha_1 \ket{1}
$$

$$
\ket{\phi}_{\text{Bob}} = \beta_0 \ket{0} + \beta_1 \ket{1}
$$
Joint system of the two:
$$
\ket{\Psi}_{\text{AB}} = \gamma_{00} \ket{00} + \gamma_{01} \ket{01} + \gamma_{10} \ket{10} + \gamma_{11} \ket{11}
$$
$$
\ket{\Psi}_{\text{AB}} =
\begin{bmatrix}
\gamma_{00} \\
\gamma_{01} \\
\gamma_{10} \\
\gamma_{11}
\end{bmatrix}
= \begin{bmatrix}
\alpha_0 \beta_0 \\
\alpha_0 \beta_1 \\
\alpha_1 \beta_0 \\
\alpha_1 \beta_1
\end{bmatrix}
$$
Given:
$$
\ket{\psi}_{\text{Alice}} = \alpha_0 \ket{0} + \alpha_1 \ket{1}, \quad
\ket{\phi}_{\text{Bob}} = \beta_0 \ket{0} + \beta_1 \ket{1}
$$

Their joint state is:
$$
\ket{\Psi}_{\text{AB}} = \ket{\psi} \otimes \ket{\phi} =
\alpha_0 \beta_0 \ket{00} + \alpha_0 \beta_1 \ket{01} + \alpha_1 \beta_0 \ket{10} + \alpha_1 \beta_1 \ket{11}
$$

So the joint amplitudes are:
$$
\gamma_{00} = \alpha_0 \beta_0, \quad
\gamma_{01} = \alpha_0 \beta_1, \quad
\gamma_{10} = \alpha_1 \beta_0, \quad
\gamma_{11} = \alpha_1 \beta_1
$$

Taking magnitudes squared gives joint probabilities:
$$
|\gamma_{ij}|^2 = |\alpha_i|^2 \cdot |\beta_j|^2
$$

Which shows:
$$
P_{AB}(ij) = P_A(i) \cdot P_B(j)
$$


THE FOLLOWING OPERATION IS CALLED THE TENSOR PRODUCT:
$$
\ket{\psi}_A =
\begin{bmatrix}
\alpha_0 \\
\alpha_1 \\
\vdots \\
\alpha_{d-1}
\end{bmatrix}, \quad
\ket{\phi}_B =
\begin{bmatrix}
\beta_0 \\
\beta_1 \\
\vdots \\
\beta_{e-1}
\end{bmatrix}
$$

$$
\ket{\Psi}_{AB} = \ket{\psi}_A \otimes \ket{\phi}_B =
\begin{bmatrix}
\alpha_0 \beta_0 \\
\alpha_0 \beta_1 \\
\vdots \\
\alpha_0 \beta_{e-1} \\
\alpha_1 \beta_0 \\
\alpha_1 \beta_1 \\
\vdots \\
\alpha_{d-1} \beta_{e-1}
\end{bmatrix}
\in \mathbb{C}^{de}
$$


More generally, tensor products for matricies
Let $A \in \mathbb{C}^{m \times n}$ and $B \in \mathbb{C}^{p \times q}$ .  
The tensor product $A \otimes B \in \mathbb{C}^{mp \times nq}$ is defined as:

$$
A \otimes B =
\begin{bmatrix}
a_{11}B & a_{12}B & \cdots & a_{1n}B \\
a_{21}B & a_{22}B & \cdots & a_{2n}B \\
\vdots  & \vdots  & \ddots & \vdots \\
a_{m1}B & a_{m2}B & \cdots & a_{mn}B
\end{bmatrix}
$$

#### Example:
Start with:
$$
\ket{0} =
\begin{bmatrix}
1 \\
0
\end{bmatrix}
$$

Tensor product:
$$
\ket{0} \otimes \ket{0} =
\begin{bmatrix}
1 \\
0
\end{bmatrix}
\otimes
\begin{bmatrix}
1 \\
0
\end{bmatrix}
=
\begin{bmatrix}
1 \cdot
\begin{bmatrix}
1 \\
0
\end{bmatrix} \\
0 \cdot
\begin{bmatrix}
1 \\
0
\end{bmatrix}
\end{bmatrix}
=
\begin{bmatrix}
1 \\
0 \\
0 \\
0
\end{bmatrix}
$$
#### Another example:
Let:
$$
\ket{0} =
\begin{bmatrix}
1 \\
0
\end{bmatrix}, \quad
\ket{+} =
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1
\end{bmatrix}
$$

Tensor product:
$$
\ket{0} \otimes \ket{+} =
\begin{bmatrix}
1 \\
0
\end{bmatrix}
\otimes
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1
\end{bmatrix}
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \cdot
\begin{bmatrix}
1 \\
1
\end{bmatrix} \\
0 \cdot
\begin{bmatrix}
1 \\
1
\end{bmatrix}
\end{bmatrix}
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1 \\
0 \\
0
\end{bmatrix}
$$
the resulting state is $\ket{0+} = \frac{1}{\sqrt{2}} \left( \ket{00} + \ket{01} \right)$
#### Another Example:
$$
\ket{+} \otimes \ket{0} =
\left( \frac{1}{\sqrt{2}} (\ket{0} + \ket{1}) \right) \otimes \ket{0}
= \frac{1}{\sqrt{2}} (\ket{00} + \ket{10})
$$

#### Another Example:
$$
\ket{+} \otimes \ket{-} =
\left( \frac{1}{\sqrt{2}} (\ket{0} + \ket{1}) \right) \otimes
\left( \frac{1}{\sqrt{2}} (\ket{0} - \ket{1}) \right)
= \frac{1}{2} (\ket{00} - \ket{01} + \ket{10} - \ket{11})
$$

#### Properties of Tensor Products
$$
(A + B) \otimes C = A \otimes C + B \otimes C
$$
$$
A \otimes (B + C) = A \otimes B + A \otimes C
$$
$$
A \otimes (B \otimes C) = (A \otimes B) \otimes C = A \otimes B \otimes C
$$
$$
(A \otimes B)^\dagger = A^\dagger \otimes B^\dagger
$$
$$
(A \otimes B)(C \otimes D) = (AC) \otimes (BD)
$$


## Back to two two-state qubits

```
Alice:  ───●──────  (control qubit)
            │
Bob:    ───X──────  (target qubit)
```



### CNOT Gate (Controlled-NOT)

The **CNOT gate** is a two-qubit gate that flips the **target qubit (Bob)** if the **control qubit (Alice)** is $\ket{1}$, and does nothing if the control is $\ket{0}$.

It acts as:
$$
\text{CNOT}(\ket{a} \otimes \ket{b}) = \ket{a} \otimes \ket{a \oplus b}
$$

Matrix representation:
$$
\text{CNOT} =
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 1 & 0
\end{bmatrix}
$$

Example:
$$
\text{CNOT}(\ket{10}) = \ket{11}, \quad
\text{CNOT}(\ket{11}) = \ket{10}
$$
### CNOT Action on Computational Basis States

$$
\text{CNOT} \ket{00} \rightarrow \ket{00}
$$

$$
\text{CNOT} \ket{01} \rightarrow \ket{01}
$$

$$
\text{CNOT} \ket{10} \rightarrow \ket{11}
$$

$$
\text{CNOT} \ket{11} \rightarrow \ket{10}
$$

The control is the **first qubit** (Alice), and the target is the **second qubit** (Bob). The gate flips Bob’s qubit **only** when Alice’s qubit is $\ket{1}$.


### Bell State Preparation

The **Bell state** is a maximally entangled two-qubit state shared between Alice and Bob. One common way to create the Bell state \( \ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11}) \) involves three steps:

---

#### 1. **Initial State**  
Alice and Bob each start with qubits in the \( \ket{0} \) state:
$$
\ket{\psi_0} = \ket{0}_A \otimes \ket{0}_B = \ket{00}
$$

---

#### 2. **Hadamard Gate on Alice’s Qubit**  
Alice applies a Hadamard gate to her qubit, creating a superposition:
$$
H \ket{0} = \frac{1}{\sqrt{2}} (\ket{0} + \ket{1})
$$
So the state becomes:
$$
\ket{\psi_1} = \left( \frac{1}{\sqrt{2}} (\ket{0} + \ket{1}) \right) \otimes \ket{0}
= \frac{1}{\sqrt{2}} (\ket{00} + \ket{10})
$$

---

#### 3. **CNOT Gate (Alice control, Bob target)**  
Now they apply a CNOT gate, with Alice’s qubit as the control and Bob’s as the target:
$$
\text{CNOT} \left( \frac{1}{\sqrt{2}} (\ket{00} + \ket{10}) \right)
= \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})
$$

---

####  Final State: The Bell State
The resulting entangled state is:
$$
\ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})
$$

This state cannot be written as a product of two individual qubit states — it’s fully entangled. Measuring one qubit instantly determines the other.


## Why is this state interesting?
- "entangled"
- ### Entanglement (Quick Math Description)

Two qubits $\ket{\psi}_{AB} \in \mathbb{C}^2 \otimes \mathbb{C}^2$ are **entangled** if their joint state **cannot** be written as a tensor product of individual states:

$$
\ket{\psi}_{AB} \neq \ket{\phi}_A \otimes \ket{\chi}_B
$$

Example: the Bell state
$$
\ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})
$$
is entangled because there are no \( \ket{\phi}_A \), \( \ket{\chi}_B \) such that
$$
\ket{\Phi^+} = \ket{\phi}_A \otimes \ket{\chi}_B
$$

In contrast, a **separable** (not entangled) state like:
$$
\ket{\psi} = \ket{+} \otimes \ket{0}
= \frac{1}{\sqrt{2}} (\ket{0} + \ket{1}) \otimes \ket{0}
= \frac{1}{\sqrt{2}} (\ket{00} + \ket{10})
$$
is **not** entangled because it's clearly a product of two individual qubit states.


