## Control Abstractions

Scala allows you to create new control abstractions.
Scala offers 5 different kind of control abstractions:
1. if else
2. Match Case
3. While loop and Do While loop
4. Higher Order Control Abstraction
5. For expression

### if else
Functional style if else try to avoid changing var <br/>
def testF(i:Int)= if(i==1) "one" else "something else" <br/>

val s = if(i==1) 1 else println("something else") <br/>
s:AnyVal=() <br/>
In the above case since for one condition it returns Int and for other Unit() the common type will be AnyVal() <br/>

### Match Case expression
match case is like switch statement in java <br/>
def matchX(x:Int)={ <br/>
  x match{ <br/>
    case 1 => "Case One" <br/>
    case 2 => "Case Two" <br/>
    case 3 => "Case Three" <br/>
    case _ => "Default Case" <br/>
  } <br/>
} <br/>
match case also returns a value. <br/>
curly braces is optional even if you have multiple lines for each case. <br/>

### While Loop
While loop is a statement because it does not return meaningful value. It always returns a Unit.
Example of while loop: <br/>
def loopN(i:Int)={ <br/>
  var j = 1 <br/>
  while(j <= i){ <br/>
    println(j) <br/>
    j = j +1 <br/>
  } <br/>
} <br/>

do While loop Example: <br/>
def loopDo(i:Int)={ <br/>
  var j = 1 <br/>
  do{ <br/>
    println(j) <br/>
    j = j +1 <br/>
  }while(j <= i)  <br/> 
} <br/>

Pure Functional approach does not provide while and do while but recommends using recursion. <br/>

### Higher Order Control Abstraction
1. Data Abstraction - Is to hide the implementation of complex data types or data structures.
2. Control Abstraction - Is to hide the implementation of complex execution flow and some low level activities.
Scala gives us an ability to create new control abstraction of our own. This capability allows us to abstract code clutter and make final code precise, neat and easy to understand.
If we are implementing library in scala we will be implementing many of such abstractions.

### Higher Order Control Abstractions available for Collections
1. foreach
2. map
3. flatMap
4. filter and withFilter
They take function as an argument and apply the function to each element of the collection.

### foreach
The return type of foreach is a Unit. It does not return any value.

Example: <br/>
val l = List("India","USA","UK","China","Russia") <br/>
  def f1(s:String)={ <br/>
    println("Printing "+s) <br/>
    "Returning " + s <br/>
  } <br/>
  
l.foreach(f1) <br/>

Output will be: <br/>
Printing India <br/>
Printing USA <br/>
Printing UK <br/>
Printing China <br/>
Printing Russia <br/>

### map
map method returns a value
l.map(f1) <br/>
output list will be: List("Returning India","Returning USA","Returning UK","Returning China","Returning Russia")

### flatMap
def f3(s:String): Array[String] = s.split(" ") <br/>
val l = List("India is a multiparty democratic system","USA is a two party democratic system") <br/>
l.map(f3) <br/>
output list will be : List(Array(India,is,a,multiparty,democratic,system), Array(USA,is,a,two,party,democratic,system)) <br/>
l.flatMap(f3) <br/>
output list will be: List(India,is,a,multiparty,democratic,system,USA,is,a,two,party,democratic,system) <br/>

The flatMap goes one step further it takes the return value of f3 and breaks them once again to create a flattened list. So the flatMap method has flattened the Array into String.

### filter
filter takes a boolean condition applies to all elements of collection and returns only those elements of the collection which satisfy the condition.
Example: <br/>
val l = List("india","USA","UK","China","Russia") <br/>
l.filter(x => x.startsWith("i")) <br/>
Output will be : List(india) <br/>

## withFilter
is similar to filter but it does not return a new collection.It will apply the boolean condition just before the subsequent method calls.
Example: <br/>
l.withFilter(x => x.startsWith("i")).map(x => x.capitalize) <br/>
Output will be : List(India) <br/>

### for loop

for(seq) yield {expr} <br/>

yield is optional. <br/>
 
Example: <br/>
for( i <- 1 to 10){ <br/>
  statement-1; <br/>
  statement-2; <br/>
} <br/>
if there is only single expression then curly braces are optional. <br/>
for( i <- 1 to 10) <br/>
    single-expression; <br/>
    
Example: <br/>
val n = 1 to 10 <br/>
Range(1,2,3,4,5,6,7,8,9,10) <br/>
for(i <- n) println(i) <br/>
Output will be: <br/>
1
2
3
4
5
6
7
8
9
10

The for expression in scala is just a syntactic sugar. Internally it converts to one of the following: foreach, map, flatMap or withFilter <br/>

In the absence of yield the for loop behaves like a foreach. If we apply the yield it behaves like a map method.
Example: <br/>
for(country <- List("India","USA","China","Japan")){ <br/>
  country match{ <br/>
    case "India" => "Delhi" <br/>
    case "USA" => "Washington D.C." <br/>
    case "China" => "Beijing" <br/>
    case "Japan" => "Tokyo" <br/>
    case _ => "I don't know" <br/>
   } <br/>
}  <br/>
The above for loop does not return anything.

### for with yield

Using yield:<br/>

for(country <- List("India","USA","China","Japan")) yield { <br/>
  country match{ <br/> 
    case "India" => "Delhi" <br/>
    case "USA" => "Washington D.C." <br/>
    case "Japan" => "Tokyo" <br/>
    case _ => "I don't know" <br/>
   } <br/>
}  <br/>
Now following List will be returned:
List(Delhi,Washington D.C.,I dont't know,Tokyo)



 










