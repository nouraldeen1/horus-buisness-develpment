# JavaScript Coding Standards
## Comments
Comments are critical to writing good code examples. They clarify the intent of the code and help developers understand it. Pay special attention to them.

- If the purpose or logic of the code isn't obvious, add a comment with your intention, as shown below:
```js
let total = 0;

// Calculate the sum of the four first elements of arr
for (let i = 0; i < 4; i++) {
  total += arr[i];
}
```
- On the other hand, restating the code in prose is not a good use of comments:
```JS
let total = 0;

// For loop from 1 to 4
for (let i = 0; i < 4; i++) {
  // Add value to the total
  total += arr[i];
}
```
- Comments are also not necessary when functions have explicit names that describe what they're doing. Write:
```JS
closeConnection();
```
Don't write:
```JS
closeConnection(); // Closing the connection
```
## Naming
### 1. Variables
- Use camelCase for variable names.
- Start variable names with a lowercase letter.
- Avoid using single-letter variable names, except for loop counters or temporary variables.
- Use descriptive and meaningful names that accurately represent the purpose of the variable.

Example:

```JS
// good
var dogName = 'Droopy';
var dogBreed = 'Beagle';
var dogAge = 3;
```
### 2. Boolean
- Boolean variables should use “is” or “has” as prefixes, making it clear that they represent a true or false condition.

Example:

```JS
// good
var hasOwner = true;
var isTrained = false;
var hasVaccinations = true;
```


### 3. Constants
- uppercase
- If the name contains more than one word, use UPPER_SNAKE_CASE (uppercase letters with underscores between words).

```JS
// good
const DAYS_IN_WEEK = 7;
const MONTHS_IN_YEAR = 12;
const MAX_DOG_WEIGHT = 150;
```
### 4. Functions
-  camel case
- descriptive nouns and verbs as prefixes


Example:

```JS
// good
function getName(dogName, ownerName) {
  return `${dogName} ${ownerName}`;
}

// good
function calculateDogAgeInHumanYears(dogAge) {
  return dogAge * 7;
}
```
### 5. Class
- Pascal case, which means that each word in the name starts with an uppercase letter.
Example:

```JS
class DogCartoon {
  constructor(dogName, ownerName) {
    this.dogName = dogName;
    this.ownerName = ownerName;
  }
}

class DogBreed {
  constructor(breedName, breedSize) {
    this.breedName = breedName;
    this.breedSize = breedSize;
  }
}
```
## Common Conventions
### Styling
Opinions on correct indentation, whitespace, and line lengths have always been controversial. Discussions on these topics are a distraction from creating and maintaining content.

On MDN Web Docs, we use Prettier as a code formatter to keep the code style consistent (and to avoid off-topic discussions). You can consult our configuration file to learn about the current rules, and read the Prettier documentation.

Prettier formats all the code and keeps the style consistent. Nevertheless, there are a few additional rules that you need to follow.

### Spaces Around Operators
Always put spaces around operators ( = + - * / ), and after commas:

Examples:
```js
let x = y + z;
const myArray = ["Volvo", "Saab", "Fiat"];
```
### Code Indentation
Always use 2 spaces for indentation of code blocks:

Functions:
```js
function toCelsius(fahrenheit) {
  return (5 / 9) * (fahrenheit - 32);
}
```
### Object Rules
General rules for object definitions:

- Place the opening bracket on the same line as the object name.
- Use colon plus one space between each property and its value.
- Use quotes around string values, not around numeric values.
- Do not add a comma after the last property-value pair.
- Place the closing bracket on a new line, without leading spaces.
- Always end an object definition with a semicolon.
Example
```js
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
```
Short objects can be written compressed, on one line, using spaces only between properties, like this:

```js
const person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```

# Resources
- https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide/JavaScript#comments
- https://www.w3schools.com/js/js_conventions.asp
- https://standardjs.com/rules.html
