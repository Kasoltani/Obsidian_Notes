#ucsc #CSE114A

- what is PL?
- intro to lambda calculus

#### What do PL people do?:
- consider the **programming language** to have a central place in solving computing problems
- consider software behavior in a rigorous and general way

#### Lambda Calculus
- everything is a function
- invented in 1936 (Alonzo Church) -- (Same year as Turing machines)
The simplest function: **The Identity Function** -- $\lambda x.x$
	$\lambda x$ - binder
	$x$ (next to $\lambda$) - formal parameter
	$.$ - delimiter
	$x$ - function body
\x -> x (Elsa Syntax)
lambda x : x (python)
**Python Function:**
```
def identity(x):
	return x
```

$\lambda z.(\lambda x.x)$ or $\textbackslash z->(\textbackslash x->x)$

**Calling Functions**
```
>identity(3)
3
```

```
>(lambda x:x)(3)
3
```

in lambda calculus, we don't put parenthesis arouund the argument in a function call
$$\textbackslash x\;-> x\;rainbow$$
This is a function whose body is x "rainbow"

A function that takes a function f and applies it to the identity function
```haskell
\f -> f (\x -> x)
```

```haskell
(\f -> f (\x -> x)) \y -> y
```

'\y -> y' - argument
'(\f -> f (\x -> x))' - function were calling

Plug in the argument in place of occurrences of the formal parameter in the function body

We get:
```haskell
(\y -> y)(\x -> x)
```
Steps to: \x -> x

The substitution rule ($\beta$-rule):$$(\textbackslash x \rightarrow e_1)\ e_2 \rightarrow_B e_1[x := e_2]$$$e_1$ but with occurrences of $x$ replaced by $e_2$

Another example:
$\textbackslash x \rightarrow (\textbackslash y \rightarrow x)$
$\textbackslash x \rightarrow (\textbackslash y \rightarrow x)5$
$\rightarrow_B \textbackslash y \rightarrow 5$
