# How to Native executable application using JavaScript/TypeScript and CoffeeScript

Hello, everyone. What about it? This tutorial shows how to create a single-line executable using JavaScript, CoffeeScript, and TypeScript programming languages, right? So, It must be **Deno**, and **Bun** are examples of JavaScript or TypeScript engines.

We have you create single-line executable applications for this feature allows the distribution of a Deno and Bun application conveniently to a system. How about this step-by-step?

## `JavaScript/TypeScript`

   It can be TypeScript or JavaScript source file.

* <h3>Deno</h3>

   Cross-compiling to different target architectures is supported using the `--target flag`. On the first invocation of `deno compile`, Deno will download the relevant binary and cache it in `$DENO_DIR`. You can cross-compile binaries for other platforms by using the `--target` flag.

   ```bash
   # Windows
   $ deno compile --target x86_64-pc-windows-msvc src/format.js

   # Apple macOS
   $ deno compile --target x86_64-apple-darwin src/format.js
   $ deno compile --target aarch64-apple-darwin src/format.js

   # Linux
   $ deno compile --target x86_64-unknown-linux-gnu src/format.js
   $ deno compile --target aarch64-unknown-linux-gnu src/format.js
   ```

   **Supported Targets**: Deno supports cross compiling to all targets regardless of the host platform.

   | Operating System | Architecture | Target |
   |:-:|:-:|:-:|
   | Windows | x86_64 | `x86_64-pc-windows-msvc` |
   | macOS | x86_64 | `x86_64-apple-darwin` |
   | macOS | ARM64 | `aarch64-apple-darwin` |
   | Linux | x86_64 | `x86_64-unknown-linux-gnu` |
   | Linux | ARM64 | `aarch64-unknown-linux-gnu` |

   **Learn more** please: [Deno compile](https://docs.deno.com/runtime/reference/cli/compile)

* <h3>Bun</h3>

   Bun's bundler implements a `--compile` flag for generating a standalone binary from a TypeScript or JavaScript file.

   ```bash
   # Default operating system
   $ bun build ./src/format.js --compile --outfile format
   ```

   This bundles `format.js` into an executable that can be executed directly:

   ```bash
   $ ./format
   ```

   All imported files and packages are bundled into the executable, along with a copy of the Bun runtime.

   The `--target` flag lets you compile your standalone executable for a different operating system, architecture, or version of Bun than the machine you're running bun build on.

   ```bash
   # Windows
   $ bun build --compile --target=bun-windows-x64 ./src/format.js --outfile format
   $ bun build --compile --target=bun-windows-x64-baseline ./src/format.js --outfile format
   $ bun build --compile --target=bun-windows-x64-modern ./src/format.js --outfile format

   # Apple macOS
   $ bun build --compile --target=bun-darwin-arm64 ./src/format.js --outfile format
   $ bun build --compile --target=bun-darwin-x64 ./src/format.js --outfile format

   # Linux
   $ bun build --compile --target=bun-linux-x64 ./src/format.js --outfile format
   $ bun build --compile --target=bun-linux-x64-baseline ./src/format.js --outfile format
   $ bun build --compile --target=bun-linux-x64-modern ./src/format.js --outfile format
   # Note: the default architecture is x64 if no architecture is specified.
   $ bun build --compile --target=bun-linux-arm64 ./src/format.js --outfile format
   ```

   **Supported Targets**: Bun supports cross compiling to all targets regardless of the host platform.

   | Operating System | Architecture | Target |
   |:-:|:-:|:-:|
   | Windows | x86_64 | `--target=bun-windows-x64` |
   | Windows | x86_64 | `--target=bun-windows-x64-baseline` |
   | Windows | x86_64 | `--target=bun-windows-x64-modern` |
   | macOS | x86_64 | `--target=bun-darwin-x64` |
   | macOS | ARM64 | `--target=bun-darwin-arm64` |
   | Linux | x86_64 | `--target=bun-linux-x64` |
   | Linux | x86_64 | `--target=bun-linux-x64-baseline` |
   | Linux | x86_64 | `--target=bun-linux-x64-modern` |
   | Linux | ARM64 | `--target=bun-linux-arm64` |

   On x64 platforms, Bun uses SIMD optimizations which require a modern CPU supporting AVX2 instructions. The `-baseline` build of Bun is for older CPUs that don't support these optimizations. Normally, when you install Bun we automatically detect which version to use but this can be harder to do when cross-compiling since you might not know the target CPU. You usually don't need to worry about it on Darwin x64, but it is relevant for Windows x64 and Linux x64. If you or your users see "Illegal instruction" errors, you might need to use the baseline version.

   **Learn more** please: [Bun executables](https://bun.sh/docs/bundler/executables)

## `CoffeeScript`

   It can be CoffeeScript source file into JavaScript source file using `npm`.

   ```
   # npm
   $ npm run coffee

   # npx
   $ coffee -c -o dist src/format.coffee
   ```

# Copyright

Copyright (c) 2025 Cyril John Magayaga