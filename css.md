# CSS

<details>
<summary>What is the difference between absolute and fixed positioning?</summary>

_Absolute positioning allows you to place any page element exactly where you want it._ You use the positioning attributes top, left, bottom. and right to set the location. Ex. `position: absolute; top: 40px; left: 40px;` (These values are relative to the parent element). When you absolute position an element you treat it as an independent element on the page, which means it  will not be affected by other elements and it won't affect other elements.

_A fixed position element is positioned relative to the viewport, or the browser window itself._ This is often used for navigation or sidebars because the viewport does not change at scrolling. So your fixed element will remain at the exact position you set it at. Ex. `position: fixed; top: 80px; left: 10px;`  

</details>

----

<details>
<summary>What is the best/most performant way to include media queries? Is it better to put them all in one CSS file or split them up into different CSS files per component or page?</summary>

</details>

_Waiting for response_

----

<details>
<summary>What are CSS pre-processors and how do I get started with one?</summary>

CSS pre-processors provide additional functionalities to CSS. Each one has its own syntax (which is generally very similar to CSS) and they compile down to CSS through a compiler.

1. Why would I use a pre-processor?
- CSS while being great at what it does gets really hard to maintain over large projects. Pre-processors add functionalities that are lacking in CSS, like nesting, importing other CSS files, mixins etc. These features make it easier to maintain the code and make it more readable.

2. What options do we have?
- There are many options, some of them are: [SASS](http://sass-lang.com/), [LESS](http://lesscss.org/) and [Stylus](http://stylus-lang.com/).

3. How do I get started?
- To use most of these, you would need a form of compiler or processor to compile the files down to CSS. How they generally work is that you ask them to watch a file(.sass, .less et al.) and they compile these files on the fly. [Koala](http://koala-app.com/) is one such option for SASS and LESS.
- If you are using [VS Code](https://code.visualstudio.com/), then you can install plugins that will act as a compiler and do it for you. [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass) is an example of such an extension.

</details>
