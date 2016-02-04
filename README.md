# Skynet SASS styleguide

## Table of content

* Syntax
* Selectors
* Properties
* Comments

## Structure
### Break Into As Many Small Files As Makes Sense
There is no penalty to splitting into many small files. Do it as much as feels good to the project. I know I find it easier to jump to small specific files and navigate through them than fewer/larger ones.

### Partials are named _partial.scss
This is a common naming convention that indicates this file isn't meant to be compiled by itself. It likely has dependencies that would make it impossible to compile by itself. Personally I like dashes in the "actual" filename though, like _dropdown-menu.scss.

### Locally, Compile with Source Maps
In development, it probably doesn't matter which format you compile your Sass in (e.g. expanded, compressed, etc) locally as long as you are producing source maps. 

### In Deployment, Compile Compressed
Live websites should only ever have compressed CSS. And gzipped with far-our expires headers to boot.

### Variables 
Variablize all common numbers and colors with meaning.
If you find yourself using a number other than 0 or 100% over and over, it likely deserves a variable. Since it likely has meaning and controls consistency, being able to tweak it en masse may be useful. Or a color other than black or white.

## Syntax

* Indent by soft tabs with two spaces — it's way to guarantee code renders the same in any environment.
```
.example {
  color: blue;
}
```
* Use only lowercase. Lowercase letters are much easier to discern when scanning a document as they tend to have more unique shapes.
```
// NOT recommended
color: #BADA55
// recommended
color: #bada55
```
* Include one space before the opening brace of declaration blocks for legibility.
* Place closing braces of declaration blocks on a new line.
* Include one space after `:` for each declaration.
* Each declaration should appear on its own line for more accurate error reporting.
* End all declarations with a semi-colon. The last declaration's is optional, but your code is more error prone without it.
* Don't prefix property values or color parameters with a leading zero (e.g., .5 instead of 0.5 and -.5px instead of -0.5px).
* Use shorthand hex values where available, e.g., #fff instead of #ffffff.
* Avoid specifying units for zero values, e.g., margin: 0; instead of margin: 0px;.
* Prefer dashes over camelCasing in class names. Underscores are OK if you're using BEM (see OOCSS and BEM below).
* When using multiple selectors in a rule declaration, give each selector its own line.
* Put a space before the opening brace { in rule declarations
* In properties, put a space after, but not before, the : character.
* Put closing braces } of rule declarations on a new line
* Put blank lines between rule declarations

### Strings
* To avoid any potential issue with character encoding, it is highly recommended to force UTF-8 encoding in the main stylesheet using the @charset directive. eg: @charset 'utf-8';
* TODO http://sass-guidelin.es/#strings

### Numbers
TODO http://sass-guidelin.es/#numbers

## Selectors
---
### Basic recommendations
* Avoid IDs, they are too specific. Avoid over-qualifying with type selectors.
```
// NOT recommended

// recommended
````
* When grouping selectors, keep individual selectors to a single line.
* Use classes over generic element tag for optimum rendering performance.
* Avoid using several attribute selectors (e.g., [class^="..."]) on commonly occuring components. Browser performance is known to be impacted by these.
* Keep selectors short and strive to limit the number of elements in each selector to three.
* Scope classes to the closest parent only when necessary (e.g., when not using prefixed classes).

### BEM Syntax

BEM stands for Block Element Modifier, a clever and clean way to name your CSS classes. Yes, I said classes, not IDs. I don’t use any IDs in my CSS and neither should you. Any. IDs are overkill and can lead to specificity issues. Of course, IDs are still very useful for JavaScript hooks and HTML anchors.

The point behind the BEM syntax is to provide context directly into the selector in order to make them easily understandable to anyone new to the project.

Here is a very basic example of BEM:
```
.block { }
.block--modifier { }
.block__element { }
.block__element--modifier { }
````
Learn about BEM syntax: 
* [BEM.info](https://en.bem.info/)
* [BEM 101](https://css-tricks.com/bem-101/)
* [Getting your head ’round BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax)

### Picking names
Instead of presentational or cryptic names, always use class names that reflect the purpose of the element in question, or that are otherwise generic. 

Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change. 

### Delimiters
Separate words in class names by a hyphen

### Formating
Use a space between the last selector and the declaration block. 
Always use a single space between the last selector and the opening brace that begins the declaration block. 
The opening brace should be on the same line as the last selector in a given rule. 
```
`/* Not recommended: missing space */
#video{
  margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
  margin-top: 1em;
}

/* Recommended */
#video {
  margin-top: 1em;
}
```
Separate selectors and declarations by new lines. 
```
/* Not recommended */
a:focus, a:active {
  position: relative; top: 1px;
}

/* Recommended */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```

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
