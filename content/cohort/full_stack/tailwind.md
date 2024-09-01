---
id: Tailwind
aliases: []
tags: []
---

# flexbox
```jsx
import "./App.css";

function App() {
  return (
    <>
      <div className="flex justify-between">
        <div className="bg-red-500">welsoxn</div>
        <div className="bg-green-500">welsoxn</div>
        <div className="bg-yellow-500">welsoxn</div>
        <div className="bg-gray-500">welsoxn</div>
      </div>
    </>
  );
}
export default App;
```
---
# grid
- equal width
```jsx
import "./App.css";

function App() {
  return (
    <>
      <div className="grid grid-cols-3">
        <div className="bg-red-500">welsoxn</div>
        <div className="bg-green-500">welsoxn</div>
        <div className="bg-yellow-500">welsoxn</div>
        <div className="bg-gray-500">welsoxn</div>
      </div>
    </>
  );
}
export default App;
```
---
- unequal width

```jsx
import "./App.css";

function App() {
  return (
    <>
      <div className="flex justify-between">
        <div className="bg-red-500">welsoxn</div>
        <div className="bg-green-500">welsoxn</div>
        <div className="bg-yellow-500">welsoxn</div>
        <div className="bg-gray-500">welsoxn</div>
      </div>
    </>
  );
}
export default App;
```
# responsiveness
```jsx
import "./App.css";

function App() {
  return (
    <>
      <div className="bg-red-500 md:bg-green-200">hi there</div>
    </>
  );
}
export default App;
```
---
```jsx
import "./App.css";

function App() {
  return (
    <>
      <div className="grid grid-cols-1 md:grid-cols-3">
        <div className="bg-red-500">welsoxn</div>
        <div className="bg-green-500">welsoxn</div>
        <div className="bg-yellow-500">welsoxn</div>
      </div>
    </>
  );
}
export default App;
```
# properties
```jsx
import "./App.css";

function App() {
  return (
    <>
      <div className="grid grid-cols-1 md:grid-cols-3">
        <div className="bg-red-500 text-blue-500">welsoxn</div>
        <div className="bg-green-500 text-2xl">welsoxn</div>
        <div className="bg-yellow-500 rounded-s-xl">welsoxn</div>
      </div>
    </>
  );
}
export default App;

```
# example
app.jsx
```jsx
import "./App.css";
import { RevenueCard } from "./components/RevenueCard";

function App() {
  return (
    <>
      <div className="grid grid-cols-3">
        <RevenueCard
          title={"amount pending"}
          orderCount={13}
          amount={92321.09}
        />
      </div>
    </>
  );
}
export default App;
```
---
RevenueCard.jsx
```js
export const RevenueCard = ({ title, orderCount, amount }) => {
  return (
    <div className="bg-white rounded shadow-md p-4 hover:bg-blue-300">
      <div className="text-gray-700 flex justify-center flex-col ">
        <div className="flex">
          <div>{title}</div>
          <div className="ml-1 flex justify-center flex-col">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              strokeWidth="1.5"
              stroke="currentColor"
              className="w-4 h-4 "
            >
              <path
                strokeLinecap="round"
                strokeLinejoin="round"
                d="M12 9v3.75m9-.75a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9 3.75h.008v.008H12v-.008Z"
              />
            </svg>
          </div>
        </div>
      </div>
      <div className="flex justify-between pt-2">
        <div className="font-bold text-2xl">${amount}</div>
        {orderCount ? (
          <div className="flex cursor-pointer underline font-medium flex flex-col justify-center">
            <div className="flex">
              <div className="text-blue-400">{orderCount}order(s)</div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                strokeWidth="1.5"
                stroke="currentColor"
                className="size-6 fill-blue-400"
              >
                <path
                  strokeLinecap="round"
                  strokeLinejoin="round"
                  d="m8.25 4.5 7.5 7.5-7.5 7.5"
                />
              </svg>
            </div>
          </div>
        ) : null}
      </div>
    </div>
  );
};
```
