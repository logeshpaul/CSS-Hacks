CSS-Hacks
=========

If you are trying to do pixel-perfect cross-browser CSS layout, then you have probably ran into problems with IE & other browsers. 
This repository is a collection of CSS hacks that we often use to have pixel perfect design.

**1) CSS Browser Selector**

[CSS Browser Selector](http://rafael.adm.br/css_browser_selector/) is a very small javascript with just one line which empower CSS selectors. It gives you the ability to write specific CSS code for each operating system and each browser.

I strongly recommend using this script for your css fixes. You don't have to include two many css(eg. ie7.css, ie8.css) files like the way we do using conditional comments.
You can just have one stylesheet named @browserfixes.css@ and write all your style tweaks according to browser, operating system, etc.,

```css
/* Windows IE styles */
.win.ie { /* Styles to apply on Windows IE*/ }
.win.ie7 { /* Styles to apply on Windows IE7 */ }
```

**2) Conditional Comments**

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


**3) Selector Hacks:**


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

**4) Attributes**

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


**5) Min-Height**

```css
selector {
  min-height: 500px;
  height: auto !important;
  height: 500px;
}
```

**6) Transparent PNGs**

IE dosn’t handle transparent PNG too well. You’ll get an ugly grayish type background wherever it’s supposed to be transparent. And we cann’t just use GIFs because aren’t good for higher resolution images. So we need a CSS hack to fix this.

* [PNG Hack/Fix for IE 6](http://css-tricks.com/snippets/css/png-hack-for-ie-6/)
* [Twin Helix Png Fix](http://www.twinhelix.com/css/iepngfix/)

**7) Underscore hack**

Will work only in IE5.5, IE6:

Text will be red in Internet Explorer 5.5 and Internet Explorer 6, blue in other browsers.

```css
.example{
  color: blue;
  _color: red;
}
```




More to be updated, Stay tuned!
