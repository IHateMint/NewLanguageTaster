## Why Scala ?
Scala is functional language. Function can be a parameter of other function, saving function as a variable, or function returning a function is possible.
```
object Timer {
    def oncePerSecond(callback: () => Unit) {
        while (true) { callback(); Thread sleep 1000 }
    }
    def timeFlies() {
        println("time flies like an arrow")
    }
    def main(args: Array[String]) {
        oncePerSecond(timeFlies)
    }
}
```
Though all will be dealt later again more precisely, `() => Unit` function type is every function that doesn't receive any parameters and returning nothing. (This is quite similar to `void` in cpp)

## Basic Compile and Execution
```
object HelloWorld {
    def main(args: Array[String]) {
        println("Hello, world")
    }
}
```
To compile the example above, simply run
```
scalac HelloWorld.scala
```
This results in a few class files inside current directory. We can now find `HelloWorld.class`

To execute after compiling,
```
scala -classpath . HelloWorld
```

## Using Scala with Java
`java.lang` package's every classes are usable without importing.

## Variables
`val` is immutable variable, and `var` is mutable variable.
String should be inside double quotes.
```
var a : String = "Foo1";
val b : String = "Foo2";
val (var1: String, var2: String) = Pair("apple", "pie");    # Assigning multiple variables at once is possible.
```

There are 3 different variable scopes.
`Fields` -> Variables belonging to an object.
`Method Params` -> Variables used to pass value inside a method, when the method is called. Always immutable(val)
`Local Vars` -> Variables declared inside a method. Both var and val are possible.

## Looping
```
for( w <- 0 to 10)
{
    println(w);
}
```
```
for( w <- 0 until 10)
{
    println(w);
}
```
```
var rank = 0;
val ranklist = List(1,2,3,4,5,6,7,8,9,10);  # Same as (1 to 10).toList
for( rank <- ranklist){
    println(rank);
}
```
```
var rank = 0;
val ranklist = (1 to 10).toList
var output = for{ rank <- ranklist
            if rank > 4; if rank != 8 }
            yield rank
for (rank <- output)
{
    println(rank)
}
```

## Class
Basic class is such as below.
```
import java.io._

class Human(val weight: Int, val height: Int) {
    var x: Int = weight
    var y: Int = height

    def grow(d_weight: Int, d_height: Int){
        x = x + d_weight
        y = y + d_height
        println("I have grown : " + x + " in weight");
        println("I have grown : " + y + " in height");
    }
}

object Ex {
    def main(args: Array[String]) {
        val Me = new Human(60, 180);
        Me.grow(5, 10);
    }
}
```


