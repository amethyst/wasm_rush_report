# Week 4: Audio and Rendering

## Summary

**Date:** 2020-04-05 to 2020-04-11

* GL depth buffer fix -- rendering is corrected on Windows.
* Audio plays in WASM, albeit delayed.

### End Result

<video controls><source src="2020-04-09_pong_wasm_audio.mp4" /></video>

## Implementation

1. Split audio logic from other systems. ([amethyst#2215], [amethyst#2216], [pong_wasm#2])

    This allows the rest of Pong to run even if audio is disabled.

2. Initialization stability on Windows:

    Make drag and drop `winit` feature optional. ([amethyst/winit#a2eea3e], [winit#1524])

3. Fixed `gfx` issues.

    - Clear GL depth buffer. ([gfx#35c45ac], [gfx#3202], [gfx#3205])
    - Load `Rgb8Srgb` texture format. ([gfx#c4b75d3], [gfx#3222], [gfx#3223])

4. Get audio to play on WASM.

    - Use [ishitatsuyuki/cpal#dpeckett-webaudio-poc], which is based off wasm-bindgen POC by `dpeckett`. ([amethyst/cpal#ee1ee1a], [cpal#372])
    - Send audio through `AudioBuffer` in JavaScript. ([amethyst#2195], [amethyst#2219])
    - Use `sed` hack to allow web workers to be instantiated without an `AudioContext`. ([pong_wasm#3])

[amethyst#2195]: https://github.com/amethyst/amethyst/issues/2195
[amethyst#2215]: https://github.com/amethyst/amethyst/issues/2215
[amethyst#2216]: https://github.com/amethyst/amethyst/issues/2216
[amethyst#2219]: https://github.com/amethyst/amethyst/pull/2219
[amethyst/cpal#ee1ee1a]: https://github.com/amethyst/cpal/commit/ee1ee1a957ec6b0f761dd2568ec487e33619ffbc
[amethyst/winit#a2eea3e]: https://github.com/amethyst/winit/commit/a2eea3e9a79c33b1c821e89c38782fc5788b77f7
[cpal#372]: https://github.com/RustAudio/cpal/pull/372
[gfx#3202]: https://github.com/gfx-rs/gfx/issues/3202
[gfx#3205]: https://github.com/gfx-rs/gfx/pull/3205
[gfx#3222]: https://github.com/gfx-rs/gfx/issues/3222
[gfx#3223]: https://github.com/gfx-rs/gfx/pull/3223
[gfx#35c45ac]: https://github.com/amethyst/gfx/commit/35c45acb43eebf989d06ba34141e43738d77b991
[gfx#c4b75d3]: https://github.com/amethyst/gfx/commit/c4b75d3d17f2fad7bd7ea93c8be8a92a6329d972
[ishitatsuyuki/cpal#dpeckett-webaudio-poc]: https://github.com/ishitatsuyuki/cpal/tree/dpeckett-webaudio-poc
[pong_wasm#2]: https://github.com/amethyst/pong_wasm/pull/2
[pong_wasm#3]: https://github.com/amethyst/pong_wasm/pull/3
[winit#1524]: https://github.com/rust-windowing/winit/pull/1524
