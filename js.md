# JavaScript   

<details>
<summary>What is a Promise and how do you use it?</summary>

Normally, JavaScript executes statements one at a time. It will not continue with the next statement until the last one has been executed. A Promise is a piece of code that _promises_ to return some data later. This allows you to execute code in a returned Promise _asynchronously_ from the rest of your code. More importantly, once your Promise resolves (that is: It returns the data it promised to return earlier), you can use this result in chained code.

There are two ways to use Promises. The first one is by chaining a function that will be executed when the Promise resolves with the data it promised. The example below showcases a use case where we do a request to an API, then use the result of that API call. `getPolarBears` is the function that _promises_ to return a list of polar bears. The Promise resolves when the `resolve` function is called. When the Promise resolves, the function you passed to the chained `.then(..)` will be called with the result.

```
const baseUrl = "http://example.com";
function getPolarBears() {
  return new Promise((resolve, reject) => {
    const req = new XMLHttpRequest();
    req.open("GET", `${baseUrl}/polar-bears`, false); // Synchronous
    req.send(null);
    resolve(JSON.parse(req.responseText));
  });
}

function doStuff() {
  getPolarBears().then(
    (polarBears) => {
      for (const polarBear of polarBears) {
        polarBear.tickle();
      }
    }
  );
}
```

Alternatively, you can prefix a function definition with `async` to create a function that returns a Promise. You can use `await` in such a function to wait on the result of another Promise.

```
// Use the getPolarBears function from above

async function doStuff() {
  const polarBears = await getPolarBears();
  for (const polarBear of polarBears) {
    polarBear.tickle();
  }
}
```
</details>

----

<details>
<summary>Is it fine to learn JavaScript as your first language for web development or is it better to start with HTML and CSS</summary>

Learn HTML and CSS first. Many take HTML and CSS understanding for granted. But without a clear understanding of the DOM and CSS you will struggle as a Web Developer. Not being able to cleanly and effectively assemble your layout with a stable set of styles can easily turn a 1-day task into a 2-week nightmare.

The big misnomer is that many individuals learn things just enough to be able to Google if they get stuck. CSS isn't one of those things. You can't Google your way out of a CSS bug. The only way is to understand how the cascade works. Once you fully understand CSS then move on to JavaScript.

</details>


----

<details>
<summary>Which JavaScript framework should I learn? Angular, Vue, React?</summary>
  
All three frameworks are front end frameworks that help developers make single page applications(SPA's) so it's less a matter of which framework should you learn and more a matter of which framework is best suited to your liking and understanding. There are pros and cons to all three and determining which one is better will vary from person to person. Ultimately all three are being widely used and there is no right or wrong choice for which framework to learn.  

For some general guidance - Vue is the newest of the three frameworks and is gaining popularity for its ease of use and scalability. Angular was developed by Google and is the oldest of the three and therefore has the largest community since its been around the longest. React was developed by Facebook and currently seems to have the most buzz and popularity. Angular has a bit more structure to it where as React, although still a framework, has some behavior built in that makes it act somewhat like a library (see below for the difference between a library and a framework). 

</details>


----

<details>
<summary>What's the difference between a library and a framework?</summary>
  
A library acts as a "toolbox" with built in resources (e.g. functions, methods, markup templates). There is flexibility in using a library in which the developer can install a library, and pick and choose which resources to use. Using a library helps a developer faciltite processes in their code without having to type everthing from scratch. This is especially helpful for processes that are commonly needed and used but do not pertain to the core functionality of the application/software that a developer is building. Just like any tool, if used in the right context a library can help a developer save time and focus more on the code that is pertinent to the end goal/final product.   

A framework is more rigid and structured in comparsion to a library. Frameworks act more as a governing entity with a set of rules and guidelines that a devopler must follow in order to use the framework and its built in functionality. Similar to a library, a framework helps faciltate certain processes to build an application. However, using a framework effectively requires a greater understanding of how the ecosystem of the framework behaves with all its built-in properites and methods that it comes with. One thing to keep mind is a developer can use certain libraries within a framework. 

When trying to understand the difference between a library and a framework, a helpful analogy is to think of building a house. If you had to build a house on your own you could either build it from scratch with the help of using various tools (i.e. libraries) or you could have a pre-fabricated structure (i.e framework) in which the outer structure, interior wall framing and piping are already constructed in place and it's up to you to then build out the rest of the home within the confines of what is already built (i.e. working within the "ecosystem" of the home). You could of course use some tools (libraries) when working in the pre-fabricated home (framework) but only certain tools will work. 

</details>


----

<details>
<summary>What is async/await?</summary>
  
  Async and await are 2 keywords in JS (not only, as they are present also in other languages like C#) which changed the game with callbacks etc.
  
  In reality, `async function` is wrapping the function into the `Promise` (read about Promises above).
  
  When `async function` returns the value it really makes `resolve(returnedValue)` and when the `async function` throws an error it really makes `reject(error)`.
   
  What it really means? Consider 2 way of doing some stuff.
  ```js
function resultWithPromise () {
  return new Promise((resolve, reject) => {
    resolve('Result');
  });
  
}

async function resultWithAsync () {
    return 'Result';
}

async function checkIt() {
    console.log(await resultWithAsync()); // -> Result
    console.log(await resultWithPromise()); // -> Result
  
    resultWithPromise().then(result => console.log(result)); // -> Result
    resultWithAsync().then(result => console.log(result)); // -> Result
}
```

As you can see above - as the result of async returning the promise and await resolving the promise, you can `await` on `Promise` and do `.then` on `async function`.

Generally it is considered  that using `async` and `await` makes code much cleaner because you are not nesting with `.then` and `.catch`.

One last thing about `.catch`. Using `await funcReturningPromise` may throw an error if promise will be rejected, so to prevent runtime errors you can wrap it in `try {} catch (e) {}`.
</details>

----

<details>
<summary>What is the difference between <em>onevent</em> handlers and <em>adddEventListener</em>?</summary>

## Demystifying Event Handlers: onevent vs addEventListener

As you may already know, HTML elements are not just static, lifeless building blocks of web pages. They are their living parts waiting for the users' interaction, upon which they react in various ways and at the same time emit various events.

When you move your cursor over an element, that element becomes aware of your mouse cursor entering its area and subsequently emits a 'mouseenter' event. Move your cursor away from that element and a 'mouseleave' event is immediately triggered.

When you place your mouse cursor in an input field and start typing your email, that element emits a single 'focus' event, signaling to the browser that it has the user's attention, along with multiple 'input' events as you change the value of this field. Move your cursor out of this input field, and that same element emits a 'blur' event to signal the lose of focus. 

A 'click' event is fired every time you click on an element and a 'submit' event when you submit a form. A 'resize' event is emitted when you resize the browser window and a 'scroll' event when you're scrolling through an element's content. Keyboard clicks produce 'keydown' events and a keyboard button release triggers a 'keyup' event. The list of events goes on and on...

As these events happen on the HTML elements, a JavaScript program can react to these events by carefully listening on them and executing specified code when they are emitted. This is where various mechanisms of listening and reacting to these element events are introduced in JavaScript, and the fall into the following categories:

### The **onevent** family of HTML attributes

This approach uses an inline HTML attribute, named after the event type, e.g. click, submit, mouseenter, focus, etc. and prefixed with the 'on' keyword, e.g. onclick, onsubmit, onmouseenter, onfocus, etc. The value of the attribute corresponds to the JavaScript code to be executed when this event will be emitted by the element. Let's see some examples:

This button's click will trigger an `alert` popup with a random number:

```html
<button onclick="alert(Math.random())">Just alert a random number!</button>
```

This oninput event handlers will replace the characters typed in the input field with their uppercase counterparts. The `this` reserved keyword in this place, is a reference to the element itself. 

```html
<input oninput="this.value = this.value.toUpperCase()"/>
```

This next div will change its color every time the mouse cursor hovers over it. (Random hex color code snippet was found here: https://stackoverflow.com/questions/1484506/random-color-generator)

```html
<div onmouseenter="this.style.color = '#'+Math.floor(Math.random()*16777215).toString(16);">Random Color</div>
```

We can even define a function somewhere inside our scripts and call this function through an onevent HTML handler. In this imaginary scenario, a function called `rollTheDice()` would come up with a random number from 1 to 6 every time the button is double-clicked:

```html
<button ondblclick="rollTheDice()">Roll!</button>
```

**Pros | When to use this method of event handling:**

Since this method has a lot of serious disadvantages (see below) and much better alternatives exist, its use is highly discouraged.

The only case where you would probably use it is when you have just a few (one or two, no more) very simple and short JavaScript code snippets that you want to execute on a couple of HTML elements, and most importantly, on web pages that only you maintain. If the code is short and simple enough to fit in an attribute value, you can probably get away with this `dirty` approach. If on the other hand you work with a team, you better stick with the recommended approach mentioned below since your JavaScript developers scorn this sloppy and lazy approach.

**Cons | When not to use this method of event handling:**

You should probably never use this approach as there as some serious drawbacks:

- You are `polluting` your HTML code (which as you remember is used for creating and structuring the content of web pages) with JavaScript code which has completely different responsibilities. Keep your code separated into HTML, CSS and JavaScript files or their respective tags (style, script). One of the mantras of computer programming is about [**Separation of Concerns**](https://en.wikipedia.org/wiki/Separation_of_concerns#HTML,_CSS,_JavaScript).
- Your HTML code will become unreadable with all these odd-looking `onevent` attributes scattered all around the markup. Frontend developers that work mainly with HTML and CSS or even content editors that are not familiar with JavaScript, will have a hard time looking through the code and updating the content.
- JavaScript Syntax highlighting will probably not work on your favorite code editor when trying to make sense of the code assigned as a value to an `onevent` attribute.
- It is much harder to search through hundreds or thousand of lines of HTML code to find the event handler you'll looking for, rather that on a well-structured and organized JavaScript file (you do keep your JavaScript files organized according to best practices, aren't you?).
- Putting JavaScript or CSS code in your HTML, has some serious maintainability drawbacks (on top of all the other drawbacks mentioned already). What if you decide to change a function name or refactor a function call at some point in time? You'll have to search all through your HTML code, find and update the functions names and then switch back to JavaScript and continue refactoring. This constant switching between different languages is a source of confusion, errors and fatigue. That's why we keep each language in its own separate area.


### The onevent HTMLElement property

Switching from HTML to JavaScript, we find the `HTMLElements'` `onevent` property which is a much cleaner approach to its HTML counterpart (attribute syntax). It works as follows:

The property will still use the `on` + `event type` convention (onclick, onsubmit, onscroll, etc.) and a function must be assigned as a value to this property in order for some code to be executed when the respective event is triggered in a selected element. 

```html
<button id="clapsBtn">Clap</button>
<div>Claps: <span id="claps">0</span></div>
```

```js
function updateClaps(){
    const clapsEl = document.querySelector("#claps");
    clapsEl.textContent = parseInt( clapsEl.textContent ) + 1; // textContent is always String so we need to turn it into a Number integer for addition
}
const clapsBtn = document.querySelector("#clapsBtn");

clapsBtn.onclick = updateClaps; // We are NOT executing, just passing a function reference here.
```

You can even pass a function directly as a value to an onevent property of an element as well as use multiple properties on that same element:

```html
<div id="magic">Hover or double click me to see the magic!</div>
```

```js
const magicEl = document.querySelector("#magic");

magicEl.ondblclick = function doubleClickHandler(){
    // In the context of an onevent handler, the `this` keywords refers to the element
    this.textContent = "Magic happening!";
}

magicEl.onmouseenter = function(){
    // We can pass an anonymous function as a value this way
    this.style.color = "hotpink";
}
magicEl.onmouseleave = function(){
    this.style.color = "black";
}
```

**Pros | When to use this method of event handling:**

The advantage of using this method, is that you keep your JavaScript code out of HTML and you get a quick and easy way to declare event handlers for HTML elements, as opposed to the `addEventListener` syntax that you'll see next. Due to some limitations of this method (see next section), it is advised to use the `addEventListener` method (up next).

**Cons | When not to use this method of event handling:**

Since we are passing the event handling function as a value to a property, it means that we are restricted to just one function per event per element. Study the code below to get a good understanding of this concept:

```html
<button>Clap and log!</button>
<div id="claps">0</div>
```

```js
const btn = document.querySelector("button");
btn.onclick = function updateClaps(){
    const clapsEl = document.querySelector("#claps");
    clapsEl.textContent = parseInt( clapsEl.textContent ) + 1;
}
btn.onclick = function logClapping(){
    console.log("Someone just clapped!");
}
```

What you think will happen if we run the code above? Copy the code in an HTML page, run it and check to see what happens. Now change the order of the event handlers and try again:

```js
const btn = document.querySelector("button");
btn.onclick = function logClapping(){
    console.log("Someone just clapped!");
}
btn.onclick = function updateClaps(){
    const clapsEl = document.querySelector("#claps");
    clapsEl.textContent = parseInt( clapsEl.textContent ) + 1;
}
```

As you can see, we have a serious limitation when using the onevent property method to handle events. Every time we assign a new value (function) to a specific event more than once, the old function gets discarded and only the last assigned function will execute during the event.

You might be thinking about the `+=` operator here, but unfortunately this will not work.

```js
btn.onclick = function logClapping(){
    console.log("Someone just clapped!");
}
// Nope! This will not work as expected. The += operator will turn these functions into a String and concatenate them.
// Javascript will immediately discard the String value and nothing will happen when the click event gets triggered.
btn.onclick += function updateClaps(){
    const clapsEl = document.querySelector("#claps");
    clapsEl.textContent = parseInt( clapsEl.textContent ) + 1;
}
```


### The addEventListener HTMLElement method (Recommended)

This is `one method to rule them all`! Although the `addEventListener` syntax shown below is a little bit verbose, it is the recommended way of adding event handlers in JavaScript for quite some time now. You can use it to assign as many event handlers as you want on a single event and you can also omit the `on` prefix when defining the event type. Here's a pseudo syntax:

```js
HTMLElement.addEventListener( EVENT_TYPE, EVENT_HANDLER_FUNCTION );
```

And here are some examples:

```html
<button>Clap and log!</button>
<div id="claps">0</div>
<div id="color">Color changing trick</div>
```

```js
const btn = document.querySelector("button");
const colorEl = document.querySelector("#color");

function updateClaps(){
    const clapsEl = document.querySelector("#claps");
    clapsEl.textContent = parseInt( clapsEl.textContent ) + 1;
}

function logClapping(){
    console.log("Someone just clapped!");
}

btn.addEventListener("click", updateClaps); // (1) We can pass a function reference (we are NOT calling it here)
btn.addEventListener("click", logClapping);

// (2) We can pass a function declaration directly as the 2nd argument:
colorEl.addEventListener("mouseenter", function updateColor(){
    this.style.color = "hotpink";
});

// (2.1) We can pass an anonymous function declaration as the 2nd argument:
colorEl.addEventListener("mouseleave", function(){
    this.style.color = "black";
});
```

The advantage of passing a named function as the 2nd argument to the `addEventListener` is that we can access that function from within itself:

```js
colorEl.addEventListener("mouseenter", function updateColor(){
    colorEl.style.color = "hotpink"; // We need to switch from `this` to `colorEl` here, as the reference won't work when the updateColor function gets called by setTimeout due to a different execution context
    setTimeout( updateColor, 5000 ); // run the updateColor function 5 seconds after it has been triggered by a click
});
```

**Pros | When to use this method of event handling:**

As you see, the `addEventListener` method is the one which provides the most benefits to us and it's the preferred way of handling events in JavaScript. Just stick to it, and you'll be safe and sound. :)

**Cons | When not to use this method of event handling:**

It's just a little bit more verbose than the `onevent` method.

### References

- [DOM onevent handlers](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Event_handlers)

- [GlobalEventHandlers](https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers)

- [addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

- [The this context in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

</details>