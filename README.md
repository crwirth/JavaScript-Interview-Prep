# JavaScript-Interview-Prep

## Common Interview Questions
Question: What is Big O Notation?

Answer: Expression of how long an algorithm takes to run depending on how long is the input, usually talking about the worst case scenario.

Question: What is DNS?
Answer: DNS translates domain names to IP addresses so browsers can load Internet resources.

Question: What is reverse DNS lookup?
Answer: Determining the domain name associated with an IP address – the reverse of the usual "forward" DNS lookup of an IP address from a domain name.

Question: What is HTTP?
Answer: Hypertext Transfer Protocol (standard web) (How browsers and servers communicate)

Question: What happens when you type google into your browser and press go?
Answer:

Question: What is in a request?
Answer: 
- Method (ex: GET)
- HTTP protocol version (almost always 1.1)
- Resource URL you want
- Headers
  - Hostname you’re asking about
  - Date your browser thinks it is
  - Language your browser wants information in
  - Any cookies that server has sent

Question: What is in a response?
Answer:
- HTTP protocol version (almost always 1.1)
- Response Status Code (200, 404, etc)
- Headers
  - Content Type (typically text/html for web pages)
  - Date/time the server thinks it is
  - Any cookies server wants to set
  - Any caching information

## Array Methods:

1. find()
- Iterates through an array and runs a callback on each value
- If the call back returns true at any point will return the value in the array that we are iterating ober
- Otherwise returns undefined
```javascript
let arr = [1,2,3];

arr.find(function(value, index, array){
  return value === 2;
});

// 2
```
2. findIndex()
- If the callback returns true for any single value, return the index at which that value is found
- Otherwise, return -1

```javascript
let arr = [1,2,3];

arr.findIndex(function(value, index, array){
  return value < 2;
}); // 0
```
3. forEach()
- Runs a callback function for each value in the array, and then returns undefined

```javascript
let arr = [1,2,3];

arr.forEach(function(value, index, array){
  console.log(value);
});

// 1
// 2
// 3
// undefined
```
4. map()
- Creates a new array
- Runs a callback function for each value in the array
- Adds the result of that callback function to the new array
- Returns a new array of the same length
```javascript
let numbers = [1,2,3];

numbers.map(function(value, index, array){
  return value * 10;
});
```
5. filter()
- Creates a new array, loops through an array
- Runs a callback function on each value in the array
- If the callback function returns true, that value is pushed to the new array
- If the callback function returns false, that value will not be included in the new array
- the result of the callback will always be evaluated into a boolean
```javascript
let letters = ["a", "b", "c", "b", "c"];

letters.filter(function(value, index, array){
  return value === "b";
});
```
6. some()
- Iterates through an array
- Runs a callback on each value in the array
- If the callback returns true for at least one single value, return true
- Otherwise, return false
- the result of the callback will always be a boolean
```javascript
let numbers = [1,2,3];

numbers.some(function(value, index, array){
  return value < 3;
});

// true
```
7. every()
- Iterates through an array
- Runs a callback on each value in the array
- If the callback returns false for any single value, return false, otherwise, return true
-The result of the callback will always be a boolean
```javascript
let numbers = [1,2,3];

numbers.every(function(value, index, array){
  return value > 0;
});

// true
```
8. reduce()
- Accepts a callback function and an optional second parameter
- Iterates through an array
- Runs a callback on each value in the array
- The first parameter to the callback is either the first value in the array or the optional second parameter
- The first parameter to the callback is often called “accumulator”
- The returned value from the callback becomes the new value of accumulator
```javascript
let evens = [2,4,6,8,10];

evens.reduce(function(accumulator, nextValue){
  return accumulator + nextValue;
});

/*
  2
  6
  12
  20
  30
*/
```

## Rest & Spread
- They are both the “same” operator and use three dots …
- When the three dots are part of a function definition, we call the operator the “rest” operator
- The rest operator is the last parameter defined in a function and will evaluate to an array of all additional arguments passed in

```javascript
function displayArguments(...restOfArgs){
  console.log("The first argument is", restOfArgs[0])
  return `You passed in ${restOfArgs.length} arguments!`
}

displayArguments(1,2,3); // "You passed in 3 arguments!"
```

When calling a function, you can “spread out” array elements:

```javascript
  console.log(one);
  console.log(two);
  console.log(three);
  console.log(four);
}

const names = ['Mary', 'Colt', 'Angela', 'Abe'];

takesFour(...names);
// Mary
// Colt
// Angela
// Abe
```
- Using spread will only make a “shallow” copy.
- If there are nested objects, they will still contain the same reference
- For a deep copy, use libraries like lodash

## Destructuring 

Example #1

```javascript
 let userData = {
   username: 'smith',
   id: 12345,
   password: 'fiddlesticks',
   firstName: 'Angela',
   lastName: 'Smith',
   age: 'guess',
   isLegit: undefined
 };

/*
  declare variables: username, firstName, lastName, id
   values taken from the keys of the same name in userData
 */
 let { username, firstName, lastName, id } = userData;

 console.log(username);  // smith
 console.log(id);        // 12345
```

Example #2 with spread syntax

```javascript
const userData = {
  username: 'smith',
  id: 12345,
  password: 'fiddlesticks',
  firstName: 'Angela',
  lastName: 'Smith',
  age: 'guess',
  isLegit: undefined
};

// extract the password key; collect the rest in 'user'
const { password, ...user } = userData;

console.log(user);
/*
{
  username: 'smith',
  id: 12345,
  firstName: 'Angela',
  lastName: 'Smith',
  age: 'guess',
  isLegit: undefined
}
*/
```

Example #3 Destructuring Nested Objects

```javascript
const instructor = {
  id: 44,
  name: 'Colt',
  isHilarious: true,
  funFacts: {
    favoriteFood: 'Burrito',
    favoriteDrink: 'Old Fashioned',
  }
};
const {funFacts: {favoriteFood, favoriteDrink}} = instructor;
console.log(favoriteFood); // 'Burrito'
```
## Maps
- Similar to objects, except the keys can be ANY data type!
- Created using the new keyword
```javascript
let m = new Map([
  [1, "Ayisha"],
  [2, "Shani"],
  [3, "Michelle"],
])

for(let [key,value] of m.entries()){
    console.log(key, value);
}

// 1 "Ayisha"
// 2 "Shani"
// 3 "Michelle"
```
## Sets
- All values in a set are unique
- Any type of value can exist in a set
```javascript
const hashTags = new Set(["#selfie", "#nofilter"])
```
- adding to sets
```javascript
const annoyingHashTags = new Set();
annoyingHashTags.add("#YOLO");
annoyingHashTags.add("#Blessed")
annoyingHashTags.add("#YOLO"); // will not be added!
```
- Iterating over a set
```javascript
const annoyingHashTags = new Set();
annoyingHashTags.add("#Selfie");
annoyingHashTags.add("#Blessed");
annoyingHashTags.add("#NoFilter");

for(let val of annoyingHashTags) {
   console.log("Please don't use", val);
}
```
