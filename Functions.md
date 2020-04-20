
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
def myMax(x:Int,y:Int) = if(x > y) x


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
 
 
 
 






