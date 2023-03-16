# What is JavaScript?

- created to `make web pages alive`.

- JS is a `lightweight`,`prototype - based`,`single - threaded`, `dynamic language`, `object - oriented`,`interpreted` or `just-in-time compiled` programming language.

- JS can execute not only in the browser, but also on the server <br/>eg.`Node.js`,`Apache CouchDB`.

- JavaScript engines :<br/>eg.<br/> `# "V8" – in Chrome, Opera and Edge`<br/>`# "SpiderMonkey" – in Firefox`<br/>`# "Chakra" - in IE`<br/>`# "JavaScriptCore", "Nitro" and "SquirrelFish" - in Safari`, etc.

# Why is it called JavaScript?

- It initially had another name: `LiveScript`.

* But `Java` was very popular at that time, so it was decided that positioning a new language as a “younger brother” of Java would help.

# How do engines (translator) work?

```
parse(read)  =>  compiles(translate)  =>  run
```

# How to link with HTML ?

- use `<script>` tag .
- for internal file : <br/>

  ```html
  <script>
    ....
  </script>
  ```

- Placing scripts at the bottom of the <body> element improves the display speed, because script interpretation slows down the display.

- for external file : <br/>
  ```html
  <script src="path/to/script.js"></script>
  ```

# What is “use strict” ?

- always at the `top` of your scripts

- with Strict mode you cannot use any variable before initializing it.

```js
// note: no "use strict" in this example

num = 5; // the variable "num" is created if it didn't exist

alert(num); // 5
```

```js
"use strict";

num = 5; // error: num is not defined
```

- Declared inside a `function`, it has `local scope` (only the code inside the function is in strict mode)

```js
x = 3.14; // This will not cause an error.
myFunction();

function myFunction() {
  "use strict";
  y = 3.14; // This will cause an error
}
```

- `Modern JS` supports “classes” and “modules” – advanced language structures, that `enable use strict automatically`. So we don’t need to add the "use strict" directive, if we use them.

# intro to variables

- used to `store information`

- we can use that information later

- we can change that information later (var, let)

```js
let message; // undefined

message = "Hello"; // Hello

message = "World"; // value changed to `World`

alert(message); // World
```

- We can also declare multiple variables in one line:
  <br/>

```js
let user = "John",
  age = 25,
  message = "Hello";
```

# Variable naming

- The name must contain only letters, digits, or the symbols $ and \_.

```js
let userName;
let test123;

let $ = 1; // declared a variable with the name "$"
let _ = 2; // and now a variable with the name "_"
alert($ + _); // 3
```

- The first character must not be a digit.

```js
let 1a;
```

- hyphens '-' aren't allowed in the name

```js
let my-name;
```

- Case matters

```js
// both variables are different
let apple = "...";
let APPLE = "...";
```

- Non-Latin letters are allowed, but not recommended

```js
let имя = "...";
```

- can't use reserved words,

```js
let let = 5;
let return = 5;
```

# var vs let vs const

|                                         | var                                            | let                                            | const                                               |
| --------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | --------------------------------------------------- |
| Redeclaration                           | YES                                            | NO                                             | NO                                                  |
| Reassignment</br>(can change its value) | YES                                            | YES                                            | NO                                                  |
| Must be Assigned                        | NO<br/>var name;<br/>name = 'Shubham'; //valid | NO<br/>let name;<br/>name = 'Shubham'; //valid | YES<br/>const PI;<br/>PI = 3.14159265359; //invalid |
| Block Scope                             | NO                                             | YES                                            | YES                                                 |

- Block Scope

```js
{
  var x = 2;
}
// x CAN be used here

------------------------

{
  let x = 2;
}
// x can NOT be used here

------------------------

var x = 10;
// Here x is 10

{
var x = 2;
// Here x is 2
}

// Here x is 2

--------------------------

let x = 10;
// Here x is 10

{
let x = 2;
// Here x is 2
}

// Here x is 10

---------------------------

const x = 2;     // Allowed
x = 2;           // Not allowed
var x = 2;       // Not allowed
let x = 2;       // Not allowed
const x = 2;     // Not allowed

{
  const x = 2;   // Allowed
  x = 2;         // Not allowed
  var x = 2;     // Not allowed
  let x = 2;     // Not allowed
  const x = 2;   // Not allowed
}
```

- If you re-declare with `var` only, it will not lose its value.

```js
var carName = "Volvo";
var carName; // Volvo

-----------------------

let message = "This";
let message = "That"; // SyntaxError: 'message' has already been declared
```

# Hoisting

- `Functions` and `variables` are stored in `memory` for an `execution context` before we execute our code. This is called `hoisting`.
- `Functions` are stored with a `reference to the entire functions`,
- `Variables` with the `var` keyword with the value of `undefined`, and variables with the `let` and `const` keyword are stored `uninitialized`.

![Hoisting](./images/hoisting/hoisting1.gif)
![Hoisting](./images/hoisting/hoisting2.gif)
![Hoisting](./images/hoisting/hoisting3.gif)
![Hoisting](./images/hoisting/hoisting4.gif)
![Hoisting](./images/hoisting/hoisting5.gif)
![Hoisting](./images/hoisting/hoisting6.gif)
![Hoisting](./images/hoisting/hoisting7.gif)

### let and const hoisting

- Variables declared with let and const are `also hoisted` but, `unlike var, are not initialized with a default value`. An `exception` will be thrown in a case of let and const

- A let or const variable is said to be in a `temporal dead zone (TDZ)` from the start of the block until code execution reaches the line where the variable is declared.

```js
{
  // TDZ starts at beginning of scope
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  var bar = 1;
  let foo = 2; // End of TDZ (for foo)
}
```

### class hoisting

- Classes defined using a `class` declaration are hoisted, which means that JavaScript has a reference to the class. However the class is not initialized by default, so any code that uses it before the line in which it is initialized is executed will throw a `ReferenceError`.

# Alert, Prompt and Confirm

### alert

- This one we’ve seen already. It shows a message and waits for the user to press “OK”.

```js
alert("Hello");
```

### prompt

- The function prompt accepts two arguments:

```js
result = prompt(title, [default]);

let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old!
```

### confirm

- The function confirm shows a modal window with a question and two buttons: OK and Cancel.

- The result is true if OK is pressed and false otherwise.

```js
let isBoss = confirm("Are you the boss?");

alert(isBoss); // true if OK is pressed
```

# Data types

- We can put `any type` in a variable.

* hence it is `dynamically typed`.

```js
// no error
let message = "hello";
message = 123456;
```

## # _Primitive Data Type_

- They are called `primitive` because their values can contain only a single thing (be it a string or a number or whatever).

- `String`, `Number`, `Boolean`, `Undefined`, `Null`, `BigInt` and `Symbol`

### 1. String

- A string is any series of characters enclosed with single quotes, double quotes or backticks.

```js
let firstName = "John";
let lastName = "Cena";

// Template String
alert(`Hello, ${firstName} ${lastName}!`); // Hello, John Cena!
```

### 2. Number

- The number type represents both integer and floating point numbers.

- There are many operations for numbers.
  |Operator| Description|
  |--|--|
  |+ |Addition|
  |- |Subtraction|
  |\* |Multiplication|
  |\*\* |Exponentiation (ES2016)|
  |/ |Division|
  |% |Modulus (Remainder)|
  |++ |Increment|
  |--| Decrement|

- `special numeric values` - `Infinity`, `-Infinity` and `NaN`.

```js
let n = 123;
n = 12.345;

alert(1 / 0); // Infinity
alert("not a number" / 2); // NaN, such division is erroneous

alert(NaN + 1); // NaN
alert(3 * NaN); // NaN
alert("not a number" / 2 - 1); // NaN
```

### 3. BigInt

- In JS, the `Number` type cannot safely represent integer values larger than (253-1) (that’s 9007199254740991)`Number.MAX_SAFE_INTEGER`, or less than -(253-1) for negatives `Number.MIN_SAFE_INTEGER`.

```js
// For example, these two numbers (right above the safe range) are the same :

console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992
```

- to get more precise results we use bigint

```js
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;

let myNumber = BigInt(12);
let sameMyNumber = 123n;

console.log(myNumber + sameMyNumber);
// for math operation both values must be of bigint type
```

### 4. Boolean (logical type)

- The boolean type has only two values: true and false.

```js
let nameFieldChecked = true; // yes, name field is checked
let ageFieldChecked = false; // no, age field is not checked

let isGreater = 4 > 1;
alert(isGreater); // true (the comparison result is "yes")
```

- Comparison Operators

| Operator | Description                       |
| -------- | --------------------------------- |
| ==       | equal to                          |
| ===      | equal value and equal type        |
| !=       | not equal                         |
| !==      | not equal value or not equal type |
| >        | greater than                      |
| <        | less than                         |
| >=       | greater than or equal to          |
| <=       | less than or equal to             |
| ?        | ternary operator                  |

| Operator | Description |
| -------- | ----------- |
| &&       | logical and |
| \| \|    | logical or  |
| !        | logical not |

### 5. Null

- In JS, null is `not` a `reference to a non-existing object` or a `null pointer` like in some other languages.

- special value - `nothing`, `empty` or `value unknown`.

* `typeof null` is `object` <= `bug`

```
let age = null;
// The code above states that age is unknown.
```

### 6 .Undefined

- The meaning of `undefined` is `value is not assigned`.

- If a variable is `declared`, but `not assigned`, then its value is `undefined`

```
let age;
alert(age); // shows "undefined"
```

### Null vs Undefined

| --        | --                                         |
| --------- | ------------------------------------------ |
| Undefined | used for `unintentionally` missing values. |
| Null      | used for `intentionally` missing values.   |

```js
console.log(null == undefined); // true
console.log(null === undefined); // false

console.log(typeof null); // Object
console.log(typeof undefined); // undefined

let a = null;
console.log(a); // null

let c;
let d = undefined;
console.log(c, d); // undefined undefined
```

### Strange result: null vs 0

```js
alert(null > 0); //  false
alert(null == 0); //  false
alert(null >= 0); //  true
```

### An incomparable undefined

```js
alert(undefined > 0); // false (1)
alert(undefined < 0); // false (2)
alert(undefined == 0); // false (3)
```

## _# Non-Primitive Data Type_

### 1. Object

- All other types are called `primitive` because their values can `contain only a single thing` (be it a string or a number or whatever).

- used to store `collections of data` and `more complex entities`.

# The typeof operator

- The `typeof` operator returns the `type of the argument`.

```js
typeof undefined; // "undefined"
typeof 0; // "number"
typeof 10n; // "bigint"
typeof true; // "boolean"
typeof "foo"; // "string"
typeof Symbol("id"); // "symbol"
typeof Math; // "object"  (1)
typeof null; // "object"  (2)
typeof alert; // "function"  (3)
```

# Type Conversion

### String Conversion

```js
let value = true;
alert(typeof value); // boolean

value = String(value); // now value is a string "true"
alert(typeof value); // string
```

### Numeric Conversion

- Numeric conversion happens in mathematical functions and expressions automatically.

```js
alert("6" / "2"); // 3, strings are converted to numbers
```

- We can use the Number(value) function to explicitly convert a value to a number

```js
let str = "123";
alert(typeof str); // string

let num = Number(str); // becomes a number 123

alert(typeof num); // number
```

### Boolean Conversion

```js
Boolean(1); // true
Boolean(0); // false

Boolean("hello"); // true
Boolean(""); // false

Boolean("0"); // true
Boolean(" "); // spaces, also true (any non-empty string is true)
```

```js
Number("3.14"); // returns 3.14
Number(" 10 "); // returns 10
Number("123z"); // NaN (error reading a number at "z")
Number(""); // returns 0
Number("John"); // returns NaN
Number("99 88"); // returns NaN
Number(true); // returns 1
Number(false); // returns 0

let string1 = "17";
let string2 = "10";

let newString = +string1 + +string2; //27
console.log(typeof newString); //Number

let y = 5; // y is a number
let x = y + ""; // x is a string

let x = 123;
x.toString(); //'123'
(100 + 23).toString(); //'123'

let x = 9.656;
x.toFixed(0); //10
x.toFixed(2); //9.66

let x = 9.656;
x.toPrecision(); //9.656
x.toPrecision(2); //9.7

parseInt("-10.33"); // returns 10
parseInt("10"); // returns 10
parseInt("10.33"); // returns 10
parseInt("10 6"); // returns 10
parseInt("10 years"); // returns 10
parseInt("years 10"); // returns NaN
```

# Falsy & Truthy values

- A falsy value is a value that is considered `false` when encountered in a Boolean context.

* all values are `truthy` - `except falsy` values.

| Value      | Description                                                                                           |
| ---------- | ----------------------------------------------------------------------------------------------------- |
| false      | The keyword false.                                                                                    |
| 0          | The Number zero (so, also 0.0, etc., and 0x0).                                                        |
| -0         | The Number negative zero (so, also -0.0, etc., and -0x0).                                             |
| 0n         | The BigInt zero (so, also 0x0n). Note that there is no BigInt negative zero the negation of 0n is 0n. |
| "", '', `` | Empty string value.                                                                                   |
| null       | null — the absence of any value.                                                                      |
| undefined  | undefined — the primitive value.                                                                      |
| NaN        | NaN — not a number.                                                                                   |

# Type coercion

- Type coercion is the `automatic or implicit conversion` of values from one data type to another (such as strings to numbers).

```js
const value1 = "5";
const value2 = 9;
let sum = value1 + value2; //59

sum = Number(value1) + value2; //14

alert(6 - "2"); // 4, converts '2' to a number
alert("6" / "2"); // 3, converts both operands to numbers
```

# Increment ++ /decrement -- (PRE/POST)

```js
let counter = 0;
alert(++counter); // 1

let counter = 0;
alert(counter++); // 0

let counter = 5;
alert(--counter); // 4

let counter = 5;
alert(counter--); // 5

let counter = 0;
counter++;
++counter;
alert(counter); // 2, the lines above did the same
```

# Logical operators

- There are four logical operators in JavaScript: || (OR), && (AND), ! (NOT), ?? (Nullish Coalescing).

## || (OR)

- If any of its arguments are `true`, it returns `true`, otherwise it returns `false`.

```js
alert(true || true); // true
alert(false || true); // true
alert(true || false); // true
alert(false || false); // false
```

- OR "||" finds the first truthy value, if all falsy, returns the last value.

```js
alert(1 || 0); // 1 (1 is truthy)

alert(null || 1); // 1 (1 is the first truthy value)
alert(null || 0 || 1); // 1 (the first truthy value)
```

```js
alert(undefined || null || 0); // 0 (all falsy, returns the last value)

let firstName = "";
let lastName = "";
let nickName = "SuperCoder";

alert(firstName || lastName || nickName || "Anonymous"); // SuperCoder

// If all variables were falsy, "Anonymous" would show up.
```

- Short-circuit evaluation

```js
true || alert("not printed"); // true (not alert)
false || alert("printed"); // (alert shown)
```

## && (AND)

- AND returns true if both operands are truthy and false otherwise

```js
alert(true && true); // true
alert(false && true); // false
alert(true && false); // false
alert(false && false); // false
```

- If the result is false, stops and returns the original value of that operand.

* If all operands have been evaluated (i.e. all were truthy), returns the last operand.

* In other words, AND returns the first falsy value or the last value if none were found.

```js
alert(1 && 2 && null && 3); // null
```

- When all values are truthy, the last value is returned:

```js
alert(1 && 2 && 3); // 3, the last one
```

- The rules above are similar to OR. The difference is that AND returns the first falsy value while OR returns the first truthy one.

```js
// if the first operand is truthy,
// AND returns the second operand:
alert(1 && 0); // 0
alert(1 && 5); // 5

// if the first operand is falsy,
// AND returns it. The second operand is ignored
alert(null && 5); // null
alert(0 && "no matter what"); // 0
```

- The precedence of AND && operator is higher than OR ||.

```
So the code a && b || c && d is essentially the same as if the && expressions were in parentheses: (a && b) || (c && d).
```

# Nullish coalescing operator '??'

- ?? returns the first argument if it’s not null/undefined. Otherwise, the second one.

```js
The result of a ?? b is:

if a is defined, then a,
if a isn’t defined, then b.

result = (a !== null && a !== undefined) ? a : b;

result = a ?? b
```

- The common use case for ?? is to provide a default value.

```js
let user;
alert(user ?? "Anonymous"); // Anonymous (user not defined)

let user = "John";
alert(user ?? "Anonymous"); // John (user defined)

let firstName = null;
let lastName = null;
let nickName = "Supercoder";
// shows the first defined value:
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder
```

### Comparison with ||

- || returns the first truthy value.
- ?? returns the first defined value.

```js
let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
```

### Using ?? with && or ||

- Due to safety reasons, JavaScript forbids using ?? together with && and || operators, unless the precedence is explicitly specified with parentheses.

```js
let x = 1 && 2 ?? 3; // Syntax error

let x = (1 && 2) ?? 3; // Works
alert(x); // 2
```

# if else condition

```js
let age = 3;

if (age >= 5) {
  console.log("coffee");
} else {
  console.log("milk");
}
// milk
```

# ternary operator

```js
let age = 3;
let drink = age >= 5 ? "coffee" : "milk";
console.log(drink); //milk
```

## # Multiple ‘?’

```js
let age = prompt("age?", 18);

let message =
  age < 3
    ? "Hi, baby!"
    : age < 18
    ? "Hello!"
    : age < 100
    ? "Greetings!"
    : "What an unusual age!";

alert(message);
```

# if - else if - else

```js
let age = 23;
if (age < 3) {
  message = "Hi, baby!";
} else if (age < 18) {
  message = "Hello!";
} else if (age < 100) {
  message = "Greetings!";
} else {
  message = "What an unusual age!";
}

// Greetings!
```

# Switch case

```js
let day = 9;

switch (day) {
  case 0:
    console.log("Sunday");
    break;
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  case 3:
    console.log("Wednesday");
    break;
  case 4:
    console.log("Thrusday");
    break;
  case 5:
    console.log("Friday");
    break;
  case 6:
    console.log("Saturday");
    break;
  default:
    console.log("Invalid Day");
}
```

# while loop

```js
let num = 10;
let total = 0;
let i = 0;

while (i <= num) {
  total = total + i;
  i++;
}

console.log(total); //55
```

# for loop

```js
for (let i = 0; i <= 9; i++) {
  console.log(i);
}
```

# for-in and for-of loop

```js
let list = [4, 5, 6];

for (let i in list) {
  console.log(i); // "0", "1", "2",
}

for (let i of list) {
  console.log(i); // "4", "5", "6"
}
```

# break keyword

```js
for (let i = 1; i <= 10; i++) {
  if (i === 4) {
    break;
  }
  console.log(i); //1,2,3
}
```

# continue keyword

```js
for (let i = 1; i <= 10; i++) {
  if (i === 4) {
    continue;
  }
  console.log(i); //1,2,3,5,6,7,8,9,10
}
```

# do while loop

```js
let i = 10;
do {
  console.log(i); //10
  i++;
} while (i <= 9);

console.log("value of i is ", i); //11
```

# Objects

- objects are used to store keyed collections of various data and more complex entities.

- A property is a “key: value” pair, where key is a string (also called a “property name”), and value can be anything.

- An empty object (“empty cabinet”) can be created using one of two syntaxes:

```js
let user = new Object(); // "object constructor" syntax
let user = {}; // "object literal" syntax

let user = {
  // an object
  name: "John", // by key "name" store value "John"
  age: 30, // by key "age" store value 30
  "likes birds": true, // multiword property name must be quoted
};
```

- Property values are accessible using the dot notation:

```js
alert(user.name); // John
alert(user.age); // 30
OR;
alert(user["likes birds"]); // true
```

- The value can be of any type. Let’s add a boolean one:

```js
user.isAdmin = true;
```

- To remove a property, we can use the delete operator:

```js
delete user.age;
```

- get value of an object

```js
let user = {
  name: "John",
  age: 30,
};

let key = "name";
alert(user[key]); // John
alert(user.key); // undefined
```

### Computed properties

- We can use square brackets in an object literal, when creating an object. That’s called computed properties.

```js
let fruit = "apple";

let bag = {
  [fruit]: 5, // the name of the property is taken from the variable fruit
  [fruit + "Juice"]: 2, // bag.appleJuice = 5
};

alert(bag.apple); // 5 if fruit="apple"
```

### Property value shorthand

```js
function makeUser(name, age) {
  return {
    name, // same as name: name
    age, // same as age: age
    address: "Pune",
  };
}
```

### Property names limitations

- As we already know, a variable cannot have a name equal to one of the language-reserved words like “for”, “let”, “return” etc.

- But for an object property, there’s no such restriction:

```js
// these properties are all right
let obj = {
  for: 1,
  let: 2,
  return: 3,
};

alert(obj.for + obj.let + obj.return); // 6
```

- Other types are automatically converted to strings

```js
let obj = {
  0: "test", // same as "0": "test"
};

// both alerts access the same property (the number 0 is converted to string "0")
alert(obj["0"]); // test
alert(obj[0]); // test (same property)
```

### Property existence test, “in” operator

```js
let user = { name: "John", age: 30 };

alert("age" in user); // true, user.age exists
alert("blabla" in user); // false, user.blabla doesn't exist
```

### iterate object

- "for..in" loop

```js
let user = {
  name: "John",
  age: 30,
  isAdmin: true,
};

for (let key in user) {
  // keys
  alert(key); // name, age, isAdmin
  // values for the keys
  alert(user[key]); // John, 30, true
}
```

### Ordered like an object

- “ordered in a special fashion”: integer properties are sorted, others appear in creation order.

```js
let codes = {
  49: "Germany",
  41: "Switzerland",
  44: "Great Britain",
  // ..,
  1: "USA",
};

for (let code in codes) {
  alert(code); // 1, 41, 44, 49
}
```

```js
let user = {
  name: "John",
  surname: "Smith",
};
user.age = 25; // add one more

// non-integer properties are listed in the creation order
for (let prop in user) {
  alert(prop); // name, surname, age
}
```
