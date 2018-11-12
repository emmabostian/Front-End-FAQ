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

