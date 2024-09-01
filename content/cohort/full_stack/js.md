---
id: js
aliases: []
tags: []
---

# Interpreted vs compiled languages

- Compiler
---
1. Write the code
2. Compile the code
3. Run the code
4. If error wont run at all

- Interpreter
---
1. Write the code
2. Run the code line by line
3. If error will run partially till the error

# JS

- JS is single threaded not multithreaded
- JS is dynamic language not a single threaded

## Simple primitive

### Variables:- (let, var, const)

```js
#let
let a = 1;
a=2;
console.log(a);
#const
let a = 1;
a=2;
console.log(a);#error
```
### Data types:- (strings, number, booleans)

```js
let firstName = "Victon";
let age = 12;
let isMarried = False;
console.log("this person is " + firstName +"their age is "+ age +"status of marrige is "+ isMarried);
```
1. Strings
----
```js
// Length
function getLength(str) {
  console.log("Original String:", str);
  console.log("Length:", str.length);
}
getLength("Hello World");

// indexOf
function findIndexOf(str, target) {
  console.log("Original String:", str);
  console.log("Index:", str.indexOf(target));
}
findIndexOf("Hello World", "World");

// lastIndexOf
function findLastIndexOf(str, target) {
  console.log("Original String:", str);
  console.log("Index:", str.lastIndexOf(target));
}
findLastIndexOf("Hello World World", "World");

// slice
function getSlice(str, start, end) {
  console.log("Original String:", str);
  console.log("After slice:", str.slice(start, end));
}
getSlice("Hello World", 0, 5);

// substring
function getSubstring(str, start, end) {
  console.log("Original String:", str);
  console.log("After substring:", str.substring(start, end));
}
getSubstring("Hello World", 0, 5);

// replace
function replaceString(str, target, replacement) {
  console.log("Original String:", str);
  console.log("After replace:", str.replace(target, replacement));
}
replaceString("Hello World", "World", "JavaScript");

// split
function splitString(str, separator) {
  console.log("Original String:", str);
  console.log("After split:", str.split(separator));
}
splitString("Hello World", " ");

// trim
function trimString(str) {
  console.log("Original String:", str);
  console.log("After trim:", str.trim());
}
trimString(" Hello World ");

// toUpperCase
function toUpper(str) {
  console.log("Original String:", str);
  console.log("After toUpperCase:", str.toUpperCase());
}
toUpper("Hello World");

// toLowerCase
function toLower(str) {
  console.log("Original String:", str);
  console.log("After toLowerCase:", str.toLowerCase());
}
toLower("Hello World");
```

2. Numbers
---
```js
function explainParseInt(value) {
  console.log("Original Value:", value);
  let result = parseInt(value);
  console.log("After parseInt:", result);
}

// Example Usage for parseInt
explainParseInt("42");
explainParseInt("42px");
explainParseInt("3.14");

function explainParseFloat(value) {
  console.log("Original Value:", value);
  let result = parseFloat(value);
  console.log("After parseFloat:", result);
}

// Example Usage for parseFloat
explainParseFloat("3.14");
explainParseFloat("42");
explainParseFloat("42px");
```
### if/else
----
```js
let gender = "Male";
if(gender=="Male"){
    console.log("welcome sir!");
}
if(gender=="Famale"){
    console.log("welcome ma'am!");
}
else{
    console.log("welcome!");
}
```
### Loops :- for loops
-----
```js
let answer = 0;
for (let i = 0; i<=1000; i=i+1){
    answer= answer + i;
}
console.log(answer);
```

## Complex primitive

1. Arrays

```js
const ages=[21,22,23,46,78,909];
const numberOfPerson= ages.length;
for(let i=0; i<numberOfPerson;i++){
    if(ages[i]%2==0){
        console.log(ages[i]);
    }
}
// push()
function pushExample(arr, element) {
  console.log("Original Array:", arr);

  arr.push(element);
  console.log("After push:", arr);
}
pushExample([1, 2, 3], 4);

// pop()
function popExample(arr) {
  console.log("Original Array:", arr);

  arr.pop();
  console.log("After pop:", arr);
}
popExample([1, 2, 3]);

// shift()
function shiftExample(arr) {
  console.log("Original Array:", arr);

  arr.shift();
  console.log("After shift:", arr);
}
shiftExample([1, 2, 3]);

// unshift()
function unshiftExample(arr, element) {
  console.log("Original Array:", arr);

  arr.unshift(element);
  console.log("After unshift:", arr);
}
unshiftExample([1, 2, 3], 0);

// concat()
function concatExample(arr1, arr2) {
  console.log("Original Arrays:", arr1, arr2);

  let arr3 = arr1.concat(arr2);
  console.log("After concat:", arr3);
}
concatExample([1, 2, 3], [4, 5, 6]);

// forEach()
function forEachExample(arr) {
  console.log("Original Array:", arr);

  arr.forEach(function(item, index) {
    console.log(item, index);
  });
}
forEachExample([1, 2, 3]);

// map()
function mapExample(arr) {
  console.log("Original Array:", arr);

  let newArr = arr.map(function(item) {
    return item * 2;
  });
  console.log("After map:", newArr);
}
mapExample([1, 2, 3]);

// filter()
function filterExample(arr) {
  console.log("Original Array:", arr);

  let newArr = arr.filter(function(item) {
    return item > 3;
  });
  console.log("After filter:", newArr);
}
filterExample([1, 2, 3, 4, 5]);

// find()
function findExample(arr) {
  console.log("Original Array:", arr);

  let found = arr.find(function(item) {
    return item > 3;
  });
  console.log("After find:", found);
}
findExample([1, 2, 3, 4, 5]);

// sort()
function sortExample(arr) {
  console.log("Original Array:", arr);

  arr.sort(function(a, b) {
    return a - b;
  });
  console.log("After sort:", arr);
}
sortExample([5, 2, 3, 4, 1]);
```

2. Objects
----
```js
const allUser=[{
    firstName:"Victon",
    gender:"Male"
},{
    firstName:"Meena",
    gender:"Female"
},{
    firstName:"Heelan",
    gender:"Female"
}]
for(let i=0;i<allUser;i++){
    if(allUser[i]["gender"]=="Male"){
        console.log(allUser[i]["firstName"])
    }
}

// Object Methods Explanation
function objectMethods(obj) {
  console.log("Original Object:", obj);

  let keys = Object.keys(obj);
  console.log("After Object.keys():", keys);

  let values = Object.values(obj);
  console.log("After Object.values():", values);

  let entries = Object.entries(obj);
  console.log("After Object.entries():", entries);

  let hasProp = obj.hasOwnProperty("property");
  console.log("After hasOwnProperty():", hasProp);

  let newObj = Object.assign({}, obj, { newProperty: "newValue" });
  console.log("After Object.assign():", newObj);


}

// Example Usage for Object Methods
const sampleObject = {
  key1: "value1",
  key2: "value2",
  key3: "value3",
};

objectMethods(sampleObject);
```
3. Function
----
```js
function sum(a,b){
    const sumValue= a+b;
    return sumValue;
}
const Value1=sum(1,2);
console.log(Value1);
const Value2=sum(1,2);
console.log(Value2);
// Anonymous function
function sumOfSomething(a,b,fn){
    const val1=fn(a);
    const val2=fn(b);
    return val1+val2;
}
console.log(sumOfSomething(a,b,function(a){
    return a*a;
}));
// arrows function
app.get("/",(req,res)=> {})
```
4. Callbacks functions
---
```js
function calculateArithmetic(a,b,arithmeticFinalFunction){
    const ans=arithmeticFinalFunction(a,b);
    return ans;
}

function sum(a,b){
    return a+b;
}
function mius(a,b){
    return a-b;
}
function multiply(a,b){
    return a*b;
}
function divide(a,b){
    return a/b;
}
 const value=calculateArithmetic(2,3,sum);
console.log(value)
```

5. Time
---
```js
function greet(){
    console.log("Hi!")
}
setTimeout(greet,3*1000);
sleep(3*1000);
setInterval(greet,3*1000);
```

6. Class
---
```js

class Animal {
  constructor(name, legCount) {
    this.name = name
    this.legCount = legCount
  }
  describe() {
    return `${this.name} has ${this.legCount} legs`
  }
}
```

7. Date
----
```js
function dateMethods() {
  const currentDate = new Date();
  console.log("Current Date:", currentDate);

  // Getting various components of the date
  console.log("Date:", currentDate.getDate());
  console.log("Month:", currentDate.getMonth() + 1); // Months are zero-indexed, so adding 1
  console.log("Year:", currentDate.getFullYear());
  console.log("Hours:", currentDate.getHours());
  console.log("Minutes:", currentDate.getMinutes());
  console.log("Seconds:", currentDate.getSeconds());

  // Setting components of the date
  currentDate.setFullYear(2022);
  console.log("After setFullYear:", currentDate);

  currentDate.setMonth(5); // Setting month to June (zero-indexed)
  console.log("After setMonth:", currentDate);

  // Getting and setting time in milliseconds since 1970
  console.log("Time in milliseconds since 1970:", currentDate.getTime());

  const newDate = new Date(2023, 8, 15); // Creating a new date
  console.log("New Date:", newDate);
}

// Example Usage for Date Methods
dateMethods();
```

9. JSON
----
```js
function jsonMethods(jsonString) {
  console.log("Original JSON String:", jsonString);

  // Parsing JSON string to JavaScript object
  let parsedObject = JSON.parse(jsonString);
  console.log("After JSON.parse():", parsedObject);

  // Stringifying JavaScript object to JSON string
  let jsonStringified = JSON.stringify(parsedObject);
  console.log("After JSON.stringify():", jsonStringified);
}

// Example Usage for JSON Methods
const sampleJSONString =
  '{"key": "value", "number": 42, "nested": {"nestedKey": "nestedValue"}}';

jsonMethods(sampleJSONString);
```
10. Math
---
```js
function mathMethods(value) {
  console.log("Original Value:", value);

  let rounded = Math.round(value);
  console.log("After round():", rounded);

  let ceiling = Math.ceil(value);
  console.log("After ceil():", ceiling);

  let flooring = Math.floor(value);
  console.log("After floor():", flooring);

  let randomValue = Math.random();
  console.log("After random():", randomValue);

  let maxValue = Math.max(5, 10, 15);
  console.log("After max():", maxValue);

  let minValue = Math.min(5, 10, 15);
  console.log("After min():", minValue);

  let powerOfTwo = Math.pow(value, 2);
  console.log("After pow():", powerOfTwo);

  let squareRoot = Math.sqrt(value);
  console.log("After sqrt():", squareRoot);
}

// Example Usage for Math Methods
mathMethods(4.56);
mathMethods(9);
mathMethods(25);
```

11. map
---
```js
const input = [1,2,3,4]
const ans = input.map(function(i){
    return 1*2;
});
```

12. filter
```js
const input = [1,2,4,4,5,6]
const ans = arr.filter((n) => {
    if (n%2==0){
        return true;
    } else {
        return false;
    }
});
console.log(ans);
```

# Synchronous vs Asnchronous
----
## Async function

1. setTimeout
2. fs.readFile
3. Fetch
----
```js
const fs = require("fs");
// filesystem module
fs.readFile("a.txt","utf-8",function(err,data){
    console.log("hi! there");
})
```
- call stack
- callback queue

## promises
- pending promise
---
```js
var d = new Promise(function(onDone){});
console.log(d)
```

- resolved promise
----
```js
const TS = require("TS")
function readsFile(){
    return new Promise(function (resolve){
        console.log("inside the promise");
        fs.readFile("a.txt","utf-8",function(err,data){
            console.log("before resolve");
            resolve(data);
        });
    })
}
function onDone(data){
    console.log(data);
}
var a = readsFile();
a.then(onDone);
```
## async await

```js
function readsFile(){
    let p = new Promise(function(resolve){
        resolve("hi!");
    });
    return p;
}

async function main(){
    cosnt value = await readsFile();
    console.log(value);
}
main();
```
