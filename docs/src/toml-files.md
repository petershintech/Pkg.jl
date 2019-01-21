# [**9.** `Project.toml` and `Manifest.toml`](@id Project-and-Manifest)

Pkg uses toml for config files.

## `Project.toml`

Describes overall state.

### The `name` field

The name of the package/project is determined by the `name` field.
Example:
```toml
name = "Example"
```
The name can contain word characters `[a-zA-Z0-9_]`, but can
not start with a number. For packages it is recommended to follow
the [package naming guidelines](@ref Package-naming-guidelines).
The `name` field is mandatory for packages.


### The `uuid` field

`uuid` is a string with a [universally unique identifier]
(https://en.wikipedia.org/wiki/Universally_unique_identifier) for the package/project.
Example:
```toml
uuid = "7876af07-990d-54b4-ab0e-23690620f79a"
```
The `uuid` field is mandatory for packages.


### The `version` field
`version` is a string with the version number for the package/project.
Example:
```toml
version = "1.2.5"
```
Julia uses [Semantic Versioning](https://semver.org/) (SemVer) and the
`version` field should follow SemVer. The basic rules are:
* Before 1.0.0, anything goes, but when you make breaking changes
  the minor version should be incremented.
* After 1.0.0 only make breaking changes when incrementing the major version.
* After 1.0.0 no new public API should be added without incrementing the
  minor version. This includes, in particular, new types, functions, methods and
  method overloads, from e.g. `Base` or other packages.


### The `[deps]` section

Dependencies of the package/project are described in the `[deps]` section.
Each dependency is listed as a name-uuid pair, for example:

```toml
[deps]
Example = "7876af07-990d-54b4-ab0e-23690620f79a"
Test = "8dfed614-e22c-5e08-85e1-65c5234f0b40"
```


### The `[compat]` section

Compatibility constraints for the dependencies listed under `[deps]`
can be set in the `[compat]` section.
Example:

```toml
[deps]
Example =

[compat]
Example = "v1"
```

The [Compatibility](@ref) section describes the different possible
compatibility constraints in detail.


## `Manifest.toml`

Describes absolute state.

### `Manifest.toml` entries
