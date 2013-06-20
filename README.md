# CSS Brush Up

[https://github.com/aeo/style-guide](https://github.com/aeo/style-guide)

Scott Kehr



## Which block is more expensive?

```css
body .myClass div {
  ...
}
```
```css
body div .myClass {
  ...
}
```


### CSS processes right to left

Make sure far right element is specific.



# Scalable CSS


### Wrong Way

```css
.arial {
  font: normal 11px/1.2 Arial, Helvetica, sans-serif;
}
.big {
  font-size: 15px;
}
```
```html
<h1 class="arial big">Big Font</h1>

<h2 class="arial">Normal Font</h2>
```


### Right Way

```css
.header,
.title {
  font: normal 11px/1.2 Arial, Helvetica, sans-serif;
}
.title {
  font-size: 15px
}
```
```html
<h1 class="title">Big Font</h1>

<h2 class="header">Normal Font</h2>
```



## Scoping CSS

```html
<html class="factoryBranding">
  <link href="/factory/stylesheets/brandstyles.css"/>
  <a class="button">My Button</a>
</html>
```
No need to scope if CSS is only used within scoped element


### Wrong Way
```css
.factoryBranding .button {
  ...
}
```


### Right Way
```css
.button {
  ...
}
```



## Selector Depth

```css
.main-nav ul li ul li div {
  ...
}
```

Stay away from complex selectors


### This will become increasingly important when using CSS pre-processors like Stylus
```styl
.main-nav
  ul
    li
      ul
        li
          div
```



### Undoing Styles

Don't do it.  If this is necessary, then there is probably something wrong with your original style.



### Other Bad Ideas

- Stay away from !important
- Don't use ID's for styling
- Don't prepend selectors with elements



### CSS Selector Profile

1. Open Webkit
2. Select the Profile tab
3. Select Collect CSS Selector Profile and click Start
4. Load the page and click Stop
5. Select your profile on the left



# Mobile First CSS

1. What will your styles look like on a mobile platform?
2. What could you do to improve the mobile experience?
3. Are these changes feasible?


## @media

Try basing media queries off of content instead of device display size


## flexbox

Try using flexbox for grid layouts

[Example](http://codepen.io/HugoGiraudel/embed/6448fc51f994a029be1facb87afe3b5c?type=result&height=300&safe=true#result-box)



# Stylus

[http://learnboost.github.io/stylus/](http://learnboost.github.io/stylus/)

[http://visionmedia.github.io/nib/](http://visionmedia.github.io/nib/)



# Stylus Manifests


### Old Manifest

/manifest/webcommon/category.json

```json
{
  "src": [
    "<%= common_css %>category/category.css",
    "<%= common_css %>category/brandstyles.css",
    "<%= common_css %>category/widget.css"
  ],
  "dest": "<%= common_css %>category/min/category.css"
}

```


### New Manifest

/webcommon.war/stylesheets/category/category.css

```styl
@import category
@import brandstyles
@import widget
```
