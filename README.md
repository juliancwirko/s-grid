## sGrid - Flexbox Grid System for Stylus

sGrid is a Flexbox grid system built with Stylus CSS preprocessor. It is prepared to use with helper classes, like Bootstrap or Foundation does it, but also in a more semantic way by using special Stylus functions.

It has many integrations like Meteor, Grund and React.

- More complex documentation: [http://stylusgrid.com](http://stylusgrid.com)
- Blog post: [sGrid - Working with Flexible Box layouts](http://julian.io/s-grid-working-with-flexible-box-layouts/)
- Blog post: [My workflow with the Stylus and Flexbox grid system](https://medium.com/@juliancwirko/my-workflow-with-the-stylus-and-flexbox-grid-system-5f4f50ac3f33)
- Article on Sitepoint.com: [Introducing sGrid: A Stylus-based Flexbox Grid System](http://www.sitepoint.com/introducing-sgrid-a-stylus-based-flexbox-grid-system/)

## Instalation

This is a standard Npm package so you can use it standalone, but you can also use it with boilerplates for Grunt and React. Also with Meteor.

## Usage

- [Npm](http://stylusgrid.com/npm.html)
- [Meteor](http://stylusgrid.com/meteor.html)
- [React Boilerplate](http://stylusgrid.com/react.html)
- [Grunt Boilerplate](http://stylusgrid.com/grunt.html)

You should use it with Autoprefixer [https://github.com/jenius/autoprefixer-stylus](https://github.com/jenius/autoprefixer-stylus) Package for Meteor is bundled with it. It is also configured in Grunt and React boilerplates.

You'll find more complex documentation and examples here: [http://stylusgrid.com/](http://stylusgrid.com).

### Simple examples

#### With only sGrid functions

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

#### You can achieve the same effect with helper classes

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

You can overwrite the settings (from `s-grid-settings.styl` file), just place your settings after `s-grid-settings` import. Do something like this:

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

Let me know if something is wrong with sGrid, its website or React, Grunt boilerplates. I'm sure that there is much more to do with it.

### Known problems

- In IE and probably also in Edge in many cases you should read this: [https://github.com/philipwalton/flexbugs](https://github.com/philipwalton/flexbugs)
- In IE 11 there is for sure a bug described here: [https://github.com/philipwalton/flexbugs#7-flex-basis-doesnt-account-for-box-sizingborder-box](https://github.com/philipwalton/flexbugs#7-flex-basis-doesnt-account-for-box-sizingborder-box) you can solve it by providing another content wrapper as it is described in 'Workaround' point 2

### License

MIT

### Changelog

#### v1.2.0
- center(width, padding) improvements - thanks to [@Splendorr](https://github.com/Splendorr). New use cases: center(1200px, 15px) ; center(80%, 5%)

#### v1.1.2
- helper classes fix

#### v1.1.1
- docs update

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
