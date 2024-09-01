---
id: React
aliases: []
tags: []
---

- react calculates the difference
- react dom: tell react about how to put in dom
- react native: tell react how to put in react native
- state: object that represent current state of the app
- componenet: how a DOM element should render, given it's state
- re-renndering: updating the state change trrigers re-rendering ie DOM manipulation

```jsx
//counter
import { useState } from "react";
function App() {
  const [count, setCount] = useState(0);
  function onClickDisplay() {
    setCount(count + 1);
  }
  return (
    <div>
      <button onClick={onClickDisplay}>Counts: {count}</button>
    </div>
  );
}

export default App;
```
---
```jsx
// simple todo
import "./App.css";
import { useState } from "react";
function App() {
  const [todos, setTodos] = useState([
    {
      title: "bookings",
      time: "10:30-4:00",
    },
    {
      title: "nah",
      time: "20:33-5:00",
    },
  ]);
  function addTodo() {
    setTodos([
      ...todos,
      {
        title: "new todo",
        time: "some time",
      },
    ]);
  }
  return (
    <div>
      <button onClick={addTodo}>add elements</button>
      {todos.map(function (todo) {
        return <Todo title={todo.title} time={todo.time} />;
      })}
    </div>
  );
}
function Todo(props) {
  return (
    <div>
      <h1>{props.title}</h1>
      <h1>{props.time}</h1>
    </div>
  );
}

export default App;
```
### React  component return
- can only return a single top level xml
- makes it easy to tell what dom update needs to happen
```jsx
import "./App.css";
import React,{Fragment} from "react";
function App() {
  return (
    <Fragment>
      <Header title="old"></Header>
      <Header title="new"></Header>
    </Fragment>
  );
}
function Header({ title }) {
  return <div>{title}</div>;
}
export default App;
```
### re-rendering
- A state variable changes
- A parent re-render triggers all children re-render as well

Preventing re-render
---
pushing the state down
```jsx
import "./App.css";
import { Fragment } from "react";
import { useState } from "react";
function App() {
  return (
    <div>
      <HeaderWithButton />
      <Header title="victon1" />
      <Header title="victon2" />
      <Header title="victon3" />
    </div>
  );
}
function HeaderWithButton() {
  const [title, setTitle] = useState("my name is new");
  function updateTitle() {
    setTitle("my name is " + Math.random());
  }
  return (
    <div>
      <button onClick={updateTitle}>Update the title</button>
      <Header title={title} />
    </div>
  );
}
function Header({ title }) {
  return <div>{title}</div>;
}
export default App;
```
memoing
----
```jsx
import "./App.css";
import React, { Fragment } from "react";
import { useState } from "react";
function App() {
  const [title, setTitle] = useState("my name is new");
  function updateTitle() {
    setTitle("my name is " + Math.random());
  }
  return (
    <div>
      <button onClick={updateTitle}>Update the title</button>
      <Header title={title} />
      <Header title={title} />
      <Header title="victon1" />
      <Header title="victon2" />
    </div>
  );
}
const Header = React.memo(function Header({ title }) {
  return <div>{title}</div>;
});
export default App;
```
keys
--
whenever rendering giving unique key to it reduces rerendering
```jsx
import "./App.css";
import { useState } from "react";
function App() {
  let counter = 3;
  const [todo, setTodo] = useState([
    {
      id: 1,
      title: "bookings",
      time: "10:30-4:00",
    },
    {
      id: 2,
      title: "nah",
      time: "20:33-5:00",
    },
  ]);
  function addTodo() {
    setTodo([
      ...todo,
      {
        id: counter++,
        title: "new todo",
        time: "some time",
      },
    ]);
  }
  return (
    <div>
      <button onClick={addTodo}>add elements</button>
      {todo.map(function (todo) {
        return <Todo key={todo.id} title={todo.title} time={todo.time} />;
      })}
    </div>
  );
}
function Todo({ title, time }) {
  return (
    <div>
      <h4>{title}</h4>
      <h4>{time}</h4>
    </div>
  );
}

export default App;
```
Wrapper component
---
```jsx
import "./App.css";
import { useState } from "react";
function App() {
  return (
    <div>
      <CardWrapper>hi there!</CardWrapper>
    </div>
  );
}

function CardWrapper({ ...children }) {
  return <div style={{ border: "2px solid black" }} {...children}></div>;
}

export default App;

```
# HOOK
useEffect()
---
```jsx
import axios from "axios";
import "./App.css";
import { useEffect, useState } from "react";
function App() {
  let counter = 3;
  const [todos, setTodos] = useState([]);
  useEffect(() => {
    setInterval(() => {
      axios.get("https://sum-server.100xdevs.com/todos")
        .then(function (response) {
          setTodos(response.data.todos);
        });
    }, 5000);
  }, []);

  return (
    <div>
      {todos.map((todo) => (
        <Todo key={todo.id} title={todo.title} description={todo.description} />
      ))}
    </div>
  );
}
function Todo({ title, description }) {
  return (
    <div>
      <h4>{title}</h4>
      <h4>{description}</h4>
    </div>
  );
}

export default App;
```
---
```jsx
import axios from "axios";
import "./App.css";
import { useEffect, useState } from "react";
function App() {
  const [selectedId, setSelectedId] = useState([1]);

  return (
    <div>
      <button
        onClick={function () {
          setSelectedId(1);
        }}
      >
        1
      </button>
      <button
        onClick={function () {
          setSelectedId(2);
        }}
      >
        2
      </button>
      <button
        onClick={function () {
          setSelectedId(3);
        }}
      >
        3
      </button>
      <button
        onClick={function () {
          setSelectedId(4);
        }}
      >
        4
      </button>
      <Todo id={selectedId} />
    </div>
  );
}
function Todo({ id }) {
  const [todo, setTodo] = useState([]);
  useEffect(() => {
    axios
      .get(`https://sum-server.100xdevs.com/todo?id=${id}`)
      .then(function (response) {
        setTodo(response.data.todo);
      });
  }, [id]);
  return (
    <div>
      <h2>Id:{id}</h2>
      <h4>{todo.title}</h4>
      <h4>{todo.description}</h4>
    </div>
  );
}

export default App;
G
```
useMemo
---
```jsx
import "./App.css";
import { useMemo, useState } from "react";
function App() {
  const [counter, setCounter] = useState(0);
  const [inputValue, setInputValue] = useState(1);

  let count = useMemo(() => {
    let finalCount = 0;
    for (let i = 1; i < inputValue; i++) {
      finalCount = finalCount + 1;
    }
    return finalCount;
  }, [inputValue]);
  return (
    <div>
      <input
        onChange={function (e) {
          setInputValue(e.target.value);
        }}
        placeholder="find sum to n"
      ></input>
      <br />
      Sum from 1 {inputValue} is {count}
      <br />
      <button
        onClick={() => {
          setCounter(counter + 1);
        }}
      >
        Counter ({counter})
      </button>
    </div>
  );
}

export default App;
```
useCallback
---
```jsx
import "./App.css";
import { memo, useCallback, useState } from "react";
var a = 1;
function App() {
  const [counter, setCounter] = useState(0);
  const a = useCallback(function () {
    console.log("HI there!");
  }, []);
  return (
    <div>
      <button
        onClick={() => {
          setCounter(counter + 1);
        }}
      >
        Counter ({counter})
      </button>
      <Demo a={a} />
    </div>
  );
}
const Demo = memo(function ({ a }) {
  console.log("rerender");
  return <div>hi there {a}</div>;
});

export default App;
```
useRef
---
```jsx
import "./App.css";
import { useEffect, useRef, useState } from "react";

function App() {
  const [incomeTax, setIncomeTax] = useState(2000);
  const divRef = useRef();
  useEffect(() => {
    setTimeout(() => {
      console.log(divRef.current);
      divRef.current.innerHTML = 10;
    }, 5000);
  }, []);
  return (
    <div>
      Your Income tax are <div ref={divRef}>{incomeTax}</div>
    </div>
  );
}
export default App
```
# Routing
```jsx
//wrong way
import "./App.css";
import { BrowserRouter, Route, Routes } from "react-router-dom";
import { Dashboard } from "./component/Dashboard";
import { Landing } from "./component/Landing";

function App() {
  return (
    <>
      <div>
        <button
          onClick={() => {
            window.location.href = "/";
          }}
        >
          Landing Page
        </button>
        <button
          onClick={() => {
            window.location.href = "/dashboard";
          }}
        >
          Dashboard Page
        </button>
      </div>
      <BrowserRouter>
        <Routes>
          <Route path="/dashboard" element={<Dashboard />} />
          <Route path="/" element={<Landing />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}
export default App;
```
---
- useNavigatae
```jsx
// right way
import "./App.css";
import { BrowserRouter, Route, Routes, useNavigate } from "react-router-dom";
import { Dashboard } from "./component/Dashboard";
import { Landing } from "./component/Landing";

function App() {
  return (
    <>
      <BrowserRouter>
        <Appbar />
        <Routes>
          <Route path="/dashboard" element={<Dashboard />} />
          <Route path="/" element={<Landing />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}
function Appbar() {
  const navigate = useNavigate();
  return (
    <div>
      <div>
        <button
          onClick={() => {
            navigate("/");
          }}
        >
          Landing Page
        </button>
        <button
          onClick={() => {
            navigate("/dashboard");
          }}
        >
          Dashboard Page
        </button>
      </div>
    </div>
  );
}
export default App;
```
---
- lazy load and suspense api
```jsx
// dashboard.jsx
export default function Dashboard() {
  return <div>Dashboard Page</div>;
}
//app.jsx
import "./App.css";
import React, { Suspense } from "react";
import { BrowserRouter, Route, Routes, useNavigate } from "react-router-dom";
const Dashboard = React.lazy(() => import("./component/Dashboard"));
const Landing = React.lazy(() => import("./component/Landing"));

function App() {
  return (
    <>
      <BrowserRouter>
        <Appbar />
        <Routes>
          <Route
            path="/dashboard"
            element={
              <Suspense fallback={"loading.."}>
                <Dashboard />
              </Suspense>
            }
          />
          <Route
            path="/"
            element={
              <Suspense fallback={"loading..."}>
                <Landing />
              </Suspense>
            }
          />
        </Routes>
      </BrowserRouter>
    </>
  );
}
function Appbar() {
  const navigate = useNavigate();
  return (
    <div>
      <div>
        <button
          onClick={() => {
            navigate("/");
          }}
        >
          Landing Page
        </button>
        <button
          onClick={() => {
            navigate("/dashboard");
          }}
        >
          Dashboard Page
        </button>
      </div>
    </div>
  );
}
export default App;
```
# prop driling
passing props down the tree
context api teleports data without drilling through prop chain
```jsx
import "./App.css";
import { useContext, useState } from "react";
import { CountContext } from "./Context";

function App() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <CountContext.Provider value={count}>
        <Count count={count} setCount={setCount} />
      </CountContext.Provider>
    </div>
  );
}
function Count({ setCount }) {
  return (
    <div>
      <Countrender />
      <Buttons setCount={setCount} />
    </div>
  );
}
function Countrender() {
  const count = useContext(CountContext);
  return <div>{count}</div>;
}
function Buttons({ setCount }) {
  const count = useContext(CountContext);
  return (
    <div>
      <button
        onClick={() => {
          setCount(count + 1);
        }}
      >
        Increase
      </button>
      <button
        onClick={() => {
          setCount(count - 1);
        }}
      >
        Decrease
      </button>
    </div>
  );
}
export default App;
```
