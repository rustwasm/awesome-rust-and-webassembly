<meta charset="utf-8"/>

# Awesome Rust and Webassembly

A list of awesome Rust and WebAssembly projects, libraries, tools, and
resources.

## Contributing

[If you want to contribute, read this.](./CONTRIBUTING.md)

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
  <img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" />
</a>

This work is licensed under a <a rel="license"
href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons
Attribution-ShareAlike 4.0 International License</a>.

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Applications](#applications)
  - [Visualization](#visualization)
- [Development Tools](#development-tools)
  - [Build and Workflow Orchestration](#build-and-workflow-orchestration)
  - [Inspecting `.wasm` Binaries](#inspecting-wasm-binaries)
  - [Optimizing `.wasm` Binaries](#optimizing-wasm-binaries)
  - [Size Profiling `.wasm` Binaries](#size-profiling-wasm-binaries)
  - [Polyfilling WebAssembly](#polyfilling-webassembly)
  - [JavaScript Toolchains and Bundler Plugins](#javascript-toolchains-and-bundler-plugins)
- [Libraries](#libraries)
  - [Allocation and Memory Management](#allocation-and-memory-management)
  - [Error Handling](#error-handling)
  - [Games](#games)
  - [Interfacing with JavaScript and the DOM](#interfacing-with-javascript-and-the-dom)
  - [Interpreting and Compiling WebAssembly](#interpreting-and-compiling-webassembly)
  - [Parsing and Generating `.wasm` Binaries](#parsing-and-generating-wasm-binaries)
- [Resources](#resources)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

--------------------------------------------------------------------------------

## Applications

### Visualization

* [macro_railroad](https://github.com/lukaslueg/macro_railroad) —  Generating "railroad style" syntax diagrams for `macro_rules!()` macros. Diagrams are generated fully automatically from rust-source as Scalable Vector Graphics, using customizable CSS for layout.

* [snowhash](https://joshleeb.com/projects/snowhash/) — Procedurally generate a unique snowflake from a hash.

* [wasmbooth](https://github.com/mtharrison/wasmbooth) — Video effect booth written in Rust and WebAssembly.

## Development Tools

### Build and Workflow Orchestration

* [wasm-pack](https://github.com/rustwasm/wasm-pack) [![](https://img.shields.io/crates/d/wasm-pack.svg)](https://crates.io/crates/wasm-pack) [![](https://api.travis-ci.org/rustwasm/wasm-pack.svg?branch=master)](https://travis-ci.org/rustwasm/wasm-pack) — `wasm-pack` seeks to be a one-stop shop for building and working with Rust-generated WebAssembly that you would like to interoperate with JavaScript, on the Web or with Node.js. `wasm-pack` helps you build and publish Rust-generated WebAssembly to the npm registry to be used alongside any other JavaScript package in workflows that you already use.

### Inspecting `.wasm` Binaries

* [wasm-objdump](https://github.com/WebAssembly/wabt) [![](https://img.shields.io/crates/d/wabt.svg)](https://crates.io/crates/wabt) [![](https://api.travis-ci.org/WebAssembly/wabt.svg?branch=master)](https://travis-ci.org/WebAssembly/wabt) — Print low-level details about a `.wasm` binary and each of its sections. Also supports disassembling into the WAT text format. It's like `objdump` but for WebAssembly.

* [wasm-nm](https://github.com/fitzgen/wasm-nm) [![](https://img.shields.io/crates/d/wasm-nm.svg)](https://crates.io/crates/wasm-nm) [![](https://api.travis-ci.org/fitzgen/wasm-nm.svg?branch=master)](https://travis-ci.org/fitzgen/wasm-nm) — List the imported, exported, and private function symbols defined within a `.wasm` binary. It's like `nm` but for WebAssembly.

### Optimizing `.wasm` Binaries

* [wasm-gc](https://github.com/alexcrichton/wasm-gc) [![](https://img.shields.Io/crates/d/wasm-gc.svg)](https://crates.io/crates/wasm-gc) [![](https://api.travis-ci.org/alexcrichton/wasm-gc.svg?branch=master)](https://travis-ci.org/alexcrichton/wasm-gc) — A small tool to garbage collect a WebAssembly module and remove all unneeded exports, imports, functions, etc. This is effectively a `--gc-sections` linker flag for WebAssembly.

* [wasm-opt](https://github.com/WebAssembly/binaryen) [![](https://img.shields.io/crates/d/binaryen.svg)](https://crates.io/crates/binaryen) [![](https://api.travis-ci.org/WebAssembly/binaryen.svg?branch=master)](https://travis-ci.org/WebAssembly/binaryen) — The `wasm-opt` tool reads WebAssembly as input, runs transformation, optimization, and/or instrumentation passes on it, and then emits the transformed WebAssembly as output. Running it on the `.wasm` binaries produced by LLVM by way of `rustc` will usually create `.wasm` binaries that are both smaller and execute faster.

* [wasm-snip](https://github.com/rustwasm/wasm-snip) [![](https://img.shields.io/crates/d/wasm-snip.svg)](https://crates.io/crates/wasm-snip) [![](https://api.travis-ci.org/rustwasm/wasm-snip.svg?branch=master)](https://travis-ci.org/rustwasm/wasm-snip) — `wasm-snip` replaces a WebAssembly function's body with an `unreachable` instruction. This is useful for forcibly removing Rust's panicking infrastructure in non-debug production builds.

### Size Profiling `.wasm` Binaries

* [twiggy](https://github.com/rustwasm/twiggy) [![](https://img.shields.io/crates/d/twiggy.svg)](https://crates.io/crates/twiggy) [![](https://api.travis-ci.org/rustwasm/twiggy.svg?branch=master)](https://travis-ci.org/rustwasm/twiggy) — `twiggy` is a code size profiler for `.wasm` binaries. It analyzes a binary's call graph to answer questions about which functions take up the most space.

### Polyfilling WebAssembly

* [wasm2js](https://github.com/WebAssembly/binaryen) [![](https://img.shields.io/crates/d/binaryen.svg)](https://crates.io/crates/binaryen) [![](https://api.travis-ci.org/WebAssembly/binaryen.svg?branch=master)](https://travis-ci.org/WebAssembly/binaryen) — The `wasm2js` tool compiles WebAssembly into "almost asm.js". This is great for supporting browsers that don't have a WebAssembly implementation, such as Internet Explorer 11.

### JavaScript Toolchains and Bundler Plugins

* [rollup-plugin-rust](https://github.com/DrSensor/rollup-plugin-rust) [![](https://img.shields.io/npm/dt/rollup-plugin-rust.svg)](https://www.npmjs.com/package/rollup-plugin-rust) [![](https://img.shields.io/circleci/project/github/DrSensor/rollup-plugin-rust.svg?branch=master)](https://circleci.com/gh/DrSensor/rollup-plugin-rust) — A Rollup plugin that loads Rust code so it can be interop with Javascript base project.

* [rs-jest](https://github.com/DrSensor/rs-jest) [![](https://img.shields.io/npm/dt/rs-jest.svg)](https://www.npmjs.com/package/rs-jest) [![](https://img.shields.io/circleci/project/github/DrSensor/rs-jest.svg?branch=master)](https://circleci.com/gh/DrSensor/rs-jest) — Jest preprocessor/transformer for Rust. Build for seamless integration with a project that use rollup-plugin-rust.

* [rust-native-wasm-loader](https://github.com/dflemstr/rust-native-wasm-loader) [![](https://img.shields.io/npm/dt/rust-native-wasm-loader.svg)](https://www.npmjs.com/package/rust-native-wasm-loader) [![](https://travis-ci.org/dflemstr/rust-native-wasm-loader.svg?branch=master)](https://travis-ci.org/dflemstr/rust-native-wasm-loader) — A Webpack loader that loads Rust code as a WebAssembly module. It uses the native Rust support for compiling to wasm32 and does not require Emscripten.

* [wasm-pack-plugin](https://github.com/wasm-tool/wasm-pack-plugin) [![](https://img.shields.io/crates/v/wasm-pack-plugin.svg)](https://crates.io/crates/wasm-pack-plugin) [![](https://api.travis-ci.org/wasm-tool/wasm-pack-plugin.svg?branch=master)](https://travis-ci.org/wasm-tool/wasm-pack-plugin) — Webpack plugin for Rust and `wasm-pack`.

## Libraries

### Allocation and Memory Management

* [wee_alloc](https://github.com/rustwasm/wee_alloc) [![](https://img.shields.io/crates/d/wee_alloc.svg)](https://crates.io/crates/wee_alloc) [![](https://api.travis-ci.org/rustwasm/wee_alloc.svg?branch=master)](https://travis-ci.org/rustwasm/wee_alloc) — The Wasm-Enabled, Elfin Allocator. A small (~1K uncompressed `.wasm`) allocator implementation for when code size is a greater concern than allocation performance.

### Error Handling

* [console_error_panic_hook](https://github.com/rustwasm/console_error_panic_hook) [![](https://img.shields.io/crates/d/console_error_panic_hook.svg)](https://crates.io/crates/console_error_panic_hook) [![](https://api.travis-ci.org/rustwasm/console_error_panic_hook.svg?branch=master)](https://travis-ci.org/rustwasm/console_error_panic_hook) — This crate lets you debug panics on `wasm32-unknown-unknown` by providing a panic hook that forwards panic messages to `console.error`.

### Games

* [gate](https://github.com/SergiusIW/gate) [![](https://img.shields.io/crates/d/gate.svg)](https://crates.io/crates/gate) [![](https://api.travis-ci.org/SergiusIW/gate.svg?branch=master)](https://travis-ci.org/SergiusIW/gate) — Gate is a game development library tailored to 2D pixel-art games, written in Rust.

### Interfacing with JavaScript and the DOM

* [js-sys](https://github.com/rustwasm/js-sys) [![](https://img.shields.io/crates/d/js-sys.svg)](https://crates.io/crates/js-sys) [![](https://api.travis-ci.org/rustwasm/wasm-bindgen.svg?branch=master)](https://travis-ci.org/rustwasm/wasm-bindgen) — Raw `wasm-bindgen` imports for all the JavaScript global types and methods, such as `Object`, `Function`, `eval`, etc. These APIs are portable across all standard ECMAScript environments, not just the Web, such as Node.js.

* [wasm-bindgen](https://github.com/rustwasm/wasm-bindgen) [![](https://img.shields.io/crates/d/wasm-bindgen.svg)](https://crates.io/crates/wasm-bindgen) [![](https://api.travis-ci.org/rustwasm/wasm-bindgen.svg?branch=master)](https://travis-ci.org/rustwasm/wasm-bindgen) — `wasm-bindgen` facilitates high-level interactions between Rust and JavaScript. It allows one to import JavaScript things into Rust and export Rust things to JavaScript.

* [wasm-bindgen-futures](https://github.com/rustwasm/wasm-bindgen-futures) [![](https://img.shields.io/crates/d/wasm-bindgen-futures.svg)](https://crates.io/crates/wasm-bindgen-futures) [![](https://api.travis-ci.org/rustwasm/wasm-bindgen.svg?branch=master)](https://travis-ci.org/rustwasm/wasm-bindgen) — `wasm-bindgen-futures` is a bridge connecting JavaSript `Promise`s and Rust `Future`s. It can convert in both directions and is useful when working with asynchronous tasks in Rust, and allows interacting with DOM events and I/O operations.

### Interpreting and Compiling WebAssembly

* [cranelift-wasm](https://github.com/CraneStation/cranelift-wasm) [![](https://img.shields.io/crates/d/cranelift-wasm.svg)](https://crates.io/crates/cranelift-wasm) [![](https://api.travis-ci.org/CraneStation/cranelift-wasm.svg?branch=master)](https://travis-ci.org/CraneStation/cranelift-wasm) — Compile WebAssembly to the native host's machine code. Part of the Cranelift (né Cretonne) code generator project.

* [wasmi](https://github.com/paritytech/wasmi) [![](https://img.shields.io/crates/d/wasmi.svg)](https://crates.io/crates/wasmi) [![](https://api.travis-ci.org/paritytech/wasmi.svg?branch=master)](https://travis-ci.org/paritytech/wasmi) — An embeddable WebAssembly interpreter.

### Parsing and Generating `.wasm` Binaries

* [parity-wasm](https://github.com/paritytech/parity-wasm) [![](https://img.shields.io/crates/d/parity-wasm.svg)](https://crates.io/crates/parity-wasm) [![](https://api.travis-ci.org/paritytech/parity-wasm.svg?branch=master)](https://travis-ci.org/paritytech/parity-wasm) — Low-level WebAssembly format library for serializing, deserializing, and building `.wasm` binaries. Good support for well-known custom sections, such as the "names" section.

* [wasmparser](https://github.com/yurydelendik/wasmparser) [![](https://img.shields.io/crates/d/wasmparser.svg)](https://crates.io/crates/wasmparser) [![](https://api.travis-ci.org/yurydelendik/wasmparser.svg?branch=master)](https://travis-ci.org/yurydelendik/wasmparser) — A simple, event-driven library for parsing WebAssembly binary files.

## Resources

* [The Rust and WebAssembly Book](https://rustwasm.github.io/book) — The official Rust and WebAssembly book authored by the Rust and WebAssembly domain working group.
