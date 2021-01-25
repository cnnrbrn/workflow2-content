# Lesson 1 - Introduction, configuration and basic types

## Introduction

TypeScript adds types to JavaScript and allows us to catch errors at design time rather than run time.

All valid JavaScript is valid TypeScript code, but TypeScript needs to be transpiled to JavaScript before it can run in the browser.

TypeScipt files have a `.ts` extension, and browsers won't recognise a file with that extension.

### Design time v run time

**Design time** - when you are your writing the code in your editor

**Run time** - when the code is running in the browser

It's far better to catch errors at design time rather than run time, but plain JavaScript makes this more difficult because it is dynamically typed, it doesn't know what type a variable holds until run time.

TypeScript adds type support, and errors are picked up when you type your code and when you compile (transpile) to JavaScript.

TypeScript will warn you if you are, for example, trying to pass a number value to a variable that is typed as a string variable.

### First example

Take this plain JavaScript function below.

It accepts one argument, tries to replace all spaces in the value passed in with dashes, and returns the value:

```js
function cleanString(stringToClean) {
	return stringToClean.replace(/\s/g, "-");
}
```

If we call the function with a string value like below, the code will work:

```js
const cleanedString = cleanString("a b c");
```

But because the `replace` method only works on string values, if we pass in a number value the code will produce an error when we run it.

```js
// this will produce and error when the code is run
const cleanedString = cleanString(7);
```

Giving the argument a type will allow us to catch potentials bugs while writing the code. The code below types the argument as a string.

```ts
function cleanString(stringToClean: string) {
	return stringToClean.replace(/\s/g, "-");
}
```

This video examines how using TypeScript can catch bugs like this at design time (when we are writing the code) versus only catching the error at run time - when the code is running in the browser.

<iframe src="https://player.vimeo.com/video/503775133" height="500" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

<a href="https://vimeo.com/503775133/3dd0ee43c8" target="_blank">Watch on Vimeo</a>

<a href="https://github.com/NoroffFEU/design-time-versus-run-time" target="_blank">Code from the video</a>

---

## Setting up TypeScript

You'll need to install TypeScript globally on your machine.

The `-g` switch installs a package globally so it's accessible from any folder.

```bash
npm install -g typescript
```

You'll write all your TypeScript code in files with `.ts` extensions and use the `tsc` command to transpile the TypeScript to JavaScript:

```bash
tsc path/to/file.ts
```

If your TypeScript file called `index.ts` is in a folder called `scripts` you would use the following command to compile it:

```bash
tsc scripts/index.ts
```

This will create a file called `index.js` in the same folder.

Add the `--watch` switch to re-compile any changes in your TS file.

```bash
tsc scripts/index.ts --watch
```

Once you've created and configured a `tsconfig.json` file in your project folder you can use the `Terminal -> Run Task -> tsc: watch` command to watch and compile your TypeScript.

<iframe src="https://player.vimeo.com/video/503819811" height="500" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

<a href="https://vimeo.com/503819811/3afb3c583d" target="_blank">Watch on Vimeo</a>

<a href="https://github.com/NoroffFEU/configuring-typescript" target="_blank">Code from the video</a>

---

## tsconfig.json

`tsonfig.json` holds the configuration for compiling our TypeScript code.

You can view all the (many) options <a href="https://www.typescriptlang.org/tsconfig" target="_blank">here</a>.

---

## Types

When we declare a variable with a type using a colon `:` that variable can only hold values of that type.

```ts
let myVar: boolean;
```

`myVar` can now only be assigned a boolean variable.

---

When initialising a variable with a value, the type of the variable will be inferred.

```ts
let title = "Book title";
```

`title` can now only hold string values.

---

## Basic Types

You will recognise `string`, `number` and `boolean` types from working with variables in regular JavaScript.

### String

```ts
let animal: string = "elephant";
```

### Number

```ts
let age: number = 20;
```

### Boolean

```ts
let isDelivered: boolean = false;
```

---

### Arrays

THere are two ways to write array types, in this case an array of strings:

```ts
const animals: string[] = ["dog", "cat", "monkey"];
// or
const animals: Array<string> = ["dog", "cat", "monkey"];
```

Here we declare an array of number types:

```ts
let winngingNumbers: number[];
// or
let winngingNumbers: Array<number>;
```

You will only be able to add values of that specific type to typed arrays.

If you wanted to allow an array to hold more than one type, you can declare the array like this:

```ts
let multipleTypes: (string | boolean)[];
```

String or boolean values could be added to the `multipleTypes` array, in any order.

---

### Tuples

Tuples are like special arrays, with a fixed amount of values and types. Unlike arrays, the variables stored in tuples must match the type at the position they're in.

```ts
let tuple: [string, boolean];
```

We can only add a string value in the first position and a boolean value in the second position:

```ts
tuple = ["hello", 32];
```

---

### Union

A union type can be more than one type, the pipe or vertical bar `|` being used to separate each type.

The parameter in this function can receive either a boolean or number value:

```ts
function DoThings(thing: boolean | number) {
	console.log(typeof thing);
}
```

---

### Null and undefined

The same as found in regular JavaScript.

```ts
const var1: undefined = undefined;
const var2: null = null;
```

---

### Any

We can turn off type checking by typing a variable as `any`.

```ts
let anyVar: any;
```

`anyVar` will accept any type.

When starting with TypeScript or converting a JavaScript project, it's often convenient to temporarily type a variable as any.

## Lesson Task

There are practice questions in the master branch of <a href="https://github.com/NoroffFEU/lesson-task-workflow2-module1-lesson1" target="_blank">this repo</a>.

There are example answers in the <a href="https://github.com/NoroffFEU/lesson-task-workflow2-module1-lesson1/tree/answers" target="_blank">answers branch</a>.

Try the exercises before checking the solutions.

---

[Go to lesson 2](2)

---
