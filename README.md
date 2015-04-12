## Stylus Flexbox grid system

<<<<<<< HEAD
More complex documentation: [http://s-grid.meteor.com](http://s-grid.meteor.com)

Why this grid:
=======
[Blog post about it](http://julian.io/s-grid-working-with-flexible-box-layouts/)

Why it is cool:
>>>>>>> 507b1d7d7448409b215cd6484de8ec0412201b5c

* Meteor.js integration (with Autoprefixer and Rupture on board) [https://atmospherejs.com/juliancwirko/s-grid](https://atmospherejs.com/juliancwirko/s-grid)
* Gruntjs integration (with autoprefixer and many more useful Grunt tasks like wiredep, usemin, livereload) [https://github.com/juliancwirko/s-grid-grunt](https://github.com/juliancwirko/s-grid-grunt)
* Helper grid classes. You can also create your own or just use Stylus functions to create clean styles
* Very light
* You can integrate it with Stylus Autoprefixer and other plugins
* It uses css calc() [http://caniuse.com/#search=calc](http://caniuse.com/#search=calc)
* It uses css Flexbox [http://caniuse.com/#search=flexbox](http://caniuse.com/#search=flexbox)

## Instalation

Install it:

```
$ npm install -g s-grid
```

Then in your main *.styl file import:

```
@import 's-grid-settings'
@import 's-grid-functions'
@import 's-grid-classes'
```

## Usage

You should use it with Autoprefixer [https://github.com/jenius/autoprefixer-stylus](https://github.com/jenius/autoprefixer-stylus)
Package for Meteor.js is bundled with it.

### Version 1.0.0 breaking changes

- cols() is now cell()
- Grid helper classes is optional. You can import s-grid-classes.styl file if you need it.
- Functions parameters order is changed. See below.. you can use named parameters too.

### Simple examples
(More complex documentation: [http://s-grid.meteor.com](http://s-grid.meteor.com))

#### With only functions

**Stylus code**:
```css
section
    grid()
    div
        padding rem-calc(15)
        cell(1, 4)
        &.other-cell
            cell(2, 4, 'bottom')
        &.different-cell
            cell(1, 3, g: 30px)
```

**HTML code**:
```html
<section>
    <div>Lorem ipsum</div>
    <div>Lorem ipsum</div>
    <div class="other-cell">Lorem ipsum</div>
    <div>Lorem ipsum</div>
    <div class="different-cell">Lorem ipsum</div>
</section>
```

#### With only helper classes

**HTML code**:
```
<section class="s-grid-top">
    <div class="s-grid-cell s-grid-cell-md-6">Lorem ipsum</div>
    <div class="s-grid-cell s-grid-cell-md-6">Lorem ipsum</div>
    <div class="s-grid-cell s-grid-cell-bottom s-grid-cell-md-12">Lorem ipsum</div>
    <div class="s-grid-cell s-grid-cell-md-6">Lorem ipsum</div>
    <div class="s-grid-cell s-grid-cell-center s-grid-cell-md-4 s-grid-cell-offset-md-4">Lorem ipsum</div>
</section>
```

### S-Grid functions and classes
(More complex documentation: [http://s-grid.meteor.com](http://s-grid.meteor.com))

#### Functions

- **rem-calc(value)** - calculates rem units.
    - Usage example:
        - `rem-calc(20)`
        - `rem-calc(20px)`
- **grid(direction = 'row', cells-align = 'top', justify = '')** Main grid function.
    - Params:
        - `direction`:
            - `'row'` (default) - cells direction left to right
            - `'row-reverse'` - cells direction right to left
            - `'column'` - cells direction top to bottom
            - `'column-reverse'` - cells direction bottom to top
        - `cells-align` (works only with row and row-reverse directions)
            - `'top'`
            - `'bottom'`
            - `'center'`
            - `'stretch'`
        - `justify`
            - `'start'` - justify all content left or top
            - `'end'` - justify all content right or bottom
            - `'center'` - justify all content center
    - Usage examples:
        - `grid()`
        - `grid('row')`
        - `grid('row-reverse', 'bottom')`
        - `grid(direction: 'column')`
        - `grid(direction: 'column', justify: 'end')`
- **cell(i = 1, cols = columns, align = '', g = gutter)**
    - Params:
        - `i / cols` - fraction
        - `align`:
            - `'top'`
            - `bottom'`
            - `'center'`
        - `g` - gutter
    - Usage examples:
        - `cell(1, 2)`
        - `cell(15, 45, 'top', 30px)`
        - `cell(2, 3, g: 30)`
- **cell-offset(i = 1, cols = columns, g = gutter)**
    - Params:
        - `i / cols` - fraction
        - `g` - gutter
    - Usage examples:
        - `cell-offset(1, 6)`
- **[Rupture](https://github.com/jenius/rupture) media queries**
    - Usage examples:
        - `+above(rem-calc(breakpoints[lg]))`
        - `+below(rem-calc(768px))`
        - `+below(768px)`

#### Helper classes

To use helper classes you need to import `s-grid-classes.styl` file. (Like shown above). You can change main classes name in settings. See how in 'Overwrite settings'.

**Main grid classes**:

- `.s-grid-top` - align cells top
- `.s-grid-bottom` - align cells bottom
- `.s-grid-center` - align cells center (middle)
- `.s-grid-stretch` - stretch cells
- `.s-grid-justify-center` - justify content center
- `.s-grid-justify-start` - justify content top or left
- `.s-grid-justify-end` - justify content bottom or right
- `.s-grid-row` - cells direction left to right
- `.s-grid-row-reverse` - cells direction right to left
- `.s-grid-column` - cells direction top to bottom
- `.s-grid-column-reverse` - cells direction bottom to top

**Main cell classes**:

- `.s-grid-cell-top` - single cell align top
- `.s-grid-cell-center` - single cell align center (middle)
- `.s-grid-cell-bottom` - single cell align bottom

You can also use autogenerated grid helper classes like those from Bootstrap or Foundation. By default you have 12 column based grid. You can change it in settings. See how in 'Overwrite settings'.

**S-Grid generated helper classes**:

- **Pattern: .{gridClass}-{breakpoint-symbol}-{number-of-columns}** - use it on main grid container (block grid)
    - Usage examples:
        - `.s-grid-sm-6`
        - `.s-grid-md-4`
        - `.s-grid-lg-3`
- **Pattern: .{cellClass}-{breakpoint-symbol}-{number-of-columns}** - use it on cell element (custom cell size)
    - Usage examples:
        - `.s-grid-cell-sm-12`
        - `.s-grid-cell-xlg-3`
        - `.s-grid-cell-md-6`
- **Pattern: .{cellClass}-offset-{breakpoint-symbol}-{number-of-columns}** - use it on cell element (offset class)
    - Usage examples:
        - `.s-grid-cell-offset-sm-2`
        - `.s-grid-cell-offset-lg-3`

### Overwrite settings

You can overwrite the settings (from s-grid-settings.styl file), just place your settings after `s-grid-settings` import. Do something like this:

```bash

// main s-grid settings file:

@import 's-grid-settings'

// my new settings goes here:

base-font-size = 16            // base font size it is 16px by default it is used to calculate rem sizes
gutter = 20px                  // gutters size
columns = 12                   // how many columns you need in your grid (usage with helper classes)
gridClassName = 's-grid'       // main grid wraper class name (usage with helper classes)
cellClassName = 's-grid-cell'  // main grid cell class name (usage with helper classes)

breakpoints = {                // media queries breakpoints
    sm: 0,
    md: 640px,
    lg: 1200px,
    xlg: 1440px,
    xxlg: 1920px
}

// s-grid imports:

@import 's-grid-functions'
@import 's-grid-classes'

// ...
// my app styles here..
// ...
```

&nbsp;

### Inspired by:

* Cory Simmons: (Creator of Jeet grid system and many other grid tools) [https://github.com/corysimmons](https://github.com/corysimmons)
* Philip Walton (Solved by Flexbox): [http://philipwalton.github.io/solved-by-flexbox/demos/grids/](http://philipwalton.github.io/solved-by-flexbox/demos/grids/)
* CSS tricks: [http://css-tricks.com/snippets/css/a-guide-to-flexbox/](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* Foundation for Apps grid [http://foundation.zurb.com/apps/docs/#!/grid](http://foundation.zurb.com/apps/docs/#!/grid)

### License

MIT
