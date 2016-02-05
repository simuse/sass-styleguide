# Skynet SASS styleguide

A team friendly approach to working with SASS on large projects


## Table of content

[TOC]


## Syntax

#### General Recommendations
* Indent by soft tabs with two spaces — it guarantees that code renders the same in any environment.
* Put a space before the opening brace `{` in rule declarations.
* Include a space after `:`, not before, for each property.
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line.
* End all properties with a semi-colon. It is optional, but makes it easier for errors to sneak in.
* Put blank lines between rule declarations.

```css
// NOT recommended
.mySelector{
    color:blue;
    font-size: 14px}
    
// Recommended
.my-selector {
  color: blue;
  font-size: 14px;
}
```

#### Strings
* Strings should be wrapped with single quotes`'`.
* URLs should be quoted as well -- `background-image: url('/images/kittens.jpg');`.

#### Numbers
* Don't add leading zeros -- `.5em` instead of `0.5em`.
* When dealing with lengths, a 0 value should never ever a unit -- `margin: 0;` instead of `margin: 0px;`.
* Always lowercase hex values -- `color: #bada55` instead of `#BADA55`.
* Use shorthand hex values where available -- `#fff` instead of `#ffffff`.
* Top-level numeric calculations should always be wrapped in parenthese -- `width: (100% / 3);` instead of `width: 100% / 3;`.
* When performing calculations, don't treat units as strings. Think of them as algebraic symbols instead. To add a unit to a number, you have to multiply this number by 1 unit. 

```css
$value: 42;

// NOT recommended
$length: $value + px;

// Recommended
$length: $value * 1px;
```


## Structure

TODO


## Selectors and BEM

#### General Recommendations
* Give your selectors names that reflect the purpose of the element, instead or presentational or cryptic names. Those names are more understandable and less likely to change.
* Avoid using IDs, they are too specific.
* Avoid over-qualifying with type selectors -- `.alert` instead of `div.alert`.
* Avoid using broad attribute selectors (e.g. `[class^="..."]`), it impacts browser performance.
* When writing multiple selectors on one line, give each one its own line.
* Use classes over tags for better performances -- `.title` instead of `h1`.
* Scope classes to the closest parent only when necessary (e.g., when not using prefixed classes).
* Keep your selectors as flat as possible. Max 3 levels deep.
* Use hypens to separate words -- `.my-class` instead of `.myClass`

#### BEM Methodology

BEM stands for **Block Element Modifier**, a clever and clean way to name your CSS classes. The point behind the BEM syntax is to provide context directly into the selector in order to make them easily understandable to anyone involved in the project. It also reduces CSS specificity by simplifying selectors. 

Here is a very basic example of the BEM syntax:
```css
// In vanilla CSS
.block { }
.block__element { }
.block--modifier { }

// The same thing in SASS
.block {
  &__element { }
  &--modifier { }
}
```

![BEM in action](http://skynettask.bc/wikimso/images/b/ba/BEM-01.jpg)

Learn more about BEM methodology: 
* [BEM.info](https://en.bem.info/)
* [BEM 101](https://css-tricks.com/bem-101/)
* [Getting your head ’round BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax)



### Nesting
Don’t nest deeper than 3 levels.
When selectors become this long, you're likely writing CSS that is:
* Strongly coupled to the HTML (fragile)
* Overly specific (powerful) 
* Not reusable

 Never nest ID selectors 

## Properties
---
### Declaration Order
1. Scoped variables
2. @extend
3. @include
4. Regular properties
5. Pseudo-classes, pseudo-elements
6. Nested elements
7. Media queries

Alphabetize properties.

### Shorthand properties
Use shorthand properties where possible. 
```
/* Not recommended */
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

/* Recommended */
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```
### Units
Omit unit specification after 0 values.
```
margin: 0;
padding: 0;
```
### Quotation Marks
 Use single quotation marks for attribute selectors and property values.

Use single ('') rather than double ("") quotation marks for attribute selectors or property values. Do not use quotation marks in URI values (url()). 
```
/* Not recommended */
@import url("//www.google.com/css/maia.css");

html {
  font-family: "open sans", arial, sans-serif;
}

/* Recommended */
@import url(//www.google.com/css/maia.css);

html {
  font-family: 'open sans', arial, sans-serif;
}
```

### Leading 0
Do not use put 0s in front of values or lengths between -1 and 1. 
```
font-size: .8em;
```
### Hexadecimal Notation
Use 3 character hexadecimal notation where possible. 
```
/* Not recommended */
color: #eebbcc;

/* Recommended */
color: #ebc;
```

### Formating
Always use a single space between property and value (but no space between property and colon) for consistency reasons. 
```
/* Not recommended */
h3 {
  font-weight:bold;
}

/* Recommended */
h3 {
  font-weight: bold;
}
```

### Vendor prefixes
Never write them, they are added automatically at compilation.

## Comments 
Comment as much as possible, but comment smart.
* Prefer line comments (// in Sass-land) to block comments.
* 
```
/*=======================================================================
   Section comment block
  =======================================================================*/

/* Sub-section comment block
 ====================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * TODO: This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

// inline comment
```

### Documenting
Write detailed comments for code that isn't self-documenting: 
* Uses of z-index
* Compatibility or browser-specific hacks

## Further reading
* [Google Styleguides](https://google.github.io/styleguide/htmlcssguide.xml)
* [Nesting in Sass and Less](http://markdotto.com/2015/07/20/css-nesting/)
* [Name Your SASS Variables Modularly](http://webdesign.tutsplus.com/tutorials/quick-tip-name-your-sass-variables-modularly--webdesign-13364)
* [SASS guidelines](http://sass-guidelin.es/)
