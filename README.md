# sassbox

Sass utils we frequently use in our projects.


## Getting Started

### Installing

Install using npm:

```sh
npm i @pixelherz/sassbox
```

## Usage

Import the toolbox in your project. 

```scss
@use '~@pixelherz/sassbox' [with (<my-config>)];
```

## Configuration

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

Have a look at the [Docs](#documentation) for a complete list of configuration options.

## Documentation

[Documentation is available online](https://pixelherz.github.io/sassbox/) included in the npm packages (`./docs`) or can be [built from source code](#build-docs).

### CSS grid vs. relative grid

Sassbox includes a bunch of mixins and functions that help you build grid layouts. Be aware that the library supports two flavours of layout grids:

- Relative grid (`rel-grid`)
- CSS grid (`css-grid`)

Variable, function and mixin names indicate their purpose (`rel-grid` for relative grids, `css-grid` for CSS grid).

### Write docs

We use [SassDoc](http://sassdoc.com) for documentation. 

### Build docs

```sh
npm run build-docs
```

## Upgrade

### Upgrade from v0.11.1 to v1.x

#### 1. Import

Update your `@forward`, `@use` or `@import` statement (`with` clause is optional). Usage of  `@import` [is discouraged](https://sass-lang.com/documentation/at-rules/import). We recommend to replace it with a configured `@forward`. If you prefere, you can also use `@use`.

```scss
// v0.x
@forward '~@pixelherz/sassbox/sassbox' [with (...)];
@use '~@pixelherz/sassbox/sassbox' [with (...)];
@import '~@pixelherz/sassbox/sassbox';
```

Use a single configured `@forward` to import the library. Then `@use` this forward. Note that _the import path has changed_. 

```scss
// Configured @forward
// e.g. styles/lib/_sassbox.scss 
@forward '~@pixelherz/sassbox' with (
  $breakpoints: (
    foo: 576px,
    bar: 768px
  ),
  $layout-max-width: 1360px,
  [...]
);
```

```scss
// Consume the configured forward in your app/components
// e.g. my-app/my-component/my-component.scss
@use '../../styles/lib/sassbox';
```

#### 2. Configuration

- Move configuration to the `with()` statement in your configured forward (s. [section import](#import)).
- Remove all prefixes from configuration variables (`ph-` and `mq-`).
- Rename the following configuration property

| v0.x                  | v1.x                    |
|-----------------------|-------------------------|
| `$grid-offset`        | `$layout-offset`        |

#### 3. Use namespace

```scss
// prior 1.x
@include offset-text();
// v1.x
@include sassbox.offset-text();
```

#### 4. Update deprecations

The names of some variables, functions and mixins have changed. Their signature has not changed. Update these with the new names.

| v0.x                  | v1.x                      |
|-----------------------|---------------------------|
| `un-button()`         | `reset-button()`          |
| `pxToRem()`           | `px-to-rem()`             |
| `remToPx()`           | `rem-to-px()`             |
| `font-size()`         | `use-type()`              |
| `inject-css-grid()`   | `use-css-grid()`          |
| `grid-offset`         | `layout-offset`           |
| `grid-width()`        | `get-rel-grid-width()`    |
| `grid-max-offset`     | `get-layout-max-offset()` |
| `apply-grid-offset()` | `use-layout-offset()`     |

#### 5. Normalize

In 0.x versions, normalize was applied by default. With 1.x, normalize has moved to a mixin to give you more control. When upgrading from 0.x you have to apply `sassbox.normalize()` manually which is typically done in your root stylesheet.

```scss
// e.g. styles.scss
@use "./styles/lib/sassbox";
@include sassbox.normalize();
```

#### 6. Test your app

That's it. Time to run and check your app!

- Check the console for errors or warnings.
- Make sure to double-check all parts of your app carefully.

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
