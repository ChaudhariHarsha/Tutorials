# JavaScript Tutorial
JavaScript was invented by Brendan Eich in 1995, and became an ECMA(European Computer Manufacturer's Association) standard in 1997.
ECMA-262 is the official name of the standard. ECMAScript is the official name of the language.

## JavaScript Can Change HTML Content
document.getElementById("demo").innerHTML = "Hello JavaScript";

## JavaScript Can Change HTML Attribute Values
document.getElementById('myImage').src='pic_bulboff.gif'

## JavaScript Can Change HTML Styles (CSS)
document.getElementById("demo").style.color = "red";

## JavaScript Can Hide HTML Elements
document.getElementById("demo").style.display = "none";

# JavaScript Display Possibilities
## JavaScript can "display" data in different ways:

Writing into an HTML element, using innerHTML.
Writing into the HTML output using document.write().
Writing into an alert box, using window.alert().
Writing into the browser console, using console.log().


# JavaScript Code Blocks
JavaScript statements can be grouped together in code blocks, inside curly brackets {...}.

The purpose of code blocks is to define statements to be executed together.

One place you will find statements grouped together in blocks, is in JavaScript functions:

# JavaScript Values
## The JavaScript syntax defines two types of values:

Fixed values
Variable values
Fixed values are called Literals.

Variable values are called Variables.

# JavaScript Variables
In a programming language, variables are used to store data values.

JavaScript uses the keywords var, let and const to declare variables.

An equal sign is used to assign values to variables.

In this example, x is defined as a variable. Then, x is assigned (given) the value 6:

let x;
x = 6;

# JavaScript Expressions
An expression is a combination of values, variables, and operators, which computes to a value.

The computation is called an evaluation.

For example, ``` 5 * 10 ``` evaluates to 50:

# JavaScript Comments
Not all JavaScript statements are "executed".

Code after double slashes // or between /* and */ is treated as a comment.

Comments are ignored, and will not be executed:

# JavaScript Identifiers / Names
Identifiers are JavaScript names.

Identifiers are used to name variables and keywords, and functions.

The rules for legal names are the same in most programming languages.

A JavaScript name must begin with:

A letter (A-Z or a-z)
A dollar sign ($)
Or an underscore (_)
Subsequent characters may be letters, digits, underscores, or dollar signs.


# JavaScript Character Set
JavaScript uses the Unicode character set.

Unicode covers (almost) all the characters, punctuations, and symbols in the world.

# 4 Ways to Declare a JavaScript Variable:
Using var
Using let
Using const
Using nothing


# When to Use JavaScript const?
If you want a general rule, always declare variables with const.

If you think the value of the variable can not change, use const.

# You cannot re-declare a variable declared with let or const.

This will not work:
```
let carName = "Volvo";
let carName;

```

# let keyword

The let keyword was introduced in ES6 (2015).

Variables defined with let cannot be Redeclared.

Variables defined with let must be Declared before use.

Variables defined with let have Block Scope.


# Block Scope
Before ES6 (2015), JavaScript had only Global Scope and Function Scope.

ES6 introduced two important new JavaScript keywords: let and const.

These two keywords provide Block Scope in JavaScript.

Variables declared inside a { } block cannot be accessed from outside the block:

Example
```
{
  let x = 2;
}

```

# Const variable

The const keyword was introduced in ES6 (2015).

Variables defined with const cannot be Redeclared.

Variables defined with const cannot be Reassigned.

Variables defined with const have Block Scope.


# JavaScript Objects
Objects are variables too. But objects can contain many values.

# Common HTML Events
Here is a list of some common HTML events:

Event	Description
onchange	An HTML element has been changed
onclick	The user clicks an HTML element
onmouseover	The user moves the mouse over an HTML element
onmouseout	The user moves the mouse away from an HTML element
onkeydown	The user pushes a keyboard key
onload	The browser has finished loading the page

# JavaScript Strings
## String Length
To find the length of a string, use the built-in length property:

# JavaScript Strings as Objects
Normally, JavaScript strings are primitive values, created from literals:
```
let x = "John"; // string
let y = new String("John"); //object

```
Comparing two JavaScript objects always returns false.

# JavaScript String Methods

## Extracting String Parts
There are 3 methods for extracting a part of a string:
```
slice(start, end)
substring(start, end)
substr(start, length)

```
## JavaScript String slice()
slice() extracts a part of a string and returns the extracted part in a new string.

The method takes 2 parameters: the start position, and the end position (end not included).

This example slices out a portion of a string from position 7 to position 12 (13-1):
```
let str = "Apple, Banana, Kiwi";
let part = str.slice(7, 13);
```
```
Output "Banana"

```

If a parameter is negative, the position is counted from the end of the string.
If you omit the second parameter, the method will slice out the rest of the string:

# JavaScript String substring()
substring() is similar to slice().

The difference is that substring() cannot accept negative indexes.

# JavaScript String substr()
substr() is similar to slice().

The difference is that the second parameter specifies the length of the extracted part.

# Replacing String Content
The replace() method replaces a specified value with another value in a string:

let text = "Please visit Microsoft!";
let newText = text.replace("MICROSOFT", "W3Schools");

By default, the replace() method replaces only the first match:
By default, the replace() method is case sensitive. Writing MICROSOFT (with upper-case) will not work:
To replace case insensitive, use a regular expression with an /i flag (insensitive):
let text = "Please visit Microsoft!";
let newText = text.replace(/MICROSOFT/i, "W3Schools");
To replace all matches, use a regular expression with a /g flag (global match):

# Converting to Upper and Lower Case
A string is converted to upper case with toUpperCase():

A string is converted to lower case with toLowerCase():
```
let text1 = "Hello World!";       // String
let text2 = text1.toLowerCase(); 
```
# JavaScript String concat()
concat() joins two or more strings:
```
let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2);

```

# JavaScript String trim()
The trim() method removes whitespace from both sides of a string:

# JavaScript String Padding
ECMAScript 2017 added two String methods: padStart and padEnd to support padding at the beginning and at the end of a string.
```
let text = "5";
let padded = text.padStart(4,0);

 // output = 0005
```
 # JavaScript String charAt()
The charAt() method returns the character at a specified index (position) in a string:
```
Example
let text = "HELLO WORLD";
let char = text.charAt(0);

// output H

```
# JavaScript String charCodeAt()
The charCodeAt() method returns the unicode of the character at a specified index in a string:

The method returns a UTF-16 code (an integer between 0 and 65535).

Example
```
let text = "HELLO WORLD";
let char = text.charCodeAt(0);

```
# JavaScript String split()
A string can be converted to an array with the split() method:

Example
```
text.split(",")    // Split on commas
text.split(" ")    // Split on spaces
text.split("|")    // Split on pipe
text.split("")    //Split on  single characters

```
# JavaScript String Search

## JavaScript Search Methods
```
String indexOf()
String lastIndexOf()
String startsWith()
String endsWith()

```

## JavaScript String indexOf()
The indexOf() method returns the index of (the position of) the first occurrence of a specified text in a string:

Example
```
let str = "Please locate where 'locate' occurs!";
str.indexOf("locate");

// Output = 7
```
## JavaScript String lastIndexOf()
The lastIndexOf() method returns the index of the last occurrence of a specified text in a string:

Example
```
let str = "Please locate where 'locate' occurs!";
str.lastIndexOf("locate");

// Output = 21
```
Both indexOf(), and lastIndexOf() return -1 if the text is not found:
Both methods accept a second parameter as the starting position for the search:

## Did You Notice?
The two methods, indexOf() and search(), are equal?

They accept the same arguments (parameters), and return the same value?

The two methods are NOT equal. These are the differences:

The search() method cannot take a second start position argument.
The indexOf() method cannot take powerful search values (regular expressions).

## JavaScript String match()
The match() method searches a string for a match against a regular expression, and returns the matches, as an Array object.

Example 1
```
Search a string for "ain":

let text = "The rain in SPAIN stays mainly in the plain";
text.match(/ain/g);
```
## javaScript String includes()
The includes() method returns true if a string contains a specified value.

Example
```
let text = "Hello world, welcome to the universe.";
text.includes("world"); // output true
```
Check if a string includes "world", starting the search at position 12:
```
let text = "Hello world, welcome to the universe.";
text.includes("world", 12); // output false
```
## JavaScript String startsWith()
The startsWith() method returns true if a string begins with a specified value, otherwise false:

Example
```
let text = "Hello world, welcome to the universe.";

text.startsWith("Hello");
Syntax
string.startsWith(searchvalue, start)
```
## JavaScript String endsWith()
The endsWith() method returns true if a string ends with a specified value, otherwise false:

Example
Check if a string ends with "Doe":
```
var text = "John Doe";
text.endsWith("Doe");
Syntax
string.endswith(searchvalue, length)

```
## Back-Tics Syntax
Template Literals use back-ticks (``) rather than the quotes ("") to define a string:

## JavaScript Arrays

Arrays are Objects
Arrays are a special type of objects. The typeof operator in JavaScript returns "object" for arrays.

But, JavaScript arrays are best described as arrays.

### Array.forEach()
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];

let text = "<ul>";
fruits.forEach(myFunction);
text += "</ul>";

function myFunction(value) {
  text += "<li>" + value + "</li>";
}
```
## Adding Array Elements
The easiest way to add a new element to an array is using the push() method:
```
const fruits = ["Banana", "Orange", "Apple"];
fruits.push("Lemon"); 
```
## Associative Arrays
Many programming languages support arrays with named indexes.

Arrays with named indexes are called associative arrays (or hashes).

JavaScript does not support arrays with named indexes.

In JavaScript, arrays always use numbered indexes.  

## The Difference Between Arrays and Objects
In JavaScript, arrays use numbered indexes.  

In JavaScript, objects use named indexes.

## When to Use Arrays. When to use Objects.
JavaScript does not support associative arrays.
You should use objects when you want the element names to be strings (text).
You should use arrays when you want the element names to be numbers.

## JavaScript new Array()
JavaScript has a built in array constructor new Array().

But you can safely use [] instead.

These two different statements both create a new empty array named points:
```
const points = new Array();
const points = [];
```
## How to Recognize an Array
A common question is: How do I know if a variable is an array?

The problem is that the JavaScript operator typeof returns "object":

To solve this problem ECMAScript 5 (JavaScript 2009) defined a new method Array.isArray():
```
Array.isArray(fruits);
```
# JavaScript Array Methods

## Converting Arrays to Strings

The join() method also joins all array elements into a string.
```
fruits.join(" * ")
```
## Popping and Pushing

const fruits = ["Banana", "Orange", "Apple", "Mango"];
```
fruits.pop();
fruits.push("newF);
```
## JavaScript Array shift()
The shift() method removes the first array element and "shifts" all other elements to a lower index.

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();
```
## JavaScript Array unshift()
The unshift() method adds a new element to an array (at the beginning), and "unshifts" older elements:

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon");
```
## Merging (Concatenating) Arrays
The concat() method creates a new array by merging (concatenating) existing arrays:

Example (Merging Two Arrays)
```
const myGirls = ["Cecilie", "Lone"];
const myBoys = ["Emil", "Tobias", "Linus"];

const myChildren = myGirls.concat(myBoys);

```

The concat() method can take any number of array arguments:
The concat() method can also take strings as arguments:

## JavaScript Array splice()
The splice() method can be used to add new items to an array:

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 0, "Lemon", "Kiwi");
```
The first parameter (2) defines the position where new elements should be added (spliced in).

The second parameter (0) defines how many elements should be removed.

The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be added.

## Using splice() to Remove Elements
With clever parameter setting, you can use splice() to remove elements without leaving "holes" in the array:

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(0, 1);
```
The first parameter (0) defines the position where new elements should be added (spliced in).

The second parameter (1) defines how many elements should be removed.

The rest of the parameters are omitted. No new elements will be added.

JavaScript Array slice()
The slice() method slices out a piece of an array into a new array.

This example slices out a part of an array starting from array element 1 ("Orange"):

Example
```
const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus = fruits.slice(1);
```
If the end argument is omitted, like in the first examples, the slice() method slices out the rest of the array.

## JavaScript Sorting Arrays

The sort() method sorts an array alphabetically:

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
```

## Reversing an Array
The reverse() method reverses the elements in an array.

You can use it to sort an array in descending order:

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.reverse();
```
## Numeric Sort
```
const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});
```
## Sorting Object Arrays
JavaScript arrays often contain objects:

Example
```
const cars = [
  {type:"Volvo", year:2016},
  {type:"Saab", year:2001},
  {type:"BMW", year:2010}
];
cars.sort(function(a, b){return a.year - b.year});
```
Comparing string properties is a little more complex:

Example
```
cars.sort(function(a, b){
  let x = a.type.toLowerCase();
  let y = b.type.toLowerCase();
  if (x < y) {return -1;}
  if (x > y) {return 1;}
  return 0;
});
```
# JavaScript Array Iteration

## JavaScript Array forEach()
The forEach() method calls a function (a callback function) once for each array element.

Example
```
const numbers = [45, 4, 9, 16, 25];
let txt = "";
numbers.forEach(myFunction);

function myFunction(value, index, array) {
  txt += value + "<br>";
}
```
## JavaScript Array map()
The map() method creates a new array by performing a function on each array element.

The map() method does not execute the function for array elements without values.

The map() method does not change the original array.

This example multiplies each array value by 2:

Example
```
const numbers1 = [45, 4, 9, 16, 25];
const numbers2 = numbers1.map(myFunction);

function myFunction(value, index, array) {
  return value * 2;
}
```
#### JavaScript Array filter()
The filter() method creates a new array with array elements that passes a test.

This example creates a new array from elements with a value larger than 18:

Example
```
const numbers = [45, 4, 9, 16, 25];
const over18 = numbers.filter(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
## JavaScript Array reduce()
The reduce() method runs a function on each array element to produce (reduce it to) a single value.

The reduce() method works from left-to-right in the array.

The reduce() method does not reduce the original array.

This example finds the sum of all numbers in an array:

Example
```
const numbers = [45, 4, 9, 16, 25];
let sum = numbers.reduce(myFunction);

function myFunction(total, value, index, array) {
  return total + value;
}
```
#### The reduce() method can accept an initial value:

Example
```
const numbers = [45, 4, 9, 16, 25];
let sum = numbers.reduce(myFunction, 100);

function myFunction(total, value) {
  return total + value;
}
```
## JavaScript Array reduceRight()
The reduceRight() method runs a function on each array element to produce (reduce it to) a single value.

The reduceRight() works from right-to-left in the array.

The reduceRight() method does not reduce the original array.

This example finds the sum of all numbers in an array:

Example
```
const numbers = [45, 4, 9, 16, 25];
let sum = numbers1.reduceRight(myFunction);

function myFunction(total, value, index, array) {
  return total + value;
}
```
## JavaScript Array every()
The every() method check if all array values pass a test.

This example check if all array values are larger than 18:

Example
```
const numbers = [45, 4, 9, 16, 25];
let allOver18 = numbers.every(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
## JavaScript Array some()
The some() method check if some array values pass a test.

This example check if some array values are larger than 18:

Example
```
const numbers = [45, 4, 9, 16, 25];
let someOver18 = numbers.some(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
## JavaScript Array indexOf()
The indexOf() method searches an array for an element value and returns its position.

Note: The first item has position 0, the second item has position 1, and so on.

Example
Search an array for the item "Apple":
```
const fruits = ["Apple", "Orange", "Apple", "Mango"];
let position = fruits.indexOf("Apple") + 1;

Syntax
array.indexOf(item, start)
```
## JavaScript Array lastIndexOf()
Array.lastIndexOf() is the same as Array.indexOf(), but returns the position of the last occurrence of the specified element.

Example
Search an array for the item "Apple":
```
const fruits = ["Apple", "Orange", "Apple", "Mango"];
let position = fruits.lastIndexOf("Apple") + 1;
```
## JavaScript Array find()
The find() method returns the value of the first array element that passes a test function.

This example finds (returns the value of) the first element that is larger than 18:

Example
```
const numbers = [4, 9, 16, 25, 29];
let first = numbers.find(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
## JavaScript Array findIndex()
The findIndex() method returns the index of the first array element that passes a test function.

This example finds the index of the first element that is larger than 18:

Example
```
const numbers = [4, 9, 16, 25, 29];
let first = numbers.findIndex(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
## JavaScript Array.from()
The Array.from() method returns an Array object from any object with a length property or any iterable object.

Example
Create an Array from a String:
```
Array.from("ABCDEFG");
```
## JavaScript Array Keys()
The Array.keys() method returns an Array Iterator object with the keys of an array.

Example
Create an Array Iterator object, containing the keys of the array:
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
const keys = fruits.keys();

for (let x of keys) {
  text += x + "<br>";
}
```
## JavaScript Array includes()
ECMAScript 2016 introduced Array.includes() to arrays. This allows us to check if an element is present in an array (including NaN, unlike indexOf).

Example
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];

fruits.includes("Mango"); // is true
```
## Creating Date Objects
Date objects are created with the new Date() constructor.

There are 4 ways to create a new date object:
```
new Date()
new Date(year, month, day, hours, minutes, seconds, milliseconds)
new Date(milliseconds)
new Date(date string)
```
## Number to Integer
There are 4 common methods to round a number to an integer:

Math.round(x)	Returns x rounded to its nearest integer
Math.ceil(x)	Returns x rounded up to its nearest integer
Math.floor(x)	Returns x rounded down to its nearest integer
Math.trunc(x)

## Math.pow()
Math.pow(x, y) returns the value of x to the power of y:

## Math.sqrt()
Math.sqrt(x) returns the square root of x:

## Math.abs()
Math.abs(x) returns the absolute (positive) value of x:

## Math.sqrt()
Math.sqrt(x) returns the square root of x:

Example
```
Math.sqrt(64);
```
## Math.abs()
Math.abs(x) returns the absolute (positive) value of x:

Example
```
Math.abs(-4.7);
```
## A Proper Random Function
As you can see from the examples above, it might be a good idea to create a proper random function to use for all random integer purposes.

This JavaScript function always returns a random number between min (included) and max (excluded):

Example
```
function getRndInteger(min, max) {
  return Math.floor(Math.random() * (max - min) ) + min;
}
```
## Primitive Data
A primitive data value is a single simple data value with no additional properties and methods.

The typeof operator can return one of these primitive types:

string
number
boolean
undefined

### Undefined
In JavaScript, a variable without a value, has the value undefined. The type is also undefined.

### Null
In JavaScript null is "nothing". It is supposed to be something that doesn't exist.

Unfortunately, in JavaScript, the data type of null is an object.

You can consider it a bug in JavaScript that typeof null is an object. It should be null.

## Difference Between Undefined and Null
undefined and null are equal in value but different in type:

typeof undefined           // undefined
typeof null                // object

null === undefined         // false
null == undefined          // true

## Number Methods
In the chapter Number Methods, you will find more methods that can be used to convert strings to numbers:

Method	Description
Number()	Returns a number, converted from its argument
parseFloat()	Parses a string and returns a floating point number
parseInt()	Parses a string and returns an integer

## What Is a Regular Expression?
A regular expression is a sequence of characters that forms a search pattern.

When you search for data in a text, you can use this search pattern to describe what you are searching for.

A regular expression can be a single character, or a more complicated pattern.

Regular expressions can be used to perform all types of text search and text replace operations.
Example explained:
```
/w3schools/i  is a regular expression.
```
w3schools  is a pattern (to be used in a search).

i  is a modifier (modifies the search to be case-insensitive).

# JavaScript Errors
Throw, and Try...Catch...Finally
The try statement defines a code block to run (to try).

The catch statement defines a code block to handle any error.

The finally statement defines a code block to run regardless of the result.

The throw statement defines a custom error.

# JavaScript Scope
Scope determines the accessibility (visibility) of variables.

JavaScript has 3 types of scope:

Block scope
Function scope
Global scope

## Block Scope
Before ES6 (2015), JavaScript had only Global Scope and Function Scope.

ES6 introduced two important new JavaScript keywords: let and const.

These two keywords provide Block Scope in JavaScript.

Variables declared inside a { } block cannot be accessed from outside the block:

Example
```
{
  let x = 2;
}
```
Variables declared with the var keyword can NOT have block scope.
Variables declared inside a { } block can be accessed from outside the block.

## Local Scope
Variables declared within a JavaScript function, become LOCAL to the function.

Example
```
// code here can NOT use carName

function myFunction() {
  let carName = "Volvo";
  // code here CAN use carName
}
```
Local variables have Function Scope:
They can only be accessed from within the function.

## Function Scope
JavaScript has function scope: Each function creates a new scope.

Variables defined inside a function are not accessible (visible) from outside the function.

Variables declared with var, let and const are quite similar when declared inside a function.

They all have Function Scope:
```
function myFunction() {
  var carName = "Volvo";   // Function Scope
}
```
## Global JavaScript Variables
A variable declared outside a function, becomes GLOBAL.

Example
```
let carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}
```
A global variable has Global Scope:

All scripts and functions on a web page can access it. 

## Global Scope
Variables declared Globally (outside any function) have Global Scope.

Global variables can be accessed from anywhere in a JavaScript program.

Variables declared with var, let and const are quite similar when declared outside a block.

They all have Global Scope:

## Automatically Global
If you assign a value to a variable that has not been declared, it will automatically become a GLOBAL variable.

This code example will declare a global variable carName, even if the value is assigned inside a function.

Example
```
myFunction();

// code here can use carName

function myFunction() {
  carName = "Volvo";
}
```
## JavaScript Hoisting
Hoisting is JavaScript's default behavior of moving declarations to the top.

### JavaScript Declarations are Hoisted
In JavaScript, a variable can be declared after it has been used.

In other words; a variable can be used before it has been declared.

Example 1 gives the same result as Example 2:

Example 1
```
x = 5; // Assign 5 to x
elem = document.getElementById("demo"); // Find an element
elem.innerHTML = x;                     // Display x in the element

var x; // Declare x

```
Hoisting is JavaScript's default behavior of moving all declarations to the top of the current scope (to the top of the current script or the current function).

## The let and const Keywords
Variables defined with let and const are hoisted to the top of the block, but not initialized.

Meaning: The block of code is aware of the variable, but it cannot be used until it has been declared.

Using a let variable before it is declared will result in a ReferenceError.

The variable is in a "temporal dead zone" from the start of the block until it is declared:

Example
```
This will result in a ReferenceError:
carName = "Volvo";
let carName;
```
## JavaScript Initializations are Not Hoisted
JavaScript only hoists declarations, not initializations.

exp 
```
var x = 5; // Initialize x

elem = document.getElementById("demo"); // Find an element
elem.innerHTML = x + " " + y;           // Display x and y

var y = 7; // Initialize y
```
Does it make sense that y is undefined in the last example?

This is because only the declaration (var y), not the initialization (=7) is hoisted to the top.

Because of hoisting, y has been declared before it is used, but because initializations are not hoisted, the value of y is undefined.

#### JavaScript in strict mode does not allow variables to be used if they are not declared.

# JavaScript Use Strict
"use strict"; Defines that JavaScript code should be executed in "strict mode".

## The "use strict" Directive
The "use strict" directive was new in ECMAScript version 5.

It is not a statement, but a literal expression, ignored by earlier versions of JavaScript.

The purpose of "use strict" is to indicate that the code should be executed in "strict mode".

With strict mode, you can not, for example, use undeclared variables.

## Declaring Strict Mode
Strict mode is declared by adding "use strict"; to the beginning of a script or a function.

Declared at the beginning of a script, it has global scope (all code in the script will execute in strict mode):

## Why Strict Mode?
Strict mode makes it easier to write "secure" JavaScript.

Strict mode changes previously accepted "bad syntax" into real errors.

As an example, in normal JavaScript, mistyping a variable name creates a new global variable. In strict mode, this will throw an error, making it impossible to accidentally create a global variable.

In normal JavaScript, a developer will not receive any error feedback assigning values to non-writable properties.

In strict mode, any assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object, will throw an error.

### Not Allowed in Strict Mode
Using a variable, without declaring it, is not allowed:

The this keyword in functions behaves differently in strict mode.

The this keyword refers to the object that called the function.

If the object is not specified, functions in strict mode will return undefined and functions in normal mode will return the global object (window):
```
"use strict";
function myFunction() {
  alert(this); // will alert "undefined"
}
myFunction();
```
## JavaScript Sets
A JavaScript Set is a collection of unique values.

Each value can only occur once in a Set.

Example
```
// Create a Set
const letters = new Set(["a","b","c"]);
```
### Set Methods
Method	Description
new Set()	Creates a new Set
add()	Adds a new element to the Set
delete()	Removes an element from a Set
has()	Returns true if a value exists
clear()	Removes all elements from a Set
forEach()	Invokes a callback for each element
values()	Returns an Iterator with all the values in a Set
keys()	Same as values()
entries()	Returns an Iterator with the [value,value] pairs from a Set
Property	Description
size	Returns the number elements in a Set

## JavaScript Maps
A Map holds key-value pairs where the keys can be any datatype.

A Map remembers the original insertion order of the keys
```
const fruits = new Map([
  ["apples", 500],
  ["bananas", 300],
  ["oranges", 200]
]);
```
### Map Methods
Method	Description
new Map()	Creates a new Map object
set()	Sets the value for a key in a Map
get()	Gets the value for a key in a Map
clear()	Removes all the elements from a Map
delete()	Removes a Map element specified by a key
has()	Returns true if a key exists in a Map
forEach()	Invokes a callback for each key/value pair in a Map
entries()	Returns an iterator object with the [key, value] pairs in a Map
keys()	Returns an iterator object with the keys in a Map
values()	Returns an iterator object of the values in a Map

# The JavaScript this Keyword

## What is this?
The JavaScript this keyword refers to the object it belongs to.

It has different values depending on where it is used:

In a method, this refers to the owner object.
Alone, this refers to the global object.
In a function, this refers to the global object.
In a function, in strict mode, this is undefined.
In an event, this refers to the element that received the event.
Methods like call(), and apply() can refer this to any object.

## this in Event Handlers
In HTML event handlers, this refers to the HTML element that received the event:

Example
```
<button onclick="this.style.display='none'">
  Click to Remove Me!
</button>
```
## JavaScript Arrow Function
Arrow functions were introduced in ES6.

Arrow functions allow us to write shorter function syntax:
```
let myFunction = (a, b) => a * b;
```

## Destructuring
To illustrate destructuring, we'll make a sandwich. Do you take everything out of the refrigerator to make your sandwich? No, you only take out the items you would like to use on your sandwich.

Destructuring is exactly the same. We may have an array or object that we are working with, but we only need some of the items contained in these.

Destructuring makes it easy to extract only what is needed.

### Destructing Arrays

```
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car, truck, suv] = vehicles;

```

### Destructuring Objects

```
const vehicleOne = {
  brand: 'Ford',
  model: 'Mustang',
  type: 'car',
  year: 2021, 
  color: 'red',
  registration: {
    city: 'Houston',
    state: 'Texas',
    country: 'USA'
  }
}

myVehicle(vehicleOne)

function myVehicle({ model, registration: { state } }) {
  const message = 'My ' + model + ' is registered in ' + state + '.';
}

```

##### Use destructuring to extract only the third item from the array, into a variable named suv.

```


const vehicles = ['mustang', 'f-150', 'expedition'];

const [
,,suv
] = vehicles;


```
## JavaScript Classes
ECMAScript 2015, also known as ES6, introduced JavaScript Classes.

JavaScript Classes are templates for JavaScript Objects.

Example
```
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}
```
Using a Class
When you have a class, you can use the class to create objects:

Example
```
let myCar1 = new Car("Ford", 2014);
```
### The Constructor Method
The constructor method is a special method:

It has to have the exact name "constructor"
It is executed automatically when a new object is created
It is used to initialize object properties
If you do not define a constructor method, JavaScript will add an empty constructor method.

## JavaScript JSON
JSON is a format for storing and transporting data.

JSON is often used when data is sent from a server to a web page
## What is JSON?
JSON stands for JavaScript Object Notation
JSON is a lightweight data interchange format
JSON is language independent *
JSON is "self-describing" and easy to understand
* The JSON syntax is derived from JavaScript object notation syntax, but the JSON format is text only. Code for reading and generating JSON data can be written in any programming language

### JSON Example
This JSON syntax defines an employees object: an array of 3 employee records (objects):

JSON Example
```
{
"employees":[
  {"firstName":"John", "lastName":"Doe"},
  {"firstName":"Anna", "lastName":"Smith"},
  {"firstName":"Peter", "lastName":"Jones"}
]
}
```
## JavaScript Primitives
A primitive value is a value that has no properties or methods.

A primitive data type is data that has a primitive value.

JavaScript defines 5 types of primitive data types:

string
number
boolean
null
undefined
Primitive values are immutable (they are hardcoded and therefore cannot be changed).

## Functions are Objects
The typeof operator in JavaScript returns "function" for functions.

But, JavaScript functions can best be described as objects.

JavaScript functions have both properties and methods.

The arguments.length property returns the number of arguments received when the function was invoked (call):

Example
```
function myFunction(a, b) {
  return arguments.length;
}
```
If a function is called with too many arguments (more than declared), these arguments can be reached using the arguments object.
```
function sumAll() {
  let sum = 0;
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}
```
## The JavaScript call() Method
The call() method is a predefined JavaScript method.

It can be used to invoke (call) a method with an owner object as an argument (parameter).

With call(), an object can use a method belonging to another object.

This example calls the fullName method of person, using it on person1:

Example
```
const person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
const person1 = {
  firstName:"John",
  lastName: "Doe"
}
const person2 = {
  firstName:"Mary",
  lastName: "Doe"
}

// This will return "John Doe":
person.fullName.call(person1);
```
## The JavaScript apply() Method
The apply() method is similar to the call() method (previous chapter).
## The Difference Between call() and apply()
The difference is:

The call() method takes arguments separately.

The apply() method takes arguments as an array.

### The apply() Method with Arguments
The apply() method accepts arguments in an array:

Example
```
const person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}

const person1 = {
  firstName:"John",
  lastName: "Doe"
}

person.fullName.apply(person1, ["Oslo", "Norway"]);

```
# JavaScript Closures
JavaScript variables can belong to the local or global scope.

Global variables can be made local (private) with closures.

### Variable Lifetime
Global variables live until the page is discarded, like when you navigate to another page or close the window.

Local variables have short lives. They are created when the function is invoked, and deleted when the function is finished.

## JavaScript Closures
Remember self-invoking / self-call functions? What does this function do?

Example
```
const add = (function () {
  let counter = 0;
  return function () {counter += 1; return counter}
})();

add();
add();
add();
```
// the counter is now 3
Example Explained
The variable add is assigned to the return value of a self-invoking function.

The self-invoking function only runs once. It sets the counter to zero (0), and returns a function expression.

This way add becomes a function. The "wonderful" part is that it can access the counter in the parent scope.

This is called a JavaScript closure. It makes it possible for a function to have "private" variables.

The counter is protected by the scope of the anonymous function, and can only be changed using the add function.

A closure is a function having access to the parent scope, even after the parent function has closed.

## JavaScript Static Methods
Static class methods are defined on the class itself.

You cannot call a static method on an object, only on an object class.

Example
```
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello() {
    return "Hello!!";
  }
}

let myCar = new Car("Ford");

// You can call 'hello()' on the Car Class:
document.getElementById("demo").innerHTML = Car.hello();

// But NOT on a Car Object:
// document.getElementById("demo").innerHTML = myCar.hello();
// this will raise an error.
```
#### If you want to use the myCar object inside the static method, you can send it as a parameter:

Example
```
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let myCar = new Car("Ford");
document.getElementById("demo").innerHTML = Car.hello(myCar);
```
## Asynchronous JavaScript
"I will finish later!"

Functions running in parallel with other functions are called asynchronous

# JavaScript Promises
JavaScript Promises
"I Promise a Result!"

"Producing code" is code that can take some time

"Consuming code" is code that must wait for the result

A Promise is a JavaScript object that links producing code and consuming code

```
function myDisplayer(some) {
  document.getElementById("demo").innerHTML = some;
}

let myPromise = new Promise(function(myResolve, myReject) {
  let x = 1;

// some code (try to change x to 5)

  if (x == 0) {
    myResolve("OK");
  } else {
    myReject("Error");
  }
});

myPromise.then(res=>{
myDisplayer(res);
},err=>{
myDisplayer(err);

});

```

## JavaScript Async
"async and await make promises easier to write"

async makes a function return a Promise

await makes a function wait for a Promise

```

async function myDisplay() {
  let myPromise = new Promise(function(resolve) {
    setTimeout(function() {resolve("I love You !!");}, 3000);
  });
  document.getElementById("demo").innerHTML = await myPromise;
}

myDisplay();

```

## JavaScript HTML DOM EventListener
```
document.getElementById("myBtn").addEventListener("click", displayDate);
syntax
element.addEventListener("click", CalbackFunction);
```
## Other Window Methods
Some other methods:
```
window.open() - open a new window
window.close() - close the current window
window.moveTo() - move the current window
window.resizeTo() - resize the current window
```
## Window Screen
The window.screen object can be written without the window prefix.

Properties:

screen.width
screen.height
screen.availWidth
screen.availHeight
screen.colorDepth
screen.pixelDepth

## JavaScript Window Location
The window.location object can be used to get the current page address (URL) and to redirect the browser to a new page.

Window Location
The window.location object can be written without the window prefix.

Some examples:
```
window.location.href returns the href (URL) of the current page
window.location.hostname returns the domain name of the web host
window.location.pathname returns the path and filename of the current page
window.location.protocol returns the web protocol used (http: or https:)
window.location.assign() loads a new document
```
# AJAX Introduction
AJAX is a developer's dream, because you can:

Read data from a web server - after the page has loaded
Update a web page without reloading the page
Send data to a web server - in the background

## Plotly.js
Plotly.js is a charting library that comes with over 40 chart types, 3D charts, statistical graphs, and SVG maps.
