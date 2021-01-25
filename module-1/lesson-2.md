# Lesson 2 - Converting JavaScript code to TypeScript, interfaces and enums

## Converting JavaScript code to TypeScript

To get started with TypeScript, try convert a small file or project from regular JavaScript.

The video below goes through the process of converting a simple, single-file JavaScript project to TypeScript.

<iframe src="https://player.vimeo.com/video/504018813" height="500" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

<a href="https://vimeo.com/504018813/6f408b23db" target="_blank">Watch on Vimeo</a>

<a href="https://github.com/NoroffFEU/converting-javascript-code-to-typescript" target="_blank">Code from the video</a>

---

## Interfaces

We can use interfaces to type objects, to make sure object values match the properties defined in the interface. This way we can check the objects have the properties and values the code we are passing them to require.

Say we have a function that accepts one argument, an object, that makes decisions based on the values of the properties of that object:

```ts
function generateMessage(message) {
	switch (message.severity) {
		case "ERROR":
			return `This is SERIOUS: ${message.content}`;
		case "WARNING":
			return `This is KIND OF SERIOUS: ${message.content}`;
		default:
			return "We're not sure what's going on.";
	}
}
```

To make our code more robust, and check for any missing properties in the message argument at design time, we can create an interface with the properties we require.

We need two properties, both of type string:

```ts
interface Message {
	severity: string;
	content: string;
}
```

We would then type our message argument with the Message interface:

```ts
function generateMessage(message: Message) {
	//...
}
```

We would then need to pass an object with a shape matching the interface otherwise we would receive a warning.

```ts
generateMessage({ severity: "ERROR", content: "Bad things happened" });
```

This way we would be sure the function receives an object with both a `severity` and `content` property of type string.

---

### Optional interface properties

To make an interface property optional we can place a `?` after its name:

```ts
interface ErrorMessage {
	warning: string;
	icon?: string;
}
```

The `icon` property is optional and we can pass a value to a ErrorMessage variable that doesn't contain an icon property:

```ts
function logError(error: ErrorMessage) {
	console.log(error.warning);
}

logError({ warning: "Damn" });
```

---

## Enums

Enums are sets of constants. A primary use case for them is to provide a limited set of options.

### Numeric enums

```ts
enum Response {
	Outraged,
	Bemused,
	Angry,
}
```

Above is a number enum with 3 `members`, with the first member having a value of `0`.

```ts
console.log(Response.Outraged);
// 0
console.log(Response.Bemused);
// 1
```

If we wanted to begin the values with a different number we could initialise the first member with a value:

```ts
enum Response {
	Outraged = 1,
	Bemused,
	Angry,
}
```

```ts
console.log(Response.Outraged);
// 1
console.log(Response.Bemused);
// 2
```

### String enums

Here is an example of an enum whose members have string values. It is common for the string values to be uppercase values.

```ts
enum MessageType {
	Error = "ERROR",
	Warning = "WARNING",
	Success = "SUCCESS",
}
```

```ts
console.log(MessageType.Warning);
// WARNING
```

We can impove our code above by changing our interface's `severity` property to be of type `MessageType` and instead of using string as the value, which is prone to errors, we'll use a constant from the enum.

```ts
enum MessageType {
	Error = "ERROR",
	Warning = "WARNING",
	Success = "SUCCESS",
}

interface Message {
	severity: MessageType;
	content: string;
}

function decideThings(message: Message) {
	switch (message.severity) {
		case MessageType.Error:
			return `This is SERIOUS: ${message.content}`;
		case MessageType.Error:
			return `This is KIND OF SERIOUS: ${message.content}`;
		default:
			return "We're not sure what's going on.";
	}
}

decideThings({ severity: MessageType.Error, content: "Bad things happened" });
```

---

This video uses an interface and an enum to improve our code from the first video above.

<iframe src="https://player.vimeo.com/video/504045256" height="500" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

<a href="https://vimeo.com/504045256/f601dfb4aa" target="_blank">Watch on Vimeo</a>

<a href="https://github.com/NoroffFEU/converting-javascript-code-to-typescript/tree/interface-and-enum" target="_blank">Code from the video</a>

---

### Compiling to a different version of ECMAScript

ECMAScript is the standard for JavaScript, it's aim is to ensure browsers' implementations of JavaScript are the same.

If you hear the term ES6 it refers to ECMAScript 6, which is the version that came out in 2015, and is also known as ES2015.

You can see what features were added to the language on <a href="https://en.wikipedia.org/wiki/ECMAScript" target="_blank">this page</a>.

We can change the version of ECMAScript that our TypeScript is compiled to using the target setting in the `tsconfig.json` file:

```json
{
	"compilerOptions": {
		"target": "es6"
	}
}
```

<iframe src="https://player.vimeo.com/video/504064281" height="500" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

<a href="https://vimeo.com/504064281/269d156bfd" target="_blank">Watch on Vimeo</a>

---

[Go to lesson 3](3)

---
