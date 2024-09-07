---
id: typescript
al1iases: []
tags: []
---
```bash
# install
npm install -g typescript
# initializing project
mkdir node-app
cd node-app
npm init -y
npx tsc --init
# compiling
tsc -b
# running server
node dist/fileName.js
```
---
# tsconfig
1. target => set version of compiler
2. rootDir => where compiler looks for file to compile
3. outDir => where compiler puts compiled js file
4. noImplicitAny => any types allowed even if it's not mentioned
5. removeComments => removes comments from compiled file
---
# function

```typescript
function greet(firstName: string){
  console.log("welcome"+firstName)
}
greet("ndskj");

function sum(a:number, b:number):number{
  return a+b;
}
const value = sum(1+2);
console.log(value);

function runAfter(fn: () => void) {
  setTimeout(fn, 1000);
}
runAfter(function () {
  console.log("hi there");
});
```
---
# interface
```typescript
interface User {
  firstName: string;
  lastName: string;
  age: number;
  email?: string;
}
function isLeagal(user: User): boolean {
  return user.age > 18 ? true : false;
}
function greet(user: User) {
  console.log("HI! " + user.firstName);
}

const result = isLeagal({
  firstName: "vicky",
  lastName: "chaudhary",
  age: 23,
});
console.log(result);
greet({
  firstName: "vicky",
  lastName: "chaudhary",
  age: 23,
});
```
---
```typescript
interface Person {
  name: string;
  age: number;
  greet(phrase: string): void;
}
class Employees implements Person {
  name: string;
  age: number;
  constructor(n: string, a: number) {
    this.name = n;
    this.age = a;
  }
  greet(phrase: string) {
    console.log(`${phrase} ${this.name}`);
  }
}
const e = new Employees("victoln", 23);
console.log(e.name);
```
---
# types
```typescript
type GreetArgs = number | string;
function greet(id: GreetArgs) {}
greet(1);
greet("3sf");
```
---
```typescript
type Employees = {
  name: string;
  startDate: Date;
};
interface Manager {
  name: String;
  department: String;
}
type techie = Employees & Manager;
const t: techie = {
  name: "vicky",
  startDate: new Date(),
  department: "fksihf",
};
```
---
# Array
```typescript
type NumberArr = number[];
function maxValue(number:NumberArr) { }
maxValue([1,2,3]);
```
---
# extends
```typescript
interface User{
  age:number;
}
interface Oragnizaton{
  oraganization:string;
}
interface Manager extends User,Oraganization{
  name:string;
  address:string;
}
```
---
# enums
```js
enum Direction {
  UP = "up",
  DOWN = "down",
  LEFT = "left",
  RIGHT = "right",
}
function doSomething(keypressed: Direction) {
  if (keypressed == Direction.UP) {
    console.log("UP");
  } else {
    console.log("sorry you pressed something else");
  }
}
doSomething(Direction.UP);
console.log(Direction.UP);
```
---
```jsx
import express from "express";
const app = express();
enum ResponseStatus {
  Success = 200,
  NotFound = 411,
  Error = 500,
}
app.get("/", (res, req) => {
  if (!req.query.userId) {
    res.status(ResponseStatus.NotFound).json({});
  } else {
    res.json();
  }
});
app.get("/new", (res, req) => {
  if (!req.query.userId) {
    res.status(ResponseStatus.Error).json({});
  } else {
    res.json();
  }
});
```
---
# generics
```typescript
function getFirstElement<T>(arr: T[]) {
  return arr[0];
}
interface User {
  name: String;
}
const el = getFirstElement<User>([{ name: "victon" }]);
console.log(el.name);
const el1 = getFirstElement<string>(["hello", "victon"]);
console.log(el1.toUpperCase())
const el2 = getFirstElement<number>([1, 2, 3]);
const el3 = getFirstElement(["victon", 1, 2, "newbie"]);
```
---
# imports and exports
1. Constant exports
```typescript
//math.ts
export function add(x:number,y:number):number{
  return x+y;
}
export function substract(x:number,y:number):number{
  return x+y;
}
//main.ts
import {add} from "./math"
add(1,2)
```
---
2. default exports
```typescript
//calculator.ts
export default class Calculator{
  add(x:number,y:number):number{
    return x=y
  }
}
//main.ts
import Calculator from ".calculator/"
const cal = new Calculator();
console.log(calc.add(3,5));
```
---
# pick
```typescript
interface User {
  id: number;
  name: string;
  email: string;
  createdAt: Date;
}

// For a profile display, only pick `name` and `email`
type UserProfile = Pick<User, 'name' | 'email'>;

const displayUserProfile = (user: UserProfile) => {
  console.log(`Name: ${user.name}, Email: ${user.email}`);
};
```
---
# exclude
```typescript
type Event = 'click' | 'scroll' | 'mousemove';
type ExcludeEvent = Exclude<Event, 'scroll'>; // 'click' | 'mousemove'

const handleEvent = (event: ExcludeEvent) => {
  console.log(`Handling event: ${event}`);
};

handleEvent('click'); // OK
```
---
# partial
```typescript
interface User {
    id: string;
    name: string;
    age: string;
    email: string;
    password: string;
};

type UpdateProps = Pick<User, 'name' | 'age' | 'email'>

type UpdatePropsOptional = Partial<UpdateProps>

function updateUser(updatedProps: UpdatePropsOptional) {
    // hit the database tp update the user
}
updateUser({})
```
---
# readonly
```typescript
type User = {
  readonly name: string,
  readonly age: number,
}
const user: User  = {
  name:'John',
  age: 12,
}
user.age = 25;
```
---
```typescript
interface Config {
  endpoint: string;
  apiKey: string;
}

const config: Readonly<Config> = {
  endpoint: 'https://api.example.com',
  apiKey: 'abcdef123456',
};

// config.apiKey = 'newkey'; // Error: Cannot assign to 'apiKey' because it is a read-only property.
```
---
# cleaner objects
1. records
```typescript
interface User {
  id: string;
  name: string;
}
//objects with key value pairs
//type Users = Record<key, value>;
type Users = Record<string, User>;

const users: Users = {
  'abc123': { id: 'abc123', name: 'John Doe' },
  'xyz789': { id: 'xyz789', name: 'Jane Doe' },
};

console.log(users['abc123']); // Output: { id: 'abc123', name: 'John Doe' }
```
---
2. maps
```typescript
interface User {
  id: string;
  name: string;
}

// Initialize an empty Map
const usersMap = new Map<string, User>();

// Add users to the map using .set
usersMap.set('abc123', { id: 'abc123', name: 'John Doe' });
usersMap.set('xyz789', { id: 'xyz789', name: 'Jane Doe' });

// Accessing a value using .get
console.log(usersMap.get('abc123')); // Output: { id: 'abc123', name: 'John Doe' }
```
# type interface in zod
```typescript
import { z } from 'zod';
import express from "express";

const app = express();

// Define the schema for profile update
const userProfileSchema = z.object({
  name: z.string().min(1, { message: "Name cannot be empty" }),
  email: z.string().email({ message: "Invalid email format" }),
  age: z.number().min(18, { message: "You must be at least 18 years old" }).optional(),
});

type FinalUsersSchema = z.infer<typeof userProfileSchema>;

app.put("/user", (req, res) => {
  const { success } = userProfileSchema.safeParse(req.body);
  const updateBody:FinalUsersSchema = req.body; // how to assign a type to updateBody?

  if (!success) {
    res.status(411).json({});
    return
  }
  // update database here
  res.json({
    message: "User updated"
  })
});

app.listen(3000);
```
