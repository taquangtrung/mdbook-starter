# MdBook Starter Kit

The Rust's mdBook package is an excellent solution for writing documentation.
However, it currently does not support highlighting source code syntax of
Solidity and LLVM IR. This is a limitation from the external library
[highlightjs](https://highlightjs.org/), which does not enable that feature for Solidity and LLVM IR by
default.

In this starter kit, I support syntax highlighting for Solidity, LLVM IR, and
many other languages by providing my own customized library
[theme/highlight.js](theme/highlight.js). It is also equipped with the pretty source code color
scheme of StackOverflow.

To use this starter kit, you'll need [Rust's cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html) and [mdbook](https://rust-lang.github.io/mdBook/guide/installation.html) to be
installed. Then, you can clone the project directly to your local machine, add
your book content, and run `mdbook build` or `mdbook serve` from the root folder
of the project.
