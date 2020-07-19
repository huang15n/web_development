welcoemto php and MySQL, two of the most important and widely used web develoment tools around 


this will teach you how to create interact web applications from the simplest order from through to complex, secure web applications. try not to leave out any basic conceptsm but we do cover them at speed, this should you give up to speed quickly 


you realize the limitations of this approach. It stays the same unless you physically updte it 
we have deliberately focused this on real world app and how to implement these aspects in PHP. 




# PHP intro 

php is a server-side scripting language designed specifically for the web 
you can embed php code that will be executed each time the page is visisted 
it was conveived in 1994. it was adopted by talented people gone through several major rewrites to bring us the broad, mature product 



php is an open-source project, which means you have access to the source code and have freedom to alter and redisribute it, which is ofically supported 


PHP had well-designed object-oriented features, which continued to be refined and improved in PHP. If you learned to program in Java or C++, you will find the features (and generally the syntax) that you expect, such as inheritance, private and protected attributes and methods, abstract classes and methods, interfaces, constructors, and destructors. You will even find some less common features such as iterators and traits.
PHP allows you to implement simple tasks simply, and equally easily adpats to implementing large apps using a framework based on design patter such as Model View Controller behind the engine powers php 



flexibility, portability, strong oop support, ease of learning and use, scalability, performance, availability 

scale down to something 
commodity servers 
database integration 
built-in libraries 
using the Open Database Connectivity ODBC standard
it was for the general public and it came to fruition 
there were ambitious plans and subsequent complications that made it difficult for the team 

under the hood, it incldues a refactor that powers it, which resulted in a significant performance boost to many apps and remain usable 


# MySQL intro 
MySQL  is a robust relational databse managment system. a dataase enables you to efficiently store, search, sort, and retrieve data 
the server controls access to data to ensure that multiple users can work with it concurrently, to provide fast access to it, and to ensure that only authorized users can obtain access 
hence, MySQL is a multiuser, multihreaded server 
it uses structured query language which has been publicly avaialable  when setting out to build a website 

you may end up with a hybrid architecture with multiple datstores 
these choices are dependent on the others  to be portable between os and web servers 

it is available at no cost 
multicore scalability 
thread pooling 
pluggavle authentication 
plugin API 
event scheduling 
automated upgrades 
diagnostic tools 




# PHP Crash Course 
a quick overview of PHP syntax and constructs
you might fil some gaps in your knowledge, get up to speed quickly 
instead of plowing through yet another syntax and function reference  


In general, the value of the action attribute is the URL that will be loaded when the user clicks the Submit button. The data the user has typed in the form will be sent to this URL via the HTTP method specified in the method attribute, either get (appended to the end of the URL) or post (sent as a separate message).
You should consider adopting a coding standard for field names so that all field names throughout your site use the same format. This way, you can more easily remember whether, for example, you abbreviated a word in a field name or put in underscores as spaces.



Embedding PHP in HTML

```PHP
------ orderform.php ------

<form action="processorder.php" method="post"> <table style="border: 0px;">
<tr style="background: #cccccc;">
<td style="width: 150px; text-align: center;">Item</td>
<td style="width: 15px; text-align: center;">Quantity</td> </tr>
<tr>
<td>Tires</td>
<td><input type="text" name="tireqty" size="3"
maxlength="3" /></td> </tr>
<tr>
<td>Oil</td>
<td><input type="text" name="oilqty" size="3"
maxlength="3" /></td> </tr>
<tr>
<td>Spark Plugs</td>
<td><input type="text" name="sparkqty" size="3"
maxlength="3" /></td> </tr>
<tr>
	<td colspan="2" style="text-align: center;"><input type="submit" value="Submit Order" /></td>
</tr> </table> </form>
```


_________________


```PHP
------ processorder.php ------
<!DOCTYPE html> <html>
<head>
<title>Bob's Auto Parts - Order Results</title>
</head> <body>
<h1>Bob's Auto Parts</h1>
<h2>Order Results</h2> </body>

<?php 
echo 'Order Processed';

?>

</html>
--------------------------------
```


none of the raw php is visiblae because the interpreter has run through the script and replaced it with the output from the script 
this means that from PHP you can produce clean HTML viewable with any browser
in other words, the user's browser does not need to understand PHP 


PHP has been interpreted and executed on the web server as distinct from JS and other client side technologies interpreted and executed within a web browser on a user's machine 


# PHP Tags 

PHP tag is similar to all HTML tags because they all begin with a less than (<) symbol and end with a greater than (>) symbol. These symbols (<?php and ?>) are called PHP tags. They tell the web server where the PHP code starts and finishes. Any text between the tags is interpreted as PHP.
Any text outside these tags is treated as normal HTML. The PHP tags allow you to escape from HTML.

### XML style
<?php echo '<p>Order processed.</p>'; ?>
This is the tag style that we use in this book; it is the preferred PHP tag style. The server administrator cannot turn it off, so you can guarantee it will be available on all servers, which is especially important if you are writing applications that may be used on different installations. This tag style can be used with Extensible Markup Language (XML) documents. In general, we recommend you use this tag style.
### Short style
<? echo '<p>Order processed.</p>'; ?>
This tag style is the simplest and follows the style of a Standard Generalized Markup Language (SGML) processing instruction. To use this type of tag—which is the shortest
to type—you either need to enable the short_open_tag setting in your config file or compile PHP with short tags enabled. You can find more information on how to use this tag style in Appendix A. The use of this style is not recommended for use in code you plan to distribute. It will not work in many environments as it is no longer enabled by default.






# PHP Statements
You tell the PHP interpreter what to do by including PHP statements between your opening and closing tags. 


using the echo construct has a very simple result: It prints
(or echoes) the string passed to it to the browser. 

Notice that there is a semicolon at the end of the echo statement. Semicolons separate statements in PHP much like periods separate sentences in English.

leaving off the semicolon is a common synta error that is easily made 


### Whitespace

These two snippets of HTML code produce identical output because they appear the same to the browser. However, you can and are encouraged to use whitespace sensibly in your HTML as an aid to humans—to enhance the readability of your HTML code. The same is true for PHP. You don’t need to have any whitespace between PHP statements, but it makes the code much easier to read if you put each statement on a separate line.  are equivalent 


### Comments 
comments in code act as notes to poeple readingthe code. comments can be used to explain the purpose of the script 
the PHP interpreter ignores any text in comments 
essentially, the parser skips over the comments, making them equivalent to whitespace 

/* \*/
with both these styles, eveything after the comemnt symbol # or // is a comment until you reach the end of the line or the ending tag, whiever comes first 

adding dynamic comment 


### Adding Dynamic Content 
the main reason for using a server side scripting lnaguage is to be ave to provide dynamic ocntent to a site's users 
this is an important application because content tha changes according to user's needs or over time will keep visotrs coing back to a site 

```PHP
<!DOCTYPE html> <html>
<head>
<title>Bob's Auto Parts - Order Results</title>
</head> <body>
<h1>Bob's Auto Parts</h1>
<h2>Order Results</h2> </body>

<?php 
echo '<p>Order Processed at';
echo date("H:i, jS F Y");
echo "</p>";

?>

</html>
```

### Calling functions 
this is general form that function calls take 
php has an extensive library of functions you can use when developing apps 
notice that it passes a string text to the funciton inside a pair of parentheses 
the element within the parentheses is called the function's argment or parameter 

### Using the date() function 
the date() funciton expects the argument you pass it to be a format string, representing the style of output you would lke 
each letter in the string represents one part of the date and time 
H is the hour in 24 hr format with leading zeros where required, i is the minutes with a leading zero where required, j is the day of the month without a leading zero, S represents the ordinal suffix in this case th, and F is the full name of the month 



### Accessing Form Variables 



form variable : within your PHP script, you ca acces each form field as a php variabel whose name relates to the name of. the fomr filed 
you can recognize variable names in PHP because they all start with a dollar sign ($)


you may access the contents of the field in the following way:
$_POST['variable_name']
$_POST is an array containing data submitted via an HTTP POST request -- that is, the form method was set to POST
 there are three of these arrays that may contain fomr data 

 $_POST, $_GET and $_REQUEST 

If the form was submitted via the POST method, the data entered in the variable_name box will be stored in $_POST['variable_name']. If the form was submitted via GET, the data will be in $_GET['variable_name']. In either case, the data will also be available in $_REQUEST['variable_name'].

One of the $_GET or $_POST arrays holds the details of all the form variables. Which array is used depends on whether the method used to submit the form was GET or POST, respectively. In addition, a combination of all data submitted via GET or POST is also available through $_REQUEST.



to copy the value of one variable into another, you use the assigment operator, which in PHP is an equal sign = 
<!DOCTYPE html> <html>
<head>
<title>Bob's Auto Parts - Order Results</title>
</head> <body>
<h1>Bob's Auto Parts</h1>
<h2>Order Results</h2> </body>

<?php 

$tireqty = $_POST['tireqty'];
$oilqty = $_POST["oilqty"];
$sparkqty = $_POST["sparkqty"];

echo $tireqty;
echo $oilqty;
echo $sparkqty;

echo '<p>Order Processed at ';
echo date("H:i, jS F Y");
echo "</p>";

echo '<table border = "1"><tr><td>tire quantity</td><td>oil quantity</td><td>spark quantity</td></tr> <tr><td>'.htmlspecialchars($tireqty).'</td><td>'.htmlspecialchars($oilqty).'</td><td>'.htmlspecialchars($sparkqty).'</td></tr></table>';

?>

</html>


### String Concatenation 
echo prints the value user typed in each form field, followed by some explanatory text 

if you look closely at the echo statements, you can see that the variable name and following text have a period (.) between them 


this period is the string concatenation oeprator, which adds strings pieces fo text together 
you will often use it when sending output to the browserwith echo 




###### Note: never use +variable+ on string convatenation in php 


thi is equivalent to the statement. either format is alid, and which one you use is a matter of personal taste 
this process, replacing a variable with its contents within a string, is known as interpolation 
note that the interpolation is a feature of double-quoted strings only 
you cannot place variable names inside a single quoted string in this way 


### Variable and Literals 

the variables and string concatented together in eahc of the echo statemetns in the sample script are different types of things 
variables are symbols for data 
the strings are data themselves 


###### there is also a third way of specifying strigs using the heredoc syntax <<<, which will be familar to Perl 
heredoc syntax allows you to specify long trings tidily, by sepcifying an end mark that will be used to terminate the string 
```PHP
echo <<<theEnd 
line1 
line2 
line3
theEnd 
```


###### the token theEnd is entirely arbitary. it just needs to be guaranteed not to appear in the text. to close a heredoc string, place a closing toekn at the start of a line 

### Understanding Identifiers 
identifiers are the names of variables 

■ Identifiers can be of any length and can consist of letters, numbers, and underscores.
■ Identifiers cannot begin with a digit.
■ In PHP, identifiers are case sensitive. $tireqty is not the same as $TireQty. Trying to use them interchangeably is a common programming error. Function names are an exception to this rule: Their names can be used in any case.
■ A variable can have the same name as a function. This usage is confusing, however, and should be avoided. Also, you cannot create a function with the same name as another function.


One of the features of PHP is that it does not require you to declare variables before using them. A variable is created when you first assign a value to it. See the next section for details.
You assign values to variables using the assignment operator (=) as you did when copying one variable’s value to another.




### Examining Variable Types

A variable’s type refers to the kind of data stored in it. PHP provides a set of data types. Different data can be stored in different data types.


PHP supports the following basic data types:
■ Integer—Used for whole numbers
■ Float (also called double)—Used for real numbers
■ String—Used for strings of characters
■ Boolean—Used for true or false values
■ Array—Used to store multiple data items  
■ Object—Used for storing instances of classes  


Three special types are also available: NULL, resource, and callable.
Variables that have not been given a value, have been unset, or have been given the specific
value NULL are of type NULL.
###### Certain built-in functions (such as database functions) return variables that have the type resource. They represent external resources (such as database connections). You will almost certainly not directly manipulate a resource variable, but frequently they are returned by functions and must be passed as parameters to other functions.
###### Callables are essentially functions that are passed to other functions.




### Type Strength
PHP is called a weakly typed or dynamically typed language. In most programming languages, variables can hold only one type of data, and that type must be declared before the variable can be used, as in C. In PHP, the type of a variable is determined by the value assigned to it.


```PHP 
<?php 

echo "hello world";
$variable = 100;
echo $variable;
$variable = "what is this";
echo $variable;

?> 
```


this ability to change types transparently on the fly can be extremely useful 
remember automagically knows what data type you put into your variable 
it returns the data with the same data type you retrieve it from the variabel 

### Type Casting 
you can pretend that a variable or value is of a different type of usinga type cast 
this feature works indentically to the way it works in C 



### Variable Variables
PHP provides one other type of variable: the variabel variable 
variable variables enable you to change the name of a variable dynamically 
PHP allows a lot of freedom in this area 
all languages enable you to ange the value of a variable, but not many allow you to change the variable's type, and even fewer allow you to change variable's name 

a variable variable works by using the value of one variable as the name of another 
```PHP 
<?php 
$name_1 = 'name_2';
$$name_1 = 19;
# this is actually $name_2 = 19;
echo "$$name_1 = $name_2 = ".$$name_1;

?> 
```

### Declaring and Using Constants

A constant stores a value just like a variable, but its value is set once and then cannot be changed elsewhere in the script.
```PHP
<?php 

define('PI_VALUE', 3.14159265389);

echo "PI_VALUE=".PI_VALUE;
phpinfo();

?> 
```

Notice that the names of the constants appear in uppercase. This convention, borrowed from C, makes it easy to distinguish between variables and constants at a glance. Following this convention is not required but will make your code easier to read and maintain.


One important difference between constants and variables is that when you refer to a constant, it does not have a dollar sign in front of it. If you want to use the value of a constant, use its name only.


As well as the constants you define, PHP sets a large number of its own. An easy way to obtain an overview of them is to run the phpinfo() function:
###### phpinfo();

This function provides a list of PHP’s predefined variables and constants, among other useful information. One other difference between variables and constants is that constants can store only boolean, integer, float, or string data. These types are collectively known as scalar values.




### Understanding Variable Scope

The term scope refers to the places within a script where a particular variable is visible. The six basic scope rules in PHP are as follows:
■ Built-in superglobal variables are visible everywhere within a script.

■ Constants, once declared, are always visible globally; that is, they can be used inside
and outside functions.

■ Global variables declared in a script are visible throughout that script, but not inside
functions.

■ Variables inside functions that are declared as global refer to the global variables of the
same name.

■ Variables created inside functions and declared as static are invisible from outside the function but keep their value between one execution of the function and the next.  

■ Variables created inside functions are local to the function and cease to exist when the function terminates.


The arrays $_GET and $_POST and some other special variables have their own scope rules. They are known as superglobals and can be seen everywhere, both inside and outside functions.
The complete list of superglobals is as follows:
■ $GLOBALS—An array of all global variables (Like the global keyword, this allows you to
access global variables inside a function—for example, as $GLOBALS['myvariable'].)
■ $_SERVER—An array of server environment variables
■ $_GET—An array of variables passed to the script via the GET method
■ $_POST—An array of variables passed to the script via the POST method
■ $_COOKIE—An array of cookie variables
■ $_FILES—An array of variables related to file uploads
■ $_ENV—An array of environment variables
■ $_REQUEST—An array of all user input including the contents of input including $_GET, $_POST, and $_COOKIE (but not including $_FILES)
■ $_SESSION—An array of session variables



### Using Operators


Operators are symbols that you can use to manipulate values and variable by performing an operation on them 

In general, operators can take one, two, or three arguments, with the majority taking two 
the = symbol and an exprssion on the right side
these arguments are called operands -- that is, the things that are being operated upon 


### Arithmetic Operators
Arithmetic operators are straightforward; they are just the normal mathematical operators.

Operator
+ - * / %



Addition and subtraction work as you would expect. The result of these operators is to add or subtract, respectively, the values stored in the $a and $b variables.


Multiplication and division also work much as you would expect. Note the use of the asterisk as the multiplication operator rather than the regular multiplication symbol, and the forward slash as the division operator rather than the regular division symbol.

The modulus operator returns the remainder calculated by dividing the $a variable by the $b variable. 


You should note that arithmetic operators are usually applied to integers or doubles. If you apply them to strings, PHP will try to convert the string to a number. If it contains an e or
an E, it will be read as being in scientific notation and converted to a float; otherwise, it will be converted to an integer. PHP will look for digits at the start of the string and use them as the value; if there are none, the value of the string will be zero.




### String Operators

You’ve already seen and used the only string operator. You can use the string concatenation operator to add two strings and to generate and store a result much as you would use the addition operator to add two numbers


### Assignment Operators

You’ve already seen the basic assignment operator (=). Always refer to this as the assignment operator and read it as “is set to.”



### Values Returned from Assignment

Using the assignment operator returns an overall value similar to other operators. When working out the value of an expression, you can use parentheses to increase the precedence of a subexpression, as shown here. 


### Combined Assignment Operators
In addition to the simple assignment, there is a set of combined assignment operators. Each of them is a shorthand way of performing another operation on a variable and assigning the result back to that variable. 
$a += 5;
This is equivalent to writing
$a = $a + 5;

Combined assignment operators exist for each of the arithmetic operators and for the string concatenation operator. 

PHP’s Combined Assignment Operators
+=
-=
*=
/=
%=
.=



### Pre- and Post-Increment and Decrement

The pre- and post-increment (++) and decrement (--) operators are similar to the += and -= operators, but with a couple of twists.
All the increment operators have two effects: They increment and assign a value.


As you can probably guess, the behavior is similar for the -- (decrement) operator. However, the value of $a is decremented instead of being incremented.


### Reference Operator

The reference operator (&, an ampersand) can be used in conjunction with assignment. Normally, when one variable is assigned to another, a copy is made of the first variable and stored elsewhere in memory. 
```PHP
<?php 

$variable_only = 4;
$reference = &$variable_only;
$reference = 10;

echo $variable_only;

?> 

```
References can be a bit tricky. Remember that a reference is like an alias rather than like a pointer. Both $a and $b point to the same piece of memory. 

You can change this by unsetting one of them as follows:
unset($a);
Unsetting does not change the value of $b (7) but does break the link between $a and


### Comparison Operators
The comparison operators compare two values. Expressions using these operators return either of the logical values true or false depending on the result of the comparison.
The Equal Operator
The equal comparison operator (==, two equal signs) enables you to test whether two values are equal. For example, you might use the expression
$a == $b
to test whether the values stored in $a and $b are the same. The result returned by this
expression is true if they are equal or false if they are not.

You might easily confuse == with =, the assignment operator. Using the wrong operator will work without giving an error but generally will not give you the result you wanted. In general, nonzero values evaluate to true and zero values to false. 

### Other Comparison Operators
PHP also supports a number of other comparison operators. A summary of all the comparison operators. One to note is the identical operator (===), which returns true only if the two operands are both equal and of the same type.

==
===
!=
!==
<>
< > <= >=

### Logical Operators

The logical operators combine the results of logical conditions. 

PHP supports logical AND, OR, XOR (exclusive or), and NOT.
The set of logical operators and their use is summarized in Table 1.4.

! NOT && AND
|| OR and AND
or OR xor XOR
Use
!$b
$a && $b
$a || $b
$a and $b $a or $b $a x or $b

The and and or operators have lower precedence than the && and || operators. 




### Bitwise Operators

The bitwise operators enable you to treat an integer as the series of bits used to represent it. You probably will not find a lot of use for the bitwise operators in PHP,

& | ~
^
<< >>
PHP’s Bitwise Operators
 Name
Bitwise AND Bitwise OR Bitwise NOT
Bitwise XOR
Left shift Right shift
Use
$a & $b $a | $b ~$a
$a ^ $b
$a << $b $a >> $b



### Other Operators
In addition to the operators we have covered so far, you can use several others.
The comma operator (,) separates function arguments and other lists of items. It is normally used incidentally.



Two special operators, new and ->, are used to instantiate a class and access class members, respectively. 


### The Ternary Operator

The ternary operator (?:) takes the following form: condition ? value if true : value if false
This operator is similar to the expression version of an if-else statement

```PHP
<?php 

$variable = 100;

echo ($variable > 10 ? 200 : 500 );

?> 
```


### The Error Suppression Operator
The error suppression operator (@) can be used in front of any expression—that is, anything that generates or has a value.


Without the @ operator, this line generates a divide-by-zero warning. With the operator
included, the error is suppressed.
If you are suppressing warnings in this way, you need to write some error handling code to check when a warning has occurred. If you have PHP set up with the track_errors feature enabled in php.ini, the error message will be stored in the global variable $php_errormsg.


### The Execution Operator
The execution operator is really a pair of operators—a pair of backticks (``) in fact. The backtick is not a single quotation mark; it is usually located on the same key as the ~ (tilde) symbol on your keyboard.
PHP attempts to execute whatever is contained between the backticks as a command at the server’s command line. The value of the expression is the output of the command.
For example, under Unix-like operating systems

<?php 

echo `ls -al`;
?> 



### Array Operators

There are a number of array operators. The array element operators ([]) enable you to access array elements. You can also use the => operator in some array contexts.

+ == === != <> !==

### The Type Operator

There is one type operator: instanceof. This operator is used in object-oriented programming, but we mention it here for completeness.


The instanceof operator allows you to check whether an object is an instance of a particular class



```PHP
<!DOCTYPE html> <html>
<head>
<title>Bob's Auto Parts - Order Results</title>
</head> <body>
<h1>Bob's Auto Parts</h1>
<h2>Order Results</h2> </body>

<?php 

$tireqty = $_POST['tireqty'];
$oilqty = $_POST["oilqty"];
$sparkqty = $_POST["sparkqty"];

define('TIRE_PRICE',10);
define('OIL_PRICE',20);
define('SPARK_PRICE',10);

echo $tireqty;
echo $oilqty;
echo $sparkqty;

echo '<p>Order Processed at ';
echo date("H:i, jS F Y");
echo "</p>";

echo '<table><tr><td>Name</td><td>Quantity</td><td>Total</td></tr>';
echo '<tr><td>Tire</td><td>'.$tireqty.'</td><td>'.TIRE_PRICE * $tireqty.'</td></tr>';

echo '<tr><td>Oil</td><td>'.$oilqty.'</td><td>'.OIL_PRICE * $oilqty.'</td></tr>';


echo '<tr><td>Spark</td><td>'.$sparkqty.'</td><td>'.SPARK_PRICE * $oilqty.'</td></tr>';


echo '</table>';

$tax_rate = 0.13;
$subtotal = ($tireqty * TIRE_PRICE + $oilqty * OIL_PRICE + $sparkqty * SPARK_PRICE) * (1 + $tax_rate);
echo "subtotal:".number_format($subtotal,2);

?>

</html>
```

It also uses the number_format() function to format the totals as strings with two decimal places. This is a function from PHP’s Math library.



# Understanding Precedence and Associativity


In general, operators have a set of precednence, or order, in which they are evalauted. 
operators also have associativity, which is the order in which operators of the same precedence are evalauted 
this order is generally left to right called left for short, right to left called right for short, or not relevant 




Also note one other operator in this table we have not yet covered: the print language construct, which is equivalent to echo. Both constructs generate output. but you can use print if you find it more readable. Neither print nor echo is really a function, but both can be called as a function with parameters in parentheses. Both can also be treated as an operator: You simply place the string to work with after the keyword echo or print.



### Using Variable Handling Functions



Testing and Setting Variable Types
Most of the variable functions are related to testing the type of function. The two most general are gettype() and settype(). They have the following function prototypes; that is, this is what arguments expect and what they return:
string gettype(mixed var);
bool settype(mixed var, string type);



To use gettype(), you pass it a variable. It determines the type and returns a string containing the type name: bool, int, double (for floats, confusingly, for historical reasons), string, array, object, resource, or NULL. It returns unknown type if it is not one of the standard types.
To use settype(), you pass it a variable for which you want to change the type and a string containing the new type for that variable from the previous list.







