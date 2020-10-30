---
title: When and How to Use the Spread (...) Operator in JavaScript
tags: JavaScript, Programming, ES6
category: JavaScript
excerpt: ES6 provides a new operator called the spread operator that consists of three dots (...). The spread operator is a useful and easy syntax for combining or adding items to arrays, objects, or spreading an array out into a function’s arguments.
created: 2020-10-29
image: ./images/spreadphoto.jpg
image_caption: Photo by Danial RiCaRoS on Unsplash
author: author1
---

# What is the Spread Operator?

In JavaScript, spread syntax refers to the use of an elipsis of three dots (...) to expand an iterable object into the list of arguments. The spread operator was added to JavaScript with the release of ES6. It is a useful and easy syntax for combining or adding items to arrays, objects, or spreading an array out into a function’s arguments. The spread (...) operator can be used for many different routine tasks including the following:

    - Copying an Array
    - Concatenating or combining arrays
    - Using an array as arguments
    - Adding an item to a list
    - Combining objects

So now that we have a quick intro into what a spread operator is and a few use cases, let's dive into some examples of the tasks listed above.

## Copying and Combining Arrays

Using the spread (...) operator is a convenient and efficient way to copy an array, comibine multiple arrays or even adding new items to an existing array.


So let's say that we have the following two arrays of Starks and Targaryens.

```js
let starks = ['Bran', 'Arya', 'Sansa'];
let targaryens = ['Daenerys', 'Rhaegar', 'The Mad King'];
```
---

If I want to make a copy of the starks, I would do the following: 

```js
let starksCopy = [...starks];

console.log(starksCopy); // Output => ['Bran', 'Arya', 'Sansa']
console.log(starksCopy[1]); //  Output => Arya
```

> Note that the spread operator will create a new reference to its primitive values. I will go over this in a little more detail down below.


But what if the Starks and Targaryens would want to combine families? This is how we would go about combining the two arrays:

```js
let combined = [...starks,...targaryens];
console.log(combined); // Output => ['Bran', 'Arya', 'Sansa', 'Daenerys', 'Rhaegar', 'The Mad King']
```
---

As you can see, it is pretty straight forward and a nice tool to have for simply combining/concatenating arrays!

## Adding an Item to a List

Not only can you use the spread (...) operator to copy or combine arrays, you can also add items to an existing list. Let's say that we find out that there might be another Targaryen. Let's name him `Jon`. We would like to add `Jon` to the list of `targaryens` and would use the following to do so:

```js
const expandedTargaryens = ['Jon', ...targaryens];
console.log(expandedTargaryens); // Output => ['Jon', 'Daenerys', 'Rhaegar', 'The Mad King']
```
---

It's that simple! Jon is now a part of the Targaryens.

## Using an Array as Arguments

Since the spread (...) operator actually “spreads” an array into different arguments, you can use a spread operator with any function that accepts multiple arguments. Below is an example of using a spread operator with a function that accepts multiple arguments.

```js
const kingChoices = ['Jon', 'Bran', 'Tyrion'];

let printChoices = (choice1, choice2, choice3) => {
    console.log(`Choices: ${choice1}, ${choice2}, ${choice3}`);
} 

printChoices(...kingChoices); // Output => Choices: Jon, Bran, Tyrion
```
---

As you can see, it actually works out quite simply to spread an array into different arguments and saves you a little time.


## Copying and Combining Objects

Much like we did for arrays, the spread syntax is useful for combining the properties and methods on objects into a new object. 

```js
const obj1 = {
    firstName: 'Jon'
}
const obj2 = {
    lastName: 'Snow'
}
const combinedObj = {...obj1, ...obj2, };
console.log(combinedObj); // Output => { firstName: 'Jon', lastName: 'Snow'}

const combinedCopy = {...combinedObj};
console.log(combinedCopy); // Output => { firstName: 'Jon', lastName: 'Snow'}
```
---

So similar to arrays, we are able to quickly combine or copy objects. Once again, when copying it creates a new object with no reference to the original object.

## Copying by Reference and a Gotcha

One of the benefits of using the spread (..) operator is that it will create a new reference. What this means is that any changes to the original array will not affect the copied array, which is what would happen if we had used the assignment operator `=`. I've put together an example of the two different ways and what the output would be.

```js
const names = ['Jon', 'Bran', 'Arya'];
const copyWithEquals = names;
const copyWithSpread = [...names];

names[0] = 'Sansa';

console.log(names); // Output => ['Sansa', 'Bran', 'Arya']
console.log(copyWithEquals); // Output => ['Sansa', 'Bran', 'Arya']
console.log(copyWithSpread); // Output => ['Jon', 'Bran', 'Arya']
```
---

Looking at the above code, you will notice that the `copyWithSpread` variable returns the unchanged array that it was set to. The `copyWithEquals` variable returns the modified array since it was created using the assignment operator `=`.

> COMMON GOTCHA: The spread operator only copies the first level with a new reference, but the deeper values are still linked together. The spread (...) operator only makes a shallow copy.

## Conclusion

The spread (...) operator is a very convenient feature that was added to ES6 and is useful for working with arrays and objects. 

One of my favorite use cases for the spread operator is making copies of arrays or objects so that there is no reference to the original object or array. It has definitely saved me time and headaches by using it. I encourage other developers who haven't used it yet to try it out and see what you think.



