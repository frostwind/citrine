Citrine
=========

A typography library for stylus to make working with vertical rhythm a little bit easier (comes with a nice set of defaults too !).

Installation
----

`npm install citrine`

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
```

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

Modular scales
----

You can find a complete list of the ratios in `_ratios.styl`

Change log
----

**0.0.3**

BREAKING CHANGE : Using citrine-presets alone while keeping the old behaviour is not possible anymore (box-sizing and reset should be called explicitely now)
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
