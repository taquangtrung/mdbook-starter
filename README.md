# MdBook Starter Kit

Rust's mdBook package is an excellent solution for writing documentation.
However, the current source code syntax highlighting feature, enabled by
[highlightjs](https://highlightjs.org/), still has not supported Solidity and LLVM IR.

In this starter kit, I support syntax highlighting for Solidity, LLVM IR, and
many other languages by using the customized library [theme/highlight.js](theme/highlight.js). It
is also equipped with the pretty source code color scheme of StackOverflow.

To use this starter kit, you'll need [Rust's cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html) and [mdbook](https://rust-lang.github.io/mdBook/guide/installation.html) to be
installed. Then, you can clone the project directly to your local machine, add
your book content, and run `mdbook build` or `mdbook serve` from the root folder
of the project.
