---

layout: default

---

# &nbsp;

## **{{ site.presentation.title }}** {#cover}

<div class="info">
	<p class="author">{{ site.author.name }}, <br/> {{ site.author.position }}</p>
</div>

## Das ist
{:.section}

### ECMAScript

## JS Syntax

### Спецификация

// Спросить про реализации

* ECMA-262
    * ... ECMA-262-3 (ES3)
    * ... ECMA-262-5 (ES5)
    * ... ECMA-262-6 (ES6)
    * ... ECMA-262-7 (ES7)
    * ... ES.Next


... [Почитать у камина под пледом](https://github.com/tc39/ecma262)


## JS Syntax

{:.with-big-quote}
> JavaScript is a general-purpose, prototype-based, object-oriented scripting language.  It is designed to be embedded in diverse applications and systems, without consuming much memory.  JavaScript borrows most of its syntax from Java, but also inherits from Awk and Perl, with some indirect influence from Self in its object prototype system.  

Brendan Eich
{:.note}

## JS Syntax

### Comments

* CommentLine

~~~ javascript
// TODO: Write useful comment
~~~

## JS Syntax

### Comments

* CommentBlock

~~~ javascript
/**
 * Выполняет URL-кодирование строки согласно RFC 3986.
 *
 * @param {String} str
 * @returns {String}
 */
function urlEncode(str) {
    return encodeURIComponent(str).replace(/[!'()*]/g, function(c) {
        return '%' + c.charCodeAt(0).toString(16);
    });
}
~~~

[JSDoc](http://usejsdoc.org/)


## JS Syntax

### Statements

### Expressions

## JS Syntax

### Statements

~~~ javascript
function f() {}

if (0) {}

try {} catch (e) {}
~~~

* returns nothing
* could be nested
* could contain expressions


## JS Syntax

### Expressions

~~~ javascript
f()

+1;

[]
~~~

* always return smth
* could be nested
* could NOT contain statements
* ...ExpressionStatement;


## Statements: Control flow & iterations

~~~ javascript
if (true)
{}
else {
}

while(1) {
}
~~~

* ... Block statement
* ... ifElse, switch, break, continue, throw, tryCatch
* ... doWhile, while, for, forIn, forOf
* ... Empty statement `;`
* ... debugger
* ... import, export

// for (i = 0; i < arr.length; arr[i++] = 0) ;
// if (1) ; else ;


## Statements: Declarations and functions

~~~ javascript
let y = 2, z = 4;
var x;

function myFunc(args) {
    return x;
}

class ES6💛 {
}
~~~

* ... var, let, const
* ... function, function\* , class
* ... return

// function always return undefined

## Statements: Declarations and functions

### Whitespaces and semicolons

~~~ javascript
function hey() {
    return
    'wtf?'
}
~~~

* ... Spaces, tabs and newlines 
* ... not always our friends
* ... ASI (automatic semicolon insertion);

... [eslint](http://eslint.org/)


## Statements: Declarations and functions

### functions hoisting

~~~ javascript
hoisted(); // "up"

function hoisted() {
    console.log("up");
}
~~~

## Statements: Declarations and functions

### variables hoisting - var

~~~ javascript
hop = 42;
var hop;
console.log(hop); // 42
~~~

Could be declared several times:

~~~ javascript
var x;
var x = 1;
var x = 11;
console.log(x); // 11
~~~

~~~ javascript
var x;
x = 1;
x = 11;
~~~

## Statements: Declarations and functions

### variables hoisting - let

~~~ javascript
console.log(a); // Error
let a = 42;
~~~

~~~ javascript
let a = 17;
let a = 17; // Error
~~~~


## Operators

* ... Assignments: `=, *=, +=`
* ... Increment, decrement operators: `i++, j--`
* ... Unary operators `+12, !false`
* ... Arithmetic operators `1 + 1, 4 % 2, 2 ** 8`
* ... Comparison operators `1 < 2, 3 >= 4`
* ... Grouping operator `(1 + 1) * 2`
* ... Logical operators `&&, ||`
* ... Ternary operator `true ? 'hello' : 'bye'`
* ... Equality operators `==, !=, ===, !===`


## Equality operators

### Abstract `==`

~~~ javascript
'' == '0' // false
'' == 0  // true
0 == '0' // true
'1' == true // true
false == undefined // false
false == null // false
null == undefined // true
{0:0} == {0:0} // false
~~~

## Equality operators

### Strict `===`

~~~ javascript
'' === '0' // false
'' === 0 // false
0 === '0' // false
'1' === true // false
false === undefined // false
false === null // false
null === undefined // false
{0:0} === {0:0} // false
~~~

## Typecasting

~~~ javascript
    '1' + 1; 
~~~
... // '11'

~~~ javascript
    true + 1
~~~
... // 2

~~~ javascript
    false + false
~~~
... // 0

* depends on operator
* depends on argument

// if one is String -> toString + toString
// else -> toNumber + toNumber

## Typecasting

~~~ javascript
    '1' + {};
~~~
... // '1[object Object]'

~~~ javascript
    '' + {};
~~~
... // '[object Object]'

~~~ javascript
    {} + '';
~~~
... // 0

// toPrimitive(input, PreferredType?)
// PreferredType is Number -> input.valueOf(), input.toString()
// PreferredType is String -> input.toString(), input.valueOf()


[WAT](https://www.destroyallsoftware.com/talks/wat)



## Data types:

* Primitive data types
    * undefined
    * null
    * Boolean
    * Number
    * String
    * Symbol (es6)

* ... Object
* ... Function

## undefined

> undefined is not a function

~~~ javascript
var x;
console.log(x); // undefined
~~~

A variable that has not been assigned a value.

~~~ javascript
typeof undefined; // 'undefined'
~~~

~~~ javascript
void 42; // undefined
~~~

// was a global object 

## null

~~~ javascript
typeof null; // 'object'
~~~

## Boolean

~~~ javascript
typeof true; // 'boolean'

Boolean(42); // true
~~~

* Primitive wrappers

## Truthy & Falsy

### Truthy:

~~~ javascript
if (true);
if ({});
if ([]);
if (42);
if ("foo");
if (new Date());
if (-42);
if (3.14);
if (-3.14);
if (Infinity);
if (-Infinity);
~~~

## Truthy & Falsy

### Falsy:

~~~ javascript
if (false);
if (null);
if (undefined);
if (0);
if (NaN);
if ('');
~~~

## Number

64-bit double precision 

~~~ javascript
0xff; // 255
42e3; // 42000
2e3; // 0.002
42 / 0; // Infinity
-42 / 0; // -Infinity
0 / 0; // NaN
~~~

* All primitives are immutable

## Number

~~~ javascript
typeof 42; // 'number'
NaN == NaN; // false
NaN === NaN; // false
isNaN(42 / undefined); // true
~~~

* `Number.MAX_VALUE`
* `Number.MIN_VALUE`
* `Number.MAX_SAFE_INTEGER 2**53 - 1`
* `Number.MIN_SAFE_INTEGER -2**53 + 1`

## Number

~~~ javascript
+'12'; // 12
+'12px'; // NaN
parseInt('12px', 10); // 12
~~~

~~~ javascript
0.42 + 0.24; // 0.6599999999999999
(0.42 + 0.24).toFixed(2); // 0.66
~~~

~~~ javascript
Math.round(4.4); // 4
Math.random(); // [0, 1)
~~~

~~~ javascript
8..toString(2); // '1000'
~~~

## String

~~~ javascript
var hello = 'hello';
var who = "world";
`hello ${who}`; // 'hello world'
'Юникод же 😜';
~~~

~~~ javascript
'hi'.length; // 2
'Hello'.charAt(3); // 'l'
'hello'[1]; // 'e'
'hello' + ' ' + 'world'; // 'hello world'
~~~

~~~ javascript
typeof typeof 42
~~~

... // "string"

## String

Lots of goods:

* String.prototype.concat()
* String.prototype.includes()
* String.prototype.match()
* String.prototype.replace()
* String.prototype.slice()
* String.prototype.split()
* String.prototype.substr()
* String.prototype.toLowerCase()
* . . .

## Object

~~~ javascript
var obj = { 1: 1 };
{ 'key': 'value'};
{ 'one':
    {
        two: 'three'
    },
    fn: function () {}
};
~~~

~~~ javascript
var obj = { hello: 'world' };
object['hello']; // 'world'
object.hello = 42;
delete object.hello;
~~~

// JSON

## Object

### ES6

~~~ javascript
var foo = 42;
{foo}; // {foo: 42}
~~~

~~~ javascript
var foo = 42;
{[foo] : 42}; // {42: 42}
~~~

~~~ javascript
var cat = {
    purr () {
    }
}
~~~

## Object

Lots of goods:

* Object.assign();
* Object.create()
* Object.keys()
* Object.defineProperty()
* Object.is()
* . . .

## Array

~~~ javascript
var arr = [1, 2, 3];
arr.push('yes');
console.log(arr); // [ 1, 2, 3, 'yes' ]

arr.length; // 4
arr[3]; // 'yes'
~~~

~~~ javascript
var arr = [1, 2, 3];
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
~~~

## Array

Lots of goods:

* Array.from()
* Array.isArray()
* Array.prototype.pop()
* Array.prototype.push()
* Array.prototype.reverse()
* Array.prototype.splice()
* Array.prototype.join()
* Array.prototype.slice()
* . . .

## Array

### Iteration

~~~ javascript
arr.map(el => el * el);
~~~

* Array.prototype.forEach()
* Array.prototype.every()
* Array.prototype.some()
* Array.prototype.filter()
* Array.prototype.map()
* Array.prototype.reduce()
* Array.prototype.reduceRight()

## built-in objects

* Date
* TypedArrays
* Maps, Sets, WeakMaps, WeakSets
* Error
* Math
* Promise
* Proxy
* RegExp
* JSON
* . . .

## Function

~~~ javascript
function ff() {} // function declaration
var ff = function() {} // function expression
var ff = function ff() {} // named function expression
(function() {}) () // IEFE
() => {} // arrow function expression
() => () 
~~~

Function - Object + [[Call]]

~~~ javascript
typeof function ff() {}; // 'function'
~~~

## Scope

Function scope

~~~ javascript
var a = 4;
function hello() {
    var b = 2;
    function world() {
        return a + b;
    }
    return world();
}
hello(); // 6
~~~

// Global

## Scope var, let

~~~ javascript
var a = 0;

if (true) {
    var a = 1;
}

a; // 1
~~~

~~~ javascript
let a = 0;

if (true) {
    let a = 1;
}

a; // 1
~~~

* let - blocked-scoped

## Function arguments

~~~ javascript
function hello() {
    arguments[0]; // 'Mike'
    arguments[1]; // 'Petr'
    arguments.length; // 3

    var args = Array.prototype.slice.call(arguments); // old-style
    var args = [...arguments] // es6 - spread operator
}
hello('Mike', 'Petr', 'Oleg');
~~~

[optimization args](https://github.com/petkaantonov/bluebird/wiki/Optimization-killers#3-managing-arguments)

~~~ javascript
function add(a = 0, b = 42, ...rest) {
    return a + b + rest.reduce((prev,  cur) => prev + cur, 0);
}
add(); // 42
~~~

## Function context

### this

~~~ javascript
function hello() {
    'use strict';
    console.log(this);
}

hello(); // undefined

var obj = { method: hello }
obj.method(); // obj
~~~

~~~ javascript
!function() {
    'use strict'; 
    [1,2,3].map(() => console.log(this), 14)
}()
~~~

## Function context

~~~ javascript
function sum(a, b) {
    console.log(this);
    return a + b;
}

sum.call(42, 1, 3); // this -> 42; returns 4
sum.apply({}, [1, 3]); // this -> {}; returns 4
~~~

~~~ javascript
function sum(a, b) {
    console.log(this);
    return a + b;
}
sum.bind(42, 11)(11)  // 42; 22;
sum.bind(42, 11).bind(33, 12)(55) // 42; 23
~~~

## Function context

~~~ javascript
function Car() {
    console.log(this);
}

new Car();
~~~

* new - creates instance of constructor function
* this - instance

## Prototype Inheritance

* All objects has link to Object.prototype
* lookup [] / .prop:
    * check instance for prop 
    * if instance has no prop look up it in prototype chain

~~~ javascript
function Car() {
    this.distance = 0;
}

Car.prototype.move = functions() {
    this.distance += 10;
}

var car = new Cat();
car.move();
~~~

## Prototype Inheritance

### es6

~~~ javascript
class Car {
    constructor () {
        this.distance = 0;
    }
    move () {
        this.distance += 10;
    }
    static isMy (car) {
        return car._id === 42;
    }
}

var car = new Car();
car.move();
~~~
// prototype - only functions
// __proto__ - link to prototype

## Prototype Inheritance

~~~ javascript
class Tesla extends Car {
  move () {
    super.move()
    this.distance += 40;
  }
}
~~~

~~~ javascript
var tt = new Tesla()
tt instanceof Tesla; // true
tt instanceof Car; // true
~~~

// B.prototype = Object.create(A.prototype);
// B.prototype.constructor = B;


## Environment

* browser
* node.js
* . . .

## Event loop

* que of events

sync

~~~ javascript
var data = fs.readFileSync('file.json');
processData(data);
~~~

async

~~~ javascript
fs.readFile('file.json', function(err, data) {
    if (err) throw err;
    processData(data);
});
~~~

// A lot of fs.reads

## setTimeout

~~~ javascript
var timerId = setTimeout(function() {
    console.log(42);
}, 1000); // not earlier
~~~

* setTimeout, clearTimeout, 
* setInterval, clearInterval
* one proccess

## Make it easy

* Callback `(err, data) => {}`
* EventEmitter `.on().off().trigger()`
* Stream `str1.pipe(str2)`
* Promise
* async/await

## **Контакты** {#contacts}

<div class="info">
<p class="author">{{ site.author.name }}</p>
<p class="position">{{ site.author.position }}</p>

    <div class="contacts">
        <p class="contacts-left contacts-top mail">yeti-or@yandex-team.ru</p>
        <p class="contacts-left twitter">@yeti_or</p>
    </div>
</div>
