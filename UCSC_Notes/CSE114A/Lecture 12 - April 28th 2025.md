#ucsc #CSE114A 

```haskell
{-# LANGUAGE BangPatterns #-}

  

-- Normal Recursion

len :: [a] -> Int

len [] = 0

len (_:xs) = len xs + 1

  

--Tail Recursion Helper

len' :: [a] -> Int

len' ls = len'' ls 0

--Tail Recursion Helper

len'' :: [a] -> Int -> Int

len'' [] !acc = acc

len'' (_:rest) !acc = len' rest (acc+1)

  

-- Here's an example where it's good:

-- Take a list and return the fifth element

-- No matter how big of a list we call this with it will be fast

fifth :: [a] -> a

fifth (_:_:_:_:x:_) = x

fifth _ = error "no fifth element"

  
  

{-

Because of lazy evaluation the tail recursion len function len'

len' [1, 2, 3, 4, 5] 0

= len' [2, 3, 4, 5] (0 + 1)

= len' [3, 4, 5] ((0 + 1) + 1)

= len' [3, 4, 5] (((0 + 1) + 1) + 1)

= len' [3, 4, 5] ((0 + 1) + 1)

and so on

  

The accumulator argument is evaluated lazily, this obciates the benefits of tail recursion.

What to do? -- Make the accumulator argument evaluated strictly

{-# LANGUAGE BangPatterns #-}

-}

  
  
  

-- The Maybe type

data Maybe a = Nothing | Just a

  

-- 'Maybe' in Haskell is the same as Option in Rust

  

-- Functions that take function as arguments

  

-- Take a predicate and an argument and apply

-- the predicate to the argument, returning the result

applyPredicate :: (a -> Bool) -> a -> Bool

applyPredicate pred a = pred a
```
