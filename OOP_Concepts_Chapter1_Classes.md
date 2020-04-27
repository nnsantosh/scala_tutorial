## Classes

Following is the concise syntax to create classes in scala:
class Customer(var id:Int, var name:String)

To create objects of type Customer:
val cust = new Customer(101,"XYZ Corp")

There is no need of getters and setters to access the class attributes or modify the class attributes"
cust.id
cust.name

cust.id=102
cust.name = "ABC Corp"

The main benefit of setter methods in java is that it allows to add some validation. But the same thing can be achieved in scala as shown below:
class Circle {

  private var pradius : Int = 0
  def this(r:Int){
    this()
    pradius = r
  }

  def radius : Int = pradius
  def radius_(r:Int): Unit ={
    if( r < 0){
      throw new Exception("negative value not allowed")
    } else
    this.pradius = r
  }
  
  def main(args: Array[String]){
    val circle = new Circle(5)
    println("radius of circle is "+circle.radius)
    circle.radius_(-10)
    println("radius of circle is "+circle.radius)
  }
  
 Output of above main method will be:
 radius of circle is 5
 Exception in thread "main" java.lang.Exception: negative value not allowed
	at com.example.Circle.radius_(Circle.scala:14)
	at com.example.CreateCircle$.main(CreateCircle.scala:8)
	at com.example.CreateCircle.main(CreateCircle.scala)

Process finished with exit code 1

So if there is no need to impose validation in setter then you can use single line class definition with all public attributes.

