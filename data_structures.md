# Data Structures

## Arrays (Mutable)
Arrays preserve order, can contain duplicates, and are mutable.

scala> val numbers = Array(1, 2, 3, 4, 5, 1, 2, 3, 4, 5)
numbers: Array[Int] = Array(1, 2, 3, 4, 5, 1, 2, 3, 4, 5)

updating element of array:
scala> numbers(3) = 10

## Lists (Immutable)
Lists preserve order, can contain duplicates, and are immutable.

scala> val numbers = List(1, 2, 3, 4, 5, 1, 2, 3, 4, 5)
numbers: List[Int] = List(1, 2, 3, 4, 5, 1, 2, 3, 4, 5)

Cannot update element of list
scala> numbers(3) = 10
<console>:9: error: value update is not a member of List[Int]
              numbers(3) = 10
  
## Sets (Immutable)
Sets do not preserve order and have no duplicates

scala> val numbers = Set(1, 2, 3, 4, 5, 1, 2, 3, 4, 5)
numbers: scala.collection.immutable.Set[Int] = Set(5, 1, 2, 3, 4)

## Tuple (Immutable)
A tuple groups together simple logical collections of items without using a class.

scala> val hostPort = ("localhost", 80)
hostPort: (String, Int) = (localhost, 80)
Unlike case classes, they don’t have named accessors, instead they have accessors that are named by their position and is 1-based rather than 0-based.

scala> hostPort._1
res0: String = localhost

scala> hostPort._2
res1: Int = 80
Tuples fit with pattern matching nicely.

hostPort match {
  case ("localhost", port) => ...
  case (host, port) => ...
}
Tuple has some special sauce for simply making Tuples of 2 values: ->

scala> 1 -> 2
res0: (Int, Int) = (1,2)

## Maps (both Mutable and Immutable map is available)
It can hold basic datatypes.

Map(1 -> 2)
Map("foo" -> "bar")
This looks like special syntax but remember back to our discussion of Tuple that -> can be used to create Tuples.

Map() also uses that variable argument syntax we learned back in Lesson #1: Map(1 -> "one", 2 -> "two") which expands into Map((1, "one"), (2, "two")) with the first element being the key and the second being the value of the Map.

Maps can themselves contain Maps or even functions as values.

Map(1 -> Map("foo" -> "bar"))
Map("timesTwo" -> { timesTwo(_) })

Operations in Class mutable.Map

WHAT IT IS	WHAT IT DOES
Additions and Updates:	 
ms(k) = v	(Or, written out, ms.update(x, v)). Adds mapping from key k to value v to map ms as a side effect, overwriting any previous mapping of k.
ms += (k -> v)	Adds mapping from key k to value v to map ms as a side effect and returns ms itself.
ms += (k -> v, l -> w)	Adds the given mappings to ms as a side effect and returns ms itself.
ms ++= kvs	Adds all mappings in kvs to ms as a side effect and returns ms itself.
ms put (k, v)	Adds mapping from key k to value v to ms and returns any value previously associated with k as an option.
ms getOrElseUpdate (k, d)	If key k is defined in map ms, return its associated value. Otherwise, update ms with the mapping k -> d and return d.
Removals:	 
ms -= k	Removes mapping with key k from ms as a side effect and returns ms itself.
ms -= (k, l, m)	Removes mappings with the given keys from ms as a side effect and returns ms itself.
ms --= ks	Removes all keys in ks from ms as a side effect and returns ms itself.
ms remove k	Removes any mapping with key k from ms and returns any value previously associated with k as an option.
ms retain p	Keeps only those mappings in ms that have a key satisfying predicate p.
ms.clear()	Removes all mappings from ms.
Transformation:	 
ms transform f	Transforms all associated values in map ms with function f.
Cloning:	 
ms.clone	Returns a new mutable map with the same mappings as ms.

