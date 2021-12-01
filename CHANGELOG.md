sassbox - Sass utils we frequently use in our projects.

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Documentation

### Changed

- Configuration: The library is now configured via `@use "@pixelherz/sassbox" with (<configuration>)` thus we can omit the prefixes on configuration properties (e.g. `$ph-font-sizes` becomes `$font-sizes`). 

- Configuration: `$ph-font-family--default` is no longer needed, as normalize uses `font-family: inherit` instead of setting the value explicitly. 

- Namespace: The API now uses a single namespace and entry-point (`@use "~@pixelherz/sassbox"` instead of `@import "~@pixelherz/sassbox/sassbox"` which was used to import the complete library or `@import "~@pixelherz/sassbox/utils/grid"` which was used for feature-picking).

- Normalize is now served as `@mixin` instead of style import.

- Breakpoint manager: `sass-mq` is now served via API (`sassbox.mq()`).

- Show relative grid: The CSS used to render the grid is now injected via mixin `show-rel-grid`. 

- Typography: `font-size` and `line-height` are set in `rem` (was `px` before).

- Update `sass-mq@latest` (beta): The latest stable release (v5.x) uses division, which is deprecated. The beta (v6) uses `math.div` instead.

## [v0.11.1] - 2021-11-02

### Fixed

- SCSS: Fix broken import in util `font-size`.

## [v0.11.0] - 2021-10-11

### Added 

- Utils/Font-Size: Mixin `font-size` supports parameter `$set-vertical-spacing`. If set true, the mixin returns definitions for `margin-top` and `margin-bottom`.

## [v0.10.0] - 2021-09-27

### Added 

- Utils/Conversion: Add function `remToPx`

## [v0.9.0] - 2021-09-25

### Added

- Utils/Conversion: Add function `pxToRem`

## [v0.8.0] - 2021-06-28

### Changed

- Base/Normalize: Use `text-align: left` for `th`

## [v0.7.0] - 2020-12-08

### Changed 

- Base/Normalize: Use default font for `textarea` and `input`

## [v0.6.1] - 2020-11-25

### Fixed

- Base/Normalize: Reset `fieldset`'s `margin`

## [v0.6.0] - 2020-11-25

### Added 

- Base/Normalize: Add reset for `fieldset` and `legend`

## [v0.5.0] - 2020-11-17

### Added

- Utils/Grid: `apply-grid-offset()` takes argument `$prop`. Defaults to 'margin', might be used with props like 'padding'.

### Changed

- Utils: Do not allow implicit defaults. Defaults must be defined using key 'default'.

## [v0.4.0] - 2020-11-17

### Added

- Utils/Grid: Add mixin `apply-grid-offset()`

## [v0.3.0] - 2020-11-17

### Added

- Utils/Grid: Add CSS grid utils

### Changed

- Utils/Grid: **Breaking:** Rename `grid` → `rel-grid`
- Utils/Grid: **Breaking:** Rename `show-grid` → `show-rel-grid`

### Fixed

- Utils/Grid: Fix typo in docs

## [v0.2.0] - 2020-11-10

### Added

- Utils/Grid: Add `grid-max-offset()`

## [v0.1.0] - 2020-11-09

### Added

- Base
  - Normalize
- Utils
  - Font-Size
  - Grid
  - Offset-Text
  - Show-Grid
  - Un-Button

[Unreleased]: https://github.com/Pixelherz/sassbox/compare/v0.11.1...HEAD
[v0.11.1]: https://github.com/Pixelherz/sassbox/compare/v0.11.0...v0.11.1
[v0.11.0]: https://github.com/Pixelherz/sassbox/compare/v0.10.0...v0.11.0
[v0.10.0]: https://github.com/Pixelherz/sassbox/compare/v0.9.0...v0.10.0
[v0.9.0]: https://github.com/Pixelherz/sassbox/compare/v0.8.0...v0.9.0
[v0.8.0]: https://github.com/Pixelherz/sassbox/compare/v0.7.0...v0.8.0
[v0.7.0]: https://github.com/Pixelherz/sassbox/compare/v0.6.1...v0.7.0
[v0.6.1]: https://github.com/Pixelherz/sassbox/compare/v0.6.0...v0.6.1
[v0.6.0]: https://github.com/Pixelherz/sassbox/compare/v0.5.0...v0.6.0
[v0.5.0]: https://github.com/Pixelherz/sassbox/compare/v0.4.0...v0.5.0
[v0.4.0]: https://github.com/Pixelherz/sassbox/compare/v0.3.0...v0.4.0
[v0.3.0]: https://github.com/Pixelherz/sassbox/compare/v0.2.0...v0.3.0
[v0.2.0]: https://github.com/Pixelherz/sassbox/compare/v0.1.0...v0.2.0
[v0.1.0]: https://github.com/Pixelherz/sassbox/releases/tag/v0.1.0
