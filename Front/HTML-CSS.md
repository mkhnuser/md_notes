Here is a rough order of selector specificity in CSS from highest priority to the lowest:
!important;
inline style;
id;
(not all!) pseudo-classes;
classes;
element selector;
universal selector.
If you've got multiple selectors with the same specificity, the last one of them applies.

Here is how the resulting width of an element is calculated by default (box-sizing: content-box): left border + left padding + content width + right padding + right border. By default, width and height CSS props set content width and height. Therefore, you may run out of space since the size of padding and border is not taken into account. This behavior can be changed with box-sizing: border-box. If you specify box-sizing: border box, then padding and border size is taken into account when you specify width and height and so the content of an element itself may shrink.

Filling area is an area of content + padding + border. When you specify background-image or background-color prop, for example, it occupies the filling area of a given element.

Remember about margin collapsing in CSS: the resulting margin the biggest one; they do not add up.

There are multiple types of boxes in CSS: block, inline, inline-block. Inline elements occupy only the space they need. Only horizontal margin applies to inline elements. Height and width property do not apply to inline elements. Inline-block elements is a mix of block and inline elements: they only occupy the space they require and you can manipulate their dimensions easily.

To lay out content, you use float, flexbox, and grid. Just forget about floats as they are obsolete and focus on mastering flexbox & grid. Flexbox has the concept of main-axis and cross-axis. You can change these axes. Grid only uses column axis and row axis - you cannot change the direction of those.

To style links, remember this mnemonic: **L**o**V**e **F**ears **HA**te: a:link, a:visited, a:focus, a:hover, a:active.

Use max-width prop and relative units to achieve responsive layout. To build responsive layout, you basically have three strategies: 1. You adapt your design based on popular devices (iPhone, Samsung Galaxy, etc.). 2. You adapt your design based on screen width ranges. 3. You gradually adapt your design as it breaks while you are shrinking your screen (the best approach).

Your image dimension should be two or three times larger than the dimension of displayed image since browsers many times scale your images.