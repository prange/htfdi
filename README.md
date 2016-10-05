# htfdi
How the fuck do i ... ? A functional cheat sheet for java developers.

*Functional programming is fun they said. No exceptions and easier to test, they said.* _But how the fuck do i get anything done?_

Fear not. Use this simple cheat sheet to get you startet. Littered with examples.

_Note, i will use types from www.functionaljava.org (FJ) throughout. Feel free to use any other functional library to provide for types, such as
javaslang.org or roll out your own._

## How do i solve a problem?
In FP, problems are solved not by orchestrating a myriad of objects that communicate and change state in an unpredictable manner. Rather,
one analyses the input you have, the output you want to produce, and how to get from input to output. It is not unusual to name the
type (or class) of your input `A`, and the type of your output `B`. You can also give the transformation itself a catchy name, for 
example _f_. In java 8, your solution would now have the type `Function<A,B>`. In FJ `F<A,B>`


## I have a List (or any iterable for that matter), and i want to do something with every element
_map_ is your friend here. _map_ can change the content of every element in a collection. All types that have a _map_ method can change 
their elements with the function you provide as an argument. The standard java collection api does noe have that ability, but use FJ datastructures, and you get it. Map has the signature `Collection<B> map(F<A,B> f)`, where "Collection" always is the same class as the owner of the map method. So: For a List, its `List<B> map(F<A,B> f)`. For a Set its  `Set<B> map(F<A,B> f)`. And so on. In fact, lots of classes can have a _map_ method. All those classes have the ability to change their "contents" with the function you provide. Why did i write ""Contents"" in as if its not _really_ contents? Because it doesnt have to be contents that change. Some classes do not contain anything, yet you can change them using map. More on that later.

Example:



## I have a collection-ish type (like a List, or maybe a Stream), and i want to collect the information in it into some other object
_foldLeft_ to the rescue (or _foldRight_). You might know "reduce" from jQuery, or "collect" from Java 8 Streams (shiver). It solves the same problem, without introducing new problems. 





