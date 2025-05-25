#ucsc #cse109 
### Basic fact of Quantum Computing
- Example: given 1000 photons/electrons, their joint "state" is defined by $2^{1000}$ numbers. (amplitudes)
- many-worlds interpretation
### What is Quantum Computation?: Classical + one extra power
- Probabilistic Computing: deterministic computation + (coinflip -> 0 or 1)
- Question: Is probabilistic computing better than classical
	- $A_1$ : "Yes" - it can simulate coin flips (randomness is a propery of particles)
	- $A_2$: (Maybe) Not
- When it comes to just computing functions a probabilistic algorithm it can match classical computing
- There is always error with probabilistic computing (ex. $\frac{1}{2^{1000}}$)
- Summary:
	- It's cool
	- Its's classical + 1 simple power
	- Analyzing it requires new math (probability theory)
	- quintissential use: simulate random
	- Seems to design more efficient algorithms in problems
	- strongly believed doesn't give exponential speedups (e.g. NP hard problems)
- Example: initialize array A[], length 1000
	```
	0<=i<1000  A[i]=coinflip(0/1)
		## Run difficult code  given A[]
	```
-Probabilistic computing seems to give exponential speedups for one problem: factoring (Shor's algorightm)

Example probabilistic program
	- initialize 1000 photons (qubits)
	- run them through obstacle course
	- joint state reqiures $2^{1000}$ numbers to describe

## Understanding and measuring 1 qubit
#### Classical:
- logical bit - either 0 or 1
- pysical bit - low voltage and high voltage
- some reasonably large amount of electrons influence the low/high voltage to convey logical bits
#### Quantum:
- Uses 1 particle that have 2 possibilities (we call them 0/1)
- One example for a particle would be the hydrogen atom - can have spin: up is 0 down is 1, or by the amount of electrons or something
- photon polarization -- horizontal = 0 and vertical = 1
- Quantum Mechanics Law #1: If a particle can be in one of two basic states $\ket{0}$ or $\ket{1}$ it can also be in a superposition state $\alpha$ and $\beta$ are amplitudes on $\ket{0}$ and $\ket{1}$ respectively where $|\alpha|^2+|\beta|^2=1$  -- THIS IS A QUBIT
- e.g. .8 on $\ket{0}$ and .6 on $\ket{1}$ check $.8^2+.6^2=1$
- Quantum Mechanics Law #2: For particle with amplitude (a on 0 and b on 1) If we measure it them
	- with prob a^2 the readout shows 0
	- with prob b^2 the readout shows 1
	AND
	- if readout is 0 particles state changes to 1 on 0 and 1 on 1
- example .8 on 0 .6 on 1 - 64% on 0 36% on 1. afterwards it is 100% 1 on 0

- qubit has 2 states qutrit has 3 and qudit, d=n with n being number of states
- qudit, n=4 for example could just be collections of 2 qubits

you can store state of a qudit in a d dimensional vector with entries being whatever amplitudes there are