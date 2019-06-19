# Typography

[![Version][version]](https://www.npmjs.com/package/@violaui/typography)
[![Travis][travis]](https://travis-ci.org/violaui/typography)
[![Size][size]](https://unpkg.com/@violaui/typography)
[![Downloads][downloads]](https://www.npmjs.com/package/@violaui/typography)
[![License][license]](https://github.com/violaui/typography/blob/master/LICENSE)

> Every typography-related stuff of the __Viola framework__ placed here.

[version]: https://img.shields.io/npm/v/@violaui/typography.svg?&logo=npm&style=flat-square
[travis]: https://img.shields.io/travis/violaui/typography.svg?&logo=travis&style=flat-square
[size]: https://img.shields.io/bundlephobia/minzip/@violaui/typography.svg?&logo=css3&label=size&style=flat-square
[downloads]: https://img.shields.io/npm/dt/@violaui/typography.svg?style=flat-square
[license]: https://img.shields.io/github/license/violaui/typography.svg?color=%23aa55aa&style=flat-square

## How to install:

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

## Usage

#### webpack

If you use webpack as your builder, the configuration of your `webpack.config.js` 
file should be something like the code below:
 
```javascript
const path = require("path")
const {peg} = require("@violaui/peg")
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
            options: {functions: peg.sassFunctions}
          }
        ]
      }
    ]
  }
}
```
>  Notice that you have to pass the `peg.sassFunctions` to the options of `sass-loader`. 
Otherwise, none of `@violaui` modules can't compile.

## Customization
If you want to customize any values of the `@violaui/typography` you can set the value of the variables that list below.

| Variable Name | Description        | Values|
| :------------ | :-------------| :-------- |
| `$primary` | A list of `font-family` names | `Helvetica, Arial, sans-serif`
| `$secondary` | A list of `font-family` names |  `Times, sans` 
| `$tertiary` | A list of `font-family` names |  `Roboto, sans-serif`
| `$primary-rtl` | A list of `font-family` names | `Tahoma, sans` or `null`
| `$secondary-rtl` | A list of `font-family` names | `Arial, sans` or `null` 
| `$tertiary-rtl` |  A list of `font-family` names | `Times, sans-serif` or `null`
| `$code` | A list of `font-family` names | `monaco, monospace`
| `$font-sizes` | A list of `font-size` with maximum items of 6 | `(1rem, 20px, 4rem, 5em, 30%, 6rem)`
| `$font-sizes-rtl` | A list of `font-size` with maximum items of 6 | `(1rem, 20px, 4rem, 5em, 30%, 6rem)` or `null`
| `$font-weights` | A list of `font-weight` with maximum items of 7 | `100 300 400 500 700 800 900`
| `$font-weights-rtl` | A list of `font-weight` with maximum items of 7 | `100 300 400 500 700 800 900` or `null`
| `$line-heights` | A list of `line-height` with maximum items of 3 | `1.2, 1.4, 1.5`
| `$line-heights-rtl` | A list of `line-height` with maximum items of 3 | `1.2, 1.4, 1.5` or `null`
| `$text-indents` |  A list of `text-indent` with maximum items of 3 | `0, 1.4em, -1.4em`
| `$text-indents-rtl` | A list of `text-indent` with maximum items of 3 | `0 1.2em -1.2em ` or `null`
| `$text-shadows` | A list of `text-shadow` with maximum items of 3 | `(1px 1px 1px rgba(0, 0, 0, 0.25)), (1px 1px 2px rgba(0, 0, 0, 0.3))`
| `$text-shadows-rtl` | A list of `text-shadow` with maximum items of 3 | `(1px 1px 1px rgba(0, 0, 0, 0.25)), (1px 1px 2px rgba(0, 0, 0, 0.3))` or `null`
| `$letter-spacings` | A list of `letter-spacing` with maximum items of 3| `0.1em -0.05em 0.25em`
| `$letter-spacings-rtl`| A list of `letter-spacing` with maximum items of 3| `0.1em -0.05em 0.25em` or `null`
| `$word-spacings` | A list of `word-spacing` with maximum items of 3 | `normal -0.15em 0.4em`
| `$word-spacings-rtl` | A list of `word-spacing` with maximum items of 3 | `normal -0.15em 0.4em` or `null`

> Notice that you should define these variables before importing the `@violaui/typography`.

For example, you can create a partial SASS file named `_variables.sass` and put all customized variables in it.

```sass
$font-sizes: (1rem, 1.2rem, 1.5rem, 2rem, 3.5rem, 6rem)
$font-sizes-rtl: (0.6rem, 1rem, 1.3rem, 2.2rem, 3.2rem, 5.8rem) 
```

#### Passing `null` value to `-rtl` variables

If you pass `null` value to any variables that ends with `-rtl`, the classes that generated for related 
properties won't support bidirectional mode and only support ltr mode.

#### Passing fewer values than what it requires

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


