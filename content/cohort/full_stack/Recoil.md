---
id: Recoil
aliases: []
tags: []
---

# Basic
- RecoilRoot
- atom
- useSetRecoilState
- useRecoilState
- useRecoilValue
```jsx
//Count.jsx
import { atom } from "recoil";
export const countAtom = atom({
  key: "countAtom",
  default: 0,
});
//app.jsx
import "./App.css";
import { useRecoilValue, useSetRecoilState, RecoilRoot } from "recoil";
import { countAtom } from "./store/atoms/Count";

function App() {
  console.log("app");
  return (
    <RecoilRoot>
      <Count />
    </RecoilRoot>
  );
}
function Count() {
  return (
    <div>
      <CountRenderer />
      <Buttons />
    </div>
  );
}
function CountRenderer() {
  console.log("render");
  const count = useRecoilValue(countAtom);
  return (
    <div>
      <b>{count}</b>
      <EvenCountRender />
    </div>
  );
}
function EvenCountRender() {
  const count = useRecoilValue(countAtom);
  return <div>{count % 2 == 0 ? "It is Even" : "It is odd"}</div>;
}
function Buttons() {
  console.log("button");
  const setCount = useSetRecoilState(countAtom);
  return (
    <div>
      <button
        onClick={() => {
          setCount((count) => count + 1);
        }}
      >
        Increase
      </button>
      <button
        onClick={() => {
          setCount((count) => count - 1);
        }}
      >
        Decrease
      </button>
    </div>
  );
}
export default App;
```
---
-selector
```jsx
//count.jsx
import { atom, selector } from "recoil";
export const countAtom = atom({
  key: "countAtom",
  default: 0,
});

export const evenSelector = selector({
  key: "evenSelector",
  get: ({ get }) => {
    const count = get(countAtom);
    return count % 2;
  },
});
//app.jsx
import "./App.css";
import { useRecoilValue, useSetRecoilState, RecoilRoot } from "recoil";
import { countAtom, evenSelector } from "./store/atoms/Count";

function App() {
  console.log("app");
  return (
    <RecoilRoot>
      <Count />
    </RecoilRoot>
  );
}
function Count() {
  return (
    <div>
      <CountRenderer />
      <Buttons />
    </div>
  );
}
function CountRenderer() {
  console.log("render");
  const count = useRecoilValue(countAtom);
  return (
    <div>
      <b>{count}</b>
      <EvenCountRender />
    </div>
  );
}
function EvenCountRender() {
  const isEven = useRecoilValue(evenSelector);

  return <div>{isEven ? "It is Even" : "It is odd"}</div>;
}
function Buttons() {
  console.log("button");
  const setCount = useSetRecoilState(countAtom);
  return (
    <div>
      <button
        onClick={() => {
          setCount((count) => count + 1);
        }}
      >
        Increase
      </button>
      <button
        onClick={() => {
          setCount((count) => count - 1);
        }}
      >
        Decrease
      </button>
    </div>
  );
}
export default App;
```
- async data queries
```jsx
//atom.jsx
import axios from "axios";
import { atom, selector } from "recoil";

export const notifications = atom({
  key: "networkAtom",
  default: selector({
    key: "networkAtomSelector",
    get: async () => {
      const res = await axios.get(
        "https://sum-server.100xdevs.com/notifications",
      );
      return res.data;
    },
  }),
});

export const totalNotificationSelector = selector({
  key: "totalNotificationSelector",
  get: ({ get }) => {
    const allNotifications = get(notifications);
    return (
      allNotifications.network +
      allNotifications.jobs +
      allNotifications.notifications +
      allNotifications.messaging
    );
  },
});
//app.jsx
import "./App.css";
import { RecoilRoot, useRecoilState, useRecoilValue } from "recoil";
import {
  notifications,
  totalNotificationSelector,
} from "./store/atoms/atom";
import { useEffect } from "react";
import axios from "axios";

function App() {
  return (
    <RecoilRoot>
      <MainApp />
    </RecoilRoot>
  );
}

function MainApp() {
  const [networkCount, setNetworkCount] = useRecoilState(notifications);
  const totalNotificationCount = useRecoilValue(totalNotificationSelector);

  useEffect(() => {
    // fetch
    axios
      .get("https://sum-server.100xdevs.com/notifications")
      .then((res) => {
        setNetworkCount(res.data);
      })
      .catch((error) => {
        console.log(error);
      });
  }, []);

  return (
    <>
      <button>Home</button>

      <button>
        My network (
        {networkCount.networks >= 100 ? "99+" : networkCount.network})
      </button>
      <button>Jobs ({networkCount.jobs})</button>
      <button>Messaging ({networkCount.messaging})</button>
      <button>Notifications ({networkCount.notifications})</button>

      <button>Me ({totalNotificationCount})</button>
    </>
  );
}

export default App;
```
# Advance
- atomFamily
---
```jsx
//atom.jsx
import { atomFamily } from "recoil";
import { TODOS } from "./todos";

export const todosAtomFamily = atomFamily({
  key: 'todosAtomFamily',
  default: id => {
    return TODOS.find(x => x.id === id)
  },
});
//app.jsx
import './App.css'
import { RecoilRoot, useRecoilState } from 'recoil';
import { todosAtomFamily } from './atoms';

function App() {
  return <RecoilRoot>
    <Todo id={1}/>
    <Todo id={2} />
  </RecoilRoot>
}

function Todo({id}) {
   const [todo, setTodo] = useRecoilState(todosAtomFamily(id));

  return (
    <>
      {todo.title}
      {todo.description}
      <br />
    </>
  )
}

export default App
```
- selectorFamily
---
```jsx
//atom.jsx
import { atomFamily, selectorFamily } from "recoil";
import axios from "axios";

export const todosAtomFamily = atomFamily({
  key: 'todosAtomFamily',
  default: selectorFamily({
    key: "todoSelectorFamily",
    get: (id) => async ({get}) => {
      const res = await axios.get(`https://sum-server.100xdevs.com/todo?id=${id}`);
      return res.data.todo;
    },
  })
});
//app.jsx
import './App.css'
import { RecoilRoot, useRecoilState } from 'recoil';
import { todosAtomFamily } from './atoms';

function App() {
  return <RecoilRoot>
    <Todo id={1}/>
    <Todo id={2} />
  </RecoilRoot>
}

function Todo({id}) {
   const [todo, setTodo] = useRecoilState(todosAtomFamily(id));

  return (
    <>
      {todo.title}
      {todo.description}
      <br />
    </>
  )
}

export default App
```
- loadables
---
```jsx
//atom.jsx
import { atomFamily, selectorFamily } from "recoil";
import axios from "axios";

export const todosAtomFamily = atomFamily({
  key: 'todosAtomFamily',
  default: selectorFamily({
    key: "todoSelectorFamily",
    get: (id) => async ({get}) => {
      await new Promise(r => setTimeout(r, 5000));
      const res = await axios.get(`https://sum-server.100xdevs.com/todo?id=${id}`);
      return res.data.todo;
    },
  })
});
//app.jsx
import "./App.css";
import { RecoilRoot, useRecoilStateLoadable } from "recoil";
import { todosAtomFamily } from "./store/atoms/atom";

function App() {
  return (
    <RecoilRoot>
      <Todo id={1} />
      <Todo id={2} />
    </RecoilRoot>
  );
}

function Todo({ id }) {
  const [todo, setTodo] = useRecoilStateLoadable(todosAtomFamily(id));
  if (todo.state === "loading") {
    return <div>loading</div>;
  } else if (todo.state === "hasValue") {
    return (
      <>
        {todo.contents.title}
        {todo.contents.description}
        <br />
      </>
    );
  } else if (todo.state === "hasError") {
    return <>has error...</>;
  }
}
export default App;
```
