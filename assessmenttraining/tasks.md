# BrowserAPI

## Exercise 1

Use `document.createElement()` and `element.appendChild()` to add elements on a web page.

## Exercise 2

Use `Element.remove()` and `Node.removeChild()` to remove elements from a web page.

## Exercise 3

Given the following html, create a eventlistener that changes the color on a element when clicked. The `rndColor()` function returns a random color.

HTML:

```HTML
<html>
  <head>
    <title>Color changer</title>
  </head>
  <body>
    <a href="#" class="clickme">The link</a>
    <script>
      const rndColor = () => {
        const rndNumber = () => Math.floor(Math.random() * 255)
        return `#${((1 << 24) + (Math.round(rndNumber()) << 16) + (Math.round(rndNumber()) << 8) + Math.round(rndNumber())).toString(16).substr(1)}`;
      };
    </script>
  </body>
</html>
```

> Hint: `element.addEventListener()`, `document.querySelector()`, `element.style.color`

## Exercise 4

Given the following HTML, when the user pushes the button the text in the input-field should be reversed.

```HTML
  <html>
    <!-- ... -->
    <form>
      <input type="text" class="thetext" value="I should be reversed" />
      <button type="submit" class="thebutton">Reverse text</button>
    </form>
    <!-- ... -->
  </html>
```

## Exercise 5

With the starting html code:

```html
<html>
  <head>
    <title>Document</title>
  </head>
  <body>
    <main class="main"></main>
  </body>
</html>
```

Use the DOM API to alter the document to the following (not using innerHTML)

```html
<html>
  <head>
    <title>Document</title>
  </head>
  <body>
    <main class="main">
      <nav>
        <a href="#">Link 1</a>
        <a href="#">Link 2</a>
        <a href="#">Link 3</a>
      </nav>
    </main>
  </body>
</html>
```

When you click on one of the links, the link should be deleted from the DOM.

> Hint: Look at `document.createElement(), element.appendChild(), element.remove()`

## Exercise 6

With the starting HTML code:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Exercise: Modify the DOM with JavaScript</title>
  </head>
  <body>
    <h1>Shopping List</h1>
    <ul id="shopping-list">
      <li class="item">Eggs</li>
      <li class="item">Bread</li>
      <li class="item">Milk</li>
      <li class="item">Butter</li>
      <li class="item">Cheese</li>
    </ul>
  </body>
</html>
```

Use the DOM API to alter the document to the following:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Exercise: Modify the DOM with JavaScript</title>
  </head>
  <body>
    <h1>Shopping List</h1>
    <ul id="shopping-list">
      <li class="item">Eggs</li>
      <li class="item">Bread</li>
      <li class="item">Milk</li>
      <li class="item">Butter</li>
      <li class="item">Cheese</li>
      <li class="item">Apples</li>
      <li class="item">Oranges</li>
      <li class="item">Bananas</li>
    </ul>
    <button id="remove-last-item">Remove Last Item</button>
  </body>
</html>
```

1. Add three new items to the shopping list: "Apples", "Oranges", and "Bananas".
1. Add a button below the shopping list with the id "remove-last-item".
1. When the "remove-last-item" button is clicked, remove the last item from the shopping list.

## Exercise 7

Using the starting HTML code:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Exercise: Create a To-Do List</title>
  </head>
  <body>
    <h1>To-Do List</h1>
    <form>
      <label for="new-item">New Item:</label>
      <input type="text" id="new-item" name="item" />
      <button type="submit">Add</button>
    </form>
    <ul id="todo-list">
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
  </body>
</html>
```

1. When the form is submitted, add a new item to the list with the text entered in the input field.
1. When an item is clicked, toggle a "completed" class on it to mark it as completed. (Tip: `text-decoration: line-through;`)
1. Add a "Delete" button to each item that removes it from the list when clicked.
1. Add a "Clear Completed" button that removes all completed items from the list.

The final HTML output should look something like:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Exercise: Create a To-Do List</title>
  </head>
  <body>
    <h1>To-Do List</h1>
    <form>
      <label for="new-item">New Item:</label>
      <input type="text" id="new-item" name="item" />
      <button type="submit">Add</button>
    </form>
    <ul id="todo-list">
      <li class="completed">Item 1 <button class="delete">Delete</button></li>
      <li>Item 2 <button class="delete">Delete</button></li>
      <li>Item 3 <button class="delete">Delete</button></li>
    </ul>
    <button id="clear-completed">Clear Completed</button>
  </body>
</html>
```

# Async

## Exercise 1

Create a function `getPastTime(callback)` that returns the seconds of the current time five (5) seconds ago.

Example use:

```javascript
getPastTime(function (pastTime) {
  console.log(new Date().getSeconds(), pastTime); //-> 37, 32 || 3, 58
});
```

> Hint: the current time can be obtain with `const now = new Date()` and then `now.getSeconds()`

## Excercise 2

Create a function `concatStrings(string1, string2, callback)` that takes two strings and concats (add them together) them. Example: string1 = 'hello' string2 = 'world' -> helloworld.

- The function does not return anything (undefined), but instead takes a function **callback** which will be called with the result of the operation as first parameter.
- The function waits two seconds before calling back with the result.

Example use:

```javascript
concatStrings("hello", "world", function (joinedString) {
  console.log(joinedString); //-> helloworld
});
```

## Exercise 3

Create a function `promiseMeThis(str)` that returns a promise that resolves after 2 seconds with the text `I'll try to promise the following: <str>`. If the input is not a string, reject after 2 seconds with the text `I'll have to reject: <str>`.

Example use:

```javascript
promiseMeThis("To keep my promises").then((result) => {
  console.log(result); //-> I'll try to promise the following: To keep my promises
});

promiseMeThis(["To", "try"])
  .then()
  .catch((err) => {
    console.log(err); //-> I'll have to reject: ["To", "try"]
  });
```

## Exercise 4

Create a async function `getWordPlays()` that returns a promise that resolves with one of the random phrases:

```javascript
const arr = [
  "Katten musen tio tusen",
  "Spaghetti makaroner, tio miljoner",
  "Blomma blad, en miljard",
  "Kalas kanon, en miljon",
  "Ettning Tvåning Trening Fyrning Femning Sexning Sjuning Åttning Nining Tidning",
];
```

Example use:

```javascript
getWordPlays().then((rhyme) => {
  console.log(rhyme); //-> Kalas kanon, en miljon
});
```

### Bonus:

Use a anonymous self calling method and await the result instead of using .then()

## Exercise 5

Create a function `calculate(num1, num2, operation, callback)` that takes two numbers (`num1` and `num2`), an arithmetic operation (`operation`), and a function `callback`. The function should perform the specified operation on the two numbers and call the callback with the result.

The possible arithmetic operations are:

- "add" (addition)
- "subtract" (subtraction)
- "multiply" (multiplication)
- "divide" (division)

If an invalid operation is provided, the function should call the callback with an error message string.

Example use:

```js
calculate(4, 2, "add", function (result) {
  console.log(result); //-> 6
});

calculate(4, 2, "subtract", function (result) {
  console.log(result); //-> 2
});

calculate(4, 2, "multiply", function (result) {
  console.log(result); //-> 8
});

calculate(4, 2, "divide", function (result) {
  console.log(result); //-> 2
});

calculate(4, 2, "invalid", function (result) {
  console.log(result); //-> "Invalid operation"
});
```

## Exercise 6

Implement a function `areObjectsEqual` that takes two objects as arguments and returns a promise that resolves with a boolean indicating whether or not they are equal. Two objects are considered equal if they have the same properties with the same values.

Example use cases:

```js
const obj1 = { name: "John", age: 25 };
const obj2 = { age: 25, name: "John" };
const obj3 = { name: "Jane", age: 30 };

areObjectsEqual(obj1, obj2).then((result) => {
  console.log(result); // true
});

areObjectsEqual(obj1, obj3).then((result) => {
  console.log(result); // false
});
```

Requirements:

- The areObjectsEqual function should take in two objects as arguments.
- The areObjectsEqual function should return a promise that resolves with a boolean indicating whether or not the two objects are equal.
- The function should ignore the ordering of properties within the objects.
- The promise should reject if either argument is not an object.

## Exercise 7 (extra hard)

Create a function `filterArray(array, filterFunction, callback)` that takes an array, a function (`filterFunction`) to use as a filter, and a callback function. The function should use the `filterFunction` to filter the array and return a new array with only the elements that pass the filter. The function should then call the `callback` function with the new array as an argument.

Example use:

```js
const originalArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

filterArray(
  originalArray,
  function (num) {
    return num % 2 === 0;
  },
  function (filteredArray) {
    console.log(filteredArray); //-> [2, 4, 6, 8, 10]
  }
);

filterArray(
  originalArray,
  function (num) {
    return num > 5;
  },
  function (filteredArray) {
    console.log(filteredArray); //-> [6, 7, 8, 9, 10]
  }
);
```

# Layout and Styling

Using HTML and SCSS, recreate the following cards. Background images can be found in [backgrounds](./backgrounds)

You should use variables for things that make sense, like colors and font.

Card 1:

Use Arial, Helvetica as font.

![card 1](./cards/card1.png)

Card 2:

Use Helvetica, Arial, sans-serif as font.

![card 2](./cards/card2.png)

Card 3:

Use the Roboto font https://fonts.google.com/specimen/Roboto

```HTML
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
```

![card 3](./cards/card3.png)
