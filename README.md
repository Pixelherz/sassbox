# sassbox

Sass utils we frequently use in our projects.


## Getting Started

### Installing

Install using npm:

```
npm install --save @pixelherz/sassbox
```

## Usage

You can import the complete toolbox in your project, pick single modules or even sub-modules (s. examples below). 

```scss
// Import sassbox (complete)
@import '~@pixelherz/sassbox/sassbox';
```

### Base

```scss
// Import module sassbox/base
@import '~@pixelherz/sassbox/base/all';
```

#### Normalize

Reset, normalize or unify browser rendering. Includes global usage of `box-sizing: border-box`. 

```scss
// Config

// Button elements are forced to use the default font-family
$ph-font-family--default: 'Fancy Font', 'Helvetica', 'Arial', sans-serif;

// Import sub-module sassbox/base/normalize
@import '~@pixelherz/sassbox/base/normalize';
```

### Utils

```scss
// Import module sassbox/utils
@import '~@pixelherz/sassbox/utils/all';
```

#### CSS Grid

```scss
// Config

// `gutter-type`: Use `static` for fixed-width gutters (px) `fluid` for 
// relative sized gutters (%)

$ph-css-grid: (
    "default": (
        "cols-num": 6,
        "col-width": 40px,
        "gutter-width": 12px,
        "gutter-type": "static",
    ),
    "rabbit": (
        "cols-num": 12,
        "col-width": 62px,
        "gutter-width": 20px,
        "gutter-type": "static",
    ),
    "cat": (
        "cols-num": 12,
        "col-width": 84px,
        "gutter-width": 32px,
        "gutter-type": "static",
    ),
);

// Usage

// Import sub-module sassbox/utils/css-grid
@import '~@pixelherz/sassbox/utils/css-grid';

.layout {
  display: grid;
  @include inject-css-grid();
}
```

#### Font-Size

Helper for responsive font-sizes. 

```scss
// Config

// Font sizes
$ph-font-sizes: (
  's': 16px,
  'm': 24px,
  'l': 36px,
);

// Line heights
$ph-line-heights: (
  's': 20px,
  'm': 30px,
  'l': 45px,
);

// Letter spacing
// NOTE: If letter-spacing for a given key is `0` you can safely omit the key.
$ph-letter-spacing: (
  's': 0.01em,
  'm': 0.005em,
);

// 'Fluid' font sizes are scaled down for the given responsive breakpoints
$ph-fluid-type: (
  'l': (
    'default': 'm',
    'rat': 'l',
  ),
  'm': (
    'default': 's',
    'rat': 'm',
  ),
);

// Usage

// Import sub-module sassbox/utils/font-size
@import '~@pixelherz/sassbox/utils/font-size';

.title {
  @include font-size('m');
}
```

#### Grid

Function `grid-max-offset()` returns the max value from map `$ph-grid-offset`. 

Mixin `apply-grid-offset()` applies the offset defined in `$ph-grid-offset`.

```scss
// Import sub-module sassbox/utils/grid
@import '~@pixelherz/sassbox/utils/grid';

// Config
$ph-grid-offset: (
  'default': 20px,
  'mouse': 40px,
  'rabbit': 80px,
);

// Usage
.page {
  // grid-max-offset() will return `80px`
  max-width: #{$ph-layout-max-width + (grid-max-offset() * 2)};
}

.layout {
  @include apply-grid-offset();
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
// Config

// Layout width in `px` without outer gutter/offset
$ph-layout-max-width: 1360px;
// Gutter width in `px`
$ph-rel-grid-gutter-width: 32px;
// Column width in `px`
$ph-rel-grid-col-width: 84px;
// Grid offset / outer gutter / horizontal margin
$ph-grid-offset: (
  'default': 15px,
  'mouse': 30px,
  'rabbit': 60px,
);

// Usage

// Import sub-module sassbox/utils/rel-grid
@import '~@pixelherz/sassbox/utils/rel-grid';

// 3 column layout
.col {
  width: grid-width($cols: 4);
  margin-right: grid-width($gutters: 1);
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
// Import sub-module sassbox/utils/offset-text
@import '~@pixelherz/sassbox/utils/offset-text';

.logotype {
  // The text "Company Name" will be set off-element in favor of the background image
  @include offset-text();
  background-image: url('logotype.svg');
}
```

#### Show relative grid

Add class `show-rel-grid` to element `html` to show layout grid. 

```html
<html class="show-rel-grid">
```

```scss
// Import sub-module sassbox/utils/show-rel-grid
@import '~@pixelherz/sassbox/utils/show-rel-grid';
```

#### Un-Button

Remove ugly default-styling from `button` element. 

```scss
// Import sub-module sassbox/utils/un-button
@import '~@pixelherz/sassbox/utils/un-button';

.action-button {
  @include un-button();
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
