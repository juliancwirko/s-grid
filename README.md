## Stylus Flexbox grid system

Why it is cool:

* Meteor.js integration (with Autoprefixer and Rupture on board) [https://atmospherejs.com/juliancwirko/s-grid](https://atmospherejs.com/juliancwirko/s-grid)
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

You can change the names of main classes. (read above).
But you can also extend custom classes and use ````cols()```` function to create your custom styles.

```
section
    @extend .{gridClassName}
    aside, main
        @extend .{cellClassName}
        cols(columns, columns, gutter)
    @media screen and (min-width: rem-calc(breakpoints[md]))
        aside
            cols(4, columns, gutter)
        main
            cols(8, columns, gutter)
```

You will have clean aside (4cols) and main (8cols) in 12 (default) columns grid;

### Inspired by:

* Cory Simmons: (Creator of Jeet grid system and many other grid tools) [https://github.com/corysimmons](https://github.com/corysimmons)
* Philip Walton (Solved by Flexbox): [http://philipwalton.github.io/solved-by-flexbox/demos/grids/](http://philipwalton.github.io/solved-by-flexbox/demos/grids/)
* CSS tricks: [http://css-tricks.com/snippets/css/a-guide-to-flexbox/](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* Foundation for Apps grid [http://foundation.zurb.com/apps/docs/#!/grid](http://foundation.zurb.com/apps/docs/#!/grid)

### TODO

* testing in real projects ..

### License

MIT
