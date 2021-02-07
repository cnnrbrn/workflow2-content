# Lesson 2 - Axios and Lodash

### Running the code examples

\*Note: Use a bundler like Parcel to run the examples, e.g. `parcel index.html`

To use `async/await` with Parcel, add the following entry in package.json:

```json
"browserslist": [
    "last 1 Chrome version"
]
```

<img src="/images/axios-1.png" alt="Using async/await with Parcel" style="max-width: 700px">

## Axios

<a href="https://github.com/axios/axios" target="_blank">Axios</a> is a popular http client, similar to JavaScript's built-in `fetch`.

```
npm init -y
npm install axios
```

An API call made with `fetch` like this

```js
// url used for both examples
const url = "https://jsonplaceholder.typicode.com/posts/1";

// using fetch
async function callApiWithFetch() {
	// GET is the default method for fetch
	const response = await fetch(url);
	const json = await response.json();
	console.log(json);
}

callApiWithFetch();
```

Would be written like this using axios:

```js
import axios from "axios";

// using axios
async function callApiWithAxios() {
	const response = await axios.get(url);
	console.log(response.data);
}
callApiWithAxios();
```

Axios performs automatic transforms of JSON data, whereas fetch is a two-step process: first you request the data, then you transform it to JSON.

If you are not going to use Axios-specific features (some of which are listed below) it is maybe not worth loading an extra library to write code that could be handled with fetch.

Some features of Axios not found in fetch:

-   allows cancelling requests
-   built-in support for download progress
-   wider browser support, including Internet Explorer
-   ability to intercept HTTP requests

<!-- ---

There are POST, PUT and DELETE examples in the answers branch of the lesson task. -->

---

### Lodash

<a href="https://lodash.com/">Lodash</a> is a JavaScript utility library that provides many useful methods to help simpliy your code, with the pay-off being you are loading an extra library into your code with a resultant increase in your code size.

We could load it directly from a CDN (Content Delivery Network) by using the latest version from <a href="https://www.jsdelivr.com/package/npm/lodash" target="_blank">here</a>:

```html
<script src="link/to/latest/version"></script>
```

Or you can install it via NPM:

```
npm install lodash
```

You can import all of lodash so that you can use any method like this:

```js
import _ from "lodash";
```

For a smaller bundle size import only the methods you are going to use:

```js
import { orderBy, isEqual } from "lodash";
```

You can find details of all Lodash methods in <a href="https://lodash.com/docs">the documentation</a>.

We'll take a look at two useful methods below.

### orderBy

This method will sort a collection (an array or a collection) in either ascending (the default) or descending order.

```js
import { orderBy } from "lodash";

const products = [
	{
		name: "Product A",
		price: 15.99,
	},
	{
		name: "Product B",
		price: 8,
	},
	{
		name: "Product C",
		price: 10.5,
	},
	{
		name: "Product D",
		price: 4.95,
	},
];

const orderedProducts = orderBy(products, ["price"], ["asc"]);

console.log(orderedProducts);
```

---

### isEqual

We can use this method to compare objects.

```js
const product1 = {
	name: "Product",
	price: 5,
};

const product2 = {
	name: "Product",
	price: 5,
};
```

We can't simply use the comparison operator to check if the object values are the same like we can with primitive values like strings or numbers.

```js
console.log(product1 === product2);
// false
```

If we use the `isEqual` method we will get the results we expect:

```js
console.log(isEqual(product1, product2));
// true
```

<!-- ### debounce -->

<!-- [Go to lesson 4](4) -->

<!-- --- -->
