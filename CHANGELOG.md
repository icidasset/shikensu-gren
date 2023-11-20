# Changelog

## 5.0.0

* Added `Shikensu.bundle`
* Added `Shikensu.Contrib.enclose`
* Improved the `Bundle` type
* Removed `Shikensu.writeDefinition` (use `bundle` instead)

## 4.0.0

Moved the `currentWorkingDirectory` to the main `Shikensu` module so that it can use the `Error` type instead for ease of use.

## 3.0.0

* Added `Shikensu.perform`
* Added `Shikensu.Error.ErrorMessage`
* Exposed `Shikensu.writeDefinition`

## 2.0.2

Upgrade to version 3 of `gren-lang/node`.

## 2.0.1

Bump version range of `gren-lang/node`.

## 2.0.0

* Added `Shikensu.programs`
* Added missing headers so docs render properly
* Removed confusing `Compendium` type alias
* Forgot to export the Error module
* Forgot to export various functions
