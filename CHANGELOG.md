# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.4.0](https://github.com/duchess-rs/duchess/compare/duchess-v0.3.0...duchess-v0.4.0) - 2026-06-08

### Fixed

- replace deprecated TempDir::into_path() with TempDir::keep() ([#210](https://github.com/duchess-rs/duchess/pull/210))

### Other

- Add JDK 25 to CI and fix Class.isInterface/isArray/isPrimitive incompatibility ([#208](https://github.com/duchess-rs/duchess/pull/208))
- Update rust.yml ([#203](https://github.com/duchess-rs/duchess/pull/203))
- Add -Xcheck:jni to java-to-rust tests ([#199](https://github.com/duchess-rs/duchess/pull/199))
- Fix issue on aarch64 with jdk-17.0.15+6-LTS ([#197](https://github.com/duchess-rs/duchess/pull/197))
- Add aarch64 to the testing matrix ([#198](https://github.com/duchess-rs/duchess/pull/198))
- Fix broken link in README.md ([#195](https://github.com/duchess-rs/duchess/pull/195))
- Rework Java function support ([#193](https://github.com/duchess-rs/duchess/pull/193))
- pretty-close-to-build-rs ([#188](https://github.com/duchess-rs/duchess/pull/188))
- Add array tests to the java-to-rust ui tests ([#189](https://github.com/duchess-rs/duchess/pull/189))
- introduce a build-rs and a `cargo-duchess` utility ([#187](https://github.com/duchess-rs/duchess/pull/187))
- rename `s/plumbing/semver_unstable`, hide in docs ([#186](https://github.com/duchess-rs/duchess/pull/186))
- extract codegen into macro-rules macros ([#185](https://github.com/duchess-rs/duchess/pull/185))
- Fix autobless ([#184](https://github.com/duchess-rs/duchess/pull/184))
# 0.3.0 (July 22nd, 2024)
This release contains many improvements for calling Rust code from Java:
1. Add support for returning scalars (#181)
2. Allow specifying a minimum JNI version (#180)

**Breaking changes**:
1. `class` or `interface` when specified in `java_package` must actually match (#168). If you get an error after upgrading, change the keyword in your `java_package` macro to match the actual type in Java.
2. A `duchess-reflect` crate has also been split out from the macro package.

**Bug fixes**:
* Fix bug where passing `None` for `Option<T>` resulted in a spurious error from Duchess (#182).

# 0.2.1 (June 4th, 2024)
* Add `JMX` APIs to Java prelude. These allow querying the current memory usage of the JVM.

# 0.2 (May 17th, 2024)
This release contains several breaking changes to be aware of:
1. The public API has been simplfied: Duchess references are now "global" references by default. The `to_rust`, `global`, and `execute` combinators have all been merged. You now invoke `execute` and then the result depends on the return value: returning a `Java<T>` will create a global reference (matching the previous behavior of `global`), and returning a Rust value like `String` will invoke the "to rust" conversion (like `to_rust` used to do). For context and examples of upgrading see https://github.com/duchess-rs/duchess/pull/147.

2. `Jvm::with` has been removed. You can no longer obtain explicit handles to the JVM, preventing panics due to nested `Jvm::with` invocations. For context and examples see https://github.com/duchess-rs/duchess/pull/147.

3. `JvmOp`, the type returned by most Duchess operations-in-progress is now `#[must_use]`. If you encounter this error in your code, note that the code as written had no effect. `JvmOp` does nothing unless `.execute()` is called.