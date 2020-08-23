**Java Coding Standards**
for use in Mr. Minich's Java courses

While the coding style guidelines below will be enforced on graded programming assignments in this course, others sets of popular and worthwhile style standards may be found at authoritative sources such as Oracle & Google.

This coding style guide is a simplified version of one that has been used with good success both in industrial practice and for academic high school and college courses. A style guide is a set of mandatory requirements for layout and formatting. Uniform style makes it easier for you to read code from your instructor, classmates, collaborators, and coworkers. It is also easier for others to grasp the essence of your programs quickly. If you already have programming experience in Java or another language, you may be initially uncomfortable at giving up some fond habits. However, it is a sign of professionalism to set aside personal preferences in minor matters and to compromise for the benefit of your group.
These guidelines are necessarily somewhat dull. They also mention features that you may not yet have seen in class. Here are the most important highlights:

*   Tabs are set every two spaces even if some of the instructor's demo programs have different tab sizes. But use spaces instead of tabs if your IDE (editor) software allows it such as repl.it. 
*   Variable and method names begin with a lowercase letter but additional words are capitalized (e.g. `numStudents` rather than `NumStudents`, `num_students`, or `numstudents`.) This notation is often called **camelCase**. 
*   Class names start with an uppercase letter (e.g. `BankAccount` rather than `bankAccount`.) 
*   Constant names are UPPERCASE, with an occasional underscore to separate words (e.g. `BANK_FEE` rather than `BANKFEE` or `bankFee`.) 
*   There are spaces after keywords (`while (num < 100)` rather than `while(num<100)` and surrounding binary operators (e.g. `num + 3` rather than `num+3`). 
*   Curly braces must line up vertically with a whole line occupied by each curly brace as in

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

*   No **magic numbers** may be used, that is numbers hard-wired into computation areas of a program. You should use constants where appropriate. \
 \
Instead of \
 \
`System.out.println(quantity * 9.99 * 0.06 + " is the amount of tax.";` \
 \
you should use \
 \
`const double PRICE_PER_MOVIE = 9.99; \
const double TAX_RATE = 0.06; \
 \
cout << quantity * PRICE_PER_MOVIE * TAX_RATE << " is the amount of tax." << endl;` \

*   Every method, except for `main` and overridden library methods, must have a comment. \

*   At most 30 lines of code may be used per method. \

*   No `continue` or `break` is allowed. \

*   All non-`final` variables must be `private`.

<h3>Source Files</h3>


Each Java program is a collection of one or more source files. The executable program is obtained by compiling these files. Organize the material in each file as follows: \




*   `package` statement, if appropriate \

*   `import` statements \

*   A comment explaining the purpose of this file \

*   A `public class \
`
*   Other classes, if appropriate \


The following header comment should be in the format recognized by the javadoc utility. Start with a `/**`, and use the `@author` tag:


```
/**
 * THE NAME OF THE CLASS
 * @author YOUR NAME
 */
Example
/**
 * ASCIIArt
 * @author John Doe
 */
```


<h3>Classes</h3>


Each class should be preceded by a class comment explaining the purpose of the class.

First list all `public` features, then all `private` features.

Within the `public` and `private` section, use the following order:



1. Instance Fields
2. Static Fields
3. Constructors
4. Instance Methods
5. Static Methods
6. Inner classes

Leave a blank line after every method.

All non-`final` variables must be `private`. (However, instance variables of a `private` inner class may be `public`.) Methods and `final` variables can be either `public` or `private`, as appropriate.

All features must be tagged `public` or `private`. Do not use the default visibility (that is, `package` visibility) or the `protected` attribute.

Avoid `static` variables (except `final` ones) whenever possible. In the rare instance that you need `static` variables, you are permitted one `static `variable per class.

<h3>Methods</h3>


Every method (except for `main`) starts with a comment in javadoc format.


<table>
  <tr>
   <td> 
   </td>
   <td><code>/** \
   Convert calendar date into Julian day. \
   Note: This algorithm is from Press et al., Numerical Recipes \
   in C, 2nd ed., Cambridge University Press, 1992 \
   @param day day of the date to be converted \
   @param month month of the date to be converted \
   @param year year of the date to be converted \
   @return the Julian day number that begins at noon of the \
   given calendar date. \
*/ \
public static int dat2jul(int day, int month, int year) \
{  \
   . . . \
} \
</code>
   </td>
  </tr>
</table>


Methods must have at most 30 lines of code. The method signature, comments, blank lines, and lines containing only braces are not included in this count. This rule forces you to break up complex computations into separate methods.

<h3>Variables and Constants</h3>


Variables and constants must be accompanied by descriptive comments when they are declared.


<table>
  <tr>
   <td> 
   </td>
   <td><code>{   \
   double totalCost = 0.0; // total cost of widgets purchased \
   int numWidgets = 0;     // total # of widgets purchased \
    \
} \
</code>
   </td>
  </tr>
</table>


Do not declare multiple variables on the same line:


<table>
  <tr>
   <td> 
   </td>
   <td><code>int dimes = 0, nickels = 0;</code>
   </td>
  </tr>
</table>


Instead, use two separate statements on different lines so you can include descriptive comments:


<table>
  <tr>
   <td> 
   </td>
   <td><code>int dimes = 0;    // # of dimes in change returned \
int nickels = 0;  // # of nickels in change returned \
</code>
   </td>
  </tr>
</table>


Do not spread one statement over two lines of code with the comma operator:


<table>
  <tr>
   <td> 
   </td>
   <td><code>int dimes = 0,  \
    nickels = 0;  \
</code>
   </td>
  </tr>
</table>


In Java, constants must be declared with the keyword `final`. If the constant is  to be used by multiple methods, declare it as `static final`. If a constant is not to be used in other classes, use `static final`. \


Do not use _magic numbers!_ A magic number is a numeric constant embedded in code, without a constant definition. Any number except -1, 0, 1, and 2 is considered magic:


<table>
  <tr>
   <td> 
   </td>
   <td><code>if (p.getX() < 300) \
</code>
   </td>
  </tr>
</table>


Use constants with `final` instead:


<table>
  <tr>
   <td> 
   </td>
   <td><code>final double WINDOW_WIDTH = 37;    // width of window in inches \
. . . \
if (p.getX() < WINDOW_WIDTH) \
</code>
   </td>
  </tr>
</table>


Even the most reasonable cosmic constant is going to change one day. You think there are 365 days per year? Your customers on Mars are going to be pretty unhappy about your silly prejudice. Make a constant so it can be edited by future developers that maintain the computer program.


<table>
  <tr>
   <td> 
   </td>
   <td><code>public static final int DAYS_PER_YEAR = 365;</code>
   </td>
  </tr>
</table>


so that multiple occurrences of the value can easily be changed at once by editing the constant's declaration statement. \


When declaring array variables, group the `[]` with the type, not the variable.


<table>
  <tr>
   <td> 
   </td>
   <td><code>int[] values; </code>
<p>
rather than<code> \
 \
int values[]; // this was typical in the older language C though \
</code>
   </td>
  </tr>
</table>


<h3>Control Flow</h3>


<h4>if Statement</h4>


Avoid the "`if ... if ... else`" trap. This is sometimes called the dangling else error. The code


<table>
  <tr>
   <td> 
   </td>
   <td><code>if ( ... ) \
   if ( ... ) ...; \
else ...; \
</code>
   </td>
  </tr>
</table>


will not do what the indentation level suggests, and it can take hours to find such a bug. Always use a pair of curly braces `{ ... }` with EVERY if statement and every else clause:


<table>
  <tr>
   <td> 
   </td>
   <td><code>if ( ... ) \
{ </code>
<p>
<code> \
   if ( ... )</code>
<p>
<code>   { \
      ...;</code>
<p>
<code>   }</code>
<p>
<code> \
} \
else</code>
<p>
<code>{</code>
<p>
<code>   ...;</code>
<p>
<code>}</code>
   </td>
  </tr>
</table>


<h4>for Statement</h4>


Use `for` loops only when a variable runs from somewhere to somewhere with some constant  \
increment/decrement:


<table>
  <tr>
   <td> 
   </td>
   <td><code>for (int i = 0; i < a.length; i++)</code>
<p>
<code>{ \
   System.out.println(a[i]);</code>
<p>
<code>} \
</code>
   </td>
  </tr>
</table>


Do not use the `for` loop for weird constructs such as


<table>
  <tr>
   <td> 
   </td>
   <td><code>for (a = a / 2; count < ITERATIONS; System.out.println(xnew)) \
</code>
   </td>
  </tr>
</table>


Convert that `for`  loop into a `while` loop so it is clearer to fellow programmers.


<table>
  <tr>
   <td> 
   </td>
   <td><code>a = a / 2;</code>
<p>
<code> \
while (count < ITERATIONS) \
{  . . . \
   System.out.println(xnew); \
} \
</code>
   </td>
  </tr>
</table>


<h4>Nonlinear Control Flow</h4>


Avoid the `switch` statement, because it is easy to fall through accidentally to an unwanted case. Use `if/else` instead.        

Avoid the `break` or `continue` statements. Use another `boolean` variable to control the execution flow.

<h4>Exceptions</h4>


Do not tag a method with an overly general exception specification:


<table>
  <tr>
   <td> 
   </td>
   <td><code>Widget readWidget(Reader in) \
   throws Exception // Bad \
</code>
   </td>
  </tr>
</table>


Instead, specifically declare any checked exceptions that your method may throw:


<table>
  <tr>
   <td> 
   </td>
   <td><code>Widget readWidget(Reader in) \
   throws IOException, MalformedWidgetException // Good \
</code>
   </td>
  </tr>
</table>


Do not "squelch" exceptions:


<table>
  <tr>
   <td> 
   </td>
   <td><code>try \
{  \
    double price = in.readDouble(); \
} \
catch (Exception e) \
{} // Bad \
</code>
   </td>
  </tr>
</table>


Beginners often make this mistake "to keep the compiler happy". If the current method is not appropriate for handling the exception, simply use a throws specification and let one of its callers handle it.

<h3>Lexical Issues</h3>


<h4>Naming Conventions</h4>


The following rules specify when to use upper- and lowercase letters in identifier names.           



*   All variable and method names and all data fields of classes are in lowercase (maybe with an occasional upperCase in the middle); for example, `firstPlayer`.   
*   
*   All constants are in uppercase letters with underscore characters used to separate two or more words; for example, `CLOCK_RADIUS` rather than `clockRadius` or `CLOCKRADIUS`. \

*   All class and interface names start with uppercase letter and are followed by lowercase letters with each word, after the first word, beginning with a capital letter; for example, `BankTeller` rather than `bankteller`, `BankTeller`, or `bank_teller`. \


Names must be reasonably long and descriptive. Your program is considered to be self-documenting if its variable names are descriptive. Use `firstPlayer `instead of `fp`. No drppng f vwls. Local variables that are fairly routine can be short (`ch`, `i`) as long as they are really just boring holders for an input character, a loop variable, and so on.      

 

Also, do not use `ctr`, `c`, `cntr`, `cnt`, `c2` for variables in your method. Surely these variables all have specific purposes and can be named to remind the reader of them (for example, `current`, `next`, `previous`, `result`, . . ).

<h4>Indentation and White Space</h4>


Use tab stops every three columns. That means you will need to change the tab stop setting in your editor! 

Use blank lines freely to separate parts of a method that are logically distinct.  

Use blank lines above and below all if statements, loops, methods, and other structures. You must even use blank lines around nested loop and if statements as in


<table>
  <tr>
   <td> 
   </td>
   <td><code>if (num > 1) \
{</code>
<p>
<code>                       // blank line here \
   if (num < 3)</code>
<p>
<code>   { \
      System.out.println(2);</code>
<p>
<code>   }</code>
<p>
<code>                       // blank line here \
}</code>
   </td>
  </tr>
</table>


Use a blank space around every binary operator (except the ++ and -- operators):


<table>
  <tr>
   <td> 
   </td>
   <td><code>x1 = (-b - Math.sqrt(b * b - 4 * a * c)) / (2 * a); // Good</code>
<p>
<code>x1=(-b-Math.sqrt(b*b-4*a*c))/(2*a);//Bad</code>
   </td>
  </tr>
</table>


Leave a blank space after (and not before) each comma or semicolon. Do not leave a space before or after a parenthesis or bracket in an expression. Leave spaces around the` ( . . . ) `part of an `if`, `while`, `for`, or `catch` statement.

Every line must fit on 80 columns. If you must break a statement, add an indentation level for the continuation:


<table>
  <tr>
   <td> 
   </td>
   <td><code>a[n] = .................................................. \
   + .................; \
</code>
   </td>
  </tr>
</table>


Start the indented line with an operator (if possible).

Even if the control expression of an `if` or `while `structure must be broken up over several lines of code, be sure to use curly braces around the body of the structure _even if the body consists of only one statement:_


<table>
  <tr>
   <td> 
   </td>
   <td><code>if ( ................... \
     && .................. \
     || .......... ) \
{   \
   . . . \
}</code> \

   </td>
  </tr>
</table>


If it were not for the curly braces, it would be hard to separate the continuation of the condition visually from the statement to be executed.

<h4>Braces</h4>


Opening and closing braces must line up vertically:


<table>
  <tr>
   <td> 
   </td>
   <td><code>while (i < n) \
{    \
   System.out.println(a[i]);                    \
   i++; \
} \
</code>
   </td>
  </tr>
</table>


Some programmers don't line up vertical braces but place the { behind the key word:


<table>
  <tr>
   <td> 
   </td>
   <td><code>while (i < n) { // DON'T \
   System.out.println(a[i]); \
   i++; \
} \
</code>
   </td>
  </tr>
</table>


Doing so makes it hard to check that the braces match.

<h4>Unstable Layout</h4>


Some programmers take great pride in lining up certain columns in their code:


<table>
  <tr>
   <td> 
   </td>
   <td><code>firstRecord = other.firstRecord; \
lastRecord  = other.lastRecord; \
cutoff      = other.cutoff; \
</code>
   </td>
  </tr>
</table>


This is undeniably neat, but the layout is not _stable_ under change. A new variable name that is longer than the preallocated  number of columns requires that you move _all_ entries around:


<table>
  <tr>
   <td> 
   </td>
   <td><code>firstRecord = other.firstRecord; \
lastRecord  = other.lastRecord; \
cutoff      = other.cutoff; \
marginalFudgeFactor = other.marginalFudgeFactor; \
</code>
   </td>
  </tr>
</table>


This is just the kind of trap that makes you decide to use a short variable name like `mff` instead.

When using `/* ... */` comments, don't "beautify" them with additional asterisks:


<table>
  <tr>
   <td> 
   </td>
   <td><code>/* comment—don't do this \
 * more comment \
 * more comment \
 */ \
</code>
   </td>
  </tr>
</table>


It looks neat, but it is a major disincentive to update the comment. Some people have text editors that lay out comments. But even if you do, you don't know whether the next person who maintains your code has such an editor. 

Instead, format long comments like this:


<table>
  <tr>
   <td> 
   </td>
   <td><code>/* \
   comment \
   more comment \
   more comment \
*/ \
</code>
   </td>
  </tr>
</table>


or this:


<table>
  <tr>
   <td> 
   </td>
   <td><code>/* \
comment \
more comment \
more comment \
*/ \
</code>
   </td>
  </tr>
</table>


These comments are easier to maintain as your program changes. If you have to choose between pretty but unmaintained comments and ugly comments that are up to date, truth wins over beauty.
