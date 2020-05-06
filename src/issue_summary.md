# Issue Summary

| Item                           | Crate(s)                  | WASM Rush links            | Upstream Status     |
| ------------------------------ | ------------------------- | -------------------------- | ------------------- |
| `Event`s must be `Clone`       | `winit`, `amethyst`       | [#2211], [#2040]           | ❌ [#1478]          |
| `rendy` to use `gfx-hal 0.5`   | `rendy`, `amethyst_rendy` | [rendy:wasm], [#2198]      | ❌ [#275], [#277]   |
| WASM: parallel dispatch        | `amethyst`, `web_worker`  | [#2177], [#2189]           | ❌ [#2191]          |
| Load assets asynchronously     | `amethyst_assets`         | [#2180], [#2182]           | ❌ [#2228]          |
| Load textures as thread local  | `amethyst_rendy`          | [#2174]                    | ✔️ [#2198]          |
| `winit` double borrow mut      | `winit`                   | [`4fbf95b`]                | ✔️ [#1512]          |
| `winit::requestAnimationFrame` | `winit`                   | [`3d5274b`]                | ✔️ [#1493], [#1519] |
| Use user provided `<canvas>`   | `rendy`, `amethyst_rendy` | [#2202], [`48915cb`], [#1] | ❓                  |
| Use same shader variable names | `amethyst_ui`             | [#2205], [#2207]           | ✔️                  |
| `winit` drag-n-drop optional   | `winit`                   | [`a2eea3e`]                | ❌ [#1524]          |
| Clear GL depth buffer          | `gfx-hal`                 | [`35c45ac`]                | ✔️ [#3202], [#3205] |
| Load `Rgb8Srgb` texture format | `gfx-hal`                 | [`c4b75d3`]                | ✔️ [#3222], [#3223] |
| Proper `AudioSocket` support   | `cpal`           | [`ee1ee1a`], [#2195], [#2219], [#3] | ❌ [#372], [#2222]  |
| Load configuration from server | `amethyst`                | [#2214], [#4]              | ❌                  |
| Integration test support       | `amethyst_test`           | [#2241], [#222], [#223]    | ✔️ [#2240], [#2245] |
| Configurable web logger        | `console_log`, `amethyst` | [#2249], [#2250]           | ✔️ [#6]             |
| Overwritten canvas dimensions  | `gfx-hal`                 | [#2247], [`8537dfb`]       | ✔️ [#3224], [#3225] |
| `WebSocket` transport layer    | `amethyst_network`        | [#2251], [#209], [#221]    | ✔️ [#2253]          |

[#1478]: https://github.com/rust-windowing/winit/pull/1478
[#1493]: https://github.com/rust-windowing/winit/issues/1493
[#1512]: https://github.com/rust-windowing/winit/pull/1512
[#1519]: https://github.com/rust-windowing/winit/pull/1519
[#1524]: https://github.com/rust-windowing/winit/pull/1524
[#1]: https://github.com/amethyst/pong_wasm/pull/1
[#2040]: https://github.com/amethyst/amethyst/pull/2040
[#209]: https://github.com/azriel91/autexousious/issues/209
[#2174]: https://github.com/amethyst/amethyst/issues/2174
[#2177]: https://github.com/amethyst/amethyst/issues/2177
[#2180]: https://github.com/amethyst/amethyst/issues/2180
[#2182]: https://github.com/amethyst/amethyst/pull/2182
[#2189]: https://github.com/amethyst/amethyst/pull/2189
[#2191]: https://github.com/amethyst/amethyst/issues/2191
[#2195]: https://github.com/amethyst/amethyst/issues/2195
[#2198]: https://github.com/amethyst/amethyst/pull/2198
[#2202]: https://github.com/amethyst/amethyst/issues/2202
[#2205]: https://github.com/amethyst/amethyst/issues/2205
[#2207]: https://github.com/amethyst/amethyst/pull/2207
[#2211]: https://github.com/amethyst/amethyst/issues/2211
[#2214]: https://github.com/amethyst/amethyst/issues/2214
[#2219]: https://github.com/amethyst/amethyst/pull/2219
[#221]: https://github.com/azriel91/autexousious/pull/221
[#2222]: https://github.com/amethyst/amethyst/issues/2222
[#2228]: https://github.com/amethyst/amethyst/issues/2228
[#222]: https://github.com/azriel91/autexousious/issues/222
[#223]: https://github.com/azriel91/autexousious/pull/223
[#2240]: https://github.com/amethyst/amethyst/pull/2240
[#2241]: https://github.com/amethyst/amethyst/issues/2241
[#2245]: https://github.com/amethyst/amethyst/pull/2245
[#2247]: https://github.com/amethyst/amethyst/issues/2247
[#2249]: https://github.com/amethyst/amethyst/issues/2249
[#2250]: https://github.com/amethyst/amethyst/pull/2250
[#2251]: https://github.com/amethyst/amethyst/issues/2251
[#2253]: https://github.com/amethyst/amethyst/pull/2253
[#275]: https://github.com/amethyst/rendy/issues/275
[#277]: https://github.com/amethyst/rendy/pull/277
[#3202]: https://github.com/gfx-rs/gfx/issues/3202
[#3205]: https://github.com/gfx-rs/gfx/pull/3205
[#3222]: https://github.com/gfx-rs/gfx/issues/3222
[#3223]: https://github.com/gfx-rs/gfx/pull/3223
[#3224]: https://github.com/gfx-rs/gfx/issues/3224
[#3225]: https://github.com/gfx-rs/gfx/pull/3225
[#372]: https://github.com/RustAudio/cpal/pull/372
[#3]: https://github.com/amethyst/pong_wasm/pull/3
[#4]: https://github.com/amethyst/pong_wasm/pull/4
[#6]: https://github.com/iamcodemaker/console_log/pull/6
[`35c45ac`]: https://github.com/amethyst/gfx/commit/35c45acb43eebf989d06ba34141e43738d77b991
[`3d5274b`]: https://github.com/amethyst/winit/commit/3d5274b9ccf0a6212cda3b01d058000f2555bfec
[`48915cb`]: https://github.com/amethyst/rendy/commit/48915cb29940dfaf4066a1ff9d148426defb9879
[`4fbf95b`]: https://github.com/amethyst/winit/commit/4fbf95b7ccf8ae9d3970e75d74c8f735f22e1a72
[`8537dfb`]: https://github.com/amethyst/gfx/commit/8537dfbe5ef742309496b7282a07653fc88f037d
[`a2eea3e`]: https://github.com/amethyst/winit/commit/a2eea3e9a79c33b1c821e89c38782fc5788b77f7
[`c4b75d3`]: https://github.com/amethyst/gfx/commit/c4b75d3d17f2fad7bd7ea93c8be8a92a6329d972
[`ee1ee1a`]: https://github.com/amethyst/cpal/commit/ee1ee1a957ec6b0f761dd2568ec487e33619ffbc
[rendy:wasm]: https://github.com/amethyst/rendy/commits/wasm
