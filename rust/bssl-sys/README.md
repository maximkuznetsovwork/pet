bssl-sys
============

A low-level binding crate for Rust that moves in lockstop with BoringSSL.

### How it works
`bssl-sys` uses `bindgen` as part of the cmake build process to generate Rust compatibility shims for the targeted platform. It is important to generate it for the correct platform because `bindgen` uses LLVM information for alignment which varies depending on architecture.

### To Use
1. Build `boringssl` with `-DRUST_BINDINGS=<rust-triple>`, which should match the [Rust target triple](https://doc.rust-lang.org/nightly/rustc/platform-support.html) when building `bssl-sys`,
2. install `bindgen`, and
3. install [`cargo-deny`](https://github.com/EmbarkStudios/cargo-deny).

After that, the `bssl-sys` crate can be built. By default, it looks for `bindgen` output and BoringSSL static libraries in the `build` directory. This can be reconfigured with `BORINGSSL_BUILD_DIR` environment variable. Note the environment variable is evaluated relative to `rust/bssl-sys/src`, so using an absolute path may be more convenient.
