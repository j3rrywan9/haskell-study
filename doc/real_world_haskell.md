# Real World Haskell

## Chapter 1

### Your Haskell environment

### First steps with types

Haskell requires type names to start with an uppercase letter, and variable names must start with a lowercase letter.

## Chapter 2

### Haskell's type system

There are three interesting aspects to types in Haskell: they are *strong*, they are *static*, and they can be automatically *inferred*.

#### Strong types

When we say that Haskell has a strong type system, we mean that the type system guarantees that a program cannot contain certain kinds of errors.
These errors come from trying to write expressions that don't make sense, such as using an integer as a function.

Another aspect of Haskell's view of strong typing is that it will not automatically coerce values from one type to another. (Coercion is also known as casting or conversion.)

The huge benefit of strong typing is that it catches real bugs in our code before they can cause problems.

#### Static types

Having a static type system means that the compiler knows the type of every value and expression at compile time, before any code is executed.
A Haskell compiler or interpreter will detect when we try to use expressions whose types don't match, and reject our code with an error message before we run it.

### Some common basic types

When we write a type explicitly, we use the notation `expression :: MyType` to say that `expression` has the type `MyType`.
If we omit the `::` and the type that follows, a Haskell compiler will infer the type of the expression.

The combination of `::` and the type after it is called a *type signature*.

### Function application

To apply a function in Haskell, we write the name of the function followed by its arguments.

We don't use parentheses or commas to group or separate the arguments to a function; merely writing the name of the function, followed by each argument in turn, is enough.

Function application has higher precedence than using operators, so the following two expressions have the same meaning.
```haskell
(compare 2 3) == LT

compare 2 3 == LT
```

### Useful composite data types: lists and tuples

A composite data type is constructed from other types.
The most common composite data types in Haskell are lists and tuples.

The `head` function returns the first element of a list.

Its counterpart, `tail`, returns all *but* the head of a list.

A tuple is a fixed-size collection of values, where each value can have a different type.
This distinguishes them from a list, which can have any length, but whose elements must all have the same type.

We write a tuple by enclosing its elements in parentheses and separating them with commas.
We use the same notation for writing its type.

There's a special type, `()`, that acts as a tuple of zero elements.
This type has only one value, also written `()`.
Both the type and the value are usually pronounced “unit”.
If you are familiar with C, `()` is somewhat similar to `void`.

A tuple's type represents the number, positions, and types of its elements.
This means that tuples containing different numbers or types of elements have distinct types, as do tuples whose types appear in different orders.

We often use tuples to return multiple values from a function.
We can also use them any time we need a fixed-size collection of values, if the circumstances don't require a custom container type.

### Functions over lists and tuples

For tuples, the `fst` and `snd` functions return the first and second element of a pair, respectively.

### Function types and purity

Let's take a look at a function's type.
```haskell
Prelude> :type lines
lines :: String -> [String]
```
We can read the `->` above as "to", which loosely translates to "returns".
The signature as a whole thus reads as "`lines` has the type `String` to list of `String`".

