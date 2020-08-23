## Java Coding Standards 
*for use in Mr. Minich's Java courses*

Consistent style makes it easier for you to read code from classmates and collaborators so they can quickly understand your code. It is respectful to give up personal preferences and work with others for the overall good of an organization.

There are several popular style standards used by developers, companies, and institutions. The coding style guidelines below will be enforced in this course on graded programming assignments even if some of the instructor or textbook's examples use different or inconsistent formats. 

* Set tabs to 2 spaces. 
* Use spaces instead of tabs.
* Variable, function, and method names begin with a lowercase letter but additional words are capitalized (e.g. `numStudents` rather than `NumStudents`, `num_students`, or `numstudents`.) One name for this notation is **camelCase**. 
* Class names begin with an uppercase letter (e.g. `BankAccount` rather than `bankAccount`.) 
* Constant names are UPPERCASE with underscores to separate words (e.g. `BANK_FEE` rather than `BANKFEE` or `bankFee`.) 
* Use single spaces after keywords (`while (num < 100)` rather than `while(num<100)`. Surround binary operators (e.g. `num + 3` rather than `num+3`). 
* Curly braces must line up vertically with a whole line occupied by each curly brace as in

```
while (num < 100)
{
   num++;
}
```

rather than

```
while (num < 100) {
   num++;
}
```

or 

```
while (num < 100)
{  num++;
} 
```

or 

```
while (num < 100) {  num++;  }

```

* Use constants instead of hardwiring magic numbers into your code.

Instead of

`System.out.println(quantity * 9.99 * 0.06 + " is the amount of tax.";` 
 
you should use

```
const double PRICE_PER_MOVIE = 9.99;
const double TAX_RATE = 0.06;
cout << quantity * PRICE_PER_MOVIE * TAX_RATE << " is the amount of tax." << endl;
```

* Every method, except for `main` and overridden library methods, must have a comment.
* Limit the size of your methods to about 30 lines of code.
* Avoid the use of `continue` or `break`.

Each Java program is a collection of one or more source files. The executable program is obtained by compiling these files. Organize the material in each file as follows:

* `package` statements
* `import` statements
* A comment explaining the purpose of this file
* A `public class`
* Other classes

The following header comment should be in the format recognized by the javadoc utility. Start with a `/**`, and use the `@author` tag:

```
/**
 * THE NAME OF THE CLASS
 * @author YOUR NAME
 */
```

Example

```
/**
 * ASCIIArt
 * @author John Doe
 */
```

* Each class should be preceded by a class comment explaining the purpose of the class.
First, list all `public` features, then all `private` features.

Within the `public` and `private` section, use the following order:

1. Instance Fields
2. Static Fields
3. Constructors
4. Instance Methods
5. Static Methods
6. Inner classes

* Place a blank line after every method.

* All non-`final` instance and class variables must be `private`. 
* Methods and `final` variables can be either `public` or `private` as appropriate.
* All members of a class must be either `public` or `private`. Do not use the default visibility (`package`) or `protected`.
* Avoid `static` variables (except ones that are `final`) when possible.
* Every method (except for `main`) starts with a comment in javadoc format.

```
   Convert calendar date into Julian day.
   Note: This algorithm is from Press et al., Numerical Recipes
   in C, 2nd ed., Cambridge University Press, 1992
   @param day day of the date to be converted
   @param month month of the date to be converted
   @param year year of the date to be converted
   @return the Julian day number that begins at noon of the
   given calendar date.
*/
public static int dat2jul(int day, int month, int year)
{
   . . . 
}
```

* Methods must be short usually with at most 30 lines of code. You should break up complex computations into separate methods.
* Variables and constants must be accompanied by descriptive comments when they are declared.

```
{ 
  double totalCost = 0.0; // total cost of widgets purchased
  int numWidgets = 0;     // total # of widgets purchased
}
```

* Do not declare multiple variables on the same line:

`` int dimes = 0, nickels = 0;``

Instead, use two separate statements on different lines so you can include descriptive comments:

```
int dimes = 0;    // # of dimes in change returned
int nickels = 0;  // # of nickels in change returned
```

* Do not spread one statement over two lines of code with the comma operator:

```
int dimes = 0,
nickels = 0;
```

* Constants must be declared with the keywords `static final`
* When declaring array variables, group the `[]` with the type, not the variable.

`` int[] values;``

rather than

`` int values[]; ``

* Avoid the "`if ... if ... else`" trap that is sometimes called the dangling else error.
```
if ( ... )
  if ( ... ) ...; 
else ...;
```

will not do what the indentation level suggests and is difficult to debug. Always use curly braces ``{ ... }`` with EVERY ``if`` statement and every ``else`` clause:


```
if ( ... )
{
  if ( ... )
  {
      ...;
  }
}
else
{
  ...;
}
```

* Use `for` loops only when a variable runs from somewhere to somewhere with some constant increment/decrement:

```
for (int i = 0; i < a.length; i++)
{
  System.out.println(a[i]);
} 
```

* Do not use the `for` loop for weird constructs such as

```
for (a = a / 2; count < ITERATIONS; System.out.println(xnew))
```

Convert that `for`  loop into a `while` loop so it is clearer to fellow programmers.

```
a = a / 2;

while (count < ITERATIONS)
{  . . .
   System.out.println(xnew);
}
```

* Names must be reasonably long and descriptive. Your program is considered to be self-documenting if its variable names are descriptive. Use `firstPlayer` instead of `fp`. Do not drop vowels as in ` frstPlyr`. 
* You may use single letters such as `i` as `for` loop control variables.   
* Use blank lines freely to separate parts of a method that are logically distinct.  
* Use blank lines above and below all `if` statements, loops, methods, and other structures. You must even use blank lines around nested loop and `if` statements as in

```
if (num > 1
{       
// blank line here
  if (num < 3)
  {
    System.out.println(2);
  }                     
  // blank line here
}
```

* Use a blank space around every binary operator (except the ++ and -- operators):

`x1 = (-b - Math.sqrt(b * b - 4 * a * c)) / (2 * a);`

rather than

`x1=(-b-Math.sqrt(b*b-4*a*c))/(2*a);`

* Place a blank space after (and not before) each comma or semicolon. Do not place a space before or after a parenthesis or brace in an expression. 
* Place spaces around the ` ( . . . ) ` part of an `if`, `while`, or `for` statement.
* Every line of code must fit on 80 columns. If you must break a statement, add an indentation level for the continuation:


```
a[n] = ...
   + .................;
```

* Start the indented line with an operator (if possible).
* Even if the control expression of an `if` or `while` structure must be broken up over several lines of code, use curly braces around the body of the structure _even if the body consists of only one statement:_

```
if ( ...................
     && ..................
     || .......... )
{
   . . .
}
```

If it were not for the curly braces, it would be hard to separate the continuation of the condition visually from the statement to be executed.

* Opening and closing braces must line up vertically:

```
while (i < n)
{
  System.out.println(a[i]);                    \
  i++;
}
```

* Some programmers don't line up vertical braces but place the { behind the key word:

```
while (i < n) { // DON'T
   System.out.println(a[i]);
   i++;
}
```

Doing so makes it hard to check that the braces match for beginner coders especially.

<h4>Unstable Layout</h4>


Some programmers take great pride in lining up certain columns in their code:

```
firstRecord = other.firstRecord;
lastRecord  = other.lastRecord;
cutoff      = other.cutoff;
```

This is undeniably neat but he layout is not _stable_ under change. A new variable name that is longer than the preallocated  number of columns requires that you move _all_ entries around:

```
firstRecord = other.firstRecord;
lastRecord  = other.lastRecord;
cutoff      = other.cutoff;
marginalFudgeFactor = other.marginalFudgeFactor;
```

This is just the kind of trap that makes you decide to use a short variable name like `mff` instead.

When using `/* ... */` comments, don't "beautify" them with additional asterisks:

```
/* comment—don't do this
 * more comment
 * more comment
 */
```

It looks neat, but it is a major disincentive to update the comment. Some people have text editors that lay out comments and, even if you do, you don't know whether the next person who maintains your code has such an editor. 

Instead, format long comments like this:

```
/*
   comment
   more comment
   more comment
*/
```

or this:

```
/*
comment
more comment
more comment
*/
```

These comments are easier to maintain as your program changes. If you have to choose between pretty but unmaintained comments and ugly comments that are up to date, truth wins over beauty.
