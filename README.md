This repo shows the effects of non-purely numeric version numbers in a rust workspace:

* Two crates `lib-foo` and `lib-bar`.
* `lib-foo` depends on `lib-bar`
* `lib-bar` is at version `0.1.0-dev.0`
* `lib-foo` still declares its dependency on `lib-bar` at version `0.1.0`.

The result is a workspace that can not function: cargo errors out with:

```
error: no matching package named `lib-bar` found
location searched: /Users/asf/Mess/current/cargo-release-test/lib-bar
prerelease package needs to be specified explicitly
lib-bar = { version = "0.1.0-dev.0" }
required by package `lib-foo v0.1.0 (/Users/asf/Mess/current/cargo-release-test/lib-foo)`
```