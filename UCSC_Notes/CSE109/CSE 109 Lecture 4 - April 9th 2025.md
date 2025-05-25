##### Notation
$\ket{v}$ "ket" $\begin{bmatrix}v_1 \\\vdots \\v_n\end{bmatrix}$
$\bra{v}$ "bra" $\begin{bmatrix} v_1 & \cdots & v_n \end{bmatrix}$

$\langle v|u \rangle$ "Bracket"

##### Example qubit:

$\ket{+} = \frac{1}{\sqrt{2}} \ket{0} + \frac{1}{\sqrt{2}} \ket{1}, \quad \ket{-} = \frac{1}{\sqrt{2}} \ket{0} - \frac{1}{\sqrt{2}} \ket{1}$




$R_\theta = \begin{bmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{bmatrix}$
First column in where $\ket{0}$ goes and second is where $\ket{1}$ goes. Used for rotation of basis.

$\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}$
Not gate

$\begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \end{bmatrix}$
This is the Hadamard gate—a key quantum gate that puts $\ket{0}$ into $\ket{+}$ and $\ket{1}$ into $\ket{-}$

$\begin{bmatrix} 1 & 0 \\ 0 & i \end{bmatrix}$
This matrix is the phase gate (also known as the S gate in quantum computing). It adds a phase of $\frac{\pi}{2}$ (i.e., multiplies by $i$) to the $\ket{1}$ state.

### Quantum Mechanics Law 3:
A qudit state can be changed by any linear transformation that preserves lengths. "Unitary Matrices"

$\text{If } \hat{A} \ket{a} = a \ket{a}, \text{ then } P(a) = |\langle a | \psi \rangle|^2, \text{ and } \ket{\psi} \rightarrow \ket{a} \text{ after measurement.}$

