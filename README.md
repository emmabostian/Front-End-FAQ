# Front-End-FAQ
A place to anonymously ask questions and receive answers from the dev community. <br /> <br />

## How It Works
The premise is simple: Ask the questions you've always had about Front-End Development but were too afraid to ask for fear of criticism, then wait for a response! <br /> <br />

## How Do I Ask A Question?
Send me a DM over on [Twitter](https://twitter.com/EmmaWedekind)! <br /> <br />

## How Do I Answer A Question?
Feel free to open a PR on this repo! <br /> <br />

## How Is This Different Than Stack Overflow?
It's true that Stack Overflow is meant for knowledge sharing. That being said, as a beginner I know I had a ton of questions about HTML, CSS, and JavaScript that I wanted answered, but anonymously. Stack Overflow requires you to be logged in. Yes, you can change your name, but that's a hassle and has a 30-day waiting period to re-change. I want to remove the hassle of asking and answering questions.

Front-End FAQ will be the one place you can go to for all your Front-end questions, while remaining anonymous.  Plus, it's a great way to contribute to open-source. <br /> <br />

# Table Of Contents
[General](#general)

[HTML](#html)

[CSS](#css)

[JavaScript](#javascript)

[Performance](#performance)

[Accessibility](#accessibility)

[Node](#node)

[React](#react)

 <br/> <br/> <br/>
 
 
 
 # General
 **What IDE should I use?**   
 _Waiting for response_   
 
 <br/><br/><br/>
 
 

# HTML   
**What are `<div>` and `<span>`?  Why would you use them?**

All HTML documents have two types of element - block and inline.  A `<p>`, or paragraph is an example of a block element; `<strong>` is an example of an inline element. These elements are treated differently when a browser dislays your page:
- a block level element has 100% width by default and any subsequent elements will appear below it.
- Inline elements do just that - they appear inside block level elements, only taking up the width that they need and they can only have padding and/or margin added to the left or right sides.

Most elements in HTML are designed for a specific purpose - a paragraph, a heading, bold text, etc, but a `<div>` is a generic block element that you can use for whatever you want. In the same vein, `<span>` is a generic inline element. But what would you use them for?

`<span>`s can be used to differentiate parts of the text in a paragraph - maybe you have a brand name that you want to style differently everywhere it appears - wrap it in a span and give it a class (`<span class="brand-mark">AwesomeBrandName</span>`) - you can then change the look of that text in your CSS.

`<div>`s can be used to break up your content into distinct areas or types - maybe an interactive image area, or the graph with flyout. With the addition of HTML5 elements such as `<footer>`, `<main>` and `<nav>`, the number of uses of a `<div>` has gone down, but you will definitely still run into situations where nothing else fits and you pull the trusty `<div>` out of your toolbox!

<br/><br/><br/>


# CSS  

**What is the difference between absolute and fixed positioning?**  
_Absolute positioning allows you to place any page element exactly where you want it._ You use the positioning attributes top, left, bottom. and right to set the location. Ex. `position: absolute; top: 40px; left: 40px;` (These values are relative to the parent element). When you absolute position an element you treat it as an independent element on the page, which means it  will not be affected by other elements and it won't affect other elements.

_A fixed position element is positioned relative to the viewport, or the browser window itself._ This is often used for navigation or sidebars because the viewport does not change at scrolling. So your fixed element will remain at the exact position you set it at. Ex. `position: fixed; top: 80px; left: 10px;`


**What is the best/most performant way to include media queries? Is it better to put them all in one CSS file or split them up into different CSS files per component or page?**  
_Waiting for response_

**What are CSS pre-processors and how do I get started with one?**   
CSS pre-processors provide additional functionalities to CSS. Each one has its own syntax (which is generally very similar to CSS) and they compile down to CSS through a compiler.

1. Why would I use a pre-processor?
- CSS while being great at what it does gets really hard to maintain over large projects. Pre-processors add functionalities that are lacking in CSS, like nesting, importing other CSS files, mixins etc. These features make it easier to maintain the code and make it more readable.

2. What options do we have?
- There are many options, some of them are: [SASS](http://sass-lang.com/), [LESS](http://lesscss.org/) and [Stylus](http://stylus-lang.com/).

3. How do I get started?
- To use most of these, you would need a form of compiler or processor to compile the files down to CSS. How they generally work is that you ask them to watch a file(.sass, .less et al.) and they compile these files on the fly. [Koala](http://koala-app.com/) is one such option for SASS and LESS.
- If you are using [VS Code](https://code.visualstudio.com/), then you can install plugins that will act as a compiler and do it for you. [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass) is an example of such an extension.

<br/><br/><br/>



# JavaScript   

**What is a Promise and how do you use it?**  
_Waiting for response_   

**Is it fine to learn JavaScript as your first language for web development or is it better to start with HTML and CSS**   
_Waiting for response_   


<br/><br/><br/>




# Performance   

**What is the best way to reduce my image file size?** 

>At minimum: use [ImageOptim](https://imageoptim.com/). It can significantly reduce the size of images while preserving visual quality. Windows and Linux [alternatives](https://imageoptim.com/versions.html) are also available.

>More specifically: run your JPEGs through [MozJPEG](https://github.com/mozilla/mozjpeg0) (q=80 or lower is fine for web content) and consider [Progressive JPEG](http://cloudinary.com/blog/progressive_jpegs_and_green_martians) support, PNGs through [pngquant](https://pngquant.org/) and SVGs through [SVGO](https://github.com/svg/svgo). Explicitly strip out metadata (--strip for pngquant) to avoid bloat. Instead of crazy huge animated GIFs, deliver [H.264](https://en.wikipedia.org/wiki/H.264/MPEG-4_AVC) videos (or [WebM](https://www.webmproject.org/) for Chrome, Firefox and Opera)! If you can’t at least use [Giflossy](https://github.com/pornel/giflossy). If you can spare the extra CPU cycles, need higher-than-web-average quality and are okay with slow encode times: try [Guetzli](https://research.googleblog.com/2017/03/announcing-guetzli-new-open-source-jpeg.html).

From the excellent [images.guide](https://images.guide/). <br/><br/>

**What is the best format for performant images? PNG? JPG? SVG?**  
> It's between SVG and JPG. It really depends on how much detail and color variation the image has. If it's a simple vector graphic (_Something like a logo or icon_) you should safely be able to go with SVG. This can be under 1k - 5k in size. If the image is more like a photo with a considerable amount of detail and colors I would go with JPG. You should only feel compelled to reach for PNG if the file has transparency.

<br/><br/><br/>




# Accessibility   

**Do I need to make my app accessible?**  
People will visit your website for a purpose. It may be reading the news, or finding a flight, you name it. Your visitors may be visually impaired, suffer from epilepsy or have trouble understanding complicated sentences. Think about these people, try imagine being them, and answer yourself a simple question: do I want to make their lifes even harder?

**How do I make my app accessible?**  

This is a big question, as accessibility (often abbreviated _a11y_) encompasses quite a lot of things from supporting screen readers and keyboard navigation, to ensuring the colors used in your designs offer an appropriate amount of contrast.

For users with visual impairments, you should ensure that your website or web app works well with screen reader software. This involves things like specifying a descripiton for images using the `alt` attribute, using semantically meaningful HTML tags like `nav`, `header`, and `main` to denote parts of your page, and so on. For other visually impaired users who may not need screen reader software, you should ensure that the colors used on your page have a good contrast ratio and avoid using fonts smaller than 14pt.

For users with motor impairments, who may have difficulty using a mouse, it's important to support keyboard navigation. For a lot of HTML elements like `input`, `button`, and `a` you get this behaviour for free, but in certain cases you may need to add `tabindex="0"` to an element's attributes to make it focusable. It's also very important that you don't remove the default styles applied to focused elements, as users using keyboard navigation heavily rely on these.

Finally, for users with hearing impairments, you should ensure that any audio you're using has a visual equivalent. This means providing closed captions or text summaries for any videos, and not relying on audio feedback to communicate things to the user.

Finally, here are some helpful resources for ensuring your site is accessible:

- The Mozilla Developer Network's [accessibility tutorials](https://developer.mozilla.org/en-US/docs/Web/Accessibility) go into gret depth on many aspects of accessibility.
- [Contrast Ratio Calculator](https://contrast-ratio.com) - A tool from Lee Veroux which helps to determine if the colours you're using in your designs offer an appropriate amount of contrast.
- [tota11y](https://khan.github.io/tota11y) - A tool from Khan Academy which helps you visualize how your site will perform with assostive technology.
- [eslint-jsx-a11y](https://www.npmjs.com/package/eslint-plugin-jsx-a11y) - An ESLint plugin which helps you spot accessibility issues with JSX code in React projects.

<br/><br/><br/>


# Node  
**Where do I find other people's Node.js code for small projects? GitHub doesn't seem to display it?**  
_Waiting for response_


<br/><br/><br/>


# React
**What are the pre requesites(excluding the general HTML, CSS, and JS) before starting off with React?**

There are no other prerequisites apart from HTML, CSS, and JS (although a good level of comfort is needed with JS). All you need is a [script tag](https://reactjs.org/docs/add-react-to-a-website.html) that pulls in React and then you can write your own React code in a simple JS file.
You can start with the official docs' [getting started](https://reactjs.org/docs/getting-started.html) page which are very beginner friendly.

