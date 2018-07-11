---
layout: post
title:      "JavaScript - The Language That Lies"
date:       2018-07-11 15:47:52 -0400
permalink:  javascript_-_the_language_that_lies
---


JavaScript is certainly a quirky language, and it seems to be full of surprises. First off, its name implies some sort of connection or tie to the Java programming language when in reality the similarities may as well end at the name. 

## JavaScript !== Java

While the names are certainly similar, these two languages differ in many key ways. Even in implementation alone, Java can and is used to create standalone applications, while JavaScript may only run in a browser. A few more differences:

* Java is a complied language (sort of), while JavaScript is interpreted 
    - More information on compilation vs. interpretation, as well as the *sort of* above can be found [here](https://www.programmerinterview.com/index.php/general-miscellaneous/whats-the-difference-between-a-compiled-and-an-interpreted-language/)
* Java is considered a "strongly typed" language, while JavaScript is definitely a "weakly typed" language - more on this below
* JavaScript, as the name implies, is a scripting language, whereas Java is not. 
    - This is essentially point one with different wording. More information [here](https://www.educba.com/programming-vs-scripting/).

While the visual syntax may appear similar on a basic level, using curly braces for blocks and wrapping if conditionals in parentheses for example, these two languages are very different in their implementation and uses. 

## Weakly Typed Language

What do we mean when we say a language is "strongly typed" or "weakly typed?" These are referring to a language's _type system_. A type system, in brief, is like a set of rules around what different types of values (and the variables that hold those values) can and cannot do. A strongly typed language enforces its set of type rules strictly, while a weakly typed language enforces its set of type rules rather loosely. I'm still developing my understanding of types and how they're enforced, but examples can help to make this pretty clear. 

Below, we will declare a String type and assign it to a variable "s", and declare an Integer (32 bit, signed) type and assign it to a variable "x". The comments following the `println!()` macro show the output when the program is run.

#### Rust:

```
fn main() {
    let s = String::from("Hello, world!");
		
	let x: i32 = 8;
		
	println!("{}", s); // => "Hello, world!"
		
	println!("{}", x); // => "8"
}
```

As you can see, we assign each variable a type at the instant of declaration. If we were to try to run the code below, the compiler would throw an error.

#### Rust:

```
fn main() {
    let s = String::from("Hello, world!");
		
	let x: i32 = 8;
	
	let y = s + x;
}
```

This will not compile, and will exit with an error stating "no implementation for 'i32 + std::string::String'". This is the compiler telling us that it has no way to add an Integer type and a String type - a great example of a strongly typed language, and a great example of useful compiler errors!

A similar program in JavaScript would look like this:

#### JavaScript:

```
let s = "Hello, world!";

let x = 8;

let z = s + x;

console.log(s) // => "Hello, world!"

console.log(x) // => "8"

console.log(z) // => "Hello, world!8"
```

### What's different here? 

Well, for one, JavaScript only has one, all-encompassing "number" type, as opposed to the many different number types of other languages. Rust, for example, has the following number types: i8, u8, i16, u16, i32, u32, i64, u64, isize, usize. _Wow, that's a lot of number types!_ Secondly, JavaScript is implicitly converting the Number type 8 to a String type in order to add the two values together. 

### So what? That seems like a nice thing!

In a way, it is! We don't have to explicitly convert the variable `x` with something like `x.toString()` before adding it, so it results in less code. **However**, this can lead to unexpected behavior and bugs if you're not intending to convert certain variable types. Consider this code: `1+2+3+4+5 // => 15` Right on - just what we wanted.

Now this code: `1+2+3+'4'+5 // => "645"`

Uh.... That's quite strange. What's happening here is that JavaScript engine is going along nicely, adding our numbers together, until it reaches the `'4'`. It sees now that we're trying to add `6` to `'4'` and does the _nice_ thing of converting one of these to the same type in order to add them together. The JavaScript engine chooses to convert `6` to `"6"` and add the two strings together, resulting in `"64"`. It then _very kindly_ converts `5` to `"5"` and returns us the string `"645"`, which is very likely not what we were intending. 

## What else is weird??

So much. The way JavaScript types work is so fast and loose, it'll make your head explode! Consider the examples below:

```
typeof({}) // => "object"

const twoEmptyObjs = {} + {} // add together two empty objects 

console.log(twoEmptyObjs) // => "[object Object][object Object]"

typeof(twoEmptyObjs) // => "string"

--------------------------------------------------------------------------------

typeof(null) // => "object"

typeof(undefined) // => "undefined"

console.log(undefined ** null) // => 1

--------------------------------------------------------------------------------

console.log([]) // => Array []

typeof([]) //=> "object"

let a = [] + []

console.log(a) // => undefined

typeof(a) // => "string"
```

As you can see, JavaScript does some pretty weird stuff. It lies to you about what types you have and gives you some totally off-the-wall return values for some behaviors. 

## Okay, JS is totally weird. What do we do?

Truthfully, there's not much _to_ be done. JavaScript is a very useful and widespread language. You almost can't write a web application or create a website without it. We kind of have to just take it at face value, accept its quirks, and work with it. Most times, simply being aware of these oddities is enough to work around them, and proper debugging skills will get you out of any ditch you manage to drive yourself into. As with any language: **practice, write code, read documentation**. Good luck out there! 
