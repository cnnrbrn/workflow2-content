<!-- # Lesson 3

## Function return types

We can type the return value of a function using a colon `:`.

This will set the return type of the function (as well as both its arguments) to be a number:

```ts
function multiply(number1: number, number2: number): number {
	return number1 * number2;
}
```

If you tried to return a value type other than a number you would see a warning.

## Void

`void` has no type at all.

If a function doesn't return a value, you can set its return type to void:

```ts
function logMessage(message: string): void {
	console.log(`The message is: ${message}`);
}
```

---

## Types

Types are similar to interfaces.

## Classes

<!-- ## Lesson Task

There are practice questions in the master branch of <a href="https://github.com/NoroffFEU/lesson-task-pf-module1-lesson3" target="_blank">this repo</a>.

There are example answers in the <a href="https://github.com/NoroffFEU/lesson-task-pf-module1-lesson3/tree/answers" target="_blank">answers branch</a>.

Try the exercises before checking the solutions. -->

---

-   [Go to lesson 4](4)

--- -->
