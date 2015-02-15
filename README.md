CSS-Hacks
=========

If you are trying to do pixel-perfect cross-browser CSS layout, then you have probably ran into problems with IE & other browsers.
This repository is a collection of CSS hacks that we often use to have pixel perfect design.

### Contents

* [1. CSS Browser Selector](#css-browser-selector)
* [2. Conditional Comments](#conditional-comments)
* [3. Selector Hacks](#selector-hacks)
* [4. Attribute Hacks](#attribute-hacks)
* [5. Min-Height Hack](#min-height-hack)
* [6. Transparent Images in IE6, IE7](#transparent-images)
* [7. Underscore Hack](#underscore-hack)
* [8. Overflow Hidden not working on IE7](#overflow-hidden)
* [9. Disable Textarea Resizing](#disable-text-resizing)
* [10. Disable input focus on click](#disable-focus)
* [11. Image Rollover Borders That Do Not Change Layout](#image-rollover)
* [12. Set color of selected text](#selected-text)
* [13. Disable user click on elements](#disable-user-click)


### 1. CSS Browser Selector <a name="css-browser-selector"/>

[CSS Browser Selector](http://rafael.adm.br/css_browser_selector/) is a very small javascript with just one line which empower CSS selectors. It gives you the ability to write specific CSS code for each operating system and each browser.

I strongly recommend using this script for your css fixes. You don't have to include two many css(eg. ie7.css, ie8.css) files like the way we do using conditional comments.
You can just have one stylesheet named @browserfixes.css@ and write all your style tweaks according to browser, operating system, etc.,

```css
/* Windows IE styles */
.win.ie { /* Styles to apply on Windows IE*/ }
.win.ie7 { /* Styles to apply on Windows IE7 */ }
```

### 2. Conditional Comments <a name="conditional-comments"/>

Conditional comments is a easiest way for targetting IE(Internet Explorer). These conditional comments are for IE-only and they’re not supported by any other browser. For other browsers they are just an ordinary comments and therefor, they are safe to use.

The typical usage is as follows:

```html
<!--[if IE]>    Some CssCode    <![endif]-->
```

The above code applies to all versions of Internet Explorer, i.e. 5.01, 5.5 and 6.0, but now we want to apply it to versions of Internet Explorer, i.e. 5.01, 5.5 and 6.0, so we will apply the following condition:

```html
<!--[if lte IE 6]>    Some Css Code    <![endif]-->
```
After we finish testing, we remove all hacks to separate file(s), so the main CSS is clean and tidy. This separate file is then called in the header section of a file within conditional comments.

```html
<!--[if lte IE 6]><link rel="stylesheet" type="text/css" href="ie_hacks.css" /><![endif]-->
```

Condition is one of the following:

* IE (Any version of IE)
* lt IE version (Versions less than version)
* lte IE version(Versions less than or equal to version)
* IE version (Only version)
* gte IE version (Versions greater than or equal to version)
* gt IE version (Versions greater than version)

Version is the version of Internet Explorer, typically 5, 5.5, 6, or 7, you can read more info about this at [Quirksmode](http://www.quirksmode.org/css/condcom.html).


### 3. Selector Hacks <a name="selector-hacks"/>


```css
/* IE6 and below */
* html #idname  { color: red; }

/* IE7 */
*:first-child+html #dos { color: red }

/* IE7, FF, Saf, Opera  */
html>body #tres { color: red }

/* IE8, FF, Saf, Opera (Everything but IE 6,7) */
html>/**/body #cuatro { color: red }

/* Opera 9.27 and below, safari 2 */
html:first-child #cinco { color: red }

/* Safari 2-3 */
html[xmlns*=""] body:last-child #seis { color: red }

/* safari 3+, chrome 1+, opera9+, ff 3.5+ */
body:nth-of-type(1) #siete { color: red }

/* safari 3+, chrome 1+, opera9+, ff 3.5+ */
body:first-of-type #ocho {  color: red }

/* saf3+, chrome1+ */
@media screen and (-webkit-min-device-pixel-ratio:0) {
 #diez  { color: red  }
}

/* iPhone / mobile webkit */
@media screen and (max-device-width: 480px) {
 #veintiseis { color: red  }
}

/* Safari 2 - 3.1 */
html[xmlns*=""]:root #trece  { color: red  }

/* Safari 2 - 3.1, Opera 9.25 */
*|html[xmlns*=""] #catorce { color: red  }

/* Everything but IE6-8 */
:root *> #quince { color: red  }

/* IE7 */
*+html #dieciocho {  color: red }

/* IE 10+ */
@media screen and (-ms-high-contrast: active), (-ms-high-contrast: none) {
   #veintiun { color: red; }
}

/* Firefox only. 1+ */
#veinticuatro,  x:-moz-any-link  { color: red }

/* Firefox 3.0+ */
#veinticinco,  x:-moz-any-link, x:default  { color: red  }

/* FF 3.5+ */
body:not(:-moz-handler-blocked) #cuarenta { color: red; }
```

### 4. Attribute Hacks <a name="attribute-hacks"/>

```css
/* Underscore to target - IE6 */
#once { _color: blue }

/* Asterisk to target - IE6, IE7 */
#doce { *color: blue; /* or #color: blue */ }

/* Everything but IE6 */
#diecisiete { color/**/: blue }

/* IE6, IE7, IE8, but also IE9 in some cases :( */
#diecinueve { color: blue\9; }

/* IE7, IE8 */
#veinte { color/*\**/: blue\9; }

/* IE6, IE7 -- acts as an !important */
#veintesiete { color: blue !ie; } /* string after ! can be anything */

/* IE8, IE9 */
#anotherone  {color: blue\0/;} /* must go at the END of all rules */

/* IE9, IE10 */
@media screen and (min-width:0\0) {
    #veintidos { color: red}
}
```

Thanks to Paul Irish for the Select and Attribute list.


### 5. Min-Height Hack <a name="min-height-hack"/>

In many cases we need to set some minimum height for a container & when content increses we need that to expand. If you just use <code>min-height</code> property it won't work in all browsers, In order to achieve that you need the follow the below hack.

```css
selector {
  min-height: 500px;
  height: auto !important;
  height: 500px;
}
```

### 6. Transparent Images in IE6, IE7 <a name="transparent-images"/>

IE dosn’t handle transparent PNG too well. You’ll get an ugly grayish type background wherever it’s supposed to be transparent. And we cann’t just use GIFs because aren’t good for higher resolution images. So we need a CSS hack to fix this.

* [PNG Hack/Fix for IE 6](http://css-tricks.com/snippets/css/png-hack-for-ie-6/)
* [Twin Helix Png Fix](http://www.twinhelix.com/css/iepngfix/)

### 7. Underscore Hack <a name="underscore-hack"/>

Will work only in IE5.5, IE6:

Text will be red in Internet Explorer 5.5 and Internet Explorer 6, blue in other browsers.

```css
.example{
  color: blue;
  _color: red;
}
```
### 8. Overflow Hidden not working on IE7 <a name="overflow-hidden"/>

It is a well-known bug in IE6 and IE7. To solve it, you need to add position:relative to the container. It should solve your problem.

Problem:
```html
<div style="overflow: hidden;">
  <div style="border:red 1px solid; height: 200px; overflow: auto;">
    <!-- Content in this div will be hidden in all major browsers but in IE7 it won't work  -->
  </div>
</div>
```

Solution:
```html
<div style="overflow: hidden; position: relative;">
  <div style="border: black 1px solid; height: 200px; overflow: auto;">
    <!-- This wil work in all browsers -->
  </div>
</div>
```

### 9. Disable Textarea Resizing <a name="disable-text-resizing"/>

```css
textarea {
  resize: none;
}
```

### 10. Disable input focus on click <a name="disable-focus"/>

```css
input {
  outline: none;
}
```

### 11. Image Rollover Borders That Do Not Change Layout <a name="image-rollover"/>

Usaully when you want to set a hover state for image, it will add an extra margin for border that will make your slight jumping of layout in some cases, Here is the technique to avoid such jumping on rollover.

```css
/* This technique rendering will be something like inner border */
#example-one a img, #example-one a {
    border: none;
    overflow: hidden;
    float: left;
}

#example-one a:hover {
    border: 3px solid black;
}

#example-one a:hover img {
    margin: -3px;
}
```

### 12. Set color of selected text <a name="selected-text"/>

```css
::selection {
    background: #ffb7b7; /* Safari */
}

::-moz-selection {
    background: #ffb7b7; /* Firefox */
}
```

### 13. Disable user click on elements <a name="disable-user-click"/>
```css
.example {
  pointer-events: none;
}
```

More to be updated, Stay tuned!
