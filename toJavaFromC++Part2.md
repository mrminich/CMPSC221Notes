<h1>To Java from C++ - Part 2</h1>
---
<h2>Methods in Java</h2>

Creating and using methods in Java is very similar to using methods in C++, so I'll summarize some key issues here (and move on to some specifics unique to Java):

*   The idea of writing a method once and being able to call it many times elsewhere is the same.
*   The ideas of parameters, arguments, scope, and local variables are all the same.
*   The idea of return types is the same, as is the process for calling both void and value-returning functions.
*   Methods may be overloaded in Java as in C++; a method's uniqueness depends on its signature (return type, name, and types of parameters).
*   In Java we add access specifiers (e.g. `public` or `private`) to individual methods before the return type.
*   Passing arrays to methods is very similar in Java:
    *   Like in C++, we pass arrays with empty brackets. The only difference is that in Java the brackets come before the name of the array in the function header, not after like in C++: \
 \
`public void foo(int[] passedArray, int size) \
`
    *   As in C++, only the name of the argument array is used in the function call \
 \
`foo(myArray, 4); \
`
*   Java dictates how parameters are passed based on their types:
    *   Primitive-type variables are **passed by value**. Thus, no changes made to primitive-type parameters in methods will persist. The way to get around this is to use a wrapper class, i.e. Integer. But, you won't likely need to worry about this issue too often as we get truly object-oriented.
    *   Reference-type variables (including arrays) are **passed by reference**. Thus, if you change an array that's a parameter to a method within the method, that change will persist. (By the way, that's the same behavior as in C++.) Objects are passed by reference by default.



---


<h2>Static Methods</h2>


All of the methods we saw last time in the `Math` class are methods that have the dot operator operating on the _class _name instead of on an _object_ name. This might seem a bit odd to you, but none of these methods _require_ an object. They behave exactly the same. Methods such as these that are not linked to objects of a class are called **static methods**.

Back up to when we learned about the main method in Java, which had this header:


```
public static void main(String[] args)
```


Notice that main is also `static`; it doesn't depend on any instance of the class.

**IMPORTANT:** Methods marked `static` within a class can call only other static methods within the same class. They cannot call methods that depend on instance variables of the class.

At the same time, note that a static method of any class can be called using the class name instead of an object name in another class (as with `Math` examples).

As a result of this requirement, if we write a program that's not really object-oriented, yet uses helper methods that are called from `main`, those methods must be `static`. The `static` keyword appears just where you see in `main`: after the `public` or `private` and before the return type.

 

<h3>Example</h3>


Consider the following method and call from `main`:


```
// PRE:  ________________________________________________
// POST: FCTVAL == percentage numer is of denom, e.g. 95.1 
public static double percentage(int numer, int denom)
{
  return ((double) numer) / denom * 100;
```


`} \
 \
public static void main(String[] args) \
{ \
   System.out.printf("8/11 = %.1f percent\n", percentage(8, 11)); \
}` \




---


<h2>Java API </h2>


There are many built-in libraries in Java that may come in handy. These libraries are collectively known as the [Java Application Programming Interface (or API)](http://docs.oracle.com/javase/8/docs/api/overview-summary.html). 



---


<h2>Random Numbers</h2>


Java handles random numbers via a static method of the `Math` class. Calling `Math.random()` returns a uniformly distributed random number between 0.0 and 1.0.

Unlike C++, there is no seeding necessary and no header files for using random numbers.

The static method named `random` in the `Math` class can be used to create a random decimal value that is greater than or equal to 0.0 and less than 1.0. 

For example, the following statement displays a random decimal value such as 0.34


```
System.out.println(Math.random());
```


You can manipulate this returned value by turning it into an integer or "spreading out" the range of possible values. Here are some examples:


```
num = Math.random() * 6;  // 0 <= num < 6 such as 0.11, 3.21, 5.99
num = Math.random() * 10; // 0 <= num < 10 such as 2.15, 7.73, 9.99
```


By typecasting the result to an integer and truncating the decimal places, we can ensure that only whole numbers are produced as in:


```
num = (int) (Math.random() * 6);     // 0, 1, 2, 3, 4, or 5
num = (int) (Math.random() * 2);     // 0 or 1
num = (int) (Math.random() * 6) + 1; // 1, 2, 3, 4, 5, or 6(dice roll)
num = (int) (Math.random() * 2) + 1; // 1 or 2 (coin flip)
num = (int) (Math.random() * 100) + 1;  // 1 <= num <= 100
num = (int) (Math.random() * 10) - 4;   // -4 <= num <= 5 
```


be careful to use the extra set of parentheses in the examples above since


```
num = (int) Math.random() * 6 + 1; // always equals one
```


The `Math.floor` method could be used instead of typecasting with the `(int)` cast operator as long as you store the returned value into a `double` variable. In the statement below you must assume that `num` is a `double`.


```
num = Math.floor(Math.random() * 6) + 1 
```


A general formula to use for generating a random integer over a range of values is


```
(int) (Math.random() * (HI - LO + 1)) + LO 
```


where `HI` is the highest integer and `LO` is the lowest integer in the desired range of integer values.

If you wanted something to occur based on a probability of say 40% in a game or simulation, then you could use the `Math.random` method like this


```
if (Math.random() < 0.4)
{
   System.out.println("The event occurred.");
}
else
{
   System.out.println("The event did not occur.");
} 
```


The `Math.random` value does not need to be seeded like some corresponding methods or functions in other computer languages.

Be careful not to create a logic error when answering a question like the following.

Write a method that returns "win", "lose", or "draw" each 1/3 of the time.


```
public String gameOutcome()
{
   if (Math.floor(Math.random() * 3) == 0)
   {
      return "win";
   }
   else if (Math.floor(Math.random() * 3 == 1)
   {
      return "lose";
   }

   return "draw";
}
```


The problem is that `Math.random` is being called twice and the conditional probability of a lose is not 1/3.

The method should be written the following way:


```
public String gameOutcome()
{
   int prob = Math.floor(Math.random() * 3);

   if (prob == 0)
   {
      return "win";
   }
   else if (prob == 1)
   {
      return "lose";
   }

   return "draw";
}
```


You can create reusable methods that generate random values. For example,


```
public static int rollDice()
{
   return (int) (Math.random() * 6) + 1;
}
```


Here is a method that accepts parameters to simulate a dice roll where the dice has 


```
public static int rollDice(int high)
{
   return (int) (Math.random() * high) + 1; 
}
```


Here is a method that generates a random whole number between two positive integers


```
public static int generateRandom(int low, int high)
{
   return (int) (Math.random() * (high - low + 1)) + low; 
}
```


Here is a method that generates a random whole number between two positive integers


```
public static int rollDice(int low, int high)
{
   return (int) (Math.random() * (high - low + 1)) + low; 
}
```


You can also generate and return `boolean` values instead of integers


```
public static boolean flipCoin()
{
   int num = (int) (Math.random() * 2) + 1;

   if (num == 1)
   {
      return true;
   }

   return false;
}
```


   

You can generate and return a boolean value based on a desired random percent or percentage. This example, accepts a parameter `percent` and returns a true `percent`% of the time.


```
public static boolean willItSnowOrNot(int percent)
{
   int num = (int) (Math.random() * 100) + 1;

   if (num <= percent)
   {
      return true;
   }

   return false;
}
```


or this version that accepts a `double` parameter instead of an `int`


```
public static boolean willItSnowOrNot(double percentage)
{
   double num = Math.random();

   if (num <= percent)
   {
      return true;
   }

   return false;
}
```


Here's a method that uses a flag variable to count the number of consecutive flips of heads on a coin:


```
public static int numConsecutiveFlips()
{
   boolean firstTailsFlip = false;
   int count = 0;    // number of consecutive heads

   while (!firstTailsFlip)
   {
      int num = (int) (Math.random() * 2) + 1; // 1 tails, 2 heads

      if (num == 1)
      {
         firstTailsFlip = true;
      }
      else
      {
         count++;
      }

   }

   return count;
}
```




---


<h2>The Enhanced `for` Loop (aka for each loop)</h2>


A relatively recent addition to Java is a new form of the `for` loop that allows us to iterate through an array without accessing elements by their indices. Instead, it uses a temporary placeholder variable for each element of the array.

This placeholder must be of the same type as the elements of the array and we declare it within the loop header. For the first iteration of the loop, the placeholder takes on the array element at index 0. It is then moved through the array element by element until the last element.

Here's the general form:


```
for ( array_data_type  placeholder_name :  array_name )
{
   // loop body logic, in terms of placeholder_name
}
```


Here's a simple example:


```
int[] array2 = {4, 2, 5, 2, 1};
Int sum = 0;

for (int num : array2)
{
   sum += num;
   System.out.println("next val: " + num);
}

System.out.println("The sum is " + sum);
```


One benefit to this structure is that we never risk exceeding the bounds of the array.



---


<h2>Variable Length Argument Lists</h2>


Java allows us to write methods that take in several arguments of the same type without knowing how many arguments the client will send. Essentially, what is going on is we are sending in an array.

In the method header, we give a single parameter that is of the data type for the arguments we want. Instead of using brackets like with an array, we use an ellipsis:

_data_type<code>... </code>name</em>

Here's a more specific example:

   


```
// PRE:  values contain one or more initialized values
// POST: all elements in values are displayed in a line
//       with spaces between
public static void printVals(int... values)
{
    for(int num : values)
    {
        System.out.print(num + "  ");
    }
}
```


Here `values` is essentially an array, and we process it as such. The enhanced for loop works nicely here due to not knowing the number of elements in `values`, but needing to iterate through all of them.

Consider a few example calls to this method:

`printVals(3); \
printVals(3, 6, 2);` \


**Question: **Could we have other parameters in a method with a variable-length argument list? How do you think we could do this or why do you think we can't?

 



---


<h2>`Arrays` Class Methods</h2>


Java provides a library called `Arrays` with some common array operations pre-coded for you.

To use this library, we need the following import statement:


```
import java.util.Arrays;
```


Here are some methods provided by `Arrays`:


<table>
  <tr>
   <td><strong>Method Header</strong>
   </td>
   <td><strong>Input Notes</strong>
   </td>
   <td><strong>Postcondition</strong>
   </td>
  </tr>
  <tr>
   <td><code>Arrays.<strong>fill</strong>(<em>array</em>, <em>value</em>)</code>
   </td>
   <td><code>value</code> must be initialized and of same type as <code>array</code>
   </td>
   <td>all elements of <code>array</code> from <code>0</code> to <code>array.length-1</code> are set to <code>value</code>
   </td>
  </tr>
  <tr>
   <td><code>Arrays.<strong>sort</strong>(<em>array</em>)</code>
   </td>
   <td>any value of <code>array</code> is fine, but it makes sense for it to be initialized
   </td>
   <td><code>array[0..array.length-1]</code> are sorted in ascending order
   </td>
  </tr>
  <tr>
   <td><code>Arrays.<strong>binarySearch</strong>(<em>array, key</em>)</code>
   </td>
   <td><code>array</code> must be sorted in ascending order and <code>key</code> must be a value of the same type as <code>array</code>
   </td>
   <td>A binary search has been done on <code>array[0..array.length-1]</code> and the location of <code>key</code> is returned if key is found. Otherwise, a negative value is returned.
<p>
Remember how binary search works when sending arrays with repeated values....
   </td>
  </tr>
  <tr>
   <td><code>Arrays.<strong>equals</strong>(<em>array1</em>, <em>array2</em>)</code>
   </td>
   <td><code>array1</code> and <code>array2</code> must be initialized
   </td>
   <td>Returns true if all elements of <code>array1</code> and <code>array2</code> are the same, false otherwise.
   </td>
  </tr>
</table>


 

Here are a few examples:


```
Arrays.sort(array2);

loc = Arrays.binarySearch(array2, 2);
System.out.printf("2 was found at %d", loc);

Arrays.fill(array2, 0);

if (Arrays.equals(array, array2))
{
   System.out.println("They're the same!");
}
