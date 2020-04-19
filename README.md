# SCALA TUTORIAL
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
 
 ## Immutability
 Meaning is unable to change.
 In FP we have
 1. var - You can change it after initializing
 2. val- You cannot change once it is initialized
 
 Immutability helps to adopt a mathematical approach and create pure functions.
 Immutable objects are more thread safe.
 It allows a thread to act upon a immutable object without worrying about other threads because it knows that no one is modifying the    object.
 
 ## Recursion and Tail Recursion
 How do we approach recursion?
 1. Identify the list
 2. Implement the termination condition.
 3. Compute the head and recurs with the tail.
 
 For Example: Factorial of a number
 def factorial(n:Int)={
    if(n <=0)
      return 1
    else return n * factorial(n-1)
  }
 
 In recursion call stack is created and every call is waiting for the next call to complete.
 In recursion every call to the function itself results in entry in the stack.
 So for large programs it can quickly run out of memory.
 So a loop is better than recursion if you consider memory requirements and performance.
 Scala compiler knows this and tries to optimize recursive calls.
 
 A tail call or tail recursion is a function call performed as the last action. It means your recursive call should be the last operation in your function.
 
 In the above factorial function multiplication is the last operation. If we can make the recursive call as the last action then it will be tail recursion. This can be done as shown below:
 
 def factorial(n:Int, f:Int)={
  if(n <= 0){
      return f
   else 
     return factorial(n-1,n*f)
 }
 The scala compiler internally converts this into loop.
 
 ## Statements
 A statement is the smallest standalone element that expresses some action to be carried out.
 
 # Functional Statements
 A functional statement returns a value.
 val x = println("Hello")
 In scala the return type of println is Unit
 x: Unit = ()
 Every statement in scala can return some value.Since scala statements return a value some people dont' call them a statement but instead call them as expression.
 
 ## Benefits of a statement returning a value
 It helps to achieve immutability.
 
 ## Strict and Non-Strict(Lazy) evaluation
 Strict means evaluate the expression now.
 Lazy means evaluate on the first use.
 
 1. Variable assignment
    val s = factorial(15)/factorial(11)
    First these function expressions are evaluated and then the result is assigned to value s.

2.  Function parameters
    def twice(i:Int)={
      return i + i;
    }
    Now to invoke this : twice(factorial(15)/factorial(11))
    In order to call this function first the function expression value is evaluated.
    
3. Higher Order functions
    def twice(f: => Int) ={
      println("We haven't used f yet")
      f + f
    }
    
    twice({factorial(15)/factorial(11)})
      You called factorial 15
      You called factorial 11
      You called factorial 15
      You called factorial 11
    So the same function f will be called twice
    
    This can be avoided using:
    def twice(f: => Int) ={
      val i = f 
      println("We haven't used i yet")
      i+i
    }
    
    In this function value is cached in value i.
    And hence the function f will be called only once and its value will be reused.
    twice(factorial(15)/factorial(11))
    You called factorial 15
    You called factorial 11
    We haven't used i yet
    result: Int = 100
    
1. The default evaluation in Scala is strict.
2. Scala evaluates function parameters before passing the value to a function. Hence they are evaluated only once.
3. If the parameter value is a function(In the case of higher order functions), Scala evaluates it inside the body of the function on       every use.
4. If you don't want multiple evaluations of a function value, you can cache it.

## Lazy Evaluation
lazy val l = factorial(15)/factorial(11)
l:Int = <lazy>
  
In the above case factorial function is not yet called.
Where as in below case factorial function is called. value derived and substitued for s.
val s = factorial(15)/factorial(11)

println(l)
Now the functions will be called to evaluate the expressions.

Now lets check the impact of laziness on a higher order function:
 def twice(f: => Int) ={
      lazy val i = f 
      println("We haven't used i yet")
      i+i
 }
  twice(factorial(15)/factorial(11))
    We haven't used i yet
    You called factorial 15
    You called factorial 11
  result: Int = 100
 
1. Scala supports Strict and lazy evaluations.
2. The default method is the Strict evaluation.
3. You can cache a pure function value in case of a Higher order function.
4. You can make an expression lazy by using Lazy val.
5. You can make a lazy function by caching it to a lazy val.

## Why Lazy?
The laziness is mostly used to create data structures to handle large volumes of data efficiently.
Apache spark libraries are the most common examples.
Spark RDD, they implement all transformations as lazy operations.

Scala gives lazy alternative to List and it is called Stream.
Lazy evaluations can combine operations.

Lets take a simple use case where we want to parse log file and filter first two lines containing text "error" from this file.
Using strict evaluation:
val s = Source.fromFile("/root/ws/test_proj/error.log").getLines().toList.filter(_.contains("[error]")).take(2)
Using stream:
val s = Source.fromFile("/root/ws/test_proj/error.log").getLines().toStream.filter(_.contains("[error]")).take(2)

Stream -> Gets one line + applies filter
List -> Gets all lines + Applies filter to all the lines

The list is evaluating one operation at a time for all the lines. But the stream combines multiple operations and implements all of them together on each line.
This kind of approach gives an advantage when we are dealing with large volumes of data and applying a series of operations.
This concept is so powerful that it allows us to create a data set of infinite length.

For Example: Lets take fibonacci series
With strict evaluation if you try to create fibonacci series system will run out of memory pretty soon.
But with lazy evaluation this can be easily achieved
def fibFrom(a:Int,b:Int):Stream[Int] = a #:: fibFrom(b,a+b)
val f = fibFrom(1,2)
f.takeWhile(_<10) for each println
1
2
3
5
8

## Pattern Matching
What is pattern matching?
The functional programming is going to look into matching objects againts other objects.
Most common example is type checking of a object.
Example of typed pattern match:
def myTest(x:any)={
  x match{
    case i:Integer => "Its an integer="+i
    case s:String => "Its a String="+s
    case d:Double => "Its a double="+d
    case _ => "Oops! something else"
    }
}

Scala pattern matching gives us a convenient alternative approach which looks like Java's switch statement.
In this example when the object x matches with an Integer type, Scala binds it to i.
This automatic binding saves you from casting the x to a matching type.

## Closures
What is a closure?

A closure is a function. Like any other scala function, a closure may be pure or impure. It may be named or anonymous, but its primarily a function.

A function that uses one or more free variables is known as a closure.

What is a free variable?
A variable that is not yet bound to the function with a valid value is called free variable.
Example:
def getHike(salary:Double) = salary * p/100
In the above example p is a free variable.

The scala compiler looks into the so called nearest local lexical environment, in which that Function was defined and tries to find a binding.

## How does a change in value of free variable impact the closure?
When you execute a closure, it takes the most recent state of the free variables. A closure may be pure or impure depending on the type of the free variable. If free variable is val then it will be pure. But if free variable is var then it will be impure.

## What if the closure modifies the free variable?
If a closure sets the free variable, the changes are visible outside the closure.

## Why Closure? What are the benefits?
Lets assume we have list of employee numbers:
val l = (1001 to 1005).toList

We want a function that we can apply to all of these ids and get the the hike.
l.map(getHike)
But for that we would need salary of every employee and only the employee number will not suffice.

List((1001,3500.0),(1002,5160.0),(1003,2100.0),(1004,3672.0),(1005,3400.0))

Let us take another function getComputation
def getComputation(empId : Int)={
  //Load employee and their current salary
  val e:Map[Int,Double] = Map(1001 -> 35000.00,
                          1002 -> 43000.00
                          1003 -> 28000.00
                          1004 -> 54000.00
                          1005 -> 17000.00)
  //Some logic to derive percentage for each employee
  val p:Map[Int,Double] = Map(1001 -> 10.00,
                          1002 -> 12.00
                          1003 -> 7.50
                          1004 -> 6.80
                          1005 -> 20.00)
  (empId, e(empId) * p(empId) / 100.00)
}
getComputation: Int => (Int, Double)

getComputation is an higher order function that returns another function

//The variable getHike is holding an anonymous function
val getHike = getComputation
getHike: Int => (Int,Double) = <functional>

So now if you call getHike with employee id 
getHike(1001) it returns (1001,3500.00)
If you call getHike with an employee id that does not exist 
getHike(1006) then it throws exception: java.util.NoSuchElementException: key not found:1006

So where is the getHike validating for the employee number?
The variables e and p are local variables for getComputation function. But they are  free variables for the anonymous function returned from the last line of getComputation.
The last line of getComputation is closure.
When we returned it from the getComputation it carries the state of e and p with it. So getHike contains the data with it.

Closures and their capability to carry state is incredible. It saves lot of complicated and unnecessary code and simplifies solution.

## Scala Types or Type System
A type system is a set of rules that assigns a property called type to the various programming constructs, such as variables, expressions, functions or modules.
Scala is a statically typed language meaning compiler verifies the type rules.
Early protection and better performance since the compiler can apply some optimizaiton because it can apply type checking.

Scala has a unified type system and the heirarchy looks like this:
![Scala Unified Type System](https://docs.scala-lang.org/resources/images/tour/unified-types-diagram.svg)

Scala value classes do not need new keyword.
All the value classes are instantiated using literals.
Example:
var y: Long = 7483;
val x: Int = 23456;
va z : Char = 'Z';
Implicit Type conversion in Scala:

![Scala Implicit type casting heirarhy](https://docs.scala-lang.org/resources/images/tour/type-casting-diagram.svg)

You can use new keyword to instantiate reference classes
Example:
val s = new String("Hi there!");

You cannot create an instance of Nothing so you cannot assign "Nothing" to a value or a variable.

For value classes you cannot assign Null. Null can be assigned only for reference clases.

Nothing is the direct child of every value class. But you cannot assign Null or Nothing to a value.

That means you cannot create a value in Scala without initializing it with some valid value other than null and nothing.

Scala has a built in type inference mechanism.So you can leave the type annotation and let Scala infer it automatically.
But for below two scenarios you need to specify the type annoation:
1. Function parameters
2. Return type of a recursive function

## Operators
1. Arithmetic operators
2. Logical operators
3. Bitwise operators

1. Operator precedence
2. Associativity Rules

Scala doesn't have any operator. Scala is a pure object oriented lanaguage because every value in scala is an object.
You create an Integer and it an object.
You will also notice that all operators like +, - etc are defined as methods for Int class
Scala allows us to use the symbols as identifiers.\
Scala implements the arithmetic, logical and bitwise operators as methods.

## How do we call these methods?
Example:
val i = 10
i.(+)5
i.(-)5

Since the above dot notation is not following mathmetical notation scala allows below syntax:
i + 5
i - 5

Every value in Scala is an object.
Every method in Scala is an operator.

Scala allows object oriented notation(dot notation) as well as the operator notation for making a method call.
Example:
i to 20
i.to(20)

If we have more than one input parameter:
<object> <method>  <(parameter1, parameter2... parametern)>

If we don't have any input parameter:
dont pass any parameter

# Unary operator

Example:

val i =10  <br />
-i * 2   <br />

i.unary_- * 2  <br />

Scala allows only four symbols as unary operators: +  -  !  ~












    
 
 
 
 
 
 
 
 
 
















    



