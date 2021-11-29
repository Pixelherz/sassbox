# sassbox

Sass utils we frequently use in our projects.


## Getting Started

### Installing

Install using npm:

```
npm i @pixelherz/sassbox
```

## Usage

Import the toolbox in your project. 

```scss
@use '~@pixelherz/sassbox' [with (<my-config>)];
```

### Configuration

Typically you'll want to `@use` a configured `@forward` of the library. Here's a sample: 

```scss
// e.g. /styles/_sassbox.scss – configured @forward of the library
@forward '@pixelherz/sassbox' with (
  $font-sizes: (
    's': 16px,
    'm': 24px,
    'l': 36px,
  ),
  $line-heights: (
    's': 20px,
    'm': 30px,
    'l': 45px,
  ),
  // ... custom configuration
);
```

```scss
// e.g. /component/component.styles.scss
@use '../styles/sassbox';
@include sassbox.normalize();
```

### Base

#### Normalize

Normalize (reset, unify) browser rendering. Includes global usage of `box-sizing: border-box`. 

```scss
// Import sub-module sassbox/base/normalize
@use '~@pixelherz/sassbox';
@include sassbox.normalize();
```

### Utils

#### Conversion

```scss
@use '~@pixelherz/sassbox';

.foo {
  font-size: sassbox.pxToRem(24px); // 1.5rem
}

.bar {
  font-size: sassbox.remToPx(1.5rem); // 24px
}

.baz {
  font-size: sassbox.strip-unit(16cm) * 1px; // 16px
}
```

#### CSS Grid

```scss
// Configuration

@use '~@pixelherz/sassbox' with (
  // `gutter-type`: Use `static` for fixed-width gutters (px) `fluid` for 
  // relative sized gutters (%)
  $css-grid: (
      default: (
        cols-num: 6,
        col-width: 40px,
        gutter-width: 12px,
        gutter-type: 'static',
      ),
      rabbit: (
        cols-num: 9,
        col-width: 62px,
        gutter-width: 20px,
        gutter-type: 'static',
      ),
      cat: (
        cols-num: 12,
        col-width: 84px,
        gutter-width: 32px,
        gutter-type: 'static',
      ),
  ),
);

// Usage

.layout {
  display: grid;
  @include sassbox.inject-css-grid();
}
```

#### Font-Size

Helper for responsive font-sizes. 

```scss
// Configuration

@use '~@pixelherz/sassbox' with (
  $font-sizes: (
    s: 16px,
    m: 24px,
    l: 36px,
  ),
  $line-heights: (
    s: 20px,
    m: 30px,
    l: 45px,
  ),
  $letter-spacing: (
    s: 0.01em,
    m: 0.005em,
    l: 0,
  ),
  // Vertical spacing (margin-top, margin-bottom), browser default is `1em`
  // The example configuration below sets equal to line-height for vertical space of a blank line
  // Same as `$ph-vertical-spacing: $ph-line-heights;`
  $vertical-spacing: (
    s: 20px,
    m: 30px,
    l: 45px,
  ),
  // 'Fluid' font sizes are scaled down for the given responsive breakpoints
  $fluid-type: (
    l: (
      default: 'm',
      rat: 'l',
    ),
    m: (
      default: 's',
      rat: 'm',
    ),
  ),
);

// Usage

.title {
  @include sassbox.font-size('l');
}

.paragraph {
  @include sassbox.font-size('m', $set-vertical-offset: true);
}
```

#### Grid

Function `grid-max-offset()` returns the max value from map `$grid-offset`. 

Mixin `apply-grid-offset()` applies the offset defined in `$grid-offset`.

```scss
// Configuration

@use '~@pixelherz/sassbox' with (
  $grid-offset: (
    default: 20px,
    mouse: 40px,
    rabbit: 80px,
  ),
  $layout-max-width: 1360px,
);

// Usage

.page {
  // grid-max-offset() will return `80px`
  max-width: #{sassbox.$layout-max-width + (sassbox.grid-max-offset() * 2)};
}

.layout {
  // $prop defaults to 'margin'
  @include sassbox.apply-grid-offset($prop: 'padding');
}
``` 

```html
<div class="page">
  <div class="layout"></div>
</div>
```

#### Relative Grid (legacy)

> Relative grid (rel-grid) refers to a legacy-style fluid grid (no CSS grid involved). Same grid is used for *all* breakpoints.

Function `grid-width()` calculates grid widths based on the given params and returns the width as absolute (`px`) or relative (`%`) value.

NOTE: The gutters enclosed by columns must not be declared in the gutters
parameter (ie. param `$cols: 3` returns the width of 3 cols and 2 gutters).The `$gutters` param is used only for extra-gutter (left/right of the cols).

**Parameters**
Name | Type | Default | Description
-----|------|---------|------------
`$cols` | int | 0 | Number of columns the width should span
`$gutters` | int | 0 | Number of extra gutters the width should span
`$base-cols` | enum int | all | Number of columns used as base for relative values. Use this param if the parent element is not using the grid's full layout width.
`$base-gutters` | int | 0 | The number of extra gutters to be included in the base calculation. NOTE: Gutters enclosed by colums ($base-cols) must not be declared. This param is used only for extra gutters *outside* the $base-cols.
`$base-extra` | int | 0 | Accepts a px value to adjust base width (e.g. if the base does not align with the global grid).
`$scale` | enum | rel | Use `rel` to return a relative value (%) or `abs` to return an absolute value (px).

**Example**
```scss
// Configuration

// Import sub-module sassbox/utils/rel-grid
@use '~@pixelherz/sassbox' with (
  // Layout width in `px` without outer gutter/offset
  $layout-max-width: 1360px,
  // Gutter width in `px`
  $rel-grid-gutter-width: 32px,
  // Column width in `px`
  $rel-grid-col-width: 84px,
  // Grid offset / outer gutter / horizontal margin
  $grid-offset: (
    default: 15px,
    mouse: 30px,
    rabbit: 60px,
  ),
);

// Usage

// 3 column layout
.col {
  width: sassbox.grid-width($cols: 4);
  margin-right: sassbox.grid-width($gutters: 1);
  &:nth-of-type(3n + 0) {
    margin-right: 0;
  }
}
```

#### Offset Text

Hide text of an element.

```html
<h1 class="logotype">Company Name</h1>
```

```scss
@use '~@pixelherz/sassbox';

.logotype {
  // The text "Company Name" will be set off-element in favor of the background image
  @include sassbox.offset-text();
  background-image: url('logotype.svg');
}
```

#### Show relative grid

Display the relative grid by adding a class-name to the `html` element. The class-name defaults to `show-rel-grid`. You can optionally pass a custom class-name. 

```scss
@use '~@pixelherz/sassbox';
@include sassbox.show-rel-grid($class-name: 'show-grid');
```

```html
<html class="show-grid">
```

#### Un-Button

Remove ugly default-styling from `button` element. 

```scss
@use '~@pixelherz/sassbox';

.action-button {
  @include sassbox.un-button();
}
```


## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/Pixelherz/sassbox/tags). 


## License

This project is licensed under the ISC License - see the [LICENSE.md](LICENSE.md) file for details.


## Contact

Pixelherz  
Design und Code für Digitales

mail@pixelherz.com

Pixelherz GmbH  
Allmendstrasse 61  
CH-8041 Zürich

pixelherz.com
