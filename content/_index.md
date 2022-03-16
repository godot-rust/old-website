+++
title = "Juice"
sort_by = "weight"
+++

The **godot-rust** project provides high-level Rust bindings to the [Godot game engine](http://godotengine.org/).

Check out the current minor version [gdnative 0.10](https://crates.io/crates/gdnative) on crates.io, or visit
the project page on [GitHub](https://github.com/godot-rust/godot-rust).

See the list of all releases [here](@/releases.md).

# Design

Beside exposing the full range of Godot APIs, the bindings are also designed to make life easier for Rust developers, while allowing detailed control over what is done at runtime.

## Accurate memory/thread safety model

Built on Rust generics, godot-rust feature a memory/thread safety model that closely matches the actual behavior of the engine, enabling users to build abstractions that push unsafe actions towards the interface, and guarantee safety in internal code. Everything is entirely static and have no run-time cost in release mode.

## Convenient procedural macros

The bindings include procedural macros that automate away most of the GDNative boilerplate, from member registration to making sense of `Variant` structures, to timing functions in Godot's frame profiler. They're also being constantly improved!

## Comprehensive trait system

godot-rust makes full use of Rust's trait system to build nice abstractions, and allow customization of low-level behavior without incurring extra run-time cost. Traits are also used to express the class hierarchy within the Godot API, enabling static generic upcasts, and static prevention of impossible downcasts, even though there is no language-level inheritance in Rust.

## Full platform support

godot-rust supports all platforms where the Rust `std` and GDNative is available, including Windows, Mac, Linux, Android, and iOS.

# Installation

To create a GDNative library using godot-rust with Godot, [install `bindgen` dependencies][bindgen] and include the dependency in a `cdylib` crate. For detailed workflow, check out [the book][getting-started].

```toml
[dependencies]
gdnative = "0.10"

[lib]
crate-type = ["cdylib"]
```

# Example

The most general use case of the bindings will be to write Rust APIs that can be invoked from GDScript (so-called _Native Classes_).

As is tradition, a simple "Hello World" should serve as an introduction. For a full tutorial, check out ["Getting Started" from the user guide][getting-started]!

```rust
use gdnative::prelude::*;

#[derive(NativeClass)]
#[inherit(Node)]
pub struct HelloWorld;

#[methods]
impl HelloWorld {
    fn new(_owner: &Node) -> Self {
        HelloWorld
    }

    #[export]
    fn _ready(&self, _owner: &Node) {
        godot_print!("hello, world.");
    }
}

fn init(handle: InitHandle) {
    handle.add_class::<HelloWorld>();
}

godot_init!(init);
```

The [/examples](https://github.com/godot-rust/godot-rust/tree/master/examples) directory in the GitHub repo contains several ready to use examples, complete with Godot projects and setup for easy compilation from Cargo.

# License

godot-rust is licensed under the [MIT License](https://github.com/godot-rust/godot-rust/tree/master/LICENSE.md).

# Code of Conduct

The godot-rust organization follows the [Rust Code of Conduct][coc].  
For details and contact persons, please check out the [CoC on GitHub][github-coc].

[bindgen]: https://rust-lang.github.io/rust-bindgen/requirements.html
[getting-started]: https://godot-rust.github.io/book/getting-started
[coc]: https://www.rust-lang.org/policies/code-of-conduct
[github-coc]: https://github.com/godot-rust/.github/blob/master/CODE_OF_CONDUCT.md
