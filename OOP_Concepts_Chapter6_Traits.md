## Traits

This is similar to interface in java. Any class that extends trait needs to implement all the methods defined in trait.

Example: <br/>
trait Polygon{ <br/>
  def getArea:Int <br/>
} <br/>

class Rectangle(length:Int,breadth:Int) extends Polygon{ <br/>
  def getArea()={ <br/>
    return length * breadth; <br/>
  } <br/>
} <br/>


