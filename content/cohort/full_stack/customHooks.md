---
id: customHooks
al1iases: []
tags: []
---
# lifecycle hhoking
hooking into lifecycle for custom component
```jsx
import "./App.css";
import React, { useEffect, useState } from "react";

function App() {
  const [render, setRender] = useState(true);
  useEffect(() => {
    setTimeout(() => {
      setRender(false);
    }, 10000);
  }, []);
  return (
    <>{render ? <Mycomponent /> : <div>Component has been unmounted</div>}</>
  );
}
function Mycomponent() {
  useEffect(() => {
    console.error("compount mounted");
    return () => {
      console.log("compount unmounted");
    };
  }, []);
  return <div>Inside the dev</div>;
}
export default App;

```
# todos
```jsx
import "./App.css";
import { useEffect, useState } from "react";
import axios from "axios";
function useTodos(n) {
  const [todos, setTodos] = useState([]);
  const [loading, setLoading] = useState(true);
  useEffect(() => {
    const value = setInterval(() => {
      axios.get("https://sum-server.100xdevs.com/todos").then((res) => {
        setTodos(res.data.todos);
        setLoading(false);
      });
    }, [n * 1000]);
    axios.get("https://sum-server.100xdevs.com/todos").then((res) => {
      setTodos(res.data.todos);
      setLoading(false);
    });
    return () => {
      clearInterval(value);
    };
  }, [n]);

  return { todos, loading };
}
function App() {
  const { todos, loading } = useTodos(5);
  if (loading) {
    return <div>Loading</div>;
  }
  return (
    <>
      {todos.map((todo) => (
        <Track todo={todo} />
      ))}
    </>
  );
}
function Track({ todo }) {
  return (
    <div>
      {todo.title}
      <br />
      {todo.description}
    </div>
  );
}
export default App;
```
# swr
---
```jsx
import useSMR from "smr";
const fetcher = async function (url){
  const data  = await fetch(url);
  const json  = await data.json();
  return json;
};
function profile(){
  const {data,error,isloading} = useSMR('url',fetcher)
  if(error) return <div>failed to do</div>
  if(isLoading) return <div>loading...</div>
  return <div>your data size is {data.todos.length}</div>
}
```
# browser functionality hooks
- useIsOnline
```jsx
import "./App.css";
import { useEffect, useState } from "react";
function useIsOnline() {
  const [isOnline, setIsOnline] = useState(window.navigator.onLine);
  useEffect(() => {
    window.addEventListener("online", () => {
      setIsOnline(true);
    });
    window.addEventListener("offline", () => {
      setIsOnline(false);
    });
    return (()=>{
      window.removeEventListener("offline");
      window.removeEventListener("online");
    })
  }, []);
  return isOnline;
}
function App() {
  const isOnline = useIsOnline();
  console.log(isOnline);
  return <>{isOnline ? "yay! connected" : "nah dude!"}</>;
}
export default App;
```
---
- useMousePointer
```jsx
import "./App.css";
import { useEffect, useState } from "react";
function useMousePointer() {
  const [position, setPosition] = useState({ x: 0, y: 0 });
  const handelMouseMove = (e) => {
    setPosition({ x: e.clientX, y: e.clientY });
  };
  useEffect(() => {
    window.addEventListener("mousemove", handelMouseMove);
    return () => [window.removeEventListener("mousemove", handelMouseMove)];
  }, []);
  return position;
}
function App() {
  const mousePointer = useMousePointer();
  return (
    <>
      your mouse pointer position is {mousePointer.x} and {mousePointer.y}
    </>
  );
}
export default App;
```
# performance/timer based
- useInterval
```jsx
import "./App.css";
import { useEffect, useState } from "react";
function useInterval(fn, timeout) {
  useEffect(() => {
    const value = setInterval(() => {
      fn();
    }, 1000);
    return () => {
      clearInterval(value);
    };
  }, []);
}
function App() {
  const [count, setCount] = useState(0);
  useInterval(() => {
    setCount((c) => c + 1);
  }, 1000);
  return <>timer is at {count}</>;
}
export default App;
```
- useDebounce
---
```jsx
import "./App.css";
import { useEffect, useState } from "react";
function useDebounce(value, timeout) {
  const [debouncedValue, setDebouncedValue] = useState(value);
  useEffect(() => {
    let timeoutNumber = setTimeout(() => {
      setDebouncedValue(value);
    }, timeout);
    return () => {
      clearTimeout(timeoutNumber);
    };
  }, [value]);
  return debouncedValue;
}
function App() {
  const [value, setValue] = useState(0);
  const debouncedValue = useDebounce(value, 500);
  useEffect(() => {
    fetch("");
  }, [debouncedValue]);
  return (
    <>
      Debounced value is {debouncedValue}
      <br />
      <br />
      <input type="text" onChange={(e) => setValue(e.target.value)} />
    </>
  );
}
export default App;
```
