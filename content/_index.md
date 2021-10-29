+++
title = "Juice"
sort_by = "weight"
+++

The **godot-rust** project provides high-level Rust bindings to the [Godot game engine](http://godotengine.org/).

(SOME TEST)

The latest version on crates.io is [gdnative 0.9.3](https://crates.io/crates/gdnative). Read the release notes [here](@/release-notes/0-9-3.md).

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

To create a GDNative library using godot-rust with Godot 3.2.3-stable, [install `bindgen` dependencies](https://rust-lang.github.io/rust-bindgen/requirements.html) and include the dependency in a `cdylib` crate. To use another version, see the [relevant chapter in the user guide](https://godot-rust.github.io/book/advanced-guides/custom-bindings.html).

```toml
[dependencies]
gdnative = "0.9.3"

[lib]
crate-type = ["cdylib"]
```

# Example

The most general use-case of the bindings will be to interact with Godot using the generated wrapper classes, as well as providing custom functionality by exposing Rust types as *NativeScript*s.

NativeScript is an extension for GDNative that allows a dynamic library to register "script classes" to Godot.

As is tradition, a simple "Hello World" should serve as an introduction. For a full tutorial, check out ["Getting Started" from the user guide](https://godot-rust.github.io/book/getting-started.html)!

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