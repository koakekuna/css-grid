![](https://res.cloudinary.com/wesbos/image/upload/v1515524452/GRID-social-share_wlfzk3.png)

# CSS Grid

Hello! This repo is for tracking and documenting the lessons from Wes Bos's CSS Grid course. I plan to also include summaries of lessons learned after each topic.

## Lesson 3 - CSS Grid Fundamentals

- when you make a grid container, all of its direct children become grid items *automatically*
- but nothing is "sliced and diced" into columns and rows yet, because we still have to define them with grid-template-columns and grid-template-rows
- you can define grids with px, em, rem, %, auto, and a new unit fr 
- grid-gap adds spacing in-between the columns and rows

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
- when you define some columns with grid-template-columns, your grid items will be placed in the columns that have been defined and you'll see some vertical explicit tracks (dashed lines). 
- when you have more grid items than you have columns, then the remaining items will be placed automatically in a row beneath the first one. Even though the rows haven't been defined, they have been created and you'll see some horizontal implicit tracks (dotted lines).
- defining rows with grid-template-rows will have a similar effect
- the edges of the explicitly defined tracks are displayed with solid lines
- when we have defined both grid columns and rows, and there are excess grid items, they will be placed beyond the solid lines with implicit tracks
- use grid-auto-rows or grid-auto-columns to specify how the implicit rows/grids should be defined
  - should be able to define multiple values in near future

## Lesson 6 - CSS grid-auto-flow Explained
- determines if the implicit items are added via rows or columns
- the default is rows
- switching to columns will add items to implicitly created columns
  - can further be defined with grid-auto-columns
  - many items will create a horizontal scroll
- similar to Flexbox's flex-direction

## Lesson 7 - Sizing tracks in CSS Grid
- use the fr (fractional) unit to divvy up the amount of free space remaining
  - percentages don't take into account the grid-gaps
  - grid-template-columns: 200px 1fr 1fr will create 1 column of 200px, and two columns that each take up 50% of the remaining space (2fr total)
  - grid-template-columns: 200px 2fr 1fr will create 1 column of 200px, one column that takes up 66%, and a final column that takes up the remaining 33% (3fr total)
  - grid-templates-columns: 200px 8fr will create 1 column of 200px, and another column that takes up 100% of the remaining space (8fr/8fr = 100%)
- auto will adjust to the max size of the content
  - so an item with a lot of text will have a larger size

## Lesson 8 - CSS Grid repeat function
- instead of grid-template-columns: 1fr 1fr 1fr 1fr, use repeat(4, 1fr);
- repeat takes two values
  - first value is the multiplier
  - second value is whatever you want repeated

## Lesson 9 - Sizing Grid Items
- defining a explicit width for an item in a column will make that entire column the width, and then any other elements with fr are divvied up
- instead we can use 'grid-column: span 2' to span 2 items worth of space
- if we have 5 columns, and we define 'grid-column: span 3' on the 4th item, the item will display on the next row
- if we 'grid-column: span 10', and we only have 5 columns, it will force the item to be wider than the grid container edges (specified with the solid lines)

## Lesson 10 - Placing Grid Items
- use grid-column-start and grid-column-end to tell an item what track to start on and where to end (visually with the white number tags)
- use the shorthand for columns and rows grid-column: 3 / 5
  - you can also use span - grid-columN: 3 / span 2 to start on track 3 and span 2
- use grid-column: 1 / -1 to span the entire width
- be sure to define grid-template-rows when using grid-row: 1 / -1

