
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





 
 
 
 
 
 
 






