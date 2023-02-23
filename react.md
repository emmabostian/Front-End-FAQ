# React

<details>
<summary>What are the pre requesites(excluding the general HTML, CSS, and JS) before starting off with React?</summary>

Apart from HTML, CSS and a good level of comfort with Javascript, learning react requires one to be be familiar with Object Oriented Concepts since React uses a lot of inheritance from classes and methods that are used to create both functional and presentational components. Knowledge of Single Page Applications is also important as it will give you an idea of how routing happens with the understanding that the routes are dynamic and not physical pages on the server. To set up you can either use a [script tag](https://reactjs.org/docs/add-react-to-a-website.html) that pulls in React in your project or to set up using [create-react-app](https://github.com/facebook/create-react-app) from Facebook. You can then write your own React code in a simple JS file for functional components and JSX file for presentational components.

You can start with the official docs' [getting started](https://reactjs.org/docs/getting-started.html) page which are very beginner friendly.

</details>

----

<details>
<summary>Why do we need hooks?</summary>

Hooks are a way of letting the developer use State or other React Features without necessarily writing class components (sounds cool, right?!). Previously React required that to create state or set State of a component on needs to declare a class component where the state could be initialized and then would be later used in the class component. Using React hooks one can easily initialize state or any lifecycle methods within functional components. An example would be setting initial state of counter in a functional component and incrementing the counter as a button is clicked. 

```
import { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

```
From the above the `useState` is the hook which we use to initialize our state, to trigger the hook we call the function that we declare while initializing the react hook which is `setCount`. It is important to note that the hook will only be used with the initial state and will only work withing react functional components. 

</details>

----

<details>
<summary>Why can’t we use variables/functions directly inside a function component?</summary>

If you know the answer to this question, please submit a pull request with the answer.

</details>

_Waiting for response_


----

<details>
<summary>What are React render props?</summary>

In React, render props is a technique used to share code between components. It involves passing a function as a prop to a component, which the component can then call to render some part of its content.

Here's an example of how render props work:  
## React Render Props Example

This example demonstrates how to use React render props.

```jsx
import React from 'react';

function RenderProp(props) {
  return (
    <div>
      <h2>{props.render("Hello, world!")}</h2>
    </div>
  );
}

function App() {
  return (
    <div>
      <h1>React Render Props Example</h1>
      <RenderProp render={(message) => <p>{message}</p>} />
    </div>
  );
}

export default App;  

```  
<small>This example demonstrates how to use the Render Props pattern in React. We have a RenderProp component that accepts a render prop, which is a function that takes a message as an argument and returns some JSX. The RenderProp component uses this function to render the message in an `<h2>` element.

In the App component, we use the RenderProp component and pass it a custom rendering function using the render prop. This function takes a message as an argument and returns a `<p> `element that displays the message.

When the RenderProp component is rendered, it calls the rendering function that was passed to it as a prop with the message "Hello, world!" as an argument. This results in the message being displayed in a `<p>` element.

By using the render prop, we can create reusable components that can be customized with different rendering functions. This makes our code more flexible and easier to maintain.</small>.

</details>  