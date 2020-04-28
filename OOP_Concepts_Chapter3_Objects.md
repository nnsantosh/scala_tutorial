## Objects

A Scala object is a special type of class that can have one and only one instance. A scala object represents a Singleton class.

### When do we use Scala objects?
For Static utility methods. Scala objects act like static classes in java.

### Some Rules
1. Objects can extend or inherit classes, but the opposite is not allowed. You cannot extend an object to create a class or another object. <br/>
2. Objects cannot have a public constructor. <br/>
3. Scala will instantiate the object on their first use. Next time onwards, it uses the same instance. If you are not using the object, Scala doesn't instantiate it. <br/>

### Scala object for Singleton pattern
import java.util._ <br/>
import java.io._ <br/>
Object appConfig{ <br/>
  private val prop = new Properties() <br/>
  prop.load(new FileInputStream("config.properties")) <br/>
  def config = prop <br/>
} <br/>
Use it as below: <br/>
app.config.getProperty("dbUser") <br/>
app.config.getProperty("database") <br/>

### Apply Method
1. Apply method is the default method of a class or object. <br/>
2. You can call the apply method without a method name. <br/>

Example of using apply method: <br/>
import java.util._ <br/>
import java.io._ <br/> 
Object appConfig{ <br/>
  private val prop = new Properties() <br/>
  prop.load(new FileInputStream("config.properties")) <br/>
  def apply(s:String) = prop.getProperty(s) <br/>
} <br/>

Now you can call it using appConfig.apply("dbUser") <br/>
However since you used apply a magic happens and that is you can invoke it by using the object name like this: <br/>
appConfig("dbUser") <br/>
There is no need to use the apply keyword. <br/>

### Companion Object
It is an extension of singleton object. <br/>
If you define a scala class and scala object with the same name in same source file they become companion of each other. <br/>

### Why do we need companion object?
1. Separation of concerns using a Companion <br/>
2. Implementing Factory Method or a Builder pattern <br/>

### Separation of Concerns
You can define all instance level fields and methods in a class. <br/>
If you have some global static fields and methods define them in object. <br/>
Object takes care of all static concerns and Class takes care of all non static concerns. <br/>

Example: <br/>
class Graph(path:String){ <br/>
&nbsp;&nbsp;println("Load the Graph from file") <br/>
&nbsp;&nbsp;def numEdges = 506 <br/>
&nbsp;&nbsp;def numVertices = 305 <br/>
&nbsp;&nbsp;def persist(StorageLevel:Int)=println("Returns a new persisted graph") <br/>
} <br/>

object Graph{ <br/>
&nbsp;&nbsp;val DISK_ONLY = 0 <br/>
&nbsp;&nbsp;val MEMORY_ONLY = 1 <br/>
&nbsp;&nbsp;val MEMORY_ONLY_COMPRESSED = 2 <br/>
&nbsp;&nbsp;val MEMORY_AND_DISK = 3 <br/>
&nbsp;&nbsp;val MEMORY_AND_DISK_COMPRESSED = 4 <br/>
&nbsp;&nbsp;def apply(path:String) = new Graph(path) <br/>
} <br/>

With the above example we can instantiate graph object as below: <br/>
val graph = Graph("some location") <br/>
But since the constructor is not private we can also instantiate using: <br/>
val graph = new Graph("Some location") <br/>
If you want to prevent users from using constructor then make it private: <br/>
class Graph private(path:String){ <br/>
&nbsp;&nbsp;println("Load the Graph from file") <br/>
&nbsp;&nbsp;def numEdges = 506 <br/>
&nbsp;&nbsp;def numVertices = 305 <br/>
&nbsp;&nbsp;def persist(StorageLevel:Int)=println("Returns a new persisted graph") <br/>
} <br/>
 
This way only the apply method of the companion object will have to be used to instantiate Graph class. <br/>






