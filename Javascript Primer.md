# Javascript Primer

Treehouse's javascript courses jump right in without explaining basic vocabulary and concepts. Here's a quick primer.

## Table of Contents

1. [Background on Javascript](#1)
2. [Basic Terminology](#2)
3. [Important Note](#3)
4. [Comments](#4)
5. [Variables](#5)
6. [Functions](#6)
7. [Arrays](#7)
8. [Objects](#8)
9. [Why Use Objects?](#9)
10. [Anything Else?](#10)

<a name="1"></a>
## Background on Javascript

**WARNING! Nerd stuff ahead.** Absolutely none of this section is useful for the course. You can skip to the next one if you want.

Generally speaking, programming languages are "functional" or "object oriented." *Functional* languages are series of actions; do this, then that, then another thing. *Object oriented* languages focus on creating independent "things" and linking them together to make programs. (That's way oversimplified, but it'll do for now.) Javascript is both of these things and neither. It's a *prototyped* language: a functional language with a bit of object oriented stuff glued on top.

Confusingly, javascript has multiple versions out in the wild right now. **ECMAScript 5** (also known as ES5) is the most basic version. It works in every current browser. **ECMAScript 6** (ES6) is a newer revision that supports things like `let` declarations, constants, lambda functions, and a whole bunch of other stuff you probably haven't heard of yet. On top of all that, there's an even *newer* revision right now called **ECMAScript 2015**. No browsers support this yet, as far as I know. You'll mostly see it used in Node.js, a backend programming language.

Okay, enough of that. Here's what you came for!

<a name="2"></a>
## Basic Terminology

<dl>
	<dt>Comment</dt>
	<dd>Lines of code that don't do anything. Allows you to leave notes for later. Good, useful comments will make other programmers love you forever.</dd>
	<dt>Keyword</dt>
	<dd>A name reserved by the programming language that can't be used for anything else. (For example, you can't name a variable <code>if</code>.)</dd>
	<dt>Type</dt>
	<dd>The kind of data a variable contains.</dd>
	<dt>Boolean</dt>
	<dd>A variable with only two values: <code>true</code> or <code>false</code>. Mostly used for conditionals.</dd>
	<dt>String</dt>
	<dd>A bit of text.</dd>
	<dt>Int / Integer</dt>
	<dd>Whole numbers.</dd>
	<dt>Float / Floating Point Numbers</dt>
	<dd>Numbers with decimal points. (Basically.)</dd>
	<dt><code>undefined</code></dt>
	<dd>A keyword that means "does not exist." Rarely used.</dd>
	<dt><code>null</code></dt>
	<dd>A keyword that means "no value." The associated variable still exists, but it doesn't have anything in it.</dd>
	<dt>Variable</dt>
	<dd>A bucket you can put things in. Declared by <code>var</code> and, in ES6 and later, <code>let</code>.</dd>
	<dt>Constant</dt>
	<dd>A variable that can't be changed after it's set.</dd>
	<dt>Array</dt>
	<dd>A ordered list of values that, maddeningly, is also a variable.</dd>
	<dt>Element</dt>
	<dd>A single value inside an array.</dd>
	<dt>Index</dt>
	<dd>The position of an element inside an array.</dd>
	<dt>Function</dt>
	<dd>A defined block of code that can be run with one command. Can accept input parameters and even return a value.</dd>
	<dt>Declaration</dt>
	<dd>Code that defines something, i.e. a function or variable.</dd>
	<dt>Function Call/Invoke</dt>
	<dd>Running a function.</dd>
	<dt>Parameter</dt>
	<dd>A copy of a value passed into a function.</dd>
	<dt>Return Value</dt>
	<dd>Sent from a function via the <code>return</code> command. It can be used to pass a result back to whoever called the function.</dd>
	<dt>Scope</dt>
	<dd>Anything inside a pair of brackets. (It's actually more complicated than that, but this'll do for now.)</dd>
	<dt>Global Variable</dt>
	<dd>Variable, usually declared at the top of your code, that can be used by everybody. This is not necessarily a good thing.</dd>
	<dt>Loop</dt>
	<dd>Specific commands that repeat until a certain event happens. It can also just loop forever, if you really want.</dd>
	<dt>Conditional</dt>
	<dd>A set of code blocks that run only under certain conditions. Basically, an <code>if</code> statement.</dd>
	<dt><code>if/then</code> Statement</dt>
	<dd>Another name for <code>if</code> statements. Comes from BASIC, a much older programming language where <code>IF</code> statements and their code had the word <code>THEN</code> between them.</dd>
</dl>

<a name="3"></a>
## Important Note

**Javascript starts counting at zero.** From `for` loops to array indexes, 0 is used as our starting number and not 1. There's inherited reasons for this and absolutely none of them matter right now. Just keep in mind: everything starts at 0.

<a name="4"></a>
## Comments

Comments come in two forms: `// single line` and `/* blocks */`. Blocks allow you to use multiple lines.

You can start any type of comment on its own line *or* at the end of a line of code.

<a name="5"></a>
## Variables

`var` declares a variable. For example:

```
var a = 4;    // "a" now references the number 4
var b = 'Test';  // "b" now references the string 'Test'
```

In addition, you can reserve a bucket for later:

```
var xyz;
/* Some code happens here, then... */
xyz = 4;
```

In most programming languages, you have to declare your variable's type ahead of time. **Javascript does not care about this.** If you put an integer into a variable, and then put a string in later, it won't even blink. Normally, it's smart enough to know what to do...

```
var a = 4 + 4;        // 8
var b = 'ab' + 'bc':  // 'abbc'
var c = 'ab' + 4;     // 'ab4'
```

...but not always.

```
var x = '4' + 4;
// I don't know if this is '44' or 8, to be honest. But, you get the point.
```

So, be careful when you mix variable types. Don't just assume javascript will do all the work for you.

<a name="6"></a>
## Functions

Declaring functions is pretty straightforward:

```
function addSomeNumbers(a, b) {
	return a + b;
}
```

Here, we have a function called `addSomeNumbers` that accepts two parameters, `a` and `b`. It returns the sum of those two numbers. This is completely useless for the real world, but it's just a simple example, so bear with me :)

Now that it's declared:

```
var x = addSomeNumbers(4, 2);  // x is now 6
```

This demonstrates how *return values* work. You don't have to return a value, though:

```
window.alert("Look at me! I'm a function that doesn't return anything!");
```

You can return a value whenever you like in a function, or not at all. **Whenever you call `return`, though, the function is done.** Execution stops immediately and the code that called it takes back over.

Again, be careful with typing! This code will work just fine:

```
var y = addSomeNumbers('Ab', 'xy');   // y now contains... 'Abxy'?!
```

...but it probably isn't what you intended. This is why strict typing is a good thing. That's a discussion way outside the scope of this class, though, and can be safely ignored.


<a name="7"></a>
## Arrays

Whenever you see `[]`, you're dealing with an array. Arrays are basically ordered buckets with data in them.

```
var anArray = [1, 2, 6, 4];
```

To access individual array elements, you use the `[]` operator with an index. Remember, **javascript starts counting at zero.**

* `anArray[0]` is 1
* `anArray[1]` is 2
* `anArray[2]` is 6
* `anArray[3]` is 4

You can change a value in an array, too:

```
anArray[1] = 4;   // Array is now [1, 4, 6, 4]
```

Finally, you can use a couple of special commands, `push` and `unshift`, to add new items. `push` will add to the *end* of the array. `unshift` will add to the *beginning.*

```
var anArray = [1, 4, 6, 4];
anArray.push(5);  // Array is now [1, 4, 6, 4, 5]
anArray.unshift(0);  // Array is now [0, 1, 4, 6, 4, 5]
```

Deletion can be accomplished through `splice`, which is way more complex. We may or may not get into that. Now's not the time, though.

One last word of warning: Don't do this...

```
var anotherArray = [1, 2, 3];
anotherArray[5] = 4;  // Array is now [1, 2, 3, null, null, 4]
```

It's legal, but you'll end up with gaps in your array. It's confusing and wasteful. Use `push` and `unshift` instead!

<a name="8"></a>
## Objects

Objects in javascript can be thought of as a named collection of variables.

```
var x = {
   a: 4,
   b: 'Test'
};
```

Each item is called a *field.* You can get values from the object by using a period and the field name:

* `x.a` is 4
* `x.b` is 'Test'

You can also add functions to objects.

```
var y = {
   a: 51,
   b: 'Lol',
   c: function() { y.d = 'A new field.'; }
};
```

Calling `y.c()` will add a new field, `y.d`, which is equal to `A new field.`. This also demonstrates how you can add fields to an object on the fly.

Removing a field is easy:

```
delete y.b;   // y.b is no longer 'Lol'... because y.b doesn't exist any more!
```

This is a lot tidier than just setting it to `null.`

<a name="9"></a>
## Why Use Objects?

1. **They're better for organization.** It's much easier to pass around a single bundle instead of constantly digging through your code to figure out which things are related and why. Programs like that are called *spaghetti code*&mdash;a pile of function calls and variables that are near impossible to untangle.
2. **They allow you to name parameters.** Look at the difference between `mysteriousFunction(4, 'A value', 41.4);` and `mysteriousFunction({startValue: 4, description: 'A value', modifier: 41.4});` Which one is less mysterious?
3. **They can be tied to a single prototype, so when the prototype changes, all its objects change.** This is a cornerstone of object oriented programming in javascript, and we won't go into it here. Just be aware that it's a thing.

<a name="10"></a>
## Anything else?

Objects and arrays can be declared as empty, which provides a good starting point for later.

```
var x = [];
var y = {};
/* Some code happens here */
x.push(4);
y.testField = 'Ready to go!';
```

Oh, and variables can hold functions, too!

```
function test() { return 'a'; }
var x = test;
var res = x();  // calls test(), res is set to 'a' afterwards
```

This is but one of the many tricks you can do, for good or ill. Javascript never runs out of ways for you to shoot yourself in the foot ;)
