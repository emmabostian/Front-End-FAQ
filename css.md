# CSS

**What is the difference between absolute and fixed positioning?**  
_Absolute positioning allows you to place any page element exactly where you want it._ You use the positioning attributes top, left, bottom. and right to set the location. Ex. `position: absolute; top: 40px; left: 40px;` (These values are relative to the parent element). When you absolute position an element you treat it as an independent element on the page, which means it  will not be affected by other elements and it won't affect other elements.

_A fixed position element is positioned relative to the viewport, or the browser window itself._ This is often used for navigation or sidebars because the viewport does not change at scrolling. So your fixed element will remain at the exact position you set it at. Ex. `position: fixed; top: 80px; left: 10px;`  

<br/><br/>

**What is the best/most performant way to include media queries? Is it better to put them all in one CSS file or split them up into different CSS files per component or page?**  

**Short answer:** Do not merge your media queries.

**Long answer:**

(`max-width` is being used in the media query examples, this answer is not suggesting that `max-width` is any better or worse than using `min-width`. It is purely for demonstrating the 2 styles.)

Technically, the **most performant** way to handle media queries is to put them all into one css file and have all of your components share media queries.

```css
/* *Most performant* media query style */

.header {
  /* header default styles */
}

.footer {
  /* footer default styles */
}

@media (max-width: 600px) {
  .header {
    /* header mobile styles */
  }

  .footer {
    /* footer mobile styles */
  }
}
```

This is **not the best** way to handle media queries though. This method of writing media queries is immensely more difficult to maintain than writing separate media queries for each component. The performance gains that this method brings with it are also [practically negligible](https://benfrain.com/inline-or-combined-media-queries-in-sass-fight/) thanks to [gzip](https://en.wikipedia.org/wiki/Gzip).

The **best way** to write your media queries is to split them up component by component.

```css
/* The *best* media query style */

/********\
  header
\********/

.header {
  /* header default styles */
}
@media (max-width: 600px) {
  .header {
    /* header mobile styles */
  }
}

/********\
  footer
\********/

.footer {
  /* footer default styles */
}
@media (max-width: 600px) {
  .footer {
    /* footer mobile styles */
  }
}
```

This keeps all of the styles for a single component in one place making the project immensely easier to maintain in the long run.

You may be thinking "tooling to the rescue!" by pointing to a PostCSS plugin like [pastcss-move-media](https://www.npmjs.com/package/postcss-move-media). On the surface, this looks like a great idea. You get to write source files with as many separate media queries as you want. You then let the tooling automatically optimize the code for you by merging all the identical media queries together. It sounds great on paper but in reality it's a death trap waiting to happen.

CSS is highly dependent on the order that the styles are declared in. If both CSS rules have the same level of specificity, a rule written lower in the stylesheet will override a rule written higher in the style sheet. These automated media merging tools must rearrange the order of your CSS in order to fulfill their duty. Having an automated tool re-arrange the order of your CSS can be extremely dangerous though. If the media merge is only integrated into your build process as part of the minification step, the minification step could cause major breakages throughout your whole site.

So in short do not merge your media queries and let gzip handle the media query optimization, not automated merging tools.

<br/><br/>

**What are CSS pre-processors and how do I get started with one?**   
CSS pre-processors provide additional functionalities to CSS. Each one has its own syntax (which is generally very similar to CSS) and they compile down to CSS through a compiler.

1. Why would I use a pre-processor?
- CSS while being great at what it does gets really hard to maintain over large projects. Pre-processors add functionalities that are lacking in CSS, like nesting, importing other CSS files, mixins etc. These features make it easier to maintain the code and make it more readable.

2. What options do we have?
- There are many options, some of them are: [SASS](http://sass-lang.com/), [LESS](http://lesscss.org/) and [Stylus](http://stylus-lang.com/).

3. How do I get started?
- To use most of these, you would need a form of compiler or processor to compile the files down to CSS. How they generally work is that you ask them to watch a file(.sass, .less et al.) and they compile these files on the fly. [Koala](http://koala-app.com/) is one such option for SASS and LESS.
- If you are using [VS Code](https://code.visualstudio.com/), then you can install plugins that will act as a compiler and do it for you. [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass) is an example of such an extension.
