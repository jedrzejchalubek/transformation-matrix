<!-------------------------------------------------------------------->
<!--                            WARNING!                            -->
<!-------------------------------------------------------------------->
<!--                                                                -->
<!-- THIS IS AN AUTOGENERATED FILE. DO NOT EDIT THIS FILE DIRECTLY. -->
<!-- for your changes use README.template.hbs file                  -->
<!--                                                                -->
<!-------------------------------------------------------------------->
<!-------------------------------------------------------------------->

# transformation-matrix
Javascript isomorphic 2D affine transformations written in ES6 syntax. Manipulate transformation matrices with this totally tested library!

[![chrvadala](https://img.shields.io/badge/website-chrvadala-orange.svg)](https://chrvadala.github.io)
[![Test](https://github.com/chrvadala/transformation-matrix/workflows/Test/badge.svg)](https://github.com/chrvadala/transformation-matrix/actions)
[![Coverage Status](https://coveralls.io/repos/github/chrvadala/transformation-matrix/badge.svg?branch=master)](https://coveralls.io/github/chrvadala/transformation-matrix?branch=master)
[![npm](https://img.shields.io/npm/v/transformation-matrix.svg?maxAge=2592000?style=plastic)](https://www.npmjs.com/package/transformation-matrix)
[![Downloads](https://img.shields.io/npm/dm/transformation-matrix.svg)](https://www.npmjs.com/package/transformation-matrix)
[![Donate](https://img.shields.io/badge/donate-PayPal-green.svg)](https://www.paypal.me/chrvadala/25)


Transformations, i.e. *linear invertible automorphisms*, are used to map a picture into another one with different size, position and orientation. Given a basis, transformations are represented by means of squared invertible matrices, called **transformation matrices**.
A geometric transformation is defined as a one-to-one mapping of a point space to itself, which preservers some geometric relations of figures. - [Geometric Programming for Computer Aided Design](https://books.google.it/books?vid=ISBN9780471899426)

This library allows us to:
- generate transformation matrices for the following operations: **translation**, **rotation**, **scale**, **shear**, **skew**
- merge multiple transformation matrices in a single matrix that is the **composition of multiple matrices**
- work with strings in both directions: **parse**, **render**
- **apply a transformation matrix to point(s)**

## Usage example (ES6)
```js
import {scale, rotate, translate, compose, applyToPoint} from 'transformation-matrix';
let {scale, rotate, translate, compose, applyToPoint} = window.TransformationMatrix;
let {scale, rotate, translate, compose, applyToPoint} = require('transformation-matrix')

let matrix = compose(
  translate(40,40),
  rotate(Math.PI/2),
  scale(2, 4)
);

applyToPoint(matrix, {x: 42, y: 42});
// { x: -128, y: 124.00000000000001 }

applyToPoint(matrix, [16, 24]);
//  [ -56, 72 ]
```

## Setup
```sh
npm install transformation-matrix
# or
yarn add transformation-matrix
```
```html
<script src="https://unpkg.com/transformation-matrix@2"></script>
```

# Reference
## Functions

<dl>
<dt><a href="#applyToPoint">applyToPoint(matrix, point)</a> ⇒ <code>Point</code></dt>
<dd><p>Calculate a point transformed with an affine matrix</p>
</dd>
<dt><a href="#applyToPoints">applyToPoints(matrix, points)</a> ⇒ <code>Array.&lt;Point&gt;</code></dt>
<dd><p>Calculate an array of points transformed with an affine matrix</p>
</dd>
<dt><a href="#fromDefinition">fromDefinition(definitionOrArrayOfDefinition)</a> ⇒ <code>Array.&lt;Matrix&gt;</code></dt>
<dd><p>Converts array of matrix descriptor to array of matrix</p>
</dd>
<dt><a href="#fromObject">fromObject(object)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Extract an affine matrix from an object that contains a,b,c,d,e,f keys
Any value could be a float or a string that contains a float</p>
</dd>
<dt><a href="#fromString">fromString(string)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Parse a string formatted as matrix(a,b,c,d,e,f)</p>
</dd>
<dt><a href="#fromTransformAttribute">fromTransformAttribute(transformString)</a> ⇒ <code>Array.&lt;MatrixDescriptor&gt;</code></dt>
<dd><p>Parser for SVG Trasform Attribute <a href="http://www.w3.org/TR/SVG/coords.html#TransformAttribute">http://www.w3.org/TR/SVG/coords.html#TransformAttribute</a> <br/>
Warning: This should be considered BETA until it is released a stable version of pegjs.</p>
</dd>
<dt><a href="#fromTriangles">fromTriangles(t1, t2)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Returns a matrix that transforms a triangle t1 into another triangle t2, or throws an exception if it is impossible.</p>
</dd>
<dt><a href="#identity">identity()</a> ⇒ <code>Matrix</code></dt>
<dd><p>Identity matrix</p>
</dd>
<dt><a href="#inverse">inverse(matrix)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a matrix that is the inverse of the provided matrix</p>
</dd>
<dt><a href="#isAffineMatrix">isAffineMatrix(object)</a> ⇒ <code>boolean</code></dt>
<dd><p>Check if the object contain an affine matrix</p>
</dd>
<dt><a href="#rotate">rotate(angle, [cx], [cy])</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a rotation matrix</p>
</dd>
<dt><a href="#rotateDEG">rotateDEG(angle, [cx], [cy])</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a rotation matrix with a DEG angle</p>
</dd>
<dt><a href="#scale">scale(sx, [sy], [cx], [cy])</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a scaling matrix</p>
</dd>
<dt><a href="#shear">shear(shx, shy)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a shear matrix</p>
</dd>
<dt><a href="#skew">skew(ax, ay)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a skew matrix</p>
</dd>
<dt><a href="#skewDEG">skewDEG(ax, ay)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a skew matrix using DEG angles</p>
</dd>
<dt><a href="#smoothMatrix">smoothMatrix(matrix, [precision])</a> ⇒ <code>Matrix</code></dt>
<dd><p>Rounds all elements of the given matrix using the given precision</p>
</dd>
<dt><a href="#toCSS">toCSS(matrix)</a> ⇒ <code>string</code></dt>
<dd><p>Serialize an affine matrix to a string that can be used with CSS or SVG</p>
</dd>
<dt><a href="#toSVG">toSVG(matrix)</a> ⇒ <code>string</code></dt>
<dd><p>Serialize an affine matrix to a string that can be used with CSS or SVG</p>
</dd>
<dt><a href="#toString">toString(matrix)</a> ⇒ <code>string</code></dt>
<dd><p>Serialize an affine matrix to a string that can be used with CSS or SVG</p>
</dd>
<dt><a href="#transform">transform(matrices)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Merge multiple matrices into one</p>
</dd>
<dt><a href="#compose">compose(matrices)</a> ⇒ <code>Matrix</code></dt>
<dd><p>Merge multiple matrices into one</p>
</dd>
<dt><a href="#translate">translate(tx, [ty])</a> ⇒ <code>Matrix</code></dt>
<dd><p>Calculate a translate matrix</p>
</dd>
</dl>

## Changelog
- **0.0** - Preview version
- **1.0** - First public version
- **1.1** - Splits lib into different files
- **1.2** - Adds shear operation
- **1.3** - Adds umd support
- **1.4** - Adds typescript definitions
- **1.5** - Upgrades deps
- **1.6** - Adds optional parameter support on `translate(tx)`, `scale(sx)`, `rotate(angle, cx, cy)`
- **1.7** - Upgrades deps
- **1.8** - Fixes [#12](https://github.com/chrvadala/transformation-matrix/issues/12), Adds `fromTransformAttribute`, Discontinues node 4 support
- **1.9** - Adds `skew(ax, ay)`, Upgrades deps, Improves `fromTransformAttribute`
- **1.10**- Updates typescript definitions [#15](https://github.com/chrvadala/transformation-matrix/pull/15)
- **1.11**- Upgrades deps
- **1.12**- Migrates tests on [Jest](https://jestjs.io/), Integrates [standard.js](https://standardjs.com/), Upgrades deps
- **1.13**- Adds `compose` function, Upgrades deps, Exposes skew operation [#37](https://github.com/chrvadala/transformation-matrix/pull/37)
- **1.14**- Adds support for points defined as `Array` in the form `[x, y]` [#38](https://github.com/chrvadala/transformation-matrix/pull/38)
- **1.15**- Adds `fromTriangle` and `smoothMatrix` functions [#41](https://github.com/chrvadala/transformation-matrix/issues/41)
- **2.0**- Migrates to Babel 7 and updates dependencies; introduces `fromDefinition` function; breaking changes on `fromTransformAttribute` function; improves docs
- **2.1**- Upgrades deps; Adds Node.js v12 to CI
- **2.2**- Upgrades deps; Improves typescript definition [#66](https://github.com/chrvadala/transformation-matrix/pull/66)
- **2.3**- Adds `(cx,cy)` on `scale` function [#62](https://github.com/chrvadala/transformation-matrix/pull/62); Improves typescript definition [#66](https://github.com/chrvadala/transformation-matrix/pull/67); Upgrades deps
- **2.4**- Improves typescript definition [#75](https://github.com/chrvadala/transformation-matrix/pull/75)
- **2.5**- Upgrades deps; Deprecates NodeJS 8; Adds NodeJs 14 support
- **2.6**- Upgrades deps; Fixes fromTransformAttribute function [#84](https://github.com/chrvadala/transformation-matrix/pull/84)
- **2.7**- Upgrades deps;
# API

## Data Model
A transformation **Matrix** is defined as a `Plain Object` with 6 keys: `a`, `b`, `c`, `d`, `e` and `f`.
```js
const matrix = {
a: 1, c: 0, e: 0,
b: 0, d: 1, f: 0
}
```
A **Point** can be defined in two different ways:
- as `Plain Object`, with inside two keys: `x` and `y`
```js
const point = { x: 24, y: 42 }
```
- as `Array`, with two items in the form `[x, y]`
```js
const point = [ 24, 42 ]
```

<a name="applyToPoint"></a>

## applyToPoint(matrix, point) ⇒ <code>Point</code>
Calculate a point transformed with an affine matrix

**Kind**: global function  
**Returns**: <code>Point</code> - Point  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | Affine Matrix |
| point | <code>Point</code> | Point |

<a name="applyToPoints"></a>

## applyToPoints(matrix, points) ⇒ <code>Array.&lt;Point&gt;</code>
Calculate an array of points transformed with an affine matrix

**Kind**: global function  
**Returns**: <code>Array.&lt;Point&gt;</code> - Array of point  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | Affine Matrix |
| points | <code>Array.&lt;Point&gt;</code> | Array of point |

<a name="fromDefinition"></a>

## fromDefinition(definitionOrArrayOfDefinition) ⇒ <code>Array.&lt;Matrix&gt;</code>
Converts array of matrix descriptor to array of matrix

**Kind**: global function  
**Returns**: <code>Array.&lt;Matrix&gt;</code> - Array of matrix  

| Param | Type | Description |
| --- | --- | --- |
| definitionOrArrayOfDefinition | <code>Array.&lt;Object&gt;</code> | Array of object describing the matrix |

**Example**  
```js
> fromDefinition([
 { type: 'matrix', a:1, b:2, c:3, d:4, e:5, f:6 },
 { type: 'translate', tx: 10, ty: 20 },
 { type: 'scale', sx: 2, sy: 4 },
 { type: 'rotate', angle: 90, cx: 50, cy: 25 },
 { type: 'skewX', angle: 45 },
 { type: 'skewY',  angle: 45 },
 { type: 'shear', shx: 10, shy: 20}
])

[
 { a: 1, b: 2, c: 3, d: 4, e: 5, f: 6 },
 { a: 1, c: 0, e: 10, b: 0, d: 1, f: 20 },
 { a: 2, c: 0, e: 0, b: 0, d: 4, f: 0 },
 { a: 6.123, c: -1, e: 0, b: 1, d: 6.123, f: 0 },
 { a: 1, c: 0.99.., e: 0, b: 0, d: 1, f: 0 },
 { a: 1, c: 0, e: 0, b: 0.99, d: 1, f: 0 },
 { a: 1, c: 10, e: 0, b: 20, d: 1, f: 0 }
]
```
<a name="fromObject"></a>

## fromObject(object) ⇒ <code>Matrix</code>
Extract an affine matrix from an object that contains a,b,c,d,e,f keys
Any value could be a float or a string that contains a float

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| object | <code>Object</code> | Object that contains a,b,c,d,e,f keys |

<a name="fromString"></a>

## fromString(string) ⇒ <code>Matrix</code>
Parse a string formatted as matrix(a,b,c,d,e,f)

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| string | <code>string</code> | String with an affine matrix |

**Example**  
```js
> fromString('matrix(1,2,3,4,5,6)')
{a: 1, b: 2, c: 3, d: 4, c: 5, e: 6}
```
<a name="fromTransformAttribute"></a>

## fromTransformAttribute(transformString) ⇒ <code>Array.&lt;MatrixDescriptor&gt;</code>
Parser for SVG Trasform Attribute http://www.w3.org/TR/SVG/coords.html#TransformAttribute <br/>
Warning: This should be considered BETA until it is released a stable version of pegjs.

**Kind**: global function  
**Returns**: <code>Array.&lt;MatrixDescriptor&gt;</code> - Array of MatrixDescriptor  

| Param | Type | Description |
| --- | --- | --- |
| transformString | <code>string</code> | Transform string as defined by w3 Consortium |

**Example**  
```js
> fromTransformAttribute('translate(-10,-10) scale(2,2) translate(10,10)')
[
 { type: 'translate', tx: -10, ty: -10},
 { type: 'scale', sx: 2, sy: 2 },
 { type: 'translate', tx: 10, ty: 10}
]

> compose(fromDefinition(fromTransformAttribute('translate(-10, -10) scale(10, 10)')))
{ a: 10, c: 0, e: -10, b: 0, d: 10, f: -10 }
```
<a name="fromTriangles"></a>

## fromTriangles(t1, t2) ⇒ <code>Matrix</code>
Returns a matrix that transforms a triangle t1 into another triangle t2, or throws an exception if it is impossible.

**Kind**: global function  
**Returns**: <code>Matrix</code> - Matrix which transforms t1 to t2  
**Throws**:

- Exception if the matrix becomes not invertible


| Param | Type | Description |
| --- | --- | --- |
| t1 | <code>Array.&lt;Point&gt;</code> | Array of points containing the three points for the first triangle |
| t2 | <code>Array.&lt;Point&gt;</code> | Array of points containing the three points for the second triangle |

<a name="identity"></a>

## identity() ⇒ <code>Matrix</code>
Identity matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  
<a name="inverse"></a>

## inverse(matrix) ⇒ <code>Matrix</code>
Calculate a matrix that is the inverse of the provided matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Inverted Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | Affine Matrix |

<a name="isAffineMatrix"></a>

## isAffineMatrix(object) ⇒ <code>boolean</code>
Check if the object contain an affine matrix

**Kind**: global function  
**Returns**: <code>boolean</code> - True if is an object and contains an affine matrix  

| Param | Type | Description |
| --- | --- | --- |
| object | <code>Object</code> | Generic Plain Object |

<a name="rotate"></a>

## rotate(angle, [cx], [cy]) ⇒ <code>Matrix</code>
Calculate a rotation matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| angle | <code>number</code> | Angle in radians |
| [cx] | <code>number</code> | If (cx,cy) are supplied the rotate is about this point |
| [cy] | <code>number</code> | If (cx,cy) are supplied the rotate is about this point |

<a name="rotateDEG"></a>

## rotateDEG(angle, [cx], [cy]) ⇒ <code>Matrix</code>
Calculate a rotation matrix with a DEG angle

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| angle | <code>number</code> | Angle in degree |
| [cx] | <code>number</code> | If (cx,cy) are supplied the rotate is about this point |
| [cy] | <code>number</code> | If (cx,cy) are supplied the rotate is about this point |

<a name="scale"></a>

## scale(sx, [sy], [cx], [cy]) ⇒ <code>Matrix</code>
Calculate a scaling matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| sx | <code>number</code> |  | Scaling on axis x |
| [sy] | <code>number</code> | <code>sx</code> | Scaling on axis y (default sx) |
| [cx] | <code>number</code> |  | If (cx,cy) are supplied the scaling is about this point |
| [cy] | <code>number</code> |  | If (cx,cy) are supplied the scaling is about this point |

<a name="shear"></a>

## shear(shx, shy) ⇒ <code>Matrix</code>
Calculate a shear matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| shx | <code>number</code> | Shear on axis x |
| shy | <code>number</code> | Shear on axis y |

<a name="skew"></a>

## skew(ax, ay) ⇒ <code>Matrix</code>
Calculate a skew matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| ax | <code>number</code> | Skew on axis x |
| ay | <code>number</code> | Skew on axis y |

<a name="skewDEG"></a>

## skewDEG(ax, ay) ⇒ <code>Matrix</code>
Calculate a skew matrix using DEG angles

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| ax | <code>number</code> | Skew on axis x |
| ay | <code>number</code> | Skew on axis y |

<a name="smoothMatrix"></a>

## smoothMatrix(matrix, [precision]) ⇒ <code>Matrix</code>
Rounds all elements of the given matrix using the given precision

**Kind**: global function  
**Returns**: <code>Matrix</code> - The rounded Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | An affine matrix to round |
| [precision] | <code>number</code> | A precision to use for Math.round. Defaults to 10000000000 (meaning which rounds to the 10th digit after the comma). |

<a name="toCSS"></a>

## toCSS(matrix) ⇒ <code>string</code>
Serialize an affine matrix to a string that can be used with CSS or SVG

**Kind**: global function  
**Returns**: <code>string</code> - String that contains an affine matrix formatted as matrix(a,b,c,d,e,f)  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | Affine Matrix |

<a name="toSVG"></a>

## toSVG(matrix) ⇒ <code>string</code>
Serialize an affine matrix to a string that can be used with CSS or SVG

**Kind**: global function  
**Returns**: <code>string</code> - String that contains an affine matrix formatted as matrix(a,b,c,d,e,f)  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | Affine Matrix |

<a name="toString"></a>

## toString(matrix) ⇒ <code>string</code>
Serialize an affine matrix to a string that can be used with CSS or SVG

**Kind**: global function  
**Returns**: <code>string</code> - String that contains an affine matrix formatted as matrix(a,b,c,d,e,f)  

| Param | Type | Description |
| --- | --- | --- |
| matrix | <code>Matrix</code> | Affine Matrix |

<a name="transform"></a>

## transform(matrices) ⇒ <code>Matrix</code>
Merge multiple matrices into one

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| matrices | <code>Matrix</code> \| <code>Array.&lt;Matrix&gt;</code> | Matrices listed as separate parameters or in an array |

<a name="compose"></a>

## compose(matrices) ⇒ <code>Matrix</code>
Merge multiple matrices into one

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Description |
| --- | --- | --- |
| matrices | <code>Matrix</code> \| <code>Array.&lt;Matrix&gt;</code> | Matrices listed as separate parameters or in an array |

<a name="translate"></a>

## translate(tx, [ty]) ⇒ <code>Matrix</code>
Calculate a translate matrix

**Kind**: global function  
**Returns**: <code>Matrix</code> - Affine Matrix  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| tx | <code>number</code> |  | Translation on axis x |
| [ty] | <code>number</code> | <code>0</code> | Translation on axis y |

## Some projects using transformation-matrix
- [**React Planner**](https://github.com/cvdlab/react-planner)
- [**React SVG Pan Zoom**](https://github.com/chrvadala/react-svg-pan-zoom)
- [**ngx-graph**](https://github.com/swimlane/ngx-graph)
- [**learn-anything**](https://github.com/learn-anything/learn-anything)
- [**Others...**](https://github.com/chrvadala/transformation-matrix/network/dependents)
- Pull request your project!

## Contributors
- [chrvadala](https://github.com/chrvadala) (author)
- [forabi](https://github.com/forabi)
- [nidu](https://github.com/nidu) (PEG.js descriptor)
- [aubergene](https://github.com/aubergene)
- [SophiaLi1](https://github.com/SophiaLi1)
- [Shuhei-Tsunoda](https://github.com/Shuhei-Tsunoda)
- [antonyRoberts](https://github.com/antonyRoberts)
- [mcwebb](https://github.com/mcwebb)
- [signalwerk](https://github.com/signalwerk)
- [estollnitz](https://github.com/estollnitz)
- [rodrigoapereira](https://github.com/rodrigoapereira)
- [formatlos](https://github.com/formatlos)
- [benhjames](https://github.com/benhjames)

