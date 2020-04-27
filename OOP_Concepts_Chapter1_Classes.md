## Classes

Following is the syntax for create classes in scala: <br/>
class Circle{} <br/>
abstract class Circle{} <br/>
private class Circle{} <br/>
protected class Circle{} <br/>

But you cannot create public class like this: public class Cirlce{} since scala class is public by default. <br/>
Unlike java scala source file can contain multiple public classes. <br/>
You don't need to match the source file name with the public class name. <br/>

Consider below example to create class in scala: <br/>
class Circle{ <br/>
 var radius = 0 <br/>
 def draw = {println("Drawing the circle of radius "+radius)} <br/>
} <br/>

Whenever you define a public variable in class scala compiler does the following by default: <br/>
It creates reader and writer methods: <br/>
reader(getter) : radius <br/>
writer(setter): radius_ <br/>

val c = new Circle <br/>
Reader can be called as:  c.radius <br/>
Writer can be called as: c.radius_ = (5) or c.radius = 5 <br/>


Following is the concise syntax to create classes in scala with public attributes:
class Customer(var id:Int, var name:String) <br/>

To create objects of type Customer: <br/>
val cust = new Customer(101,"XYZ Corp") <br/>

There is no need of getters and setters to access the class attributes or modify the class attributes" <br/>
cust.id <br/>
cust.name <br/>

cust.id=102 <br/>
cust.name = "ABC Corp" <br/>

The main benefit of setter methods in java is that it allows to add some validation. But the same thing can be achieved in scala as shown below:
class Circle { <br/>

  private var pradius : Int = 0 <br/>
  def this(r:Int){ <br/>
    this() <br/>
    pradius = r <br/>
  } <br/>

  def radius : Int = pradius <br/>
   def radius_= (r:Int)= {
    if( r < 0){
      throw new Exception("negative value not allowed")
    } else
    pradius = r
  } <br/>
   
  def main(args: Array[String]){ <br/>
    val circle = new Circle(5) <br/>
    println("radius of circle is "+circle.radius) <br/>
    circle.radius_(-10) <br/>
    println("radius of circle is "+circle.radius) <br/>
  } <br/>
  
 Output of above main method will be: <br/>
 radius of circle is 5 <br/>
 Exception in thread "main" java.lang.Exception: negative value not allowed <br/>
	at com.example.Circle.radius_(Circle.scala:14) <br/>
	at com.example.CreateCircle$.main(CreateCircle.scala:8) <br/>
	at com.example.CreateCircle.main(CreateCircle.scala) <br/>

Process finished with exit code 1 <br/>

So if there is no need to impose validation in setter then you can use single line class definition with all public attributes. <br/>

