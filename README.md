# Marrakech

Marrakech is a collection of common Sass helper mixins and functions helping you 
write more maintainable styles ✨

[![forthebadge](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)
[![forthebadge](http://forthebadge.com/images/badges/makes-people-smile.svg)](http://forthebadge.com)
[![forthebadge](http://forthebadge.com/images/badges/you-didnt-ask-for-this.svg)](http://forthebadge.com)


### Why
Writing styles can be repetitive and slow. Marrakech's collection of mixins makes 
it easy and fast to write more **DRY** code.


## Table of Contents

* [Requirements](#requirements)
* Documentation
  * [aspect-ratio](#aspect-ratio)
  * [border-radius](#border-radius)
  * [border-width](#border-width)
  * [center](#center)
  * [center-block](#center-block)
  * [circle](#circle)
  * [clearfix](#clearfix)
  * [hide-visually](#hide-visually)
  * [hide-text](#hide-text)
  * [margin](#margin)
  * [modular-scale](#modular-scale)
  * [padding](#padding)
  * [position](#position)
  * [size](#size)
  * [system-ui-font](#system-ui-font)
  * [timing](#timing)
  * [triangle](#triangle)
  * [truncate](#truncate)
  * [ui-color](#ui-color)
  * [word-wrap](#word-wrap)
* [Contributors](#contributors)
* [License](#license)


## Requirements
- [Sass] 3.4+ or [LibSass] 3.3+

  [Sass]: https://github.com/sass/sass
  [LibSass]: https://github.com/sass/libsass


## Documentation

### Aspect Ratio
Set a aspect ratio for an element
- @mixin aspect-ratio([width], [height]);

##### Parameters
| Parameter         | Type             | Default             | Optional      |
| :---------------- | :--------------- | :------------------ | :------------ |
| width             | number           | -                   | No            |
| height            | number           | -                   | No            |

##### Example
```scss
/** Usage */
.youtube-fluid {
  width: 100%;
  @include aspect-ratio(16, 9);
}
```

```css
/** Output */
.youtube-fluid {
  width: 100%;
  position: relative;
  display: block;
  height: 0;
  overflow: hidden;
  padding: 0;
  padding-bottom: 56.25%;
}
```


### Border Radius
A shorhand syntax for adding border radius to different sides of an element
- @mixin border-top-radius([radius]);
- @mixin border-right-radius([radius]);
- @mixin border-bottom-radius([radius]);
- @mixin border-left-radius([radius]);

##### Parameters
| Parameter         | Type               | Default         | Optional      |
| :---------------- | :----------------- | :-------------- | :------------ |
| radius            | Border radius size | -               | No            |

##### Example
```scss
/** Usage */
.box-1 {
  @include border-top-radius(1px);
}

.box-2 {
  @include border-right-radius(1px);
}

.box-3 {
  @include border-bottom-radius(3px);
}

.box-4 {
  @include border-left-radius(4px);
}
```

```css
/** Output */
.box-1 {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}

.box-2 {
  border-top-right-radius: 2px;
  border-bottom-right-radius: 2px;
}

.box-3 {
  border-bottom-left-radius: 3px;
  border-bottom-right-radius: 3px;
}

.box-4 {
  border-bottom-left-radius: 4px;
  border-top-left-radius: 4px;
}
```


### Border Width
A shorthand syntax for setting different border widths on each side of an element
- @mixin border-width([widths]);

##### Parameters
| Parameter         | Type                       | Default      | Optional     |
| :---------------- | :------------------------- | :----------- | :----------- |
| widths            | List of border width sizes | -            | No           |

##### Example
```scss
/** Usage */
.box {
  @include border-width(2px null 3px 1px);
}
```

```css
/** Output */
.box {
  border-top-width: 2px;
  border-bottom-width: 3px;
  border-left-width: 1px;
}
```


### Center
Center an element vertically and horizontally relative to closest positioned parent
- @mixin center;

##### Example
```scss
/** Usage */
.box {
  @include center;
}
```

```css
/** Output */
.box {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```


### Center Block
Center a block element with a display horizontally
- @mixin center-block;

##### Example
```scss
/** Usage */
.box {
  width: 250px;
  @include center-block;
}
```

```css
/** Output */
.box {
  width: 250px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```


### Circle
Create a circle shape
- @mixin circle([diameter], [color]);

##### Parameters
| Parameter         | Type                 | Default      | Optional     |
| :---------------- | :------------------- | :----------- | :----------- |
| diameter          | size                 | -            | No           |
| color             | color                | #000         | Yes          |

##### Example
```scss
/** Usage */
.circle {
  @include circle(200px, darkred);
}
```

```css
/** Output */
.circle {
  height: 200px;
  width: 200px;
  border-radius: 50%;
  background-color: darkred;
}
```


### Clearfix
Clearfix hack clears floated child elements without extra markup
- @mixin clearfix;

##### Example
```scss
/** Usage */
.clearfix {
  @include clearfix;
}
```

```css
/** Output */
.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
```


### Hide Visually
Hides element and makes the content only visible to screen readers
- @mixin hide-visually;

##### Example
```scss
/** Usage */
.sr-only {
  @include hide-visually;
}
```

```css
/** Ouput */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  overflow: hidden;
  padding: 0;
  margin: -1px;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
```


### Hide Text
- @mixin hide-text;

##### Example
```scss
/** Usage */
.logo {
  @include hide-text;
}
```

```css
/** Ouput */
.logo {
  overflow: hidden;
  text-indent: 101%;
  white-space: nowrap;
}
```


### Margin
A shorthand way of adding individual margins
- @mixin margin([margins]);

##### Parameters
| Parameter         | Type                 | Default      | Optional     |
| :---------------- | :------------------- | :----------- | :----------- |
| margins           | List of sizes (4)    | -            | No           |

#### Example
```scss
/** Usage */
.box {
  @include margin(5px 10px null 5%);
}
```

```css
/** Ouput */
.box {
  margin-top: 5px;
  margin-left: 10px;
  margin-right: 5%;
}
```


### Modular Scale
Modular scale calculator for consistent typographical scale http://www.modularscale.com/
- @function modular-scale([increment], [ratio], [value]);

##### Parameters
| Parameter         | Type                 | Default      | Optional     |
| :---------------- | :------------------- | :----------- | :----------- |
| increment         | integer              | -            | No           |
| ratio             | number               | 1.25 (4:5)   | Yes          |
| value             | size                 | 1rem         | Yes          |

##### Example
```scss
/** Usage */
h1 {
  font-size: modular-scale(5);
}

h2 {
  font-size: modular-scale(4);
}

h3 {
  font-size: modular-scale(3);
}

h4 {
  font-size: modular-scale(2);
}

h5 {
  font-size: modular-scale(1);
}

h6 {
  font-size: modular-scale(0);
}
```

```css
/** Ouput */
h1 {
  font-size: 3.05176rem;
}

h2 {
  font-size: 2.44141rem;
}

h3 {
  font-size: 1.95312rem;
}

h4 {
  font-size: 1.5625rem;
}

h5 {
  font-size: 1.25rem;
}

h6 {
  font-size: 1rem;
}
```


### Padding
A shorthand way of adding individual paddings
- @mixin padding([paddings]);

##### Parameters
| Parameter         | Type                 | Default      | Optional     |
| :---------------- | :------------------- | :----------- | :----------- |
| paddings          | List of sizes (4)    | -            | No           |

#### Example
```scss
/** Usage */
.box {
  @include padding(5px 10px null 5%);
}
```

```css
/** Ouput */
.box {
  padding-top: 5px;
  padding-left: 10px;
  padding-right: 5%;
}
```


### Position
A shorthand syntax for defining an elements position and its lenghts
- @mixin position([position], [lengths]);

##### Parameters
| Parameter         | Type                 | Default      | Optional     |
| :---------------- | :------------------- | :----------- | :----------- |
| position          | CSS position value   | -            | No           |
| lengths           | map of lengths       | -            | No           |

##### Example
```scss
/** Usage */
.box {
  @include position(absolute, (top: 10%, right: 250px));
}
```

```css
/** Ouput */
.box {
  position: absolute;
  top: 10%;
  right: 250px;
}
```


### Size
Set the height and width of an element in one line
- @mixin size([width], [height]);

##### Parameters
| Parameter         | Type                 | Default      | Optional     |
| :---------------- | :------------------- | :----------- | :----------- |
| width             | unit size            | -            | No           |
| height            | unit size            | width        | Yes          |

##### Example
```scss
/** Usage */
.square {
  @include size(200px);
}

.rectangle {
  @include size(500px, 300px);
}
```

```css
/** Ouput */
.square {
  width: 200px;
  height: 200px;
}

.rectangle {
  width: 500px;
  height: 300px;
}
```


### System UI Font
Get a list of font list to enable system UI font
- @function system-ui-font;

##### Example
```scss
/** Usage */
body {
  font-family: system-ui-font();
}
```

```css
/** Ouput */
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", Helvetica, sans-serif;
}
```


### Timing
Extra cubic-bezier timing functions for animations and transitions
- @function timing([timing-function]);

##### Parameters
| Parameter         | Type                  | Default      | Optional     |
| :---------------- | :-------------------- | :----------- | :----------- |
| timing-function   | timing function name  | -            | No           |

##### Timing functions
- ease-in-quad
- ease-in-cubic
- ease-in-quart
- ease-in-quint
- ease-in-sine
- ease-in-expo
- ease-in-circ
- ease-in-back
- ease-out-quad
- ease-out-cubic
- ease-out-quart
- ease-out-quint
- ease-out-sine
- ease-out-expo
- ease-out-circ
- ease-out-back
- ease-in-out-quad
- ease-in-out-cubic
- ease-in-out-quart
- ease-in-out-quint
- ease-in-out-sine
- ease-in-out-expo
- ease-in-out-circ
- ease-in-out-back

##### Example
```scss
/** Usage */
.box {
  transition: transform 250ms timing(ease-in-sine);
}
```

```css
/** Ouput */
.box {
  transition: transform 250ms cubic-bezier(0.47, 0, 0.745, 0.715);
}
```


### Triangle
Create a triangle facing up, down, right, left, up-right, up-left, down-right or 
down-left
- @mixin triangle([size], [color], [direction]);

##### Parameters
| Parameter    | Type                                                               | Default  | Optional |
| :----------- | :----------------------------------------------------------------- | :------- | :------- |
| size         | size                                                               | -        | No       |
| color        | color                                                              | -        | No       |
| direction    | up, down, right, left, up-right, up-left, down-right or down-left  | -        | No       |

##### Example
```scss
/** Usage */
.triangle {
  @include triangle(30px, #000, right);
}
```

```css
/** Ouput */
.triangle {
  height: 0;
  width: 0;
  border-bottom: 15px solid transparent;
  border-left: 15px solid #000;
  border-top: 15px solid transparent;
}
```


### Truncate
Truncate overflowing text and add a ellipsis
- @mixin truncate;

##### Example
```scss
/** Usage */
.foo {
  @include truncate;
}
```

```css
/** Ouput */
.foo {
  word-wrap: normal;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```


### UI Color
Get a UI color from the Open Color scheme https://yeun.github.io/open-color/
- @function ui-color([color], [shade], [opacity]);

##### Parameters
| Parameter         | Type                  | Default      | Optional     |
| :---------------- | :-------------------- | :----------- | :----------- |
| color             | gray, red, pink, grape, violet, indigo, blue, cyan, teal, green, lime, yellow or orange | -            | No           |
| shade             | 0-9                   | 5            | Yes          |
| opacity           | 0-1                   | 1            | Yes          |

##### Example
```scss
/** Usage */
.box {
  color: ui-color(gray, 9);
  background: ui-color(yellow, 3);
}
```

```css
/** Ouput */
.box {
  color: #212529;
  background: #FFE066;
}
```


### Word wrap
A shorhand way of changing the word-wrap property
- @mixin word-wrap([wrap]);

##### Parameters
| Parameter         | Type                                    | Default      | Optional     |
| :---------------- | :-------------------------------------- | :----------- | :----------- |
| wrap              | normal, break-word, initial or inherit  | break-word   | Yes          |

##### Example
```scss
/** Usage */
.foo {
  @include word-wrap;
}
```

```css
/** Ouput */
.foo {
  overflow-wrap: break-word;
  word-break: break-all;
  word-wrap: break-word;
}
```


## Contributors
[Tahseen Malik](https://tahseenmalik.com)


## License
MIT