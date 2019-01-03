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

A side effect introduces a dependency between the global state of the system and the behavior of a function.

### Haskell source files, and writing simple functions

Haskell source files are usually identified with a suffix of `.hs`.
```haskell
add a b = a + b
```
On the left hand side of the `=` is the name of the function, followed by the arguments to the function. On the right hand side is the body of the function.

Haskell doesn't have a `return` keyword, as a function is a single expression, not a sequence of statements.
The value of the expression is the result of the function.

When you see an `=` symbol in Haskell code, it represents "meaning": the name on the left is defined to be the expression on the right.

#### Just what is a variable, anyway?

In Haskell, a variable provides a way to give a name to an expression.
Once a variable is *bound to* (i.e. associated with) a particular expression, its value does not change: we can always use the name of the variable instead of writing out the expression, and get the same result either way.

#### Conditional evaluation

Like many other languages, Haskell has an `if` expression.

Finally, our if expression spans several lines.
We align the then and else branches under the if for neatness.
So long as we use some indentation, the exact amount is not important.
If we wish, we can write the entire expression on a single line.

We will usually break an if expression across several lines to keep the predicate and each of the branches easier to follow.

### Understanding evaluation by example

#### Lazy evaluation

In a language that uses *strict* evaluation, the arguments to a function are evaluated before the function is applied.
Haskell chooses another path: *non-strict* evaluation.

### Polymorphism in Haskell

To capture this idea, its type signature contains a *type variable*.

When a function has type variables in its signature, indicating that some of its arguments can be of any type, we call the function polymorphic.

Parametric polymorphism is the most visible kind of polymorphism that Haskell supports.
A parameterized type in Haskell is similar to a type variable in Java generics.

### Why the Fuss over Purity?

Few programming languages go as far as Haskell in insisting that purity should be the default.

Because the result of applying a pure function can only depend on its arguments, we can often get a strong hint of what a pure function does by simply reading its name and understanding its type signature.

Purity makes the job of understanding code easier.
The behavior of a pure function does not depend on the value of a global variable, or the contents of a database, or the state of a network connection.
Pure code is inherently modular: every function is self-contained and has a well-defined interface.

A non-obvious consequence of purity being the default is that working with *impure* code becomes easier.
Haskell encourages a style of programming in which we separate code that *must* have side effects from code that doesn't need side effects.
In this style, impure code tends to be simple, with the "heavy lifting" performed in pure code.

## Chapter 3

### Defining a New Data Type

### Type Synonyms

We can introduce a *synonym* for an existing type at any time, in order to give a type a more descriptive name.

The `type` keyword introduces a type synonym.
The new name is on the left of the `=`, with the existing name on the right.
The two names identify the same type, so type synonyms are *purely* for making code more readable.

### Algebraic Data Types

An algebraic data type can have more than one value constructor:
```haskell
data Bool =  False | True
```
When a type has more than one value constructor, they are usually referred to as *alternatives* or *cases*.
We can use any one of the alternatives to create a value of that type.

Each of an algebraic data type's value constructors can take zero or more arguments.

### Pattern Matching

Haskell has a simple, but tremendously useful, *pattern matching* facility that lets us do both of these things.

