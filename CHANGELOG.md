# Changelog

## 8.0.0

Update to gren v0.6.x


## 7.0.0

Update to gren v0.5.x


## 6.0.0

- Updated to gren 0.4.x and the new node package.
- Replaced Path & Focus modules with `FileSystem.Path` from Gren's node package.
- Should technically work on Windows now (not tested though)


## 5.1.0

Changed the behaviour of the `Shikensu.programs` function, programs are now performed sequentially instead of concurrently (+ the documentation of the function now states this).

## 5.0.1

Fixes an issue with listing extension-less files.

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
