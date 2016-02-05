# Skynet SASS styleguide

A team friendly approach to working with SASS on large projects


## Table of content

1. [Syntax](#syntax)
	* [General recommendations](#general-recommendations)
	* [Strings](#strings)
	* [Numbers](#numbers)
2. [Structure](#structure)
3. [Selectors and BEM](#selectors-and-bem)
	* [General recommendations](#general-recommendations)
	* [BEM methodology](#bem-methodology)
4. [Properties declarations](#properties-declarations)
	* [Declaration Order](#declaration-order)



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
* Keep your selectors as flat as possible. With SASS particularly, it is easy to get carried away. Keep your nesting to 3 levels deep at max. 
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


## Properties Declarations

#### Declaration Order
This order is used as a general rule. 
1. Scoped variables
2. @extend
3. @include
4. Regular properties
5. Pseudo-classes, pseudo-elements
6. Nested elements
7. Media queries

#### Shorthand properties
Use shorthand properties where possible. You might need to be specific when overriding existing properties though.

```css
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

#### Vendor Prefixes
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
