## Factory Method Pattern
The factory method is used to offer a single interface to instantiate one of the multiple classes. <br/>

Example: <br/>
abstract class Room{ <br/>
&nbsp;&nbsp;def bookingPrice : Double <br/>
&nbsp;&nbsp;def facilities : List[String] <br/>
&nbsp;&nbsp;def availability: Int <br/>
&nbsp;&nbsp;def book(noOfRooms : Int) <br/>
} <br/>

object Room{ <br/>
&nbsp;&nbsp;val STANDARD = 0 <br/>
&nbsp;&nbsp;val DELUXE = 1 <br/>
&nbsp;&nbsp;val SUPER_DELUXE = 2 <br/>
  
&nbsp;&nbsp;private class StandardRoom extends Room{ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;private var _availability = 20 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def bookingPrice = 70 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def facilities = List("Queen Bed","TV","Chair","Table","Fan") <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def availability = _availability <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def book(noOfRooms: Int)={ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;_availability =  _availability - noOfRooms <br/>
&nbsp;&nbsp;} <br/>
} <br/>
  
&nbsp;&nbsp;private class DeluxeRoom extends Room{ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;private var _availability = 10 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def bookingPrice = 90 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def facilities = List("Bed","TV","Chair","Table","AC") <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def availability = _availability <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def book(noOfRooms: Int)={ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;_availability =  _availability - noOfRooms <br/>
&nbsp;&nbsp;&nbsp;&nbsp;} <br/>
&nbsp;&nbsp; <br/>
  
&nbsp;&nbsp;private class SuperDeluxeRoom extends Room{ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;private var _availability = 5 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def bookingPrice = 120 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def facilities = List("Double Bed","Single Bed","TV","Sofa","Table","AC") <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def availability = _availability <br/>
&nbsp;&nbsp;&nbsp;&nbsp;override def book(noOfRooms: Int)={ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;_availability =  _availability - noOfRooms <br/>
&nbsp;&nbsp;&nbsp;&nbsp;} <br/>
&nbsp;&nbsp;} <br/>
  
&nbsp;&nbsp;def apply(roomType:Int):Room = { <br/>
&nbsp;&nbsp;&nbsp;&nbsp;roomType match{ <br/>
&nbsp;&nbsp;&nbsp;&nbsp;case SUPER_DELUXE  => new SuperDeluxeRoom() <br/>
&nbsp;&nbsp;&nbsp;&nbsp;case DELUXE  => new DeluxeRoom() <br/>
&nbsp;&nbsp;&nbsp;&nbsp;case _  => new StandardRoom() <br/>
&nbsp;&nbsp;&nbsp;&nbsp;} <br/>
&nbsp;&nbsp;} <br/>
  
} <br/>
