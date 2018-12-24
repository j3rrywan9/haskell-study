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

