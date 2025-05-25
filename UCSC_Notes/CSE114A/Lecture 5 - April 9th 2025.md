#ucsc #CSE114A 

-adding numbers
-variable scope
-free and bound variables
-computing a set of free variables of an expression
-revisiting the B-rule
-if time: capture-avoiding substitution

### Variable Scope
A binding is an association of a name to some entity
The scope of a binding in a program is the part of the program where the name can be used to refer to the entity
```haskell
\x->e
```
e would be the scope of the binding from the formal parameter x to whatever argument is passed to this function when it's called

we say that any occurrence of x in e is bound by \x
An occurrence of a variable is free if it's not bound.


