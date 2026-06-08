# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.4.0](https://github.com/duchess-rs/duchess/compare/duchess-reflect-v0.3.0...duchess-reflect-v0.4.0) - 2026-06-08

### Fixed

- replace deprecated TempDir::into_path() with TempDir::keep() ([#210](https://github.com/duchess-rs/duchess/pull/210))

### Other

- Add JDK 25 to CI and fix Class.isInterface/isArray/isPrimitive incompatibility ([#208](https://github.com/duchess-rs/duchess/pull/208))
- Rework Java function support ([#193](https://github.com/duchess-rs/duchess/pull/193))
- pretty-close-to-build-rs ([#188](https://github.com/duchess-rs/duchess/pull/188))
- introduce a build-rs and a `cargo-duchess` utility ([#187](https://github.com/duchess-rs/duchess/pull/187))
- rename `s/plumbing/semver_unstable`, hide in docs ([#186](https://github.com/duchess-rs/duchess/pull/186))
- extract codegen into macro-rules macros ([#185](https://github.com/duchess-rs/duchess/pull/185))
