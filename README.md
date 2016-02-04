# Skynet SASS styleguide

## Table of content
---
* Formatting
* Selectors
* Properties

## Formatting
---
### Indentation
Indent with 2 spaces
```
.example {
  color: blue;
}
```
### Capitalization
Use only lowercase
```
// NOT recommended
color: #BADA55
// recommended
color: #bada55
```
## Selectors
---
### Basic recommendations
Avoid IDs, they are too specific. Avoid over-qaulifying with type selectors. 

### Avoid type selectors

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
## Properties
---
### Declaration Order
Alphabetize declarations. 

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
Omit unit specification after “0” values.
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
## Further reading
---
[Google Styleguides](https://google.github.io/styleguide/htmlcssguide.xml)
