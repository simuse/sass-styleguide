# SASS styleguide

A team friendly approach to working with SASS on large projects.


## Table of content

1. [Structure](#structure)
	* [Project folder](#project-folder)
2. [Syntax](#syntax)
	* [General recommendations](#general-recommendations)
	* [Strings](#strings)
	* [Numbers](#numbers)
3. [Selectors and BEM](#selectors-and-bem)
	* [General recommendations](#general-recommendations)
	* [BEM methodology](#bem-methodology)
4. [Properties declarations](#properties-declarations)
	* [Declaration Order](#declaration-order)
	* [Shorthand Properties](#shorthand-properties)
	* [Vendor Prefixes](#vendor-prefixes)
5. [Comments and Documentation](#comments-and-documentation)
	* [The importance of documenting](#the-importance-of-documenting)
	* [Using SassDoc](#using-sassdoc)
	* [Example of a SassDoc comment](#example-of-a-sassdoc-comment)
6. [Further reading](#further-reading)


## Structure

#### Project folder

All Sass related files are located in: `resources/static/` with the following file/directory structure: 
* `config.rb` - compass configuration file
* `/sass` - sass folder
* `/images` - images

/!\ TODO /!\ Document the structure precisely, based on the existing structure and what we can adapt for the new project.


## Syntax

#### General Recommendations
* Indent by soft tabs with two spaces — it guarantees that code renders the same in any environment.
* Put a space before the opening brace `{` in rule declarations.
* Include a space after `:`, not before, for each property.
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line.
* End all properties with a semi-colon. It is optional, but makes it easier for errors to sneak in.
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

#### Strings
* Strings should be wrapped with single quotes `'`.
* URLs should be quoted as well -- `background-image: url('/images/kittens.jpg');`.

#### Numbers
* Don't add leading zeros -- `.5em` instead of `0.5em`.
* When dealing with lengths, a 0 value should never ever a unit -- `margin: 0;` instead of `margin: 0px;`.
* Always lowercase hex values -- `color: #bada55` instead of `#BADA55`.
* Use shorthand hex values where available -- `#fff` instead of `#ffffff`.
* Top-level numeric calculations should always be wrapped in parenthese -- `width: (100% / 3);` instead of `width: 100% / 3;`.
* When performing calculations, don't treat units as strings. Think of them as algebraic symbols instead. To add a unit to a number, you have to multiply this number by 1 unit. 

```scss
$value: 42;

// NOT recommended
$length: $value + px;

// Recommended
$length: $value * 1px;
```


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

![BEM in action](http://skynettask.bc/wikimso/images/b/ba/BEM-01.jpg)

Learn more about BEM methodology: 
* [BEM.info](https://en.bem.info/)
* [BEM 101](https://css-tricks.com/bem-101/)
* [Getting your head ’round BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax)


## Properties Declarations

#### Declaration Order
This order is used as a general rule. Within sets of properties (be it includes or regular), try sorting them alphabetically consistantly.

1. Scoped variables
2. @extend
3. @include
4. Regular properties
5. Pseudo-classes, pseudo-elements
6. Nested elements
7. Media queries

#### Shorthand properties
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

#### Vendor Prefixes
Never write them, they are added automatically at compilation.


## Comments and Documentation

#### The importance of documenting
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

#### Using SassDoc
>[SassDoc](http://sassdoc.com/) is to Sass what JSDoc is to JavaScript: a documentation system to build pretty and powerful docs in the blink of an eye. 
>

SassDoc is an `npm` task that generates documentation for your Sass projects. It uses the same kind of syntax as Doxygen. 
You can annotate elements in your code with `@` attributes.
Functions, mixins, placeholders and variables are the most important items to annotate.

Here are just a few useful annotations: 
* [@author](http://sassdoc.com/annotations/#author) - describes the author of the documented item
* [@example](http://sassdoc.com/annotations/#example) - describes a use case for the documented item
* [@output](http://sassdoc.com/annotations/#output) - provide a description of what’s being printed by the mixin
* [@parameter](http://sassdoc.com/annotations/#parameter) - describes a parameter of the documented item
* [@see](http://sassdoc.com/annotations/#see) - describes an item that is somehow related to the documented item
* [@todo](http://sassdoc.com/annotations/#todo) - defines any task to do regarding the documented item
* [...](http://sassdoc.com/annotations/)


#### Example of a SassDoc comment

```scss
/**
 * Add padding to the element - this example is not particularly useful
 *
 * @param {String} $param The padding value to use
 * @example scss
 *     .element {
 *       @include pad(10px)
 *     }
 * @output css
 *     .element {
 *       padding: 10px;
 *     }
 * @since 1.0
 */
@mixin pad(param: 50px) {
  padding: $param;
}
```


## Further Reading

Never stop reading ! 

* [Sass Documentation](http://sass-lang.com/)
* [Compass Documentation](http://compass-style.org/)
* [SMACSS Architecture](https://smacss.com/)
* [BEM 101](https://css-tricks.com/bem-101/)
* [SassDoc](http://sassdoc.com/)







