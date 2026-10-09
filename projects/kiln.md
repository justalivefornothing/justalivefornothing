# Kiln

A small typed language that compiles to WebAssembly in the browser.

[Source and run instructions](https://github.com/justalivefornothing/kiln-lang) · TypeScript · WebAssembly

![Kiln bytecode inspector and Mandelbrot canvas output](../assets/kiln-preview.png)

The editor connects source code to tokens, a syntax tree, emitted bytes, disassembly, and program output. The compiler writes WebAssembly binaries directly. The Mandelbrot example draws through the canvas host's `setpixel` function.

## Supported subset

- `i32`, `f32`, and `bool` values, with explicit numeric casts and local type inference.
- Functions, recursion, lexical scopes, conditionals, and loops.
- Linear-memory views and host functions for printing and drawing on a 256 × 256 canvas.

There are no strings, structs, modules, or general array type. Emitted modules start with one 64 KiB memory page; the language does not expose memory growth. There is no separate optimization stage.

## A concrete fix

[Keep program execution off the UI thread (#1)](https://github.com/justalivefornothing/kiln-lang/pull/1), merged September 24, 2026, removed the inline-execution fallback. When workers were unavailable, that fallback could let an infinite loop freeze the UI and bypass cancellation.

Programs now run in a dedicated worker. Cancellation and the default eight-second timeout terminate it. If worker creation fails, compilation and inspection remain available, while execution reports an error.

The [runner](https://github.com/justalivefornothing/kiln-lang/blob/main/src/runtime/runner.ts) and [runtime tests](https://github.com/justalivefornothing/kiln-lang/blob/main/src/runtime/runner.test.ts) show the behavior and its regression coverage.

[Back to profile](../README.md)
