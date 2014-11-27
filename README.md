Citrine
=========

A typography library for stylus to make working with vertical rhythm a little bit easier (comes with a nice set of defaults too !).

Installation
----

`npm install citrine`

Compilation using the command line
----

```sh
stylus -u citrine -w my_file.styl
```

Compilation using gulp
----

```coffeescript
gulp        = require 'gulp'
stylus      = require 'gulp-stylus'
citrine     = require 'citrine'

gulp.task 'stylesheets', () ->
  gulp.src './src/my_file.styl'
  .pipe stylus
    use: [citrine()]
  .pipe gulp.dest('./build')

gulp.task 'watch', () ->
  gulp.watch 'src/**/*.styl', ['stylesheets']

gulp.task 'start', ['stylesheets', 'watch']
```

Usage
----

```stylus
@import 'citrine'

// Optional : Define your own settings
citrine-base-font-size = 16
citrine-base-line-height = 1.5
citrine-ratio = major-third

// Optional : Select the packages you want to include
citrine-box-sizing()
citrine-reset()
citrine-presets()

// Optional : Or simply include all of them
citrine()

p
  font-size remify(16) // converts pixel units to rem
  margin-bottom rhythm(1, 16) // add a margin equal to 1 empty line

h1
  font-size remify(ms(4, golden))
  margin-bottom rhythm(1, ms(4, golden))
  margin-left rhythm(1, ms(4, golden))
```

Available options
----
`citrine-base-font-size` : Set the base font-size for rem conversion

`citrine-base-line-height` : Set the base line-height (you can fine tune it depending on the font you use, the recommended values are between 1.4 and 1.6)

`citrine-ratio` : Set the modular scale used to calculate the presets, for a complete list, refer to the modular scales section.

`citrine-definition-list-style` : Definition lists should be `inline` or `indented` ? It's `indented` by default, but you have the ability to change it, just in case.

`citrine-blockquote-border-color` : Set the border color for quote blocks.

Available mixins
----
`citrine-box-sizing()` : Set box-sizing to border-box by default.

`citrine-reset()` : Include Eric Meyer's reset.

`citrine-preset()` : A set of defaults to help you out.


`citrine()` : Include all the above mixins.


`ms(number[, ratio])` : x value (up or down) the modular scale (or 0 to get the base font size).

`remify(font_size)` : Convert the pixel values to rem.

`rhythm(number_of_lines, font_size[, correction])` : For use in margin and paddings, it adds empty lines relative to the chosen font-size, with the ability to use a correction in pixels to help you center the elements. (For example if you have a Header with an inset box shadow of 4px, set the correction to 4).

Modular scales ratios
----

```stylus
minor-second   = 1.067
major-second   = 1.125
minor-third    = 1.2
major-third    = 1.25
perfect-fourth = 1.333
aug-fourth     = 1.414
perfect-fifth  = 1.5
minor-sixth    = 1.6
golden         = 1.618
major-sixth    = 1.667
minor-seventh  = 1.778
major-seventh  = 1.875
octave         = 2
major-tenth    = 2.5
major-eleventh = 2.667
major-twelfth  = 3
double-octave  = 4
```

Demo
----
<http://citrine.frostwind.me>

Change log
----

**0.0.7**

- It is now possible to pass a ratio as an optional parameter to ms().
- Updated README

**0.0.6**

- Added a new function (ms) to calculate the modular scale.
- Updated README

**0.0.5**

- Added new presets for definition lists, s and em tags, and block quotes.
- Improved demo.html
- Improved README

**0.0.3**

**BREAKING CHANGE** : Using citrine-presets alone while keeping the old behaviour is not possible anymore (box-sizing and reset should be called explicitely now)
Please use either citrine() to include all the packages, or refer to the Usage section to see all the available options)

License
----

The MIT License (MIT)

Copyright (c) 2014 Frostwind <hi@frostwind.me>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
