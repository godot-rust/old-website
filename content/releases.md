+++
title = "Releases"
description = "Releases"
weight = 1
+++

This page gives a broad overview; check the [changelog] for details.

# 0.10.0 - 2022-03-19

After more than a year, version **0.10.0** brings a lot of progress to godot-rust. There are several new quality-of-life features, such as basic `async` and `serde` support, more flexible exporting of Rust symbols to Godot, better CI and doc integration, among many more. The API is now much more user-friendly than at version 0.9, with more consistent naming, flatter module structure and fewer redundancies.

For users coming from godot-rust 0.9, the [migration guide](https://godot-rust.github.io/book/advanced-guides/migrating-0-9.html) helps with updating code to 0.10.

# 0.10.0-rc.0 - 2022-02-21

A release candidate for upcoming the upcoming version 0.10. Allows preliminary testing and last-minute feedback.

# [0.9.3 - 2021-02-03](@/release-notes/0-9-3.md)

0.9.3 is an incremental release with improvements in documentation and API completeness. `GodotString` supports more operations, and support is added for a few common patterns.

The 0.9.2 version is skipped and yanked from crates.io due to an bug that was undetected due to a rustc regression.

This release is made from tag [`0.9.3`](https://github.com/godot-rust/godot-rust/tree/0.9.3), commit [`574e0f7`](https://github.com/godot-rust/godot-rust/commit/574e0f7bca7fd21738331316746f7bdd2844d44f).

Read the full release notes and changelog for this version [here](@/release-notes/0-9-3.md).

# [0.9.1 - 2020-10-19](@/release-notes/0-9-1.md)

0.9.1 is an incremental release with mostly bug fixes since the 0.9.0 release. Missing mathematic methods are added, as well as support for Godot RPC modes, thanks to contributions.

This release is made from tag [`0.9.1`](https://github.com/godot-rust/godot-rust/tree/0.9.1), commit [`97a0b41`](https://github.com/godot-rust/godot-rust/commit/97a0b4110449862716fb25cc3fea9d01c4da5553).

Read the full release notes and changelog for this version [here](@/release-notes/0-9-1.md).

# [0.9.0 - 2020-09-20](@/release-notes/0-9-0.md)

The 0.9.0 release consists of a massive redesign of the godot-rust API in order to solve long-standing soundness problems in the old API. 0.9.0 contains numerous breaking changes from previous versions. To help users update their code, we have created a [migration guide from godot-rust 0.8.x in the user guide](https://godot-rust.github.io/book/migrating-0-8.html).

This release is made from tag [`0.9.0`](https://github.com/godot-rust/godot-rust/tree/0.9.0), commit [`a370645`](https://github.com/godot-rust/godot-rust/commit/a370645363b85e10d3f1a49cd127174a4fb6bad9).

Read the full release notes and changelog for this version [here](@/release-notes/0-9-0.md).

# Earlier releases

Release notes are not available for releases before 0.9.0. For the changelog since 0.7.0, see [CHANGELOG.md][changelog] in the main repo.

[changelog]: https://github.com/godot-rust/godot-rust/blob/master/CHANGELOG.md