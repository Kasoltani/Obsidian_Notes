#ucsc #cse109  
## Quantum Computing Basics

### Classical Computing — "Circuit Model"
- Classical circuit: input (bits), gates, outputs
- Computes a function: $F: \{0,1\}^n \to \{0,1\}^m$
- Efficiency: number of gates vs. input size $n$
- Gates $\sim \frac{\text{steps}}{\text{time}}$
- If Python code computes $f$ on inputs of length $n$ in $T$ steps, can build a circuit computing $F$ with $\mathcal{O}(T \log T)$ gates

> [!example] Classical AND Gate
> $$
> \text{Input: } (x, y) \quad \xrightarrow{\text{AND}} \quad x \land y
> $$

---

### Probabilistic Computing
- Add **FLIP** gate: no input, outputs 0 or 1, each with probability $\frac{1}{2}$

> [!example] Probabilistic FLIP Gate
> $$
> \text{Input: } \varnothing \quad \xrightarrow{\text{FLIP}} \quad 
> \begin{cases}
> 0 \quad (50\%) \\
> 1 \quad (50\%)
> \end{cases}
> $$

---

### Quantum Computing
- Inputs: qubits (superpositions), set of quantum gates
- Measurement produces classical outputs
- Computes a function: $F: \{0,1\}^n \to \{0,1\}^m$
- Correct with probability at least 99.9%
- Circuit evolves quantum mechanically until measurement collapses state

> [!example] Quantum Hadamard (H) Gate
> $$
> H|0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \\
> H|1\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)
> $$

---

### Questions
> [!question] Q1: Classical Supremacy
> Is there a function $F$ that quantum computers can compute much more efficiently than classical computers?

> [!question] Q2: Reverse question
> Is quantum computing at least as powerful as classical?

> [!question] Q3
> Does the exact set of quantum gates matter?

## QC $\geq$ Classical Computer?

- Quantum computers evolve via **unitary operations**, meaning they are **reversible**:  
  $$
  UU^\dagger = U^\dagger U = I \quad \text{(where } U^\dagger = U^{-1} \text{)}
  $$
- Classical (irreversible) circuits **discard information**, leading to **energy dissipation** (Landauer's Principle).
- Quantum computers, as **closed systems**, avoid this energy loss by preserving information.
- **Reversible classical computing** was studied in the 1960s–70s (notably by Rolf Landauer, Charles Bennett).
- Reversible gates allow classical computation without fundamental energy loss (in theory).

> [!example] Reversible Classical Gate: Fredkin (CSWAP) Gate
> - 3 inputs: control bit $c$, data bits $x$, $y$
> - 3 outputs:
> $$
> (c, x, y) \mapsto
> \begin{cases}
> (c, x, y) & \text{if } c = 0 \\
> (c, y, x) & \text{if } c = 1
> \end{cases}
> $$
> - Swaps $x$ and $y$ if $c=1$, otherwise leaves them unchanged.

---

> [!note] Why Reversibility Matters
> Reversible computing preserves information, which is crucial for thermodynamic efficiency — minimizing entropy increase and heat production.

### Simulating AND Gate with Fredkin (CSWAP)

Fix inputs:
- Control: $c = x$
- Data 1: $x = y$
- Data 2: $y = 0$

Third output = $x \land y$

> [!example] Fredkin gate simulating AND
> $$
> (x, y, 0) \quad \xrightarrow{\text{Fredkin}} \quad (x, \text{---}, x \land y)
> $$

---
> [!abstract] Diagram
> Fredkin Gate as AND (CSWAP)
> ```
> Inputs              Outputs
> ────────────────────────────────
> x ──●──────────────────────── x
>      │
> y ───┼───○── y′   (if x=0: y; if x=1: 0)
>      │   │
> 0 ───┘   ○── z    (z = x ∧ y)
> ```

---
### Fanout Gate

- Fanout copies a classical bit to two outputs.
- **Not possible** in quantum computing (no-cloning theorem).
- Allowed in classical and reversible classical computing.

> [!abstract] Diagram
> Fanout Gate
> ```
> Input                Outputs
> ─────────────────────────────────
> x ──●───────┬──────── x (copy 1)
>             └──────── x (copy 2)
> ```

---

> [!note] Why no Fanout in Quantum Computing?
> Quantum states cannot be copied arbitrarily because of the **No-Cloning Theorem**:  
> It is impossible to create an identical copy of an unknown quantum state.


### Classical Circuits → Reversible (Quantum) Circuits

Thus:  
Any classical circuit $C$ computing a function $F$ can be efficiently converted into a reversible (hence quantum) circuit.

- Inputs: original bits + ancilla bits ($a$)
- Outputs: desired outputs + garbage bits ($g$)

> [!abstract] Input-Output Relation
> $$
> (\text{Input bits}) + (\text{Ancilla } a) \quad \longrightarrow \quad (\text{Output bits}) + (\text{Garbage } g)
> $$

---

> [!note] Efficiency
> The reversible circuit can compute $F$ with only a modest overhead compared to the original classical circuit.

---
### Reversible Computation and Garbage

We can classically compute the product $P \times Q$ using a circuit.  
To make it **reversible**:
- Build a reversible version of the multiplication circuit.
- Then **reverse** the computation to clean up ancilla/garbage bits.

Problem: **Garbage** bits accumulate during reversible computation.

---

#### Uncomputing Garbage [Bennett 1980]

- After computing the output, **copy** the desired result to a clean register.
- **Run the circuit backward** to erase intermediate garbage, leaving only the output.

> [!abstract] Uncompute Process
> $$
> \text{Initial: } (P, Q, 0) \quad \longrightarrow \quad (P, Q, P \times Q, g)
> $$
> Copy $P \times Q$ to a fresh register → $(P, Q, P \times Q, P \times Q, g)$  
> Reverse circuit → $(P, Q, 0, P \times Q, 0)$

---

> [!note] Key Idea
> By reversing the computation, we clean up garbage without disturbing the desired output.

### Quantum Computation with Ancilla and Output

Start with input $\ket{x}$, ancilla qubits $\ket{0}^a$, and an output register.

---

#### Case 1: Output register initialized to $\ket{0}$

> [!abstract] Setup
> $$
> \ket{x} \otimes \ket{0}^a \otimes \ket{0}
> $$

Apply unitary $U$:

> [!abstract] After computation
> $$
> U \left( \ket{x} \otimes \ket{0}^a \otimes \ket{0} \right) = \ket{x} \otimes \ket{g(x)} \otimes \ket{f(x)}
> $$

- $g(x)$ = garbage
- $f(x)$ = desired output

---

#### Case 2: Output register initialized to $\ket{y}$

> [!abstract] Setup
> $$
> \ket{x} \otimes \ket{0}^a \otimes \ket{y}
> $$

Apply unitary $U$:

> [!abstract] After computation
> $$
> U \left( \ket{x} \otimes \ket{0}^a \otimes \ket{y} \right) = \ket{x} \otimes \ket{g(x)} \otimes \ket{y \oplus f(x)}
> $$

- Output is $y$ modified by $f(x)$ via bitwise addition (XOR if binary).

---

> [!note] Key
> - $\ket{0}$: clean fresh output register.
> - $\ket{y}$: allows accumulation or updating an existing value.

A quantum circuit implements a function F if it computes it in the above garbage-free manner.



