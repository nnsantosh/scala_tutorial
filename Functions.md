
## Functions

Functions are the basic building blocks in Scala.

A simple example:

def myMax(x:Int,y:Int):Int={ <br/>
  if(x > y) <br/>
    return x; <br/>
  else <br/>
    return y; <br/>
} <br/>

Semicolon after every line is optional since we use enter key to start new line.
Return keyword is optional. Since a scala function always returns a value, we can understand that a functional always returns value of the last executed expression.

So eliminating semicolon and return statement above function looks like this:

def myMax(x:Int,y:Int):Int={ <br/>
  if(x > y) <br/>
    x <br/>
  else <br/>
    y <br/>
} <br/>

This can be further squeezed like this:
def myMax(x:Int,y:Int):Int={ <br/>
  if(x > y) x else y <br/>
} <br/>

If a function has single line in the body then even the curly braces can be eliminated as below: <br/>
def myMax(x:Int,y:Int):Int= if(x > y) x else y <br/>

Scala compiler can interpret return type of a function so removing that the function would look like this: <br />
def myMax(x:Int,y:Int) = if(x > y) x <br/>


1. Semicolon after every line is optional since we use enter key to start new line.
2. Return keyword is optional. Since a scala function always returns a value, we can understand that a functional always returns value of the last executed expression.
3. If a function has single line in the body then even the curly braces can be eliminated.
4. Scala compiler can interpret return type of a function automatically. So specifying return type is also optional.

If a function does not have any parameters then it can be called without paranthesis: <br/>
Ex: def helloWorld() = println("Hello World!") <br/>
val h = helloWorld() <br/>
val h1 = helloWorld <br/>

If the function is defined without parantheis then it cannot be called with parantheis: <br/>
Ex: def helloWorld = println("Hello World!") <br/>
Then it can be called as: <br/>
 val h = helloWorld <br/>
 
 When the function has a side effect use paranthesis in the function definition.
 When the function does not have side effect then remove the parantheis.
 
 ## Function Literals
 
 Also known as :
 1. Anonymous functions
 2. Lambda expressions
 
 Functions are the first class citizens.
 
 val f = (x:Int) => {x+5} <br/>
 
Since scala interprets return type we skipped specifying the return type. However it can be specified as shown: <br />

 val f = (x:Int) => {x+5}:Int <br/>
 
 We can also specify the input type and return type of the function as shown below: <br />
 
 val f:Int => Int = (x:Int) => {x+5}:Int <br/>
 
 ## Where do we use function literals? 
 Most of time we use function literals with higher order functions.
 Example: map function
 val data = List(120, 130,150)
 val res = data.map(x => x + 10)
 
 ## Placeholder syntax
 Lets take example of map and reduce functions in scala:
 
 val data = List(120, 130,150) <br/>
 val res = data.map(x => x + 10) <br/>
 val res1 = data.reduce((x,y) => x +y) <br/>
 
 Since map and reduce function definitions are enforced by the compiler there is no need to specify input parameters for the function.
 But if we try below syntax the compiler will complain as to what is x and what is y
 val res = data.map(x+10) <br/>
 val res1 = data.reduce(x+y) <br/>
 
 So we need to replace the reference to the parameters with an underscore as shown below:
  val res = data.map(_ + 10) <br/>
  val res1 = data.reduce(_ + _) <br/>
 
This is known as placeholder syntax. The placeholder syntax makes it possible to remove the list of parameters. We only give the body and tell Scala that we want to use the parameter here.
The first underscore represents the first parameter.
The second underscore represents the second parameter and so on.
The number of parameters and the number of underscores must be same. Scala will fill in the parameters in a sequence.

Consider below example: <br/>
data.reduce((x,y) => x+y/x min y) <br/>
In this example we cannot replace the parameters with underscore because we are using the parameters more than once in the body.

## Function values
Consider below function literal: <br/>
val f = (x:Int) => x + 10 <br/>
In this line f is function value whereas the code here is the function literal.
Value is like object and function literal is like class.

## Local Functions
Local functions are like private methods. You can define function inside a function. They are visible only in their enclosing block.
They are also referred to as nested function.

## Higher Order Functions
Can take function as an argument <br/>
Can return a function <br/>

Lets take an example for passing function as an argument to a function: <br/>

def intDecorator(x:Int, f: Int => String)={ <br/>
  f(x) <br/>
} <br/>

val decRes = intDecorator(5, (x:Int) => { "[" + x + "]"}) <br/>
println(decRes) <br/>
Result will be [5] <br/>

Lets take another example for passing function as an argument to a function: <br/>
def sumX(x:Int, y:Int, f: (Int,Int) => Int)={ <br/>
  f(x,y) <br/>
} <br/>

val sumRes = sumX(3,5,(x,y) => x*x*x + y*y*y) <br/>
println(sumRes) <br/>
Result will be 152 <br/>

Lets take an example of a function that returns another function as output: <br/>

 def greetSomeOne(prefix:String): String => Unit ={ <br/>
    (name:String) => println(prefix + " " + name) <br/>
  } <br/>

 val hiSomeOne = greetSomeOne("Hi") <br/>
 val hiSantosh = hiSomeOne("Santosh") <br/>
 println(hiSantosh) <br/>
 Result will be: Hi Santosh <br/>
 The same thing can be achieved in single step using: <br/>
 greetSomeOne("Hi")("Santosh") <br/>
 This method of calling function in a series is known as function currying <br/>
 
Whenever you want to return function from another function make sure the last expression in the function is an anonymous function.
Lets take another example:
def f1(x:Int): Int => Double ={ <br/>
    println(Math.sqrt(x)) <br/>
    (y:Int) => Math.sqrt(x+y) <br/>
} <br/>

 val res1 = f1(9)(7)  <br/>
 println(res1) <br/>
 Result will be 4.0 <br/>
 
 In the above function if we remove println then it becomes single expression function and can be replaced as shown below: <br/>
 
 val f1 = (x:Int) => (y:Int) => Math.sqrt(x+y) <br/>
 
 ## Named Arguments and Default Value
 
  ### Variable length argument
    def echo(s:String*) = s foreach println <br/>
    echo("one","two","three) <br/>
   
 1. The repeating argument must be the last argument. <br/>
 2. All values must be of same data type. <br/>
 3. All values are packed into an array. <br/>
 
 ### Named arguments
Consider below function: <br/>
def doSomething(f:String => Unit,s:String)=f(s) <br/>
doSomething(x => println("[" + x + "]"),"Hi There!") <br/>
Result will be [Hi There!] <br/>

Now if we try to change the order of parameter values while invoking the function: <br/>
doSomething("Hi There!",x => println("[" + x + "]")) <br/>
Now we get an error.

Named arguments allow us to pass the input parameter values in a different order. <br/>
doSomething(s = "Hi There!",f = x => println("[" + x + "]")) <br/>
Result will be [Hi There!] <br/>

Named arguments makes sense if we give default values for arguments.
Let us take previous example and assign default value println for the first parameter
def doSomething(f:String => Unit=println,s:String)=f(s) <br/>

Now if we give only one parameter for the method during invocation we get error saying not enough arguments: <br/>
doSomething("Hi There!") <br/>

Now use the named argument and you can skip the first argument since it has default value <br/>
doSomething(s="Hi There!") <br/>
Result will be: Hi There! <br/>

To make some parameters optional use the default value to define them and then use the named argument to call them.





 
  
    
 
 
 
 

  


 
 
 
 
 
 
 






