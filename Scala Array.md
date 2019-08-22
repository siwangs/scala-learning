## Scala Array

### Key Points

• Use an **Array** if the length is fixed, and an **ArrayBuffer** if the length can vary.
• **Don’t use** new when supplying initial values.
• Use () to access elements.
• Use for (elem <- arr) to traverse the elements.
• Use for (elem <- arr if . . . ) . . . yield . . . to transform into a new array.
• Scala and Java arrays are **interoperable**; with ArrayBuffer, use scala.collection.
JavaConversions.



#### Introduction use for array

```scala
val nums = new Array[int](10) // an Array with 10 integers, all initiailized with 0

import scala.collection.mutable.ArrayBuffer
val b = ArrayBuffer[Int]() // an empty Array buffer, ready to hold integers
b += 1 // add additional elements
b.trimEnd(5) // remove the last five elements
b.insert(2,6) // insert before index 2
b.remove(2)
b.remove(2,3) // first parameter to remove the index 2 element and second tell how many elements to remove

b.toArray // convert to array, work with list
b.toBuffer // convert to array buffer.

```



#### Traversing Array and Array Buffers

 in scala, 1 to 10  including the last element while until exclude the last elements.

 common use cases:

```scala
0 until 10 by 2 // Range (0,2,4...)
0 until 10 by -1 // Range(...2, 1, 0) to start from the end of Array
```



**Transferring Arrays** 

the Best way to transform an Array is to use Yield?

**Important Functions**

*filter*, *map* same to *for/yield*， but filter looks like handy with functional programming

```scala
b.filter(_ % 2 == 0).map (2 * _	);

```

**Common Methods**

```scala
import scala.collection.mutable.ArrayBuffer

Array(1, 7, 2, 9).sum
ArrayBuffer("Mary", "had", "a", "little", "lamb").max
val b = ArrayBuffer(1, 7, 2, 9)
val bSorted = b.sorted;
val bDesc = b.sortWith(_ > _);
val a = Array(1, 7, 2， 9)
scala.util.Sorting.quickSort(a)
```



Other Common method can be found from *ScalaDoc*

**Multidimensional Arrays**

```scala
val matrix = Array.ofDim[Double] (3, 4)

```

**Inter operating with Java**



### Assignment

#### write code snippet that sets a to an array of n random integers

Markdown all the **libraries**



```scala
import java.awt.datatransfer.{DataFlavor, SystemFlavorMap}
import java.util.TimeZone

import scala.collection.mutable
import scala.collection.mutable.ArrayBuffer
import scala.util.{Random, Sorting}
/* Task 1
 Write a code snippet that sets a to an array of n random integers between 0 (inclusive) and n
(exclusive).
*/
def randomIntArray(n: Int): Array[Int] = {
    val result = for (i < 0 to n) yield Random.nextInt(n)
    result.toArray/*
    val result = for (i < 0 until n) yield Random.nextInt(n)
    result
    */
    // result is a type of IndexedSeq[Int] need to add toArray
    }

/*
2. Write a loop that swaps adjacent elements of an array of integers. For example, Array(1,
2, 3, 4, 5) becomes Array(2, 1, 4, 3, 5).
*/

val array = Array(1, 2, 3, 4, 5)

array.grouped(2).flatMap(_.reverse).toArray // Best Solution, check grouped(2) and flatMap method

for ( i <- 0 until a.length-1 by 2) 
{val tmp: Int = a(i+1); 
 a(i+1) = a(i);
 a(i) = tmp;
 a}

/* 3 using for/yield to create an new array
*/
for (i <- a.indices.grouped(2).flatMap(_.reverse).toArray) yield a(i)


```

