# Con's temporary native-presentation compatibility snapshot

These three packages are copies of the published `gpui-pre` 0.3.7 packages,
based on Zed revision `1a28cff4b409169bac058bca40dfbfeb7621d19b`.
Their manifests retain the original registry dependencies and package versions.
Con patches all three packages together to preserve one compatible GPUI type
identity with its existing components and assets.

Modified source files contain only the frame-scoped native presentation API
and its tests, ported from the reviewed candidate at
`8bd2ec8cd022e3b4c2a0d62e9b39b4c0f1508aa1`:

- `gpui-pre/src/platform.rs`
- `gpui-pre/src/window.rs`
- `gpui-pre-apple/src/metal_renderer.rs`
- `gpui-pre-macos/src/window.rs`

The Apple test is placed in a new test module because this older snapshot does
not contain the newer upstream renderer test module. The production algorithm
is unchanged. Original copyright and Apache-2.0 licensing are retained; the
repository's `LICENSE-APACHE` applies to these packages.

Each changed source file carries a modification notice. The manifests and
all other package files remain identical to the published snapshot.

This is not an upstream package release. Remove Con's overrides when a
compatible official snapshot and component pair includes the API. No registry
files or local `3pp` sources are changed by consumers.

Native macOS verification of this compatibility graph passed 348 core, five
Apple, and 12 macOS unit tests, including the four presentation regressions.
An initial run failed an unchanged spring-animation timing test; the complete
rerun passed. This is separate from verification of the newer official source
candidate. Windows/Linux runtime validation remains a consumer CI requirement.
