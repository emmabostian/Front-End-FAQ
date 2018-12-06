# Redux

<details>
<summary>What are Redux Epics? Why would you use them?</summary>

If you know the answer to this question, please submit a pull request with the answer.

</details>

## _Waiting for response_

---

<details>
<summary>Will the new React Hooks replace Redux? How would they work together?</summary>

At the time of writing, Hooks are an alpha feature in React (current version: 16.7.0-alpha). If you are reading this from the future, this information may have changed. As always, check [the docs](https://reactjs.org/docs/hooks-intro.html).

Redux is a library which allows us to keep the state of our app in some central location, called a _store_, which can be accessed from anywhere within the app. Hooks, on the other hand, enable components to store and access _their own_ state. This has always been possible with class-based components, but not with functional components.

So in short, no, Hooks in their present form will not replace Redux. They have completely opposite aims. In fact, Hooks and Redux might work very well together, rather than against each other. We could use a hook to connect a component to a store when it mounts. That component might manage its own state with the `useState` hook, and also dispatch Redux actions from the connected store. Let's imagine a search bar that keeps its own text value in state, and dispatches that text to the Redux store when a button is clicked:

```js
// NOT REAL CODE... YET!

import React, { useState } from "react";
import { useRedux } from "imaginary-future-redux-library";

export const SearchBar = () => {
  const [searchString, setSearchString] = useState("");
  const [state, { makeSearchRequest }] = useRedux(state => state, actions);

  return (
    <div className="search-bar">
      <input type="text" value={searchString} onChange={event => setSearchString(event.target.value)}/>
      <button onClick={makeSearchRequest(searchString)}></button>
    </div>
  )
};
```

</details>

---
