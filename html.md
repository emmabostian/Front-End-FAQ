# HTML

<details>
<summary>What are <div> and <span>?  Why would you use them?</summary>

All HTML documents have two types of element - block and inline. A `<p>`, or paragraph is an example of a block element; `<strong>` is an example of an inline element. These elements are treated differently when a browser displays your page:

-   a block level element has 100% width by default and any subsequent elements will appear below it.
-   Inline elements do just that - they appear inside block level elements, only taking up the width that they need and they can only have padding and/or margin added to the left or right sides.

Most elements in HTML are designed for a specific purpose - a paragraph, a heading, bold text, etc, but a `<div>` is a generic block element that you can use for whatever you want. In the same vein, `<span>` is a generic inline element. But what would you use them for?

`<span>`s can be used to differentiate parts of the text in a paragraph - maybe you have a brand name that you want to style differently everywhere it appears - wrap it in a span and give it a class (`<span class="brand-mark">AwesomeBrandName</span>`) - you can then change the look of that text in your CSS.

`<div>`s can be used to break up your content into distinct areas or types - maybe an interactive image area, or the graph with flyout. With the addition of HTML5 elements such as `<footer>`, `<main>` and `<nav>`, the number of uses of a `<div>` has gone down, but you will definitely still run into situations where nothing else fits and you pull the trusty `<div>` out of your toolbox!

</details>
