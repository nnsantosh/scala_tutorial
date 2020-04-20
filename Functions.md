Functions are the basic building blocks in Scala.

A simple example:

def myMax(x:Int,y:Int):Int={ <br/>
  if(x > y) <br/>
    return x; <br/>
  else <br/>
    return y; <br/>
} <br/>

1. Semicolon after every line is optional since we use enter key to start new line.
2. Return keyword is optional. Since a scala function always returns a value, we can understand that a functional always returns value of the last executed expression.

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

If a function has single line in the body then even the curly braces can be eliminated as below:
def myMax(x:Int,y:Int):Int= if(x > y) x else y <br/>



