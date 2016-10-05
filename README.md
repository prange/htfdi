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
_foldLeft_ to the rescue (or _foldRight_). You might know "reduce" from jQuery, or "collect" from Java 8 Streams (shiver). It solves the same problem, without introducing new problems. The signature of _foldLeft_ is `B foldLeft(F2<B,A,A> accumulator, B init)`. WTF is that monster called "accumulator" in there you ask? Its a function that takes two argument. In Java 8 lingo its "BiFunction" (shiver). The task of the accumulator is first to take your init value and the first leftmost element in your collection, and return a new object og the same class as your init object. Then it takes _that_ object, and the next object in your collection, and returns yet another object, until the collection is exhausted. The last object you return is now returned from _foldLeft_.
You can use foldLeft to produce any new object you want, based on the contents of the collection. It doesn't _have_ to be a collection of course. Any object with _foldLeft_ can be transformed into a new object of a different class based on its contents. Or "contents".

Exameple:


## I want to use _null_ to express the absence of a value, but i get yelled at. What is the alternative?
Use `Option` (Or `Optional` from Java 8 - actually not too bad). Option is like a list with zero or one element. It has _map_, but not _foldLeft_. But it has a fold method. In FJ the fold is called _option_, and is a bit confusing. But you will get it after a little while. Both _fold_ and _foldLeft_ transforms your object into a new type of object. The difference between _fold_ and _foldLeft_ is that _foldLeft_ takes an initial value, and adds the elements to that value, whereas _fold_ handles each internal element seperately.
The signature of _option_ makes it a bir clearer: `B option(B ifNone, F<A,B> ifSome)`. If your option is empty, contains no value, is undefined, is None, then the value _isNone_ is returned. Otherwise: If your Option really contains a value, that value is applied to the function _ifSome_, and the result of that function is returned.

Example:







