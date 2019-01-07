# vue-polar

A simple Vue component to create polar layouts. Position and rotate around a center-point to arrange elements in a circle or spiral shape. It contains a slot, so you have full control of what to place inside a polar instance.

Vue-polar is a stateless [functional component](https://vuejs.org/v2/guide/render-function.html#Functional-Components), meaning it is very lightweight and quick to render.

## Examples

Some simple demonstations [here](https://snirp.github.io/vue-polar/)

+ Emoticons arranged in a circle
+ Random cats with additional rotation
+ A clock, complete with numbers, indicators and hands. 
+ A colorful spiral,

All completely (and easily) done with vue-polar elements. Do you have other examples how you are using vue-polar? Please let me know.

## Project setup
```
# npm
$ npm install vue-polar

#yarn
$ yarn add vue-polar
```

## How it works
The `polar` instances rely on absolute positioning around the center of first surrounding element with `position: relative`. If no such element is encountered, the positioning will be relative to the center of the screen/document???, which is what you may intent.
 
 The instance creates a `div` that is first centered on the relative element. It is then given a combined transformation: first a rotation, then a translation along its x-axis and finally another (optional) rotation.

 ## How to use

 ```html
 <polar>
 ```

## Constructor Options
|prop|description|default|options|
|:---|---|---|---|
|`zeroAngle`|starting angle relative to default zero angle (=right/3o-clock)|`0`|`Number`|
|`segments`|equal subdivisions of 360 degrees.|`12`|`Number`|
|`item`|determines relative rotation, angle is calculated by: item/segments * 360|`0`|`Number`|
|`offset`|translation in direction of the X-axis of the element|`'100%'`|`px`, `em`, `pt`, `%`, `vh`, `vw`|
|`setStraight`|whether to reset the x-axis of the element to horizontal after translation|`true`|`true`, `false`|
|`extraRotation`|addtional rotation to apply to element|`12`|`Number`|
|`height`|height of element|`'50px'`|`px`, `em`, `pt`, `%`, `vh`, `vw`|
|`width`|width of element|`'50px'`|`px`, `em`, `pt`, `%`, `vh`, `vw`|
|`z-index`|value for z-index property|`1`|`Integer`|
|`customStyles`|Object with CSS properties and values, gets merged with postioning and rotation styles|`{}`|`prop: val`|

The following properties are not allowed in the `customStyles` object:

+ `width`
+ `height`
+ `margin`
+ `transform`
+ `zIndex`
+ `position`
+ `top`
+ `left`
+ `right`
+ `bottom`

Some of these will be set directly though the props, and others will be calculated or set in the CSS. Every polar element has a `slot` where you can provide your own elements and styling, free from these limitations.

## License
[The MIT License](http://opensource.org/licenses/MIT)
