## Traits

This is similar to interface in java. Any class that extends trait needs to implement all the methods defined in trait.

Example:
trait Polygon{
  def getArea:Int
}

class Rectangle(length:Int,breadth:Int) extends Polygon{
  def getArea()={
    return length * breadth;
  }
}


