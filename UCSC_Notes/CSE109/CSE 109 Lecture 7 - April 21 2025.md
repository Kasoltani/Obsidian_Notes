#ucsc #cse109 

#### Using method 1 From last Notes to find probability of EPR pair
## EPR Pair in $+/-$ Basis

Let  
$$\ket{\Phi^+} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11})$$

Use:  
$\ket{0} = \frac{1}{\sqrt{2}}(\ket{+} + \ket{-})$,  
$\ket{1} = \frac{1}{\sqrt{2}}(\ket{+} - \ket{-})$

Then:  
$$
\ket{00} = \frac{1}{2}(\ket{++} + \ket{+-} + \ket{-+} + \ket{--})
$$
$$
\ket{11} = \frac{1}{2}(\ket{++} - \ket{+-} - \ket{-+} + \ket{--})
$$

So:  
$$
\ket{\Phi^+} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11}) = \frac{1}{\sqrt{2}}(\ket{++} + \ket{--})
$$

## CHSH Game Setup

Alice and Bob share the entangled state:  
$$\ket{\Phi^+} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11})$$

Alice is on Mars, Bob is on Jupiter. They cannot communicate once the game begins.

### Measurement Choices

- Alice chooses between:
  - $x = 0$: measure in the $\ket{+}, \ket{-}$ basis  
    ($\ket{+} = \frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$,  
     $\ket{-} = \frac{1}{\sqrt{2}}(\ket{0} - \ket{1})$)
  - $x = 1$: measure in the computational basis $\{\ket{0}, \ket{1}\}$

- Bob chooses between:
  - $y = 0$: measure in basis rotated by $\alpha_0 = \frac{\pi}{8}$  
  - $y = 1$: measure in basis rotated by $\alpha_1 = -\frac{\pi}{8}$

Bob's measurement basis vectors are:  
For $y = 0$:  
$$
\ket{b_0^0} = \cos\left(\frac{\pi}{8}\right)\ket{0} + \sin\left(\frac{\pi}{8}\right)\ket{1}, \quad
\ket{b_1^0} = \sin\left(\frac{\pi}{8}\right)\ket{0} - \cos\left(\frac{\pi}{8}\right)\ket{1}
$$

For $y = 1$:  
$$
\ket{b_0^1} = \cos\left(-\frac{\pi}{8}\right)\ket{0} + \sin\left(-\frac{\pi}{8}\right)\ket{1}, \quad
\ket{b_1^1} = \sin\left(-\frac{\pi}{8}\right)\ket{0} - \cos\left(-\frac{\pi}{8}\right)\ket{1}
$$

## CHSH Game: Quantum Win Probability

Alice and Bob share the entangled state:  
$$\ket{\Phi^+} = \frac{1}{\sqrt{2}}(\ket{00} + \ket{11})$$

They are given random inputs:
- Alice receives $x \in \{0,1\}$
- Bob receives $y \in \{0,1\}$  
Each pair $(x, y)$ occurs with probability $\frac{1}{4}$

They win if:
$$a \oplus b = x \cdot y$$

---

## Quantum Strategy

- Alice:
  - $x = 0$: measure in $A_0 = \ket{+}, \ket{-}$
  - $x = 1$: measure in $A_1 = \ket{0}, \ket{1}$

- Bob:
  - $y = 0$: measure in $B_0$, rotated by $\theta = \frac{\pi}{8}$
  - $y = 1$: measure in $B_1$, rotated by $-\theta = -\frac{\pi}{8}$

---

## Probability of Winning

We compute $\Pr[\text{win}]$ as:
$$
\Pr[\text{win}] = \frac{1}{4} \sum_{x,y} \Pr[a \oplus b = x \cdot y \mid x, y]
$$

From quantum mechanics, we use:
- When $x = 0$ and $y = 0$: correlation angle is $\theta = \frac{\pi}{8}$  
- When $x = 0$ and $y = 1$: correlation angle is $\theta = \frac{3\pi}{8}$  
- When $x = 1$ and $y = 0$: correlation angle is $\theta = \frac{\pi}{8}$  
- When $x = 1$ and $y = 1$: correlation angle is $\theta = \frac{3\pi}{8}$

Quantum probability of matching outputs:
$$
\Pr[a = b] = \cos^2\left(\frac{\theta}{2}\right)
$$
$$
\Pr[a \ne b] = \sin^2\left(\frac{\theta}{2}\right)
$$

Apply win condition $a \oplus b = x \cdot y$:

- If $x \cdot y = 0$: we want $a = b$ → use $\cos^2(\theta/2)$  
- If $x \cdot y = 1$: we want $a \ne b$ → use $\sin^2(\theta/2)$

So:
$$
\Pr[\text{win}] = \frac{1}{4} \left[
2 \cdot \cos^2\left(\frac{\pi}{8}\right) +
\cos^2\left(\frac{3\pi}{8}\right) +
\sin^2\left(\frac{3\pi}{8}\right)
\right]
$$

Simplify:
$$
\cos^2\left(\frac{\pi}{8}\right) \approx 0.85,\quad
\cos^2\left(\frac{3\pi}{8}\right) \approx 0.15,\quad
\sin^2\left(\frac{3\pi}{8}\right) \approx 0.85
$$

Final:
$$
\Pr[\text{win}] \approx \frac{1}{4}(2 \cdot 0.85 + 0.15 + 0.85) = \frac{1}{4}(2.7) = 0.675
$$

## Result

Quantum max win probability:  
$$\boxed{\Pr[\text{win}] = \cos^2\left(\frac{\pi}{8}\right) \approx 0.85}$$  
Classical max is $0.75$ → quantum advantage proven.

## Classical CHSH Win Probability

Alice and Bob receive random inputs:
- $x \in \{0,1\}$ to Alice
- $y \in \{0,1\}$ to Bob  
They must output $a, b \in \{0,1\}$ without communication.

**Win condition:**  
$$a \oplus b = x \cdot y$$

They must pre-agree on a deterministic strategy: functions $a(x), b(y)$.

---

### Deterministic Strategies

There are $2^2 = 4$ possible functions for Alice (since $x$ has 2 values), and the same for Bob.

Try any strategy, e.g.:

- Alice always outputs $a(x) = 0$
- Bob always outputs $b(y) = 0$

Then:
- $x = 0, y = 0$: $a \oplus b = 0$, win (target: $0 \cdot 0 = 0$)
- $x = 0, y = 1$: $a \oplus b = 0$, win (target: $0$)
- $x = 1, y = 0$: $a \oplus b = 0$, win (target: $0$)
- $x = 1, y = 1$: $a \oplus b = 0$, lose (target: $1$)

This wins in 3 out of 4 cases → success rate = $75\%$

---

### Why 75% is Max

Every deterministic classical strategy fails on **at least one** of the four $(x, y)$ input pairs.

Since inputs are uniform, this gives:
$$\Pr[\text{win}] \leq \frac{3}{4} = 0.75$$

Randomized strategies are convex combinations of deterministic ones → still $\leq 0.75$.

---

## Classical Limit

$$
\boxed{\Pr[\text{win}] \leq 0.75 \text{ for all classical strategies}}
$$

Quantum strategy exceeds this → proves violation of Bell inequality.


