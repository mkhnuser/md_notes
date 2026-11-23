# Core CSS

## Overview

Here I note CSS fundamentals.

## Cascading

Style sheets are cascading: each next stylesheet overrides the previous one.

1. User-agent stylesheet (browser stylesheet);
2. User-specific stylesheet;
3. Site's author's stylesheet.

## Selector Specificity

Here is a rough order of selector specificity in CSS from highest priority to the lowest:

1. !important;
2. inline style;
3. id;
4. (not all!) pseudo-classes;
5. classes;
6. element selector;
7. universal selector.

If you've got multiple selectors with the same specificity, the last one applies.

## Pseudo Classes and Pseudo Elements

* `:` for classes;
* `::` for elements;

To style links, remember this mnemonic: **L**o**V**e **F**ears **HA**te: a:link, a:visited, a:focus, a:hover, a:active.

By the way, hover pseudo-class does not work on mobile devices!
Use it only for some optional styling.

## CSS Units

Here is a rough recommendation for choosing CSS units:

* Use `%` or `vh`, `vw` for width and height;
* Use `ch` to limit the length of paragraphs on your page.
* Use `rem` and `em` for margins and paddings and font sizes; or `px` as a last resort.
* Use `px` for shadows.

Usually, `16px` is the default font size. You can adjust it by using:

    html {
      font-size: 24px;
    }

So, `1rem` becomes `24px`.

## Display Property

Here are three possible values for `display` property:

* inline;
* inline-block;
* block.

`inline` elements only occupy the width and height of their content.
Only horizontal margin applies to inline elements.

`inline-block` elements don't go to a new line, compared to block elements,
but can have width and height.

## Box Model

Content -> padding -> border -> margin.

Some examples of margins:

* margin: top right bottom left;
* margin: vertical horizontal;
* margin: 2rem auto; (centers horizontally)

You can use negative margins, by the way.

## [Vertical] Margin Collapsing

Remember about margin collapsing in CSS:
the resulting vertical margin is the biggest one;
vertical margins do not add up if you have two elements side by side, for example.
Horizontal margins do, in fact, add up.

## Box sizing (box-sizing)

Here is how the resulting width of an element is calculated by default (`box-sizing: content-box`):

    left border + left padding + content width + right padding + right border

By default, width and height CSS props set content width and height.
Therefore, you may run out of space since the size of padding and border is not taken into account.
This behavior can be changed with `box-sizing: border-box`.

If `box-sizing: border-box` is set,
then padding and border size are taken into account when you specify width and height.
And so the content of an element itself may shrink.

Filling area is an area of content + padding + border.
When you specify `background-image` or `background-color` property, for example,
it occupies the filling area of a given element.

## Position Property

`position` property allows you to control how elements are positioned on the page.

## Stacking Context and Z index

Stacking Context and Z index allow you to control the layering of elements.
Z indexes are scoped to Stacking Contexts.

## Background Images

Background Images can be used for styling as well.
Your image dimension should be two or three times larger than the dimension of displayed image since browsers many times scale your images.

## Inheritance

Some properties are inherited and some are not. You can control inheritance.

## Visibility

`visibility: hidden` hides an element: it still takes up some space;
`display: none` completely removes an element - it does not take up any space.

## Content Layout

To lay out content, you use float, flexbox, and grid.
Just forget about floats as they are obsolete and focus on mastering flexbox & grid.

## Flexbox

Flexbox has the concept of main-axis and cross-axis.
You can change the direction of these axes.

Props related to the Main Axis (or rows in grid):

* flex-direction;
* justify-*;

Props related to the Cross Axis (or columns in grid):

* align-*;

https://css-tricks.com/snippets/css/a-guide-to-flexbox/

## Grid

Grid only uses column axis and row axis - you cannot change the direction of those.
Perhaps resort to flexbox since grid is too rigid.

https://css-tricks.com/complete-guide-css-grid-layout/

## Adaptive Layout

Use `max-width` property and relative units to achieve responsive layout.

To build responsive layout, you have these three strategies:

1. You adapt your design based on popular devices (iPhone, Samsung Galaxy, etc.);
2. You adapt your design based on screen width ranges;
3. You gradually adapt your design as it breaks.
