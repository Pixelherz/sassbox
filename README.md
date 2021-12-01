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

Documentation is included in the npm packages (`./docs`). 

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
