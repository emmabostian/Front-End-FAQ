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
