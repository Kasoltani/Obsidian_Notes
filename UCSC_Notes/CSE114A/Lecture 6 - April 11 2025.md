#ucsc #CSE114A 

#### Agenda
- capture-avoiding substitution
- encoding pairs in lambda calculus

#### Example of Capture-Avoiding Substitution
```haskell
(\x -> (\y -> x))y

-- This beta reduction would be wrong
=b> \y -> y
```

We would need an $\alpha$-step, which renames a lambda function.

```haskell
(\x -> (\y -> x))y
-- Alpha step: rename lambda y to anything. These two statements are Alpha equivalent
=a> (\x -> (\z -> x))y
=b> \z -> y
```


#### Encoding Pairs (two-element tuples)
- What do we want to do with pairs?
	- Access the first element
	- Access the second element
	- take two things and construct a pair

this unfinished look at april 11th video
```haskell
let TRUE = \x y -> x
let FALSE = \x y -> y
-- ITE = if then else
let ITE = \b x y -> b x y


let PAIR = \x y -> ...
let FST = \p -> ...
let SND = \p -> ...
```
