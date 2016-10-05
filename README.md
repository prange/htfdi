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



