**To Java from C++ - Part 1**

It is assumed that you took the C++-based prerequisite courses CMPSC 121 & 122.



---



## Similarities to C++

Many aspects of Java are _identical_ to C++ including:

*   assignment statements and the assignment operator =
*   declarations for `int`, `double`, and `char` variables (more below)
*   arithmetic operators: `+, -, *, /, %`
*   relational operators: `>, >=, &lt;, &lt;=, ==, !=`
*   logical operators: `&&, ||, !`
*   Boolean expressions
*   `if `statements
*   `switch `structures
*   `for `loops
*   `while `loops
*   `do`...`while` loops

---



## Differences with C++


### Program Framework and Classes



*   Java is fully object-oriented, so everything must be written in the context of a class. 

*   The name of the class must be the same as the name of the source file (e.g. a class called `HelloWorld` must be saved in a file named  `HelloWorld.java 
`
*   A Java executable program is a class that must have a method named `main` with the header

    
`public static void main(String[] args)` 

*   This method must be marked **static**, meaning that it cannot be called on objects of the class.
*   The array `args` could be used to send in command-line arguments.
*   Any class could technically have a `main` method. For example, if you create a class named `Player `you might want to add a `main` method so that you can test this class without creating a more practical class called `Game `that would likely have a more meaningful `main` method. 


This is the typical framework for a Java class (and therefore a typical Java source code file): 



```
public class ClassName
{
   public static void main(String[] args)
   {
      // logic goes here!
   }
}
```



### Command Line Output

There are two basic commands for outputting information: 




*   <code>System.out.print<strong>(</strong></code> <em>argument</em> <strong><code>);</code></strong>         prints the <em>argument</em> without a line break.  
 
This would be similar to the C++ statement          <code>cout &lt;< <em>argument</em></code>; 

*   <code>System.out.println<strong>(</strong></code> <em>argument</em> <strong><code>);</code></strong>     prints the argument with a line break. 
 
This would be similar to the C++ statement          <code>cout &lt;< <em>argument </em><&lt; endl;</code> 


The arguments in the examples above are technically Strings. However, you can use the + concatenation operator + to concatenate (i.e. join) strings with numeric values as in: 



```
int hourPart = 9;
int minPart = 45;
System.out.println(hourPart +  ":" + minPart + " a.m.");
```


 


### Command Line Input

We use the `Scanner` class for command line input. This has a few differences from C++: 




*   Streams are not used. Everything is a function.
*   Input code is specific to the type of variable that you are reading from the input values.

The import statement         `import java.util.Scanner;`

is required above the class when using a Scanner object.  
 
Then in the main method, you declare and instantiate a Scanner object like this:

<code>Scanner input = new Scanner(System.in);<strong> 
</strong></code>

To read from the input, make a call to one of the following methods for numeric data:



*   `nextInt()`
*   <code>nextDouble()<strong> 
</strong></code>

Here is an example that puts it all together: 



```
Scanner input = new Scanner(System.in);
System.out.print("Enter the hour: ");
hourPart = input.nextInt();
System.out.print("Enter the minute: ");
```


`minPart = input.nextInt();` \


To read in text, we have the following two methods:



*   `next()`                      which reads text up to whitespace
*   `nextLine()      `which reads text up to a line break (like `getline `in C++)

 
Note that there is **not** a `nextChar()` method. But here's a workaround:

`char choice; 
System.out.print("Option: "); 
choice = input.next().charAt(0);` 


Finally, you can use the `hasNext()` method of Scanner to test if there is more input, for inputting an unknown number of data points terminated with Ctrl+D on Unix-based systems or Ctrl+C on Windows-based systems. You can also use `hasNextDouble()` and analogous methods to test if the next input is of type `double`, and thus use a character sentinel to end input. For example, you could use: 



```
while (input.hasNext())
{
     // Code to process data with input.nextInt() or the like
}
```


 


### Formatted Output

Java provides a more advanced output method called `printf()`. See [this page](http://alvinalexander.com/programming/printf-format-cheat-sheet) which is a decent reference  as well as this explanation:



*   Write one string for the output with placeholders in it for numeric data. This is the first argument.
*   List all outputs in order as the second and subsequent arguments.
*   Some placeholder formats:
    *   `%d` for an `int` value.
    *   `%f` for an `double` or `float` value.
    *   `%3d` for an `int` value printed to the right of a field of width 3. (Of course, the 3 can change. This is analogous to `cout &lt;< setw(3) &lt;< ...`.)
    *   `%.2f` for an `double` or `float` value with 2 decimal places. (Of course, the 2 can change.) 


**Example 1: **The following code prints out the time exactly as in an earlier example:

`System.out.printf("Time: %d:%d\n", hourPart, minPart);` 


**Example 2: **Here's an example block of code that computes and prints sales tax: 


`final double TAX_PCT = 0.06;    // sales tax rate 
double price = 0.0;             // price of an item in $ 
double finalPrice = 0.0;        // price of item w/ tax, $ 
 
System.out.print("Enter price: $"); 
price = input.nextDouble(); 
 
final_price = price * (1 + TAX_PCT); 
 
System.out.printf("Price with tax is $%.2f.\n", final_price);` 




---



## Data Types in Java: Scalars


### Primitive Types

Data types in Java fall into two categories: **primitive types**, i.e. the basic types that are not objects, and **reference types**, i.e. those that are objects. Nearly everything in Java is an object, but there are primitives that operate just as we know them from C++:



*   The types `int`, `double`, and `char` are the same as in C++.
*   C++'s `bool` type in `boolean` in Java.

We declare these just like we did in C++ and can use assignment statements with them just as we did in C++.

 


### Reference Types

Most everything else in Java is a reference type. For example, type `String` (note the uppercase "S" here) is built into the language, and is a reference type.

Reference types are objects. They're declared as we'd expect, for example:


```
String myString;
```


However, to use them, we need to call upon their constructors. We do so using the **<code>new</code></strong> keyword. We could follow the previous statement with this code:


```
myString = new String();
```


It's common to do this all in one line of code:


```
String myString = new String();
```


The latter is common for local variables. The former would be necessary when `myString` would be a data member of a class and we needed to initialize it in a constructor.

The same philosophy applies to instantiating other built-in classes and classes you make yourself.

 


### Wrapper Types

The designers of Java did create a way for the language to be fully object-oriented. Each of the primitive data types has a corresponding **wrapper class**, whose objects would contain a sole data member: a primitive type variable. For working with basic calculations and local variables, this is overkill for sure. But, these wrapper classes will come in handy later when we want to pass variables into certain methods.

In addition, these classes provide some helpful methods, as we saw the other day: `Integer.parseInt()` and `Double.parseDouble()`. Each takes a single String argument and returns it converted to type `int` or `double`. When we're collecting input from most sources that aren't the command line, we'll need these conversions.

Wrapper classes include `Integer`, `Double`, `Character`, and `Boolean`.

Here's a simple example that shows how to wrap an `int` in an `Integer` and unwrap it: 



```
int hourPart = 0;
Integer hourPartWrapped;


System.out.print("Enter the hour: ");
hourPart = input.nextInt();
hourPartWrapped = new Integer(hourPart);
       
System.out.printf("Hour: %d\n", hourPartWrapped.intValue());
```




---



## Data Types in Java: Arrays

Arrays are also reference types. As a result, we need to specify that we're dealing with an array in two places: 




*   In declaring the array, when we give the type before the name, we must include **_empty_** brackets after any other type to indicate that we're dealing with an array.
*   We then use the `new` keyword similarly to declaring a scalar reference type variable, but give brackets with the physical size of the array inside afterward.

Here's a general form of declaring and initializing an array separately: 


<code><em>type</em>[] arrayName; 
arrayName = new <em>type</em>[size];</code> 


Here's an example:


```
int[] data;
data = new int[100];
```


We could do this on one lines as well, provided the array stays local to one method:


```
int[] data = new int[100];
```


Much of what we know about arrays from C++ applies to Java:



*   Arrays are homogeneous, linear data structures
*   Arrays provide direct access to elements via indices and the subscript operator `[]`
*   Array indices start at 0

 


### Array Initializer

Java also provides an array initializer. We can list the elements of an array in braces (`{ }`) and thus assign all of the contents of an array at once. If the array is initialized in the data dictionary, the general form is:

<code>int[] <em>arrayName </em></code>= { <em>list of comma-separated values</em> };

For example, we might write the following code:


```
int[] testValues = {14, 82, 12, 49, 17};
```


If the array is initialized outside of the data dictionary, the general form is:

<code>int[] <em>arrayName</em></code>;

_arrayName<code> = new int[]{ </code>list of comma-separated values<code> };</code></em>

For example, we might write the following code:


```
int[] testValues;
testValues = new int[]{14, 82, 12, 49, 17};
```


 


### Sizing

Arrays in Java know their sizes. We simply add `.length` to the name of an array to get its size. For example, `testValues.length` would be 5 in the context of the above example.

A key difference between C++ and Java is that we can **dynamically size** arrays in Java. In other words, we could use a variable for the physical size of an array.

Still, we should maintain the idea of using a constant physical size separately from a variable for an array's logical size, as we generally do not know how many input data points we will have.

 



---



## Built-in Math Functions: The `Math` Class

Recall those `math.h` functions we used in C++? As you'd expect, Java provides similar functionality. Instead of importing anything though, we simply put `Math.` in front of any of these methods. 

Here are several methods from the `Math` utility class:


<table>
  <tr>
   <td><strong>Function</strong>
   </td>
   <td><strong>Conditions on the Input (Preconditions)</strong>
   </td>
   <td><strong>Output</strong>
   </td>
   <td><strong>Example</strong>
   </td>
   <td><strong>Result </strong>
   </td>
  </tr>
  <tr>
   <td><code>Math.abs</code>
   </td>
   <td>only that it has been initialized, if it's a variable
   </td>
   <td>absolute value of the input
   </td>
   <td><code>Math.abs(-3)</code>
   </td>
   <td>3
   </td>
  </tr>
  <tr>
   <td><code>Math.sqrt</code>
   </td>
   <td>must be nonnegative
   </td>
   <td>square root of the input
   </td>
   <td><code>Math.sqrt(25)</code>
   </td>
   <td>5
   </td>
  </tr>
  <tr>
   <td><code>Math.exp</code>
   </td>
   <td>only that it has been initialized, if it's a variable
   </td>
   <td><em>e<sup>x</sup></em>, where <em>x</em> is the input
   </td>
   <td><code>Math.exp(1)</code>
   </td>
   <td>2.718
   </td>
  </tr>
  <tr>
   <td><code>Math.log</code>
   </td>
   <td>must be positive
   </td>
   <td>ln <em>x</em>, where <em>x</em> is the input
   </td>
   <td><code>Math.log(100)</code>
   </td>
   <td>4.6052
   </td>
  </tr>
  <tr>
   <td><code>Math.log10</code>
   </td>
   <td>must be positive
   </td>
   <td>log<sub>10</sub> <em>x</em>, where <em>x</em> is the input
   </td>
   <td><code>Math.log10(100)</code>
   </td>
   <td>2
   </td>
  </tr>
</table>


The basic trig functions and their inverses are also available. Note that all use radians. 


<table>
  <tr>
   <td><strong>Function</strong>
   </td>
   <td><strong>Conditions on the Input (Preconditions)</strong>
   </td>
   <td><strong>Output</strong>
   </td>
  </tr>
  <tr>
   <td><code>Math.sin</code>
   </td>
   <td rowspan="3" >angle is measured in radians
   </td>
   <td>sine of angle
   </td>
  </tr>
  <tr>
   <td><code>Math.cos</code>
   </td>
   <td>cosine of angle
   </td>
  </tr>
  <tr>
   <td><code>Math.tan</code>
   </td>
   <td>tangent of angle
   </td>
  </tr>
  <tr>
   <td><code>Math.asin</code>
   </td>
   <td>input is between -1.0 and 1.0
   </td>
   <td>arcsine of input
<p>
in range -π/2 through π/2
   </td>
  </tr>
  <tr>
   <td><code>Math.acos</code>
   </td>
   <td>input is between -1.0 and 1.0
   </td>
   <td>arccosine of input
<p>
in range 0.0 through π
   </td>
  </tr>
  <tr>
   <td><code>Math.atan</code>
   </td>
   <td>input is between -1.0 and 1.0
   </td>
   <td>arctangent of input
<p>
in range -π/2 through π/2
   </td>
  </tr>
</table>


There are other methods in the `Math` library. See [Oracle's official documentation](http://docs.oracle.com/javase/6/docs/api/java/lang/Math.html) to learn more.

**Example:** Here's an example block of Java code that computes the base-2 logarithm of a number input by the user:


```
Scanner input = new Scanner(System.in);   // for user input

double x = 0.0;               // number whose base-2 log user wants
double result = 0.0;          // base-2 logarithm of x

// INPUT
System.out.print("Enter a number to get its base-2 log: ");
x = input.nextDouble();

// PROCESS 
result = Math.log(x)/Math.log(2.0);     // invoke change of base

// OUTPUT
System.out.println("The base-2 log of " + x + " is " + result);
```


 


### Constants

The `Math` library also defines constants `Math.PI` and `Math.E`.
