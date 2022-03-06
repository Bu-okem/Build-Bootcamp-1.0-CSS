# Build Bootcamp 1.0 CSS
### Anatomy of a CSS rule

A CSS rule is made up of a (1)selector, (2)property and (3)value

	.header(1) {
		background-color(2): blue(3);
	}

If the same property is used more than once in a given rule, the last definition in the rule is processed

```
.header {
	background-color: blue;
	background-color: red;
}
```
_This element will have a red background_


### Comments
Comments in CSS are written using a combination of the forward slash and asterisk (/* */)
```
/* This is a comment */
```

### How CSS is used
#### Inline styles
These are styles written in the html file using the style attribute
```
   <div style="background-color: red;">
	   Cascading Style Sheet
   <div>
```
	
#### Style blocks
These styles are also written in the html document but in style blocks inside the `<head>` tag

	
	
	<!DOCTYPE html>
	<html lang="en">
	  <head>
	    <style>
		div {
		  background-color: green;
		}
	    </style>
	  </head>
	  <body>
	    <div></div>
	  </body>
	</html>
	
	
	
#### External Style sheets
These are styles written outside the html document in it's own file, with the .css extension. This is then linked to the html document through the link tag
	   
	   
```
<!DOCTYPE html>
<html lang="en">
  <head>
	<link rel="stylesheet" href="style.css" />  
  </head>
  <body>
    <div></div>
  </body>
</html>
```
	   

### How CSS works in the browser
#### DOM (Document Object Model)
This is a tree of objects that represents the elements in the document and their structure and heirarchy.


#### CSSOM
This is a representation of the heirarchy of the styles in the document. DOM and CSSOM are quite similar, however, CSSOM is a seperate structure from the DOM.


#### The Render Tree
This is a combination of the DOM and the CSSOM, which contains all the data the browser needs to render the page


## CSS Selectors
#### The Universal Selector (*)
This is used to select all elements in the document.

```
* {
  margin: 10px;
}
```
	   
_This will apply a margin of 10px to all elements in the document_



#### Element Selectors (h1, p, etc.)
This is used to select a html element by it's tag name.
```   
p {
  font-size: 10px;
}
```
	   
_This will apply a font size of 10px to all elements with the `<p>` tag in the document_

	   
	   
#### ID Selectors (#)
HTML elements have an ID attribute. By the HTML specification, there should be only one element with a given ID. However, if there are multiple elements with the same id, the browser will match the rule with all the elements having that ID.
   
```
#chapter_header {
  padding: 20px;
}
```
	   
	   
_This rule will apply a padding on elements with the #chapter_heading id._

***ie. The class selector is best used for selecting multiple elements.***

	   
#### Class selectors(.)
HTML elements can also have a class attribute, which can be used to target all the elements of a similar type. HTML elements can have any number of classes in the class attribute.

```
.title {
  background-color: black;
  color: white;
}
```	   

_This rule will affect every element with the class, `.title`._


#### Attribute Selectors
This is specified using square brackets ([ ]) and can take several forms
- [name] = This selects all the elements with the given attribute

- [name="value"] = selects all the elements that have the given attribute, whose value is string value 

- [name~="value"] = selects all the elements that have the given attribute, whose value contains the string value seperated by whitespace

- [name*="value"] = selects all the elements that have the given attribute, whose value contains the substring value

- [name^="value"] = selects all the elements that have the given attribute, whose value begins with value

- [name$="value"] = selects all the elements that have the given attribute, whose value ends with value


These selectors can be combined to make the selector more specific

```
div.chapter_header {
  padding: 20px;
}
```


A CSS rule can have multiple selectors by simply seperating them with commas.

```	   
.chapter_header,
.title_header {
  padding: 20px;
}
```
	   

### Selector combinators
Combinators, combined with selectors can be used to select more specific elements
 #### Descendant Combinator 
 This is specified with a space
 ```
 .header div
 ```
 _This targets all divs that are descendants (direct or indirect children) of elements with class header_
 
 
 #### Child Combinator 
 This is specified with `>`
 ```
 .header > div
 ```
 _This targets all divs that are direct children of elements with class header_
 
 #### General Sibling combinator 
 This is specified with ~
 ```
 .header ~ div
 ```
 _This targets all divs that are siblings of elements with class header_
 
 #### Adjacent Sibling combinator 
 This is specified with +
 ```
 .header + div
 ```
 _This targets all divs that are immediate siblings of elements with class header_
 
## Specificity
This is the hierarchy in which rules are applied based on the selector used

In order of preference
- Inline Styles in an lements style attribute
- ID selectors
- Class selectors, attribute selectors and pseudo-classes
- Element selectors


## Basic CSS concepts
### The box model 
![The Box Model]/box-model.png

Elements in CSS are treated as a rectangular box made up of four major parts
- margin
- border 
- padding 
- content

 - Padding (space between an element's content and it's border)
 - Margin (space between an element's border and other elements)

- Block and Inline Elements
There are two types of HTML elements, block and inline elements

Block elements always appear on their own line and takes up the full width of their containing element. The default height is set to fit the height of it's content eg <div>are 

Inline elements are rendered inside the normal flow of text and take up enough height and width for the content in them. Their height and width can't be changed explicitlye

- Units 
 - px
 - em (relative to the font size of the element)
 
	 .title {
		font-size: 20px;
		padding: 0.5em;
	}

In this rule, the font size is set to 20px, so 0.5em equals 20 x 0.5 = 10px


 - rem (relative to the base font size of the browser)
 If the base font size of the browser is 16px (it is in most cases), 0.5rem will equal 16 x 0.5 = 8px
 
 - % (percentage)
 This is the percentage of the width of the direct parent
	   
	   
	 .parent {
		font-size: 60px;
	}

	.child {
		font-size: 20%;
	}
	   
	   

The font-size of elements with the child class equals 20% of 60px = 12px
 
 - vw (viewport width)
 This is the current width of the browser
 Therefore 30vw equals 30% of the current width of the browser
 
 - vh (viewport height)
 This is the current height of the browser
  Therefore 40vh equals 40% of the current height of the browser
  
  Some CSS properties do not require units eg. opacity. They just use integers.


 
Basic Styling
- Box Shadow (X offset, Y offset, Blur Radius, Spread Radius)

Backgrounds (Solid colors, images or gradients) and Gradients
- Solid background colors (background-color)
- Background Images (background-image)
- Gradients (Linear gradients, radial gradients)

Fonts
 - font-size, font-weight

Layout and Positioning
- 

Positioning
The positioning property determines the position of elements. The top, right, bottom and left properties are used to determine an element's position. The default position for every element is static
- Static (The default position)
- Relative
When an element's position is set to relative, other elements in the document are not affected and it's change in position is relative to it's self.

	   
	.title {
		postion: relative;
		top: 30px;
	}
	   

This rule sets the element 30px away from the top of it's original position

- Absolute
When an element's position is set to absolute, other elements in the document flow are affected and it's change in position is relative to the closest surrounding relative parent element.

```	   
.title {
	postion: absolute;
	top: 30px;
}
```	   

This rule sets the element 30px away from the top of closest surrounding relative parent


Z-index (stacking order of elements along the z-index, which element is on top of which)
