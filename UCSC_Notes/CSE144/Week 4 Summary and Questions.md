#ucsc #CSE144
**Reading 8.1: Backpropogation**

Our goal is to find an efficient technique for evaluating the gradient $E(w)$ for a feed-forward neural network. The algorithm for a general network having arbitrary feedforward topology with differentiable non-linear activation functions and a broad class of error functions is as follows:
$$
E(w)=\sum_{n=1}^{N}E_n(w) 
$$

**General feed-forward networks**

In general a feed-forward network consists of a set of units that is used to compute a weighted sum of its inputs.
$$
a_j=\sum_iw_{ji}z_i
$$
Where $z_i$ is either an activation of a unit or input unit that sends connection to unit j and $w_{ji}$ is the weight of that connection. This sum is known as *pre-activation*, which is transformed by an activation function $h()$ to give the activation $z_j$ of unit j
$$
z_j=h(a_j)
$$
This process is called *forward propagation*. Now consider the derivative of $E_n$ with respect to $w_{ji}$. 
$$
\frac{\partial{E_n}}{\partial{w_{ji}}}=\frac{\partial{E_n}}{\partial{a_j}}\frac{\partial{a_j}}{\partial{w_{ji}}}
$$
Which can also be written with the notation
$$
\delta_j=\frac{\partial{E_n}}{\partial{a_j}}
$$
Using the general form of the equation we can now write
$$
\frac{\partial{a_j}}{\partial{w_{ji}}}=z_i
$$
After substituting we need to calculate the only value of $\delta_j$ for each hidden and output unit. The sum needs to run from all units $k$ to the unit $j$ that sends the connection. Then we end with the following *backpropagation* formula
$$
\delta_j=h'(a_j)\sum_kw_{kj}\delta_k
$$


