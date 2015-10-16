## Stylus Flexbox grid system

- More complex documentation: [http://stylusgrid.com](http://stylusgrid.com)
- Blog post about it: [http://julian.io/s-grid-working-with-flexible-box-layouts/](http://julian.io/s-grid-working-with-flexible-box-layouts/)

Why this grid:

* Meteor.js integration (with Autoprefixer and Rupture on board) [https://atmospherejs.com/juliancwirko/s-grid](https://atmospherejs.com/juliancwirko/s-grid)
* Gruntjs integration (with autoprefixer and many more useful Grunt tasks like wiredep, usemin, livereload) [https://github.com/juliancwirko/s-grid-grunt](https://github.com/juliancwirko/s-grid-grunt)
* There is also React boilerplate with s-Grid [https://github.com/juliancwirko/react-boilerplate](https://github.com/juliancwirko/react-boilerplate)
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
(More complex documentation: [http://stylusgrid.com](http://stylusgrid.com))

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

### Changelog

#### v1.1.0
- stack() function
- center() function
- rwd images in cells for FF fix

#### v1.0.1
- better rem-calc() function

#### v1.0.0
- refactor and api changes
- cols() is now cell()
- Grid helper classes is optional. You can import s-grid-classes.styl file if you need it.
- Functions parameters order is changed. See below.. you can use named parameters too.
