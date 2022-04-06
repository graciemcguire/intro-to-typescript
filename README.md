# Introduction to TypeScript

## Learning Goals

- Understand TypeScript at a high level
- Explain some of the benefits of using TypeScript when developing web applications

## Introduction

If you've ever worked with JavaScript, you've undoubtedly run into bugs that took
what felt like forever to find the root of or weird errors (looking at you, 
`'undefined' is not a function`), and cursed the JavaScript gods for allowing such
problems to always happen. If this sounds familiar, then TypeScript may be the
answer to your curses.

A superset of JavaScript, TypeScript was created by Microsoft in 2012 to help
developers write code, and catch errors and bugs quickly and efficiently. This
allows developers like you to put your energy and focus towards designing a good
experience for end users of the application.

In this lesson, we will discuss what exactly TypeScript is and why it is so
awesome and useful.

## TypeScript Overview

In a study done for the [2021 State of JS][state-of-js], 69% of the developers
polled said they preferred to use TypeScript as their JavaScript compiler, and
in the Github study, [Top Languages Over The Years][top-languages], TypeScript
came in as the #4 most popular language for 2 years in a row! (2020-2021)

![Octoverse - Top Languages Over The Years 2021 Image](https://curriculum-content.s3.amazonaws.com/blackrock/intro-to-typescript/top-languages-used-2021.png)

As mentioned above, TypeScript is a superset of JavaScript... so what does that
mean? A superset expands and elaborates on all the parts of a language, while
still fully encompassing the entirety of the original language.

Think about JavaScript before ES6. If you were writing a program in ES5 or
before, and tried to use `const` to declare a constant variable, it wouldn't
work, right? On the other hand, if you were writing your program using ES6 and
wanted to go old school and use `var` to declare your constant variable, it
would still work, but you would be opening your code up to a lot of potential
bugs in the future. The same idea goes for TypeScript. We can write regular
JavaScript code into a TypeScript file and it will work fine, but by using
TypeScript it will work a whole lot better, and save us a lot of debugging
and hair-pulling down the line.

TypeScript builds onto JavaScript by adding type-checking and type declaration
abilities for all different data-types, as well as classes and other
object-oriented features, through its type system.

By declaring types, we can write extremely explicit JavaScript code by telling
our program what type of datatype a variable should be, what a function argument
should be, what our arrays will contain, and more!

By using this type system and the TypeScript compiler, TypeScript is able to
easily highlight and unexpected behaviors in our code, taking most of the guess
work out of debugging!

## Working with Types

We recommend getting to know the [TypeScript docs][typescript], as they are very
thorough, easy to follow, and an all around great resource, but we wanted to go
over a couple of the ways we can work with Types in TypeScript to give you a good
sense of what the benefits of TypeScript are!

- **Type by Inference**
- **Type Annotation**

Let's dig into each of these features and talk a bit more about each one.

### Type by Inference

TypeScript uses type inference to assume the type of a variable in a program,
based on the data type it was assigned at its initial declaration. If we try to
change the data type, type inference will log a complaint.

```ts
let helloWorld = 'Hello, World!'

helloWorld = 2
// => Type 'number' is not assignable to type 'string'.
```

Let's say we want to create an object where the properties `firstName`,
`lastName`, and `occupation` are all strings, but the `id` property is a number.

```ts
const userObj = {
  id: 1,
  firstName: 'Audre',
  lastName: 'Lorde',
  occupation: 'Poet',
}

// {id: number, firstName: string, lastName: string, occupation: string}
```

Thanks to type inference, TypeScript correctly infers the type we want to use
for each property. However, what if we want to do things a bit more dynamically?

### Defining Types

Sometimes inferring the types we're using in our code isn't always as explicit
and straightforward as the example above. TypeScript always knows the shapes of
our types - what methods and properties our variables do/don't contain. We can
use this concept of _shaping_, and define our types to fit the specific needs of
our programs, by using _type annotations_. Type annotations ensure that we only
ever assign certain types to our variables. Let's take a look.

```ts
// We can use an interface declaration to describe our object's shape:

interface User {
  id: number;
  firstName: string;
  lastName: string;
  occupation: string;
}

// Then we can use type annotations to ensure our object fits to this shape.

const userObj : User = {
  id: 1,
  firstName: 'Audre',
  lastName: 'Lorde',
  occupation: 'Poet',
}
```

If we had defined our `userObj` like the following TypeScript would have logged
a complaint:

```ts
const userObj : User = {
  id: 1,
  name: 'Audre Lorde',
  occupation: 'Poet',
}

// => Type '{ id: number; name: string; occupation: string; }' is not assignable to type 'User'.
// Object literal may only specify known properties, and 'name' does not exist
// in type 'User'.
```

We'll get more into this later, but for now just remember that type annotations
are super helpful!

## Conclusion

As you saw, TypeScript is a super helpful and powerful tool for us to write
clean and error-free code. TypeScript helps us catch errors at compile time,
makes refactoring much easier, and stops JavaScript type coercion in its tracks!

## Resources

- [2021 State of JS][state-of-js]
- [Top Languages Over The Years][top-languages]
- [TypeScript docs][typescript]

[state-of-js]: https://2021.stateofjs.com/en-US/other-tools
[top-languages]: https://octoverse.github.com/#top-languages-over-the-years
[typescript]: https://www.typescriptlang.org/docs/
