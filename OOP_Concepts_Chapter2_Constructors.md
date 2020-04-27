## Constructors

When you create a class in Scala without any arguments it will give you default constructor without arguments. <br/>
Example: class Cirlce{} <br/>
When you pass some arguments to the class then Scala will give Constructor with those arguments. We call that one primary constructor. <br/>
Example: class Circle(var radius:Int){} <br/>

If you dont specify var or val for the attribute of a class then Scala will not create reader and writer. <br/>
Example: <br/>
class Circle(radius:Int) <br/>
In this case Scala makes radius object private field. It is as good as private val. <br/>

### Primary Constructor
Whenever primary constructor is created we lose the default constructor. <br/>

### Auxiliary Constructor
Example: <br/>
Let us assume we have Box class that has 3 attributes height,width and depth. <br/>
class Box(var height:Int, var width:Int, var depth:Int){} <br/>
In the above case Primary constructor is created with 3 fields. <br/>
Now in let us say we need another constructor with only 2 arguments height and width and also the default constructor without any arguments. <br/>
class Box(var height:Int, var width:Int, var depth:Int){ <br/>
&nbsp;&nbsp;def this() = { <br/>
&nbsp;&nbsp;&nbsp;&nbsp;this(1,1,1) <br/>
&nbsp;&nbsp;} <br/>
  
&nbsp;&nbsp;def this(height:Int,width:Int) = { <br/>
&nbsp;&nbsp;&nbsp;&nbsp;this(height,width,1) <br/>
&nbsp;&nbsp;} <br/>
} <br/>

Always make the all arguments constructor as the primary constructor.
One more rule for auxiliary constructor is that it should always begin with a call to the previously defined auxiliary constructor or the primary constructor.




