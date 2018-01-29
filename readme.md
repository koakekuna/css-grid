![](https://res.cloudinary.com/wesbos/image/upload/v1515524452/GRID-social-share_wlfzk3.png)

# CSS Grid

Hello! This repo is for tracking and documenting the lessons from Wes Bos's CSS Grid course. I also include summaries of lessons learned after each topic.

Also checkout and bookmark the CSS Tricks [article](https://css-tricks.com/snippets/css/complete-guide-grid/) for a thorough explanation of all grid concepts

## Lesson 3 - CSS Grid Fundamentals

- when you make a grid container, all of its direct children become grid items *automatically*
- but nothing is "sliced and diced" into columns and rows yet, because we still have to define them with `grid-template-columns` and `grid-template-rows`
- you can define grids with px, em, rem, %, auto, and a new unit fr 
- `grid-gap` adds spacing in-between the columns and rows

## Lesson 4 - CSS Grid Dev Tools

- Firefox Dev tools has a Grid section in the layout tab
- Helpful settings:
  - Display line numbers
  - Display area names
  - Extend lines indefinitely
  - Change grid lines to black
  - Turn on OSX accessibility zoom
- Different lines mean different things:
  - explicit track - dashed line
  - implicit track - dotted line
  - gap - diagnol line
  - explicit grid edge - solid line

## Lesson 5 - Grid Implicit vs Explicit Tracks
- when you define some columns with `grid-template-columns`, your grid items will be placed in the columns that have been defined and you'll see some vertical explicit tracks (dashed lines). 
- when you have more grid items than you have columns, then the remaining items will be placed automatically in a row beneath the first one. Even though the rows haven't been defined, they have been created and you'll see some horizontal implicit tracks (dotted lines).
- defining rows with `grid-template-rows` will have a similar effect
- the edges of the explicitly defined tracks are displayed with solid lines
- when we have defined both grid columns and rows, and there are excess grid items, they will be placed beyond the solid lines with implicit tracks
- use `grid-auto-rows` or `grid-auto-columns` to specify how the implicit rows/grids should be defined
  - should be able to define multiple values in near future

## Lesson 6 - CSS grid-auto-flow Explained
- determines if the implicit items are added via rows or columns
- the default is rows
- switching to columns will add items to implicitly created columns
  - can further be defined with `grid-auto-columns`
  - many items will create a horizontal scroll
- similar to Flexbox's flex-direction

## Lesson 7 - Sizing tracks in CSS Grid
- use the fr (fractional) unit to divvy up the amount of free space remaining
  - percentages don't take into account the grid-gaps
  - `grid-template-columns: 200px 1fr 1fr` will create 1 column of 200px, and two columns that each take up 50% of the remaining space (2fr total)
  - `grid-template-columns: 200px 2fr 1fr` will create 1 column of 200px, one column that takes up 66%, and a final column that takes up the remaining 33% (3fr total)
  - `grid-templates-columns: 200px 8fr` will create 1 column of 200px, and another column that takes up 100% of the remaining space (8fr/8fr = 100%)
- auto will adjust to the max size of the content
  - so an item with a lot of text will have a larger size

## Lesson 8 - CSS Grid repeat function
- instead of `grid-template-columns: 1fr 1fr 1fr 1fr`, use `grid-template-columns: repeat(4, 1fr);`
- repeat takes two values
  - first value is the multiplier
  - second value is whatever you want repeated

## Lesson 9 - Sizing Grid Items
- defining a explicit width for an item in a column will make that entire column the width, and then any other elements with fr are divvied up
- instead we can use `grid-column: span 2` to span 2 items worth of space
- if we have 5 columns, and we define `grid-column: span 3` on the 4th item, the item will display on the next row
- if we `grid-column: span 10`, and we only have 5 columns, it will force the item to be wider than the grid container edges (specified with the solid lines)

## Lesson 10 - Placing Grid Items
- use `grid-column-start` and `grid-column-end` to tell an item what track to start on and where to end (visually with the white number tags)
- use the shorthand for columns and rows - `grid-column: 3 / 5`
  - you can also use span - `grid-column: 3 / span 2` to start on track 3 and span 2
- use `grid-column: 1 / -1` to span the entire width
- be sure to define `grid-template-rows` when using `grid-row: 1 / -1`

## Lesson 11 - Spanning and Placing Cardio
- practice using different variations of previous lessons

## Lesson 12 - auto-fit and auto-fill
- `auto-fill` will automatically generate columns/rows depending on the size of the grid. It will responsively create or remove columns as the container is adjusted as well as move the explicit grid edge to the end of the container.
- `auto-fit` will do the same, but if all the columns/rows fit in the container, the explicit grid edge will end at the last item

## Lesson 13 - minmax() for Responsive Grid
- use `minmax()` to define how little or big items can be
- useful with `auto-fit` to responsively generate items that can span the width of the grid
- use `fit-content()` to 'clamp' the item at a desired value, if auto is stretching the item too much

## Lesson 14 - Grid Template Areas
- if we have a 3 x 3 grid, we can define areas with:
  ```
  grid-template-areas:
    "sidebar-1 content sidebar-2"
    "sidebar-1 content sidebar-2"
    "footer footer footer"
  ```
- these areas will be shown visually with tags on the grid as well
- then we can specify the items to take up the area with:
  grid-area: footer
- use media queries to easily switch the areas
- you can use the area names in grid-column: 'areaname'-start / 'areaname'-end to define where the items should start or stop depending on the area

## Lesson 15 - Naming Lines in CSS Grid
- the way you can name the lines is by using square brackets like grid-template-columns: [site-left] 1fr [content-start] 500px [content-end] 1fr [site-right];
- you can also have multiple names - [site-left sidebar-start]
- then you can reference the lines - `grid-row: content-top / content-bottom;`
- devtools don't show the lines, but maybe in a future update

## Lesson 16 - grid-auto-flow dense Block Fitting
- `grid-auto-flow` by default places items too wide for the container onto the next row, sometimes leaving a huge gap
- using the dense option will have the same behavior, but it will look to see if any other items can fit in the space and fill it in

## Lesson 17 - CSS Grid Alignment + Centering
- "justify" properties are for horizontal placing and the "align" properties are for vertical placing
- `justify-items` and `align-items` aligns the content within a grid item
  - can use the shorthand `place-items` to specify both at once (but beware browser support)
- `justify-content` and `align-content` is useful if your grid is smaller than the container itself (which can happen if items are sized with px), and then you can set the alignment of the grid within the container
- `justify-self` and `align-self` is useful to overwrite the alignment on a case by case basis for each item

## Lesson 18 - Re-ordering Grid Items
- use the `order` property on specific items to rearrange them based on order
- default is `order: 0`
- don't use for content necessary for screen readers

## Lesson 19 - Nesting Grid with Album Layouts
- emmet expression for auto generating the albums (with spaces for readability)
  - base: `div > img + div > h2 + p + p + p`
  - with classes: `.album > img.album__artwork + .album__details > h2.album__title + p.album__artist + p.album__desc + p.album__desc`
  - with normal text: `.album > img.album__artwork + .album__details > h2.album__title{Album Title} + p.album__artist{Artist Name} + p.album__desc + p.album__desc`
  - with auto lorem text: `.album > img.album__artwork + album__details > h2.album__title{Album Title} + p.album__artist{Artist Name} + p.album__desc > lorem10 ^ p.album__desc > lorem20`
    - Using `p.album__desc{lorem10}` *does not* work. It will return the text "lorem10" instead of generating lorem text
    - Use `p.album__desc > lorem10` to properly generate lorem text
    - Use `p.album__desc > lorem 10 ^ p.album__desc > lorem20` to go back up a level to generate another lorem paragraph
  - with image source: `.album > img.album__artwork[src="https://source.unsplash.com/random/300x300"] + album__details > h2.album__title{Album Title} + p.album__artist{Artist Name} + p.album__desc > lorem10 ^ p.album__desc > lorem20`
  - multiplied: `(.album > img.album__artwork[src="https://source.unsplash.com/random/300x300"] + h2.album__title{Album Title} + h3.album__artist{Artist Name} + p.album__desc + p.album__desc > lorem)*10`
  - final - no spaces: `(.album>img.album__artwork[src="https://source.unsplash.com/random/300x300"]+.album__details>h2{Album Title}+p.album__artist{Artist Name}+p.album__desc>lorem10^p.album__desc>lorem20)*10`
- must specify album image with `width: 100%`
  - image from unsplash is 300px x 300px
  - firefox will autoresize the image to fit the column, but chrome will not and the image will spill outside the column
  - the container height will be 300px though, and the container will be taller than expected
  - by specifying `width: 100%` we force the image to size itself not using its natural width of 300px, but rather the available space (which is a 150px column)
  - the height will in turn kick the height to readjust since the images are proportional

## Lesson 20 - CSS Grid Image Gallery
- Use Array.from() and pass in a length property to generate an array of fixed length
  - `Array.from({ length: 50 })`