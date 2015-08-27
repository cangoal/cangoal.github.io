---
layout: post
title: "Notes for CSS Mastery"
date: 2015-08-26
---

Background will apply to **content** area and **padding** area.

When two or more vertical margins meet, they will collapse to form a single margin. The height of this margin will equal the height of the larger of the two collapsed margins. 
When one element is contained within another element, assuming there is no padding or border separating margins, their top and/or bottom margins will also collapse together the **larger** of the two collapsed margins.
Margins can even collapse on themselves. Say you have an empty element with a margin but no border or padding. In this situation, the top margin is touching the bottom margin, and they collapse together.

Margin collapsing only happens with the **vertical margins** of **block boxes** in the normal flow of the document. Margins between **inline boxes**, **floated**, or **absolutely positioned boxes** never collapse.

There are three basic positioning schemes in CSS: **normal flow**, **floats**, and **absolute positioning**.

Block-level boxes will appear vertically one after the other.

Inline boxes are laid out in a line horizontally. Their horizontal spacing can be adjusted using horizontal padding, borders, and margins.

Most boxes are formed from explicitly defined elements. However, there is one situation where a block-level element is created even if it has not been explicitly defined—when you add some text at the start of a block-level element like a div.
```html
  <div>
    some text
    <p> some more text</p>
  </div>
```
When you clear an element, the browser adds enough margin to the top of the element to push the element’s top border edge vertically down, past the float.

Background images always sit on the top of the background color, so when the image runs out the color will be displayed.

If you set a background position using **pixels** or **ems**, the top-left corner of the image is positioned from the top-left corner of the element by the specified number of pixels. So if you were to specify a vertical and horizontal position of 20 pixels, the top-left corner of the image will appear 20 pixels from the top-left corner of the element. However, background positioning using **percentages** works slightly differently. Rather than positioning the top-left corner of the background image, percentage positioning uses a corresponding point on the image. So if you set a vertical and horizontal position of 20 percent, you are actually positioning a point 20 percent from the top left of the image, 20 percent from the top left of the parent element

RGBa is a mechanism for setting color and opacity in one go. RGB stands for “Red,” “Green,” and “Blue,” while the “a” stands for “alpha transparency.”

One of the biggest benefits of the **PNG** file format is its support for **alpha transparency**.

IE 6 Conditional comment:
```html
  <!--[if ie 6]>
  <link rel="stylesheet" type="text/css" href="ie6.css"/>
  <![endif]-->
```
To ensure your pages are as accessible as possible, **it is always a good idea to add a:focus pseudo-class to your links when defining hover states**. This will allow your links to take on the same styles when they are tabbed to using the keyboard as they have when hovered over using the mouse.
```css
  a:hover, a:focus { color: red;}
```

It’s a good idea to apply your link styles in the following order: a:link, a:visited, a:hover, a:focus, a:active'
“Lord Vader Hates Furry Animals”
The reason for this is the casacde which means: when two rules have the same specificity, the last rule to be defined wins out. Take following example:
This is the correct one:
```css
  a:link, a:visited {text-decoration: none;}
  a:hover, a:focus, a:active {text-decoration: underline;}
```
This is the wrong one:
```css
  a:hover, a:focus, a:active {text-decoration: underline;}
  a:link, a:visited {text-decoration: none;}
```
In this situation, both rules have the same specificity so the :link and :visited styles will override the :hover and :active styles

Links should only ever be used for GET requests, and never for POST requests.

There are several ways to make parent elements contain floated children. 
One method is to add a clearing element. Unfortunately, this adds unnecessary markup to the page so should be avoided if possible. 
Another other method is to float the parent element as well and clear it further down the line, say, using the site footer. The third method it to use the overflow:hidden technique.

To make the list items **line up horizontally instead of vertically** you could set their display property to inline. However for more complex horizontal list styling you will gain more control if you float the items and then use margins to space the space them out instead.

Legends are notoriously difficult to style because of the inconsistent way browsers place them. Some browsers, like Firefox and Safari, use padding to create a small indent. However, other browsers, such as Opera and IE, have large default indents that are not controllable using padding, margins, or even positioning.

The id attribute is required to create the association between the **form input** and the **label**, while the name is required so that the **form data can be sent back to the server**.

Changing the cursor style of the label to pointer is a good idea here, as it shows that the labels can be interacted with.
``` html
  <div>
    <label for="author">Name:</label>
    <input name="author" id="author" type="text" />
  </div>
```
```css
  label {
    display: block;
    cursor: pointer;
  }
```
Many operating systems, like OS X, prevent authors from changing the style of their input buttons, preferring to keep consistency throughout the operating system. However, the **button element** doesn’t suffer from these constraints.

The main limitation with button elements is the way IE 6 and, to a lesser extent, IE 7 handle their submission. Rather than submitting the contents of the value attribute, as other browsers do, IE 6 and IE 7 submit the contents of the element. Furthermore, if you have multiple buttons on a page, IE 6 will submit the contents of all the buttons, rather than just the one that was clicked. As such, if you wanted to use more than one button per page, you need to make sure that they all have the same function, as you won’t be able to tell which one had been activated in older version of Internet Explorer.

All these CSS layout techniques rely on three basic concepts: **positioning**, **floating**, and **margin manipulation**.

IE misunderstands ```css text-align: center ```, centering everything instead of just the text, which is an advantage we can use.

Normally, when people create float-based layouts, they float both columns left and then create a gutter between the columns using margin or padding.When using this approach, the columns are packed tightly into the available space with no room to breathe.Although this wouldn’t be a problem if browsers behaved themselves, buggy browsers can cause tightly packed layouts to break, forcing columns to drop below each other.To prevent your layouts from breaking, you need to avoid cramming floated layouts into their containing elements. Rather than using horizontal margin or padding to create gutters, you can create a virtual gutter by floating one element left and one element right.If one element inadvertently increases in size by a few pixels, rather than immediately running out of horizontal space and dropping down, it will simply grow into the virtual gutter.

For images that need to span a wide area, such as those found in the site header or branding areas, consider using a **background image** rather than an **image element**. As the branding element scales, more or less of the background image will be revealed.

Most problems with margin collapsing can be fixed by **adding a small amount of padding or a thin border** with the same color as the background of the element.
