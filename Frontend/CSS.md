# CSS

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

If you've got multiple selectors with the same specificity, the last one of them applies.

## Pseudo Classes and Pseudo Elements

* `:` for classes;
* `::` for elements;

To style links, remember this mnemonic: **L**o**V**e **F**ears **HA**te: a:link, a:visited, a:focus, a:hover, a:active.

By the way, hover pseudo-class does not work on mobile devices! Use it only for some optional styling.

## CSS Units

Here is a rough recommendation for choosing CSS units:

* Use `%` or `vh`, `vw` for width and height;
* Use `ch` to limit the length of paragraphs on your page.
* Use `rem` and `em` for margins and paddings and font sizes; or `px` as a last resort.

Usually, `16px` is the default font size. You can adjust it by using:

```
```
html {
  font-size: 24px;
}
```
```

Once this is done, `1rem` becomes `24px`.

## Display Property

Here are three possible values for `display` prop:

* inline;
* inline-block;
* block.

inline elements only occupy the width and height of their content. Only horizontal margin applies to inline elements.
inline-block elements don't go to a new line, but can have width and height.

## Box Model

You can use negative margins.

## [Vertical] Margin Collapsing

Remember about margin collapsing in CSS: the resulting vertical margin is the biggest one; vertical margins do not add up if you have two elements side by side, for example. Horizontal margins do add up.

## Box sizing (box-sizing)

Here is how the resulting width of an element is calculated by default (box-sizing: content-box): left border + left padding + content width + right padding + right border. By default, width and height CSS props set content width and height. Therefore, you may run out of space since the size of padding and border is not taken into account. This behavior can be changed with box-sizing: border-box. 

If you specify box-sizing: border box, then padding and border size is taken into account when you specify width and height and so the content of an element itself may shrink.

Filling area is an area of content + padding + border. When you specify background-image or background-color prop, for example, it occupies the filling area of a given element.

## Content Layout

To lay out content, you use float, flexbox, and grid. Just forget about floats as they are obsolete and focus on mastering flexbox & grid. Flexbox has the concept of main-axis and cross-axis. You can change these axes. Grid only uses column axis and row axis - you cannot change the direction of those.

## Flexbox

Props related to the Main Axis (or rows in grid):

* flex-direction;
* justify-*;

Props related to the Cross Axis (or columns in grid):

* align-*;

## Adaptive Layout

Use max-width prop and relative units to achieve responsive layout. To build responsive layout, you basically have three strategies: 

1. You adapt your design based on popular devices (iPhone, Samsung Galaxy, etc.).
2. You adapt your design based on screen width ranges.
3. You gradually adapt your design as it breaks while you are shrinking your screen (the best approach).

Your image dimension should be two or three times larger than the dimension of displayed image since browsers many times scale your images.
