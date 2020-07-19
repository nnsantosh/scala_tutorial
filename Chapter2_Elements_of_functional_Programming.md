
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
If you don't give a name to a function then it is an anonymous function. <br/>
Example: <br/>
Standard function <br/>
def doubler(i : Int):Int={ <br/>
  return i * 2 <br/>
} <br/>
Anonymous function <br/>
(i:Int) => {i * 2}:Int <br/>

This syntax is known as function literal syntax. <br/>
You can assign anonymous function to a variable in order to  call it. <br/>
val x = (i:Int) => {i*2}:Int <br/>
You can call it using x(5) <br/>

## What is the purpose of an anonymous function?
There might be scenarios where you want to create an inline function for one time usage.

## What is the benefits of passing functions around?
Abstraction is the main benefit of higher order functions. <br/>
Abstraction makes the application easily extendable. <br/>
When developing with a higher level of abstraction, you communicate the behaviour and less the implementation. <br/>
Example: <br/>
Lets say we have an array of customers <br/>
var customers = Array("Mike","Zara","Abdul","Peter") <br/>
Now you want to send greeting message to all of these clients. Simplest way to do this is using for loop: <br/>
for(i <- 0 to customers.length -1){ <br/>
  println("Hi "+ customers(i)); <br/>
 } <br/>
 Next lets assume we need to send payment reminder to all customers <br/>
 def remindPayment(x:String) = println("Payment reminder for "+x) <br/>
 for(i <- 0 to customers.length -1){ <br/>
  remindPayment(customers(i)); <br/>
 } <br/>
 for each customer remind payment <br/>
 If we design this using higher order function final code will look like this: <br/>
 forEach(customers,remindPayment) <br/>

 This kind of programming approach is more precise, easy to understand and more reusable. <br/>
 Lets look at forEach function: <br/>
 def forEach(a: Array[String], f:String => Unit) ={ <br/>
    var i =0; <br/>
    for(i <- o to a.length-1){ <br/>
      f(a(i)); <br/>
    } <br/>
 } <br/>

 Scala provides iterators. <br/>
 Example: customers foreach remindPayment <br/>

 ## Immutability
 Meaning is unable to change. <br/>
 In FP we have <br/>
 1. var - You can change it after initializing <br/>
 2. val- You cannot change once it is initialized <br/>

 Immutability helps to adopt a mathematical approach and create pure functions. <br/>
 Immutable objects are more thread safe. <br/>
 It allows a thread to act upon a immutable object without worrying about other threads because it knows that no one is modifying the    object. <br/>

 ## Recursion and Tail Recursion
 How do we approach recursion? <br/>
 1. Identify the list <br/>
 2. Implement the termination condition. <br/>
 3. Compute the head and recurs with the tail. <br/>

 For Example: Factorial of a number <br/>
 def factorial(n:Int)={ <br/>
    if(n <=0) <br/>
      return 1 <br/>
    else return n * factorial(n-1) <br/>
  } <br/>

 In recursion call stack is created and every call is waiting for the next call to complete. <br/>
 In recursion every call to the function itself results in entry in the stack. <br/>
 So for large programs it can quickly run out of memory. <br/>
 So a loop is better than recursion if you consider memory requirements and performance. <br/>
 Scala compiler knows this and tries to optimize recursive calls. <br/>

 A tail call or tail recursion is a function call performed as the last action. It means your recursive call should be the last operation in your function. <br/>

 In the above factorial function multiplication is the last operation. If we can make the recursive call as the last action then it will be tail recursion. This can be done as shown below: <br/>

 def factorial(n:Int, f:Int)={ <br/>
  if(n <= 0){ <br/>
      return f <br/>
   else  <br/>
     return factorial(n-1,n*f) <br/>
 } <br/>
 The scala compiler internally converts this into loop. <br/>

 ## Statements
 A statement is the smallest standalone element that expresses some action to be carried out. <br/>

 # Functional Statements
 A functional statement returns a value. <br/>
 val x = println("Hello") <br/>
 In scala the return type of println is Unit <br/>
 x: Unit = () <br/>
 Every statement in scala can return some value.Since scala statements return a value some people dont' call them a statement but instead call them as expression. <br/>

 ## Benefits of a statement returning a value
 It helps to achieve immutability. <br/>

 ## Strict and Non-Strict(Lazy) evaluation
 Strict means evaluate the expression now. <br/>
 Lazy means evaluate on the first use. <br/>

 1. Variable assignment <br/>
    val s = factorial(15)/factorial(11) <br/>
    First these function expressions are evaluated and then the result is assigned to value s. <br/>

2.  Function parameters <br/>
    def twice(i:Int)={ <br/>
      return i + i; <br/>
    } <br/>
    Now to invoke this : twice(factorial(15)/factorial(11)) <br/>
    In order to call this function first the function expression value is evaluated. <br/>

3. Higher Order functions <br/>
    def twice(f: => Int) ={ <br/>
      println("We haven't used f yet") <br/>
      f + f <br/>
    } <br/>

    twice({factorial(15)/factorial(11)}) <br/>
      You called factorial 15 <br/>
      You called factorial 11 <br/>
      You called factorial 15 <br/>
      You called factorial 11 <br/>
    So the same function f will be called twice <br/>

    This can be avoided using: <br/>
    def twice(f: => Int) ={ <br/>
      val i = f  <br/>
      println("We haven't used i yet") <br/>
      i+i <br/>
    } <br/>

    In this function value is cached in value i. <br/>
    And hence the function f will be called only once and its value will be reused. <br/>
    twice(factorial(15)/factorial(11)) <br/>
    You called factorial 15 <br/>
    You called factorial 11 <br/>
    We haven't used i yet <br/>
    result: Int = 100 <br/>

1. The default evaluation in Scala is strict. <br/>
2. Scala evaluates function parameters before passing the value to a function. Hence they are evaluated only once. <br/>
3. If the parameter value is a function(In the case of higher order functions), Scala evaluates it inside the body of the function on       every use. <br/>
4. If you don't want multiple evaluations of a function value, you can cache it. <br/>

## Lazy Evaluation
lazy val l = factorial(15)/factorial(11) <br/>
l:Int = <lazy> <br/>

In the above case factorial function is not yet called. <br/>
Where as in below case factorial function is called. value derived and substitued for s. <br/>
val s = factorial(15)/factorial(11) <br/>

println(l) <br/>
Now the functions will be called to evaluate the expressions. <br/>

Now lets check the impact of laziness on a higher order function: <br/>
 def twice(f: => Int) ={ <br/>
      lazy val i = f  <br/>
      println("We haven't used i yet") <br/>
      i+i <br/>
 } <br/>
  twice(factorial(15)/factorial(11)) <br/>
    We haven't used i yet <br/>
    You called factorial 15 <br/>
    You called factorial 11 <br/>
  result: Int = 100 <br/>

1. Scala supports Strict and lazy evaluations. <br/>
2. The default method is the Strict evaluation. <br/>
3. You can cache a pure function value in case of a Higher order function. <br/>
4. You can make an expression lazy by using Lazy val. <br/>
5. You can make a lazy function by caching it to a lazy val. <br/>

## Why Lazy?
The laziness is mostly used to create data structures to handle large volumes of data efficiently. <br/>
Apache spark libraries are the most common examples. <br/>
Spark RDD, they implement all transformations as lazy operations. <br/>

Scala gives lazy alternative to List and it is called Stream. <br/>
Lazy evaluations can combine operations. <br/>

Lets take a simple use case where we want to parse log file and filter first two lines containing text "error" from this file. <br/>
Using strict evaluation: <br/>
val s = Source.fromFile("/root/ws/test_proj/error.log").getLines().toList.filter(_.contains("[error]")).take(2) <br/>
Using stream:<br/>
val s = Source.fromFile("/root/ws/test_proj/error.log").getLines().toStream.filter(_.contains("[error]")).take(2) <br/>

Stream -> Gets one line + applies filter <br/>
List -> Gets all lines + Applies filter to all the lines <br/>

The list is evaluating one operation at a time for all the lines. But the stream combines multiple operations and implements all of them together on each line. <br/>
This kind of approach gives an advantage when we are dealing with large volumes of data and applying a series of operations. <br/>
This concept is so powerful that it allows us to create a data set of infinite length. <br/>

For Example: Lets take fibonacci series <br/>
With strict evaluation if you try to create fibonacci series system will run out of memory pretty soon. <br/>
But with lazy evaluation this can be easily achieved <br/>
def fibFrom(a:Int,b:Int):Stream[Int] = a #:: fibFrom(b,a+b) <br/>
val f = fibFrom(1,2) <br/>
f.takeWhile(_<10) for each println <br/>
1 <br/>
2 <br/>
3 <br/>
5 <br/>
8 <br/>
## Pattern Matching
What is pattern matching? <br/>
The functional programming is going to look into matching objects againts other objects. <br/>
Most common example is type checking of a object. <br/>
Example of typed pattern match:
def myTest(x:any)={ <br />
  x match{ <br />
    case i:Integer => "Its an integer="+i <br />
    case s:String => "Its a String="+s <br />
    case d:Double => "Its a double="+d <br />
    case _ => "Oops! something else" <br />
    } <br />
} <br />
Scala pattern matching gives us a convenient alternative approach which looks like Java's switch statement. <br/>
In this example when the object x matches with an Integer type, Scala binds it to i. <br/>
This automatic binding saves you from casting the x to a matching type. <br/>
## Closures
What is a closure? <br/>
A closure is a function. Like any other scala function, a closure may be pure or impure. It may be named or anonymous, but its primarily a function. <br/>
A function that uses one or more free variables is known as a closure. <br/>
What is a free variable? <br/>
A variable that is not yet bound to the function with a valid value is called free variable. <br/>
Example: <br/>
def getHike(salary:Double) = salary * p/100 <br/>
In the above example p is a free variable. <br/>
The scala compiler looks into the so called nearest local lexical environment, in which that Function was defined and tries to find a binding. <br/>
## How does a change in value of free variable impact the closure?
When you execute a closure, it takes the most recent state of the free variables. A closure may be pure or impure depending on the type of the free variable. If free variable is val then it will be pure. But if free variable is var then it will be impure.
## What if the closure modifies the free variable?
If a closure sets the free variable, the changes are visible outside the closure.
## Why Closure? What are the benefits?
Lets assume we have list of employee numbers: <br/>
val l = (1001 to 1005).toList <br/>
We want a function that we can apply to all of these ids and get the the hike. <br/>
l.map(getHike) <br/>
But for that we would need salary of every employee and only the employee number will not suffice. <br/>
List((1001,3500.0),(1002,5160.0),(1003,2100.0),(1004,3672.0),(1005,3400.0)) <br/>
Let us take another function getComputation <br/>
def getComputation(empId : Int)={ <br/>
  //Load employee and their current salary <br/>
  val e:Map[Int,Double] = Map(1001 -> 35000.00, <br/>
                          1002 -> 43000.00 <br/>
                          1003 -> 28000.00 <br/>
                          1004 -> 54000.00 <br/>
                          1005 -> 17000.00) <br/>
  //Some logic to derive percentage for each employee <br/>
  val p:Map[Int,Double] = Map(1001 -> 10.00, <br/>
                          1002 -> 12.00 <br/>
                          1003 -> 7.50 <br/>
                          1004 -> 6.80 <br/>
                          1005 -> 20.00) <br/>
  (empId, e(empId) * p(empId) / 100.00) <br/>
} <br/>
getComputation: Int => (Int, Double) <br/>
getComputation is an higher order function that returns another function <br/>
//The variable getHike is holding an anonymous function <br/>
val getHike = getComputation <br/>
getHike: Int => (Int,Double) = <functional> <br/>
So now if you call getHike with employee id  <br/>
getHike(1001) it returns (1001,3500.00) <br/>
If you call getHike with an employee id that does not exist  <br/>
getHike(1006) then it throws exception: java.util.NoSuchElementException: key not found:1006 <br/>
So where is the getHike validating for the employee number? <br/>
The variables e and p are local variables for getComputation function. But they are  free variables for the anonymous function returned from the last line of getComputation. <br/>
The last line of getComputation is closure. <br/>
When we returned it from the getComputation it carries the state of e and p with it. So getHike contains the data with it. <br/>
Closures and their capability to carry state is incredible. It saves lot of complicated and unnecessary code and simplifies solution. <br/>

## Scala Types or Type System
A type system is a set of rules that assigns a property called type to the various programming constructs, such as variables, expressions, functions or modules. <br/>
Scala is a statically typed language meaning compiler verifies the type rules. <br/>
Early protection and better performance since the compiler can apply some optimizaiton because it can apply type checking. <br/>
Scala has a unified type system and the heirarchy looks like this: <br/>
![Scala Unified Type System](https://docs.scala-lang.org/resources/images/tour/unified-types-diagram.svg)
Scala value classes do not need new keyword. <br/>
All the value classes are instantiated using literals. <br/>
Example: <br/>
var y: Long = 7483; <br/>
val x: Int = 23456; <br/>
va z : Char = 'Z'; <br/>
Implicit Type conversion in Scala: <br/>
![Scala Implicit type casting heirarhy](https://docs.scala-lang.org/resources/images/tour/type-casting-diagram.svg)
You can use new keyword to instantiate reference classes <br/>
Example: <br/>
val s = new String("Hi there!"); <br/>
You cannot create an instance of Nothing so you cannot assign "Nothing" to a value or a variable. <br/>
For value classes you cannot assign Null. Null can be assigned only for reference clases. <br/>
Nothing is the direct child of every value class. But you cannot assign Null or Nothing to a value. <br/>
That means you cannot create a value in Scala without initializing it with some valid value other than null and nothing. <br/>
Scala has a built in type inference mechanism.So you can leave the type annotation and let Scala infer it automatically. <br/>
But for below two scenarios you need to specify the type annoation: <br/>
1. Function parameters <br/>
2. Return type of a recursive function <br/>
