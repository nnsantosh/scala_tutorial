# scala_tutorial
Scala basics and functional programming concepts to remember

## Why Scala
Scala shines for big data processing and machine learning

## Reasons
1. Functional paradigm and scripting approach
2. Concise and expressive.
3. Apache spark is another compelling reason to learn scala.

## SBT (The Simple Build Tool)
Its a build tool for scala projects
Sccala projects follow same structure as java projects
Main Project folder
  build.sbt
  src
      main  
          java
          scala
          resources
     test  
          java
          scala
          resources
          
 Notice that sbt definition is in build.sbt file similar to pom.xml in a maven project
To compile and run the project the command used is : sbt run from the main project folder

You can also use scala REPL(read-print-eval-loop)
run the command: sbt console
It will start scala REPL or interactive scala shell or you can think it as scala commmand line interpreter.
Scala REPL supports experiment driven development.
Whenever you start your sbt console in a project scope SBT will compile your project and bring all the source code and dependencies into current scope.

Scala is a hybrid language it supports functional programming and object oriented programming

## Elements of functional programming
Functional programming is a way of writing software applications using only pure functions and immutable values.
1. Pure functions and side effects
2. Referential Transparency
3. First Class Functions and Higher Order Functions
4. Anonymous Functions
5. Immutability
6. Recursion and Tail Recursion
7. Statements
8. Strict and Non-Strict(Lazy) Evaluation
9. Pattern Matching
10. Closures

Library design and data crunching are some of the problems where Functional programming approach works best.

## Pure Functions:
 Function relates an input to a output. A mathematical function consists of input, output and relationship.
It is the relationship that determins the output based on the input.
1. The input solely determines the output.  There is no other thing like global variable or content of a file or input from the console that determines the output.
2. The function does not change its input. No matter what it does not change its input value.
3. The function does not do anything else except computing the output.It doesn't read anything from a file or console. It doesn't write anything to console. It doesn't read or modify a global variable or for that matter anything outside the function. It should not perform any IO.

So a function is pure if it is free from side effects. 
## How to validate purity of a function and that is by testing it for referential transparency.
## Referential Transparency:
A function is said to be referentially transparent if we can replace it with a corresponding value without changing the program's behaviour. In other words if evaluating it gives same output value for same input values.
Example: If a program uses Math.sqrt(4.0) we can replace all references of Math.sqrt(4.0) with 2.0

## Why Pure Functions:
1. Encourage safe ways of programming.
2. Composable or modular.
3. Easy to test.
4. Memoizable- Nothing but caching of deterministic functions. You can store the results if you have to reuse or compiler can do that as optimization.
5. Can be lazy.

## First class Functions:
If you can treat a function as a value, it is a first class function.
You should be able to do everything with a function that you can do with a value.
1. You can assign it to a variable.
2. You can pass it as an argument to other functions.
3. You can return it as value from other functions.
In scala all functions are first class functions by default.

## Higher Order Functions:
A function that does atleast one of the following is a higher order function:
1. Takes one or more functions as arguments.
2. Returns a function as its result.

## Anonymous Function
If you don't give a name to a function then it is an anonymous function.
Example:
Standard function
def doubler(i : Int):Int={
  return i * 2
}
Anonymous function
(i:Int) => {i * 2}:Int

This syntax is known as function literal syntax.
You can assign anonymous function to a variable in order to  call it.
val x = (i:Int) => {i*2}:Int
You can call it using x(5)

## What is the purpose of an anonymous function?
There might be scenarios where you want to create an inline function for one time usage.

## What is the benefits of passing functions around?
Abstraction is the main benefit of higher order functions.
Abstraction makes the application easily extendable.
When developing with a higher level of abstraction, you communicate the behaviour and less the implementation.
Example:
Lets say we have an array of customers
var customers = Array("Mike","Zara","Abdul","Peter")
Now you want to send greeting message to all of these clients. Simplest way to do this is using for loop:
for(i <- 0 to customers.length -1){
  println("Hi "+ customers(i));
 }
 Next lets assume we need to send payment reminder to all customers
 def remindPayment(x:String) = println("Payment reminder for "+x)
 for(i <- 0 to customers.length -1){
  remindPayment(customers(i));
 }
 for each customer remind payment
 If we design this using higher order function final code will look like this:
 forEach(customers,remindPayment)
 
 This kind of programming approach is more precise, easy to understand and more reusable.
 Lets look at forEach function:
 def forEach(a: Array[String], f:String => Unit) ={
    var i =0;
    for(i <- o to a.length-1){
      f(a(i));
    }
 }
 
 Scala provides iterators.
 Example: customers foreach remindPayment
 
 
 
 
















    



