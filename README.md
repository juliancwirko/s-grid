## Stylus Flexbox grid system

Why it is cool:

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
@import 's-grid'
```

## Usage

You should use it with Autoprefixer [https://github.com/jenius/autoprefixer-stylus](https://github.com/jenius/autoprefixer-stylus)
Package for Meteor.js is bundled with it.

### You can use it like a block grid. For example:

```
<div class="s-grid-top s-grid-sm-12 s-grid-md-6 s-grid-lg-4 s-grid-xlg-3 s-grid-xxlg-2">
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio, doloribus!
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae!
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Architecto sed, rerum ratione at modi sunt!
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, repellendus!
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet.
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet.
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, repellendus!
    </div>
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet.
    </div>
</div>
```
#### You can align all cells vertically by using:

* ````s-grid-top````
* ````s-grid-center````
* ````s-grid-bottom````
* ````s-grid-stretch````

#### You can also add:

* ````s-grid-justify-center```` - centering all columns horizontally

### If you want different cells sizes You can use it like for example:

```
<div class="s-grid-top s-grid-justify-center">
    <div class="s-grid-cell s-grid-cell-sm-12 s-grid-cell-md-12 s-grid-cell-lg-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio, doloribus!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-12 s-grid-cell-md-12 s-grid-cell-lg-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-12 s-grid-cell-md-6 s-grid-cell-lg-12">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Architecto sed, rerum ratione at modi sunt!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-6 s-grid-cell-md-6 s-grid-cell-lg-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, repellendus!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-6 s-grid-cell-md-12 s-grid-cell-lg-6">
        Lorem ipsum dolor sit amet.
    </div>
</div>
```

#### You can also use offsets here, just add classes like:

* ````s-grid-cell-offset-sm-2````
* ````s-grid-cell-offset-lg-3````
* ````s-grid-cell-offset-xxlg-6````
* ..etc

### Nested grids

You should be able to use nested grids. Example:

```
<div class="s-grid-top s-grid-sm-4 s-grid-justify-center">
    <div class="s-grid-cell">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio, doloribus!
    </div>
    <div class="s-grid-cell">
        <div class="s-grid-top s-grid-sm-6 s-grid-justify-center">
            <div class="s-grid-cell">
                Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vitae, dicta?
            </div>
            <div class="s-grid-cell">
                Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ea esse molestiae odit iusto at sapiente dicta reiciendis doloremque optio, atque!
            </div>
        </div>
    </div>
</div>
```

### Grid direction:

#### You can change direction of the grid cells. To do so, just add one more class:

* ````s-grid-column```` (from top to bottom)
* ````s-grid-column-reverse```` (from bottom to top)
* ````s-grid-row```` (from left to right - default)
* ````s-grid-row-reverse```` (from right to left)

**If you use column direction (top to bottom or bottom to top) you can control your main s-grid container height. Width of the container should be dynamic or you can set overflow-x: auto on it.**

&nbsp;

#### Grid direction example 1:
&nbsp;
```
<div style="max-height: 400px; overflow-x: auto;" class="s-grid-top s-grid-column s-grid-sm-12 s-grid-md-6 s-grid-lg-4 s-grid-xlg-3 s-grid-xxlg-2">
    <div class="s-grid-cell">
        1 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio, doloribus!
    </div>
    <div class="s-grid-cell">
        2 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid quae sint sapiente distinctio error molestias officiis tenetur porro perferendis doloribus!
    </div>
    <div class="s-grid-cell">
        3 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis, perspiciatis!
    </div>
    <div class="s-grid-cell">
        4 Lorem ipsum dolor sit.
    </div>
    <div class="s-grid-cell">
        5 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ratione, architecto.
    </div>
    <div class="s-grid-cell">
        6 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci minus laboriosam nisi vero, est dignissimos.
    </div>
    <div class="s-grid-cell">
        7 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, repellendus!
    </div>
    <div class="s-grid-cell">
        8 Lorem ipsum dolor sit amet.
    </div>
</div>
```
&nbsp;

#### Grid direction example 2:
&nbsp;
```
<div class="s-grid-top s-grid-row-reverse s-grid-sm-12 s-grid-md-6 s-grid-lg-4 s-grid-xlg-3 s-grid-xxlg-2">
    <div class="s-grid-cell">
        1 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio, doloribus!
    </div>
    <div class="s-grid-cell">
        2 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid quae sint sapiente distinctio error molestias officiis tenetur porro perferendis doloribus!
    </div>
    <div class="s-grid-cell">
        3 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis, perspiciatis!
    </div>
    <div class="s-grid-cell">
        4 Lorem ipsum dolor sit.
    </div>
    <div class="s-grid-cell">
        5 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ratione, architecto.
    </div>
    <div class="s-grid-cell">
        6 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Adipisci minus laboriosam nisi vero, est dignissimos.
    </div>
    <div class="s-grid-cell">
        7 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, repellendus!
    </div>
    <div class="s-grid-cell">
        8 Lorem ipsum dolor sit amet.
    </div>
</div>
```

### Overwrite settings

You can overwrite settings, just place your settings after ````s-grid-settings```` import. Do something like this:

```
@import 's-grid-settings'

// my new settings goes here:

base-font-size = 16            // base font size it is 16px by default it is used to calculate rem sizes
gutter = 20px                  // gutters size
columns = 12                   // how many columns you need in your grid
gridClassName = 's-grid'       // main grid wraper class name
cellClassName = 's-grid-cell'  // main grid cell class name

breakpoints = {                // media queries breakpoints
    sm: 0,
    md: 640px,
    lg: 1200px,
    xlg: 1440px,
    xxlg: 1920px
}

@import 's-grid-functions'
@import 's-grid'

// my app styles here
```

### Cells reordering

You can use standard Flexbox order features. Example:

stylus:
```
.item
    order 1

.my-special-item
    order 0
```

html:
```
<div class="s-grid-top s-grid-justify-center">
    <div class="s-grid-cell s-grid-cell-sm-3 item">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio, doloribus!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-3 item">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-3 my-special-item">
        It should be first!
    </div>
    <div class="s-grid-cell s-grid-cell-sm-3 item">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque, repellendus!
    </div>
</div>
```

So ````my-special-item```` element should be first now.

### So many ugly classes..

Yes I know :) It could be simpler, but sometimes it is good to have namespace.
You can change the names of main classes. (read above).
You can also extend custom classes and use ````cols()```` function to create your custom styles. (Semantic approach)

```
section
    grid()
    aside, main
        grid-cell()
        cols(columns, columns, gutter)
    @media screen and (min-width: rem-calc(breakpoints[md]))
        aside
            cols(columns / 3, columns, gutter)
        main
            cols((columns / 3) * 2, columns, gutter)
```

```html
<section>
    <aside>
        Lorem ipsum dolor sit amet.
    </aside>
    <main>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Earum enim perferendis aspernatur neque, repellat ducimus laborum iure, eos inventore omnis vitae provident mollitia quisquam quibusdam! Eveniet earum nostrum, adipisci. Veritatis aliquid cum maxime fugit perspiciatis maiores, at doloribus? Tempore quisquam cum officia. Similique, itaque earum officia, minus animi at harum porro placeat aliquam ducimus dolor, quia eius accusamus doloremque odit?
    </main>
</section>
```

You will have clean aside (4cols) and main (8cols) in 12 (default) columns grid.
Go and see which classes you can extend: [https://github.com/juliancwirko/s-grid/blob/master/s-grid.styl](https://github.com/juliancwirko/s-grid/blob/master/s-grid.styl)

&nbsp;

### Sortable (drag and drop) js plugins integration

There is a default test config with jQuery UI Sortable and RubaXa Sortable here:

* [sortable-test.s-grid.meteor.com](http://sortable-test.s-grid.meteor.com/)

It definately needs more tests. I want to play with masonry layouts too. Based on Flexbox and also in cooperation with other masonry like js plugins.

### Inspired by:

* Cory Simmons: (Creator of Jeet grid system and many other grid tools) [https://github.com/corysimmons](https://github.com/corysimmons)
* Philip Walton (Solved by Flexbox): [http://philipwalton.github.io/solved-by-flexbox/demos/grids/](http://philipwalton.github.io/solved-by-flexbox/demos/grids/)
* CSS tricks: [http://css-tricks.com/snippets/css/a-guide-to-flexbox/](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* Foundation for Apps grid [http://foundation.zurb.com/apps/docs/#!/grid](http://foundation.zurb.com/apps/docs/#!/grid)

### TODO

* testing in real projects ..

### License

MIT
