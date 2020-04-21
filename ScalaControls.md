## Control Abstractions

Scala allows you to create new control abstractions.
Scala offers 5 different kind of control abstractions:
1. if else
2. Match Case
3. While loop and Do While loop
4. Higher Order Control Abstraction
5. For expression

### if else
Functional style if else try to avoid changing var
def testF(i:Int)= if(i==1) "one" else "something else"

val s = if(i==1) 1 else println("something else")
s:AnyVal=()
In the above case since for one condition it returns Int and for other Unit() the common type will be AnyVal()

### Match Case expression
match case is like switch statement in java
def matchX(x:Int)={
  x match{
    case 1 => "Case One"
    case 2 => "Case Two"
    case 3 => "Case Three"
    case _ => "Default Case"
  }
}
match case also returns a value.
curly braces is optional even if you have multiple lines for each case.

### While Loop
While loop is a statement because it does not return meaningful value. It always returns a Unit.
Example of while loop:
def loopN(i:Int)={
  var j = 1
  while(j <= i){
    println(j)
    j = j +1
  }
}

do While loop Example:
def loopDo(i:Int)={
  var j = 1
  do{
    println(j)
    j = j +1
  }while(j <= i)  
}

Pure Functional approach does not provide while and do while but recommends using recursion.

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

Example:
val l = List("India","USA","UK","China","Russia")
  def f1(s:String)={
    println("Printing "+s)
    "Returning " + s
  }
  
l.foreach(f1)

Output will be:
Printing India
Printing USA
Printing UK
Printing China
Printing Russia

### map
map method returns a value
l.map(f1)
output list will be: List("Returning India","Returning USA","Returning UK","Returning China","Returning Russia")

### flatMap
def f3(s:String): Array[String] = s.split(" ")
val l = List("India is a multiparty democratic system","USA is a two party democratic system")
l.map(f3)
output list will be : List(Array(India,is,a,multiparty,democratic,system), Array(USA,is,a,two,party,democratic,system))
l.flatMap(f3)
output list will be: List(India,is,a,multiparty,democratic,system,USA,is,a,two,party,democratic,system)

The flatMap goes one step further it takes the return value of f3 and breaks them once again to create a flattened list. So the flatMap method has flattened the Array into String.

### filter
filter takes a boolean condition applies to all elements of collection and returns only those elements of the collection which satisfy the condition.
Example:
val l = List("india","USA","UK","China","Russia")
l.filter(x => x.startsWith("i"))
Output will be : List(india)

## withFilter
is similar to filter but it does not return a new collection.It will apply the boolean condition just before the subsequent method calls.
Example:
l.withFilter(x => x.startsWith("i")).map(x => x.capitalize)
Output will be : List(India)

### for loop

for(seq) yield {expr}

yield is optional.

Example:
for( i <- 1 to 10){
  statement-1;
  statement-2;
}
if there is only single expression then curly braces are optional.
for( i <- 1 to 10)
    single-expression;
    
Example:
val n = 1 to 10
Range(1,2,3,4,5,6,7,8,9,10)
for(i <- n) println(i)
Output will be:
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

The for expression in scala is just a syntactic sugar. Internally it converts to one of the following: foreach, map, flatMap or withFilter

In the absence of yield the for loop behaves like a foreach. If we apply the yield it behaves like a map method.
Example:
for(country <- List("India","USA","China","Japan")){
  country match{
    case "India" => "Delhi"
    case "USA" => "Washington D.C."
    case "China" => "Beijing"
    case "Japan" => "Tokyo"
    case _ => "I don't know"
   }
} 
The above for loop does not return anything.

### for with yield

Using yield:

for(country <- List("India","USA","China","Japan")) yield {
  country match{
    case "India" => "Delhi"
    case "USA" => "Washington D.C."
    case "Japan" => "Tokyo"
    case _ => "I don't know"
   }
} 
Now following List will be returned:
List(Delhi,Washington D.C.,I dont't know,Tokyo)



 










