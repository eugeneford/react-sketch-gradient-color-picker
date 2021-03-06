<p align="center">
  <img src="https://raw.githubusercontent.com/eugeneford/collit/master/.github/collit-logo.png" width="100" height="100">
</p>

<h3 align="center">
  Collit
</h3>

<p align="center">
  A modern JavaScript library delivering fast and modular color utils.
</p>

<p align="center">
  <a href="https://travis-ci.org/eugeneford/collit">
    <img src="https://travis-ci.org/eugeneford/collit.svg?branch=master" alt="Build Status">
  </a>
  <a href='https://coveralls.io/github/eugeneford/collit?branch=master'>
    <img src='https://coveralls.io/repos/github/eugeneford/collit/badge.svg?branch=master' alt='Coverage Status' />
  </a>
  <a href='https://www.npmjs.com/package/collit'>
    <img src='https://img.shields.io/npm/v/collit.svg' alt='NPM Version' />
  </a>
</p>

## Basic Overview
Collit is a modern JavaScript library delivering fast and modular color utils.

> Our mission is to create a complete, fast, modular and well-documented library for any kind of color operations
  (eg. parsers, converters, transformers, manipulation etc.).

Library can be used both in Node.js and directly in Browser.
It is well-documented and completely covered with test specs (excluding webpack bundling definitions and expressions).

If you want to add some features or to suggest any idea, feel free — [contributions are always welcome](#contributing-to-collit).

## What Included
There are several modules available in Collit so far:
* [Converter](#converter) — convert one specific color format into another. (Hex, RGB, HSL)
* [Validator](#validator) — validate CSS color values eg. #000, rgb(0,0,0), rgba(0,0,0,1), hsl(0,0%,0%) etc.
* [Parser](#parser) — parse CSS color values to [Color](#color-object) objects.

## How to Install
#### Using NPM
To use Collit with NPM simply call:
```js
npm install --save collit
```

#### In Browser
To use Collit directly in browser simply download this repository and copy dist/collit.js into your project.
Next, include it on your .html page:
```html
<script src="path/to/your/js/collit.js"></script>
```

## Get Started
You are able to use Collit as the importable npm package or directly in browser.

#### In Node.js
```js
import { Parser } from "collit";

var color = Parser.parseRgb("rgb(128,128,128");
// color => { hex: "#808080", rgb: {r:128, g:128, b:128}, hsl: {h:0, s:0, l:0.5}}
```

#### In Browser
```html
<script>
var Parser = Collit.Parser;

var color = Parser.parseRgb("rgb(128,128,128");
// color => { hex: "#808080", rgb: {r:128, g:128, b:128}, hsl: {h:0, s:0, l:0.5}}
</script>
```

## Converter
Convert one specific color format into another. (Hex, RGB, HSL).

### hexToRgb(hex)
Converts an HEX color value to RGB.

```js
import Converter from "collit"; // or var Converter = Collit.Converter if using in browser

var rgb = Converter.hexToRgb("#333"); // rgb => {r:51, g:51, b: 51};
```

### hexToHsl(hex)
Converts an HEX color value to HSL.
> Converting hex to hsl is done using a additional converting to RGB. HEX -> RGB -> HSL.

```js
import Converter from "collit"; // or var Converter = Collit.Converter if using in browser

var hsl = Converter.hexToHsl("#333"); // hsl => {h: 0, s: 0, l: 0.2};
```

### rgbToHex(rgb)
Converts an RGB color value to HEX.
```js
import Converter from "collit"; // or var Converter = Collit.Converter if using in browser

var hex = Converter.rgbToHex({r: 51, g: 51, b: 51}); // hex => "#333";
```

### rgbToHsl(rgb)
Converts an RGB color value to HSL.
```js
var hsl = Converter.rgbToHsl({r: 11, g: 11, b: 11}); // hsl => {h: 0, s: 0, l: 0.04};
```

### hslToHex(hsl)
Converts an HSL color value to Hex.
> Converting hsl to hex is done using a additional converting to RGB. HSL -> RGB -> HEX.

```js
import Converter from "collit"; // or var Converter = Collit.Converter if using in browser

var hex = Converter.hslToHex({h: 0, s: 0.5, l: 0.3}); // hex => "#732626;
```

### hslToRgb(hsl)
Converts an HSL color value to RGB.
```js
import Converter from "collit"; // or var Converter = Collit.Converter if using in browser

var rgb = Converter.hslToRgb({h: 300, s: 0.5, l: 0.5}); // rgb => {r: 191, g: 64, b: 191};
```

## Validator
Validator Helper that allows you to check if color is defined as a correct hex, rgb, rgba, hsl, hsla CSS string or gradient defined correctly.

### isColorName(name)
Check if target name is a valid CSS1, CSS2.1, CSS3 color name
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isColor = Validator.isColorName("black"); // true
var isNotColor = Validator.isColorName("avadakedavra"); // false
```

### isHex(color)
Check if target string is a valid hex color
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isHex = Validator.isHex("#333"); // true
var isNotHex = Validator.isHex("#rgb"); // false
``` 

### isRgb(color)
Check if target string is a valid css rgb color definition
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isRgb = Validator.isRgb("rgb( 0, 0, 0 )") // true
var isNotRgb = Validator.isRgb("hsl( 0, 0, 100% )") // false
```

### isHsl(color)

Check if target string is a valid css HSL color definition
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isHsl = Validator.isHsl("hsl(0,0%,0%)") // true
var isNotHsl = Validator.isHsl("hsl( 0, 5, 100% )") // false
```

### isRgba(color)
Check if target string is a valid css rgba color definition
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isRgba = Validator.isRgba("rgba(255,255,255,.5)") // true
var isNotRgba = Validator.isRgba("hsla(255,100%,100%,.5)") // false
```

### isHsla(color)
Check if target string is a valid css HSLa color definition
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isHsla = Validator.isHsla("hsla(0,0%,0%, .5)") // true
var isNotHsla = Validator.isHsla("hsl( 0, 5, 100% )") // false
```

### isColor(color)
Check if target string is a valid css color definition
```js
import Validator from "collit"; // or var Validator = Collit.Validator if using in browser

var isColor = Validator.isColor("hsla(0,0%,0%, .5)") // true
var isColorToo = Validator.isColor("black") // true
var isNotColor = Validator.isColor("color") // false
```

## Parser
Parser Helper allows you to parse a CSS based color definition into the ColorInfo object, which contains a hex, rgb and hsl values of target css value.

### parseColorName(name)
Parse a valid CSS1, CSS2.1, CSS3 color name into a set of hex, rgb and hsl values.
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseColorName("black");
// color => { hex: "#000", rgb: {r:0, g:0, b:0}, hsl: {h:0, s:0, l:0}}
```

### parseHex(color)
Parse a valid hex color into a set of hex, rgb and hsl values
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseHex("#000");
// color => { hex: "#000", rgb: {r:0, g:0, b:0}, hsl: {h:0, s:0, l:0}}
```

### parseRgb(color)
Parse a valid css rgb color into a set of hex, rgb and hsl values
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseRgb("rgb(128,128,128");
// color => { hex: "#808080", rgb: {r:128, g:128, b:128}, hsl: {h:0, s:0, l:0.5}}
```

### parseHsl(color)
Parse a valid css hsl color into a set of hex, rgb and hsl values
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseHsl("hsl(240,100%,50%");
// color => { hex: "#00f", rgb: {r:0, g:0, b:255}, hsl: {h:240, s:1, l:0.5}}
```

### parseRgba(color)
Parse a valid css rgba color into a set of hex, rgb and hsl values
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseRgba("rgba(255,0,0,.5)");
// color => { hex: "#f00", rgb: {r:255, g:0, b:0, a: 0.5}, hsl: {h:0, s:1, l: 0.5, a: 0.5} }
```

### parseHsla(color)
Parse a valid css hsla color into a set of hex, rgb and hsl values
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseRgba("hsla(0,255,0,.5)");
// color => { hex: "#0f0", rgb: {r:0, g:255, b:0, a: 0.5}, hsl: {h:120, s:1, l: 0.5, a: 0.5} }
```

### parseColor(color) 
Parse a valid css color into a set of hex, rgb and hsl values
```js
import Parser from "collit"; // or var Parser = Collit.Parser if using in browser

var color = Parser.parseColor("hsla(0,255,0,.5)");
// color => { hex: "#0f0", rgb: {r:0, g:255, b:0, a: 0.5}, hsl: {h:120, s:1, l: 0.5, a: 0.5} }

var anotherColor = Parser.parseColor("rgba(255,0,0,.5)");
// color => { hex: "#f00", rgb: {r:255, g:0, b:0, a: 0.5}, hsl: {h:0, s:1, l: 0.5, a: 0.5} }

var oneMoreColor = Parser.parseColor("black");
// color => { hex: "#000", rgb: {r:0, g:0, b:0}, hsl: {h:0, s:0, l:0}}
```

## Contributing to Collit
Contributions are always welcome.
Before contributing please read the [code of conduct](https://js.foundation/community/code-of-conduct) &
[search the issue tracker](https://github.com/eugeneford/collit/issues) (your issue may have already been discussed or fixed).

To contribute, follow next steps:
* Fork Collit
* Commit your changes
* Open a Pull Request.

### Feature Requests
Feature requests should be submitted in the issue tracker, with a description
of the expected behavior & use case, where they’ll remain closed until sufficient interest (e.g. 👍 reactions).
Before submitting a feature request, please search for similar ones in the closed issues.

## Manifest
The entire logic of modules is and should be based on use of the Color, LinearGradient and RadialGradient data types.

### Color object
Describes a specific color as a set of hex, rgb and hsl values
```js
{
   hex: "#333",
   rgb: { r: 51, g: 51, b: 51, a: 1 },
   hsl: { h: 0, s: 0 l: 0.1 a: 1 }
}
```

* "R", "G" and "B" — should contains the numeric values between 0 and 255 (eg. 128).<br />
* "H" — should contain the numeric value between 0 and 360 (eg. 270).<br />
* "S", "L" and "A" — should contains a numeric value between 0 and 1 (eg. 0.5).<br />

> "A" — inside the rgb and hsl values is optional and can be omitted.

### LinearGradientInfo object
Describes a specific set of linear gradient values.
```js
{
   angle: 45,
   sideCorner: "top right"
   colorStopList: [
      {
         position: 0, // 0%
         color: { rgb: { r: 51, g: 51, b: 51, a: 1 } }
      },
      {
         position: 1, // 100%
         color: { hex: "#333" }
      }
   ],
}
```

* angle — defines the angle (from 0 to 360) of gradient line. Can be omitted.
* sideCorner — defines the direction of gradient line. Can be on of "top", "right", "left", "bottom", "top right", "bottom right", "bottom left", "top left" values.
* colorStopList — contains a set of color-stop values.
  - position - defines the optional color stop position. Can be set as percentage (from 0 to 1) or length (any CSS number — px, em, pc, in, mm... eg. "20px") value.
  - color - defines the actual stop color. Should contain at least one of ColorInfo's value.

### RadialGradientInfo object
Describes a specific set of radial gradient values.
```js
{
   position: [.25, .75], // at 25% 75%
   shape: "circle",
   extent: "closest-side",
   colorStopList: [
      {
         position: 0, // 0%
         color: { hsl: { h: 0, s: 0 l: 0.1 a: 1 } }
      },
      {
         position: 1, // 100%
         color: { rgb: { r: 51, g: 51, b: 51, a: 1 } }
      }
   ],
}
```

* position — defines the position of the gradient, interpreted in the same way as css background-position property values. Can be set as a percentage (from 0 to 1) or length (any CSS number — px, em, pc, in, mm... eg. "20px") value. Can be omitted.
* shape — defines the actual shape of gradient. Can be set as "circle" or "ellipse" and can be omitted.
* extent - describes how big the ending shape must be. The possible values are: "closest-side", "closest-corner", "farthest-side", "farthest-corner"
* colorStopList — contains a set of color-stop values.
  - position - defines the optional color stop position. Can be set as percentage (from 0 to 1) or length (any CSS number — px, em, pc, in, mm... eg. "20px") value.
  - color - defines the actual stop color. Should contain at least one of ColorInfo's value.

## License
Released under the [MIT License](https://github.com/eugeneford/collit/blob/master/LICENSE)