## Case Classes

When you create a case class in scala all the fields are immutable or val only by default. <br/>
Also you get default implementation of equals, hashcode and toString methods in addition to the constructor. <br/>
Also Scala creates associated companion object of the same name with apply method using which you can instantiate the class without using new keyword. <br/>
Also Scala provides copy method using which you can create copy of this class instance easily. <br/>

case class Circle(radius:Int){ <br/>
} <br/>

//Create instance of Circle using apply method <br/>
val myCircle = Circle(5) <br/>
//Creating copy using copy method <br/>
val myCircleCopy = myCircle.copy() <br/>
You can also specify only the parameters that you want to change in the copy method. <br/>



