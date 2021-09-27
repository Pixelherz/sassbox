sassbox - Sass utils we frequently use in our projects.

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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

[Unreleased]: https://github.com/Pixelherz/sassbox/compare/v0.10.0...HEAD
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
