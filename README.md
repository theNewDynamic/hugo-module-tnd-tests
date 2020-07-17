# TND Tests Hugo Module

A simple repo to run unit tests on TND Module features. For now it only tests partials.

## Requirements

Requirements:
- Go 1.14
- Hugo 0.61.0


## Installation

If not already, [init](https://gohugo.io/hugo-modules/use-modules/#initialize-a-new-module) your project as Hugo Module:

```
$: hugo mod init {repo_url}
```

Configure your project's module to import this module:

```yaml
# config.yaml
module:
  imports:
  - path: github.com/theNewDynamic/hugo-module-tnd-tests
```

## Usage

Each partials to be tested can count as many as 10 unit tests, each sporting a different context and expected returned value.

### Directory Structure.

To create unit test on a given partial located or mounted in `layouts/partials/images/GetFeatureImage.html`
User should create two partials per unit tests:
1. `layouts/partials/tnd-tests/partials/images/GetFeaturedImage/1/context.html`
  The above should return the context to be passed to the partial for the unit test number 1
2. `layouts/partials/tnd-tests/partials/images/Add/1/GetFeaturedImage/excpected.html`
  The above should return the expected value returned by the partial when aforementioned context is passed.

#### GetFeaturedImage unit test 1

```
{{/* layouts/partials/tnd-tests/partials/images/GetFeaturedImage/1/context.html */}}
{{ return site.GetPage "/post/monaco" }}
```

```
{{/* layouts/partials/tnd-tests/partials/images/GetFeaturedImage/1/expected.html */}}
{{ return "/uploads/grand-prix.jpg" }}
```

#### GetFeaturedImage unit test 2
```
{{/* layouts/partials/tnd-tests/partials/images/GetFeaturedImage/1/context.html */}}
{{ return site.GetPage "/post/san-francisco" }}
```

```
{{/* layouts/partials/tnd-tests/partials/images/GetFeaturedImage/1/expected.html */}}
{{ return "/uploads/golden-gate.jpg" }}
```

### Some Partial/Feature

#### GetPartialUnitTests

This will return an array of the results and data of every unit tests of a given partial.

#### testPartial

This will return a boolean. True if every unit tests of a given partial succeeds, false if one or more fails.

## theNewDynamic

This project is maintained and love by [thenewDynamic](https://www.thenewdynamic.com).