# Typography

[![Version][version]](https://www.npmjs.com/package/@violaui/typography)
[![Travis][travis]](https://travis-ci.org/violaui/typography)
[![Downloads][downloads]](https://www.npmjs.com/package/@violaui/typography)
[![License][license]](https://github.com/violaui/typography/blob/master/LICENSE)

The **typography** module of the ViolaUI  

[version]: https://img.shields.io/npm/v/@violaui/typography.svg?&logo=npm&style=flat-square
[travis]: https://img.shields.io/travis/violaui/typography.svg?&logo=travis&style=flat-square
[downloads]: https://img.shields.io/npm/dt/@violaui/typography.svg?style=flat-square
[license]: https://img.shields.io/github/license/violaui/typography.svg?color=%23aa55aa&style=flat-square

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
 

- [Installation](#installation)
- [Configuring build systems](#configuring-build-systems)
  - [webpack](#webpack)
- [Usage](#usage)
  - [Classes list](#classes-list)
  - [Sample code](#sample-code)
- [Customization](#customization)
  - [Properties](#properties)
    - [`font-family`](#font-family)
    - [`font-size`](#font-size)
    - [`font-weight`](#font-weight)
    - [`line-height`](#line-height)
    - [`text-indent`](#text-indent)
    - [`text-shadow`](#text-shadow)
    - [`letter-spacing`](#letter-spacing)
    - [`word-spacing`](#word-spacing)
  - [Passing `null` value to `-rtl` variables](#passing-null-value-to--rtl-variables)
  - [Passing fewer values than what it requires](#passing-fewer-values-than-what-it-requires)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->
 
## Installation

```bash
$ npm i --save-dev @violaui/typography
```

__or__

```bash
$ yarn add @violaui/typography --dev
```

>If you want to use pre-defined values of `@violaui/typography` variables or you don't want to use any build system 
like __webpack__ or __gulp__, you can use the CDN link, and add it to the `<head>` element of your page.

```html
<link href="https://unpkg.com/@violaui/typography/css/typography.min.css" rel="stylesheet">
```
## Configuring build systems

### webpack

If you use webpack as your builder, the configuration of your `webpack.config.js` 
file should be something like the code below:
 
```javascript
const path = require("path")
const {peg} = require("@violaui/peg") // <-- you should add this line
const MiniCssExtractPlugin = require("mini-css-extract-plugin")
module.exports = {
  mode: "development",
  entry: "./style/main.scss",
  output: {
    path: path.resolve(__dirname, "css"),
  },
  plugins: [
    new MiniCssExtractPlugin({filename: "main.css"}),
  ],
  module: {
    rules: [
      {
        test: /\.s(a|c)ss$/,
        use: [
          MiniCssExtractPlugin.loader,
          "css-loader",
          {
            loader: "sass-loader",
            options: {
              functions: peg.sassFunctions  // <-- and you should set the functions value
            }
          }
        ]
      }
    ]
  }
}
```
>  Notice that you have to pass the `peg.sassFunctions` to the options of `sass-loader`. 
Otherwise, none of `@violaui` modules can't compile.

## Usage
For using the typography module, you need to add the classes that you want to the element that you want. 

These are the generated classes of the typography module:

### Classes list

`.primary` `.scondary` `.teriary` `.code`
 
`.f1` `.f2` `.f3` `.f4` `.f5` `.f6`

`.f-thin` `.f-light` `.f-regular` `.f-medium` `.f-bold` `.f-extra-bold` `.f-black`

`.i`

`.tl` `.tr` `.tc` `.tj` `.ts` `.te` 

`.tt-none` `.tt-cap` `.tt-low` `.tt-upp`

`.no-underline` `.underline` `.strike` 

`.no-indent` `.indent` `.outdent` 

`.text-clip` `.ellipsis`

`.t-shadow-1` `.t-shadow-2` `.t-shadow-3`

`.vertical-base` `.vertical-m` `.vertical-t` `.vertical-b` 

`.lh1` `.lh2` `.lh3` 

`.letter-normal` `.letter-dense` `.letter-sparse` 

`.word-normal` `.word-dense` `.word-sparse` 

`.writing-h` `.writing-vrl` `.writing-vlr` 

`.nowrap` `.pre-only` `.pre-wrap` `.pre-line`

### Sample code

```html
<p class="primary f4 f-medium letter-sparse tt-cap ts">
	ViolaUI is a direction-agnostic and mobile-first UI toolkit
</p>
```

In this sample, the paragraph has the primary font with 4th font size.
Also, it has a little boldness and a little space between its letter.
The sentence transforms to capitalize form and at the end, 
the alignment of the text set to start, in this case, left. However,
if you add the `.rtl` class to its class list, the alignment change to the right.
 
## Customization
If you want to customize any values of the `@violaui/typography` you can set the value of the variables that list below.
### Properties

#### `font-family`

You can change the default value of `font-family` classes by changing these variables: 

* `$primary`
* `$primary-rtl`
* `$secondary`
* `$secondary-rtl`
* `$tertiary`
* `$tertiary-rtl`
* `$code`

You can assign a list of font names to each variable. All three `-rtl` variables can have the `null` value.

```sass
$primary: Arial 'Segoe UI' serif
$primary-rtl: null
```

#### `font-size`

You can change the default value of `font-size` classes by changing these variables:

* `$font-sizes`
* `$font-sizes-rtl`

These two variables can have at most 6 items and exceeded values omit at compile time.

#### `font-weight`

You can change the default value of `font-weight` classes by changing these variables:

* `$font-weights`
* `$font-weights-rtl`

These two variables can have at most 7 items and exceeded values omit at compile time.
The 7 provided values assigned to its corresponding names

> __thin, light, regular, medium, bold, extra-bold, black__

#### `line-height`

You can change the default value of `line-height` classes by changing these variables:

* `$line-heights`
* `$line-heights-rtl`

These two variables can have at most 3 items and exceeded values omit at compile time.

#### `text-indent`

You can change the default value of `text-indent` classes by changing these variables:

* `$text-indents`
* `$text-indents-rtl`

These two variables can have at most 3 items and exceeded values omit at compile time.

The 3 provided values assigned to its corresponding names

> __no-indent, indent, outdent__ 

#### `text-shadow`

You can change the default value of `text-shadow` classes by changing these variables:

* `$text-shadows`
* `$text-shadows-rtl`

These two variables can have at most 3 items and exceeded values omit at compile time.

#### `letter-spacing`

You can change the default value of `letter-spacing` classes by changing these variables:

* `$letter-spacings `
* `$letter-spacings-rtl`

These two variables can have at most 3 items and exceeded values omit at compile time.

The 3 provided values assigned to its corresponding names

> __letter-normal, letter-dense, letter-sparse__ 
  

#### `word-spacing`

You can change the default value of `word-spacing` classes by changing these variables:

* `$word-spacings`
* `$word-spacings-rtl`

These two variables can have at most 3 items and exceeded values omit at compile time.

The 3 provided values assigned to its corresponding names
  
> __word-normal, word-dense, word-sparse__


_**Notice that you should define these variables before importing the `@violaui/typography`.**_

For example, you can create a partial SASS file named `_variables.sass` and put all customized variables in it.

```sass
$font-sizes: 1rem, 1.2rem, 1.5rem, 2rem, 3.5rem, 6rem
$font-sizes-rtl: 0.6rem, 1rem, 1.3rem, 2.2rem, 3.2rem, 5.8rem 
```

### Passing `null` value to `-rtl` variables

If you pass `null` value to any variables that ends with `-rtl`, the classes that generated for related 
properties won't support bidirectional mode and only support ltr mode.

### Passing fewer values than what it requires

If you pass fewer values that a variable requires, ViolaUI uses the last value of the sequence for the 
rest of the classes of that property.

For example, if you pass 3 values for the `$font-sizes` variable, instead of 6:

```sass
$font-sizes: (1rem, 1.2rem, 1.5rem)
```  

you get the following result:

```css
.f1 {font-size: 1rem;}
.f2 {font-size: 1.2rem;}
.f3 {font-size: 1.5rem;}
.f4 {font-size: 1.5rem;}
.f5 {font-size: 1.5rem;}
.f6 {font-size: 1.5rem;}
```


