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
val i = 10  <br />
i.(+)5  <br />
i.(-)5  <br />

Since the above dot notation is not following mathmetical notation scala allows below syntax:
i + 5  <br />
i - 5  <br />

Every value in Scala is an object.
Every method in Scala is an operator.

Scala allows object oriented notation(dot notation) as well as the operator notation for making a method call.
Example:
i to 20  <br />
i.to(20)  <br />

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












    
 
 
 
 
 
 
 
 
 
















    



