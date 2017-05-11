# SASS styleguide :bear:
A team friendly approach to working with SASS on large projects. 

## Table of content

1. [Syntax](#syntax)
	* [General recommendations](#general-recommendations)
	* [Strings](#strings)
	* [Numbers](#numbers)
2. [Selectors and BEM](#selectors-and-bem)
	* [General recommendations](#general-recommendations)
	* [BEM methodology](#bem-methodology)
3. [Properties declarations](#properties-declarations)
	* [Declaration Order](#declaration-order)
	* [Shorthand Properties](#shorthand-properties)
	* [Vendor Prefixes](#vendor-prefixes)
4. [Comments and Documentation](#comments-and-documentation)
	* [The importance of documenting](#the-importance-of-documenting)
5. [Further reading](#further-reading)

## Syntax

### General Recommendations
* Indent usign soft tabs (2 spaces) — it guarantees that code renders the same in any environment.
* Put a space before the opening brace `{` in rule declarations.
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line.
* End all properties with a semi-colon.
* Put blank lines between rule declarations.

```scss
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

### Strings
* Strings should be wrapped with single quotes `'`.
* URLs should be quoted as well -- `background-image: url('/images/kittens.jpg');`.

### Numbers
* Don't add leading zeros -- `.5em` instead of `0.5em`.
* When dealing with lengths, a 0 value should never have a unit -- `margin: 0;` instead of `margin: 0px;`.
* Always lowercase hex values -- `color: #bada55` instead of `#BADA55`.
* Top-level numeric calculations should always be wrapped in parenthese -- `width: (100% / 3);` instead of `width: 100% / 3;`.
* When performing calculations, don't treat units as strings. Think of them as algebraic symbols instead. To add a unit to a number, multiply this number by 1 unit. 

```scss
$value: 42;

// NOT recommended
$length: $value + px;

// Recommended
$length: $value * 1px;
```


## Selectors and BEM

### General Recommendations
* Do not use ID selectors.
* Use classes over tags for better performances -- `.title` instead of `h1`.
* Use hypens to separate words -- `.my-class` instead of `.myClass`
* Don't over-specify selectors -- `.alert` instead of `div.alert`.
* Avoid using broad attribute selectors (e.g. `[class^="..."]`).
* When using multiple selectors in one declaration, give each one its own line.
* Give your selectors names that reflect the **purpose** of the element, not its **look**. Those names are more understandable and less likely to change.
* Scope classes to the closest parent only when necessary (e.g., when not using prefixed classes).
* Keep your selectors as flat as possible. With SASS particularly, it is easy to get carried away. Keep your nesting to 3 levels deep max. 

### BEM Methodology

> BEM stands for Block Element Modifier, a clever and clean way to name your CSS classes. 

The point behind the BEM syntax is to provide context directly into the selector in order to make them easily understandable to anyone involved in the project. It also reduces CSS specificity by simplifying selectors. 

Here is a very basic example of the BEM syntax:
```scss
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

### Javascript hooks

Avoid binding to the same class in both your CSS and JavaScript. Using the same class for two situations leads to, time wasted during refactoring when a developer must cross-reference each class they are changing and/or developers being afraid to make changes for fear of breaking code.

Create Javascript-specific classes, prefixed with `js-`:
```
<button class="btn js-update-info">Update info</button>
```

## Properties Declarations

### Declaration Order
This order is used as a general rule. 
Within sets of properties, sort them alphabetically consistantly.

1. @include
2. CSS properties
3. Pseudo-classes, pseudo-elements
4. Nested selectors
5. Media queries

### Nested selectors
**Never** nest selectors more than three levels deep!
```scss
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```
If you end up nesting more, it probably means your CSS is:
* Strongly coupled to the HTML
* Overly specific 
* Not reusable

Again: **never** nest ID selectors!

### Shorthand properties
Use shorthand properties where possible. You might need to be specific when overriding existing properties though.

```scss
// NOT recommended
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

// Recommended 
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

### Mixins
Mixins should be used to DRY up your code, add clarity, or abstract complexity. 

### Extend directive
`@extend` should be avoided. It has unintuitive and possibly dangerous behaviour, espeacially when used in nested selectors. 

### Vendor Prefixes
Never write vendor prefixes, they are added automatically at compilation.

## Comments and Documentation
* Use line comments (// in Sass) to document within the code
* Use block comments do separate main code blocks
```
/**
 * Wrapper
 */
 .wrapper { 
    ...
 }
````
### The importance of documenting
You should write detailed comments for code that is not self-documenting: 
* Browser-specific hacks (try to avoid them anyway)
* Seemingly arbitrary numeric values
* Order of z-indexes
* Use of variables (at declaration)
* Purpose for a mixin (at declaration)
* etc.

To explain the use of a hacky/unusual properties, use an inline comment right after it.
```scss
.hacky-selector {
  *zoom: 1; // for IE 6/7 only
}
```

## Further Reading

Never stop reading ! 

### SASS
* [Sass Documentation](http://sass-lang.com/)
* [SassDoc](http://sassdoc.com/)

### BEM
* [BEM Official](https://en.bem.info/)
* [BEM 101](https://css-tricks.com/bem-101/)
* [Battling BEM: 10 Common Problems And How To Avoid Them](https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them/)

### Other styleguides
* [Airbnb](https://github.com/airbnb/css)
* [Hugo Giraudel](https://www.sitepoint.com/css-sass-styleguide/)
