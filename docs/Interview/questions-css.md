# Interview - CSS

## Concepts

### Accessibility

1. Text readable
Font-size should be between 15 and 18px.
Line-height 1.2 or 1.5.
Align text to left or right - text-align: justify.
Paragraph width (45-85 characters) max-width: 65ch;

2. Skip links
For skip sections.

3. Hiding content
Sometimes it makes sense to display content visually, but hide it from screen readers, for example when you’re using icons.

```
<span class="icon icon-hamburger" aria-hidden="true"></span>
```

4. The minimum contrast ratio
5. Outline
6. Styles for links (active, hover, visited)

## Questions

### How CSS code is parsing by browsers?

> Browsers match selectors from rightmost (key selector) to left.

Browsers filter out elements in the DOM according to the key selector and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector.

Hence avoid key selectors that are tag and universal selectors. They match a large number of elements and browsers will have to do more work in determining if the parents do match.

For example with this selector p span, browsers firstly find all the `<span>` elements and traverse up its parent all the way up to the root to find the `<p>` element. For a particular `<span>`, as soon as it finds a `<p>`, it knows that the `<span>` matches and can stop its matching.

`BEM` (Block Element Modifier) methodology recommends that everything has a single class, and, where you need hierarchy, that gets baked into the name of the class as well, this naturally makes the selector efficient and easy to override.

<https://developers.google.com/web/fundamentals/performance/rendering/>

### What is CSS selector specificity and how does it work?

Is the set of the rules applied to CSS selectors in order to determine which style is applied to an element.

From the most important:

1. inline css style
2. id attribute
3. class, pseudo-class, attribute
4. elements

### Difference between `reseting` and `normalizing` styles?

`reseting` - set up the same value for all elements: headers, margins, font-sizes, paddings. Prefered if the  page is very custom.

`normalizing` - correct browsers differences, bugs and preserves useful default styles

### Have you ever used a grid system, and if so, what do you prefer?

Before Flex became popular (around 2014), the float-based grid system was the most reliable because it still has the most browser support among the alternative existing systems (flex, grid). Bootstrap was using the float approach until Bootstrap 4 which switched to the flex-based approach. As of writing (2020), flex is the recommended approach for building grid systems and has decent browser support.

For the adventurous, they can look into CSS Grid Layout, which uses the shiny new grid property; it is even better than flex for building grid layouts and will be the de facto way to do so in the future.

### How can we style `SVG` elements?

Basic elements: `stroke`, `fill`.

```html
<rect
  x="10"
  y="10"
  width="100"
  height="100"
  stroke="blue"
  fill="purple"
  fill-opacity="0.5"
  stroke-opacity="0.8"
/>
```

### Types of @media properties

all - for all media type devices
print - for printers
speech - for screenreaders that "reads" the page out loud
screen - for computer screens, tablets, smart-phones etc.

### Advantages/disadvantages of CSS preprocessors?

Advantages:

- CSS is made more maintainable.
- Easy to write nested selectors.
- Variables for consistent theming. Can share theme files across different projects.
- Mixins to generate repeated CSS.
- Sass features like loops, lists, and maps can make configuration easier and less verbose.
- Splitting your code into multiple files. CSS files can be split up too but doing so will require an HTTP request to download each CSS file.

Disadvantages:

- Requires tools for preprocessing. Re-compilation time can be slow.
- Not writing currently and potentially usable CSS. For example, by using something like postcss-loader with webpack, you can write potentially future-compatible CSS, allowing you to use things like CSS variables instead of Sass variables. Thus, you're learning new skills that could pay off if/when they become standardized.

### CSS `display` property, examples and description

- `none`, `block`, `inline`, `inline-block`, `flex`, `grid`, `table`, `table-row`, `table-cell`, `list-item`.

| `display` | Description |
| :-- | :-- |
| `none` | Does not display an element (the elementv no longer affects the layout of the document). All child element are also no longer displayed. The document is rendered as if the element did not exist in the document tree |
| `block` | The element consumes the whole line in the block direction (which is usually horizontal) |
| `inline` | Elements can be laid out beside each other |
| `inline-block` | Similar to `inline`, but allows some `block` properties like setting `width` and `height` |
| `table` | Behaves like the `<table>` element |
| `table-row` | Behaves like the `<tr>` element |
| `table-cell` | Behaves like the `<td>` element |
| `list-item` | Behaves like a `<li>` element which allows it to define `list-style-type` and `list-style-position` |

### Difference between `block` and `inline-block` display properties

|  | `block` | `inline-block` | `inline` |
| --- | --- | --- | --- |
| Size | Fills up the width of its parent container. | Depends on content. | Depends on content. |
| Positioning | Start on a new line and tolerates no HTML elements next to it (except when you add `float`) | Flows along with other content and allows other elements beside it. | Flows along with other content and allows other elements beside it. |
| Can specify `width` and `height` | Yes | Yes | No. Will ignore if being set. |
| Can be aligned with `vertical-align` | No | Yes | Yes |
| Margins and paddings | All sides respected. | All sides respected. | Only horizontal sides respected. Vertical sides, if specified, do not affect layout. Vertical space it takes up depends on `line-height`, even though the `border` and `padding` appear visually around the content. |
| Float | - | - | Becomes like a `block` element where you can set vertical margins and paddings. |

### Difference between `block` and `inline-block` display properties

|  | `block` | `inline-block` | `inline` |
| --- | --- | --- | --- |
| Size | Fills up the width of its parent container. | Depends on content. | Depends on content. |
| Positioning | Start on a new line and tolerates no HTML elements next to it (except when you add `float`) | Flows along with other content and allows other elements beside it. | Flows along with other content and allows other elements beside it. |
| Can specify `width` and `height` | Yes | Yes | No. Will ignore if being set. |
| Can be aligned with `vertical-align` | No | Yes | Yes |
| Margins and paddings | All sides respected. | All sides respected. | Only horizontal sides respected. Vertical sides, if specified, do not affect layout. Vertical space it takes up depends on `line-height`, even though the `border` and `padding` appear visually around the content. |
| Float | - | - | Becomes like a `block` element where you can set vertical margins and paddings. |

### Have you played around with the new CSS Flexbox or Grid specs?

Yes. Flexbox is mainly meant for 1-dimensional layouts while Grid is meant for 2-dimensional layouts.

Flexbox solves many common problems in CSS, such as vertical centering of elements within a container, sticky footer, etc. Bootstrap and Bulma are based on Flexbox, and it is probably the recommended way to create layouts these days. Have tried Flexbox before but ran into some browser incompatibility issues (Safari) in using `flex-grow`, and I had to rewrite my code using `inline-blocks` and math to calculate the widths in percentages, it wasn't a nice experience.

Grid is by far the most intuitive approach for creating grid-based layouts (it better be!) but browser support is not wide at the moment.
