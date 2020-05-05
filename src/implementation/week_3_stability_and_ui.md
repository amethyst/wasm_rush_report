# Week 3: Stability and UI

## Summary

**Date:** 2020-03-29 to 2020-04-04

* UI pass works
* WASM app doesn't crash 90% of the time from double mutable borrow in winit.

### End Result

![](pong_move.gif)

## Implementation

1. Winit stability fixes.

    - Fix double borrow mut. ([amethyst/winit#4fbf95b], [winit#1512])
    - Add `requestAnimationFrame` support to `winit`. ([amethyst/winit#3d5274b], [winit#1493], [winit#1519])

2. Take in HTML `<canvas>` element from user. ([amethyst#2202], [rendy#48915cb], [pong_wasm#1])

    - Update to `gfx-hal 0.5`.
    - Don't invert coordinate system. ([rendy#5d10084])

3. Fixed UI pass by using consistent shader variable names. ([amethyst#2205], [amethyst#2207])

[amethyst#2202]: https://github.com/amethyst/amethyst/issues/2202
[amethyst#2205]: https://github.com/amethyst/amethyst/issues/2205
[amethyst#2207]: https://github.com/amethyst/amethyst/pull/2207
[amethyst/winit#3d5274b]: https://github.com/amethyst/winit/commit/3d5274b9ccf0a6212cda3b01d058000f2555bfec
[amethyst/winit#4fbf95b]: https://github.com/amethyst/winit/commit/4fbf95b7ccf8ae9d3970e75d74c8f735f22e1a72
[pong_wasm#1]: https://github.com/amethyst/pong_wasm/pull/1
[rendy#48915cb]: https://github.com/amethyst/rendy/commit/48915cb29940dfaf4066a1ff9d148426defb9879
[rendy#5d10084]: https://github.com/amethyst/rendy/commit/5d100845cdae0b187e618bf3e8d130c21aeb2418
[winit#1493]: https://github.com/rust-windowing/winit/issues/1493
[winit#1512]: https://github.com/rust-windowing/winit/pull/1512
[winit#1519]: https://github.com/rust-windowing/winit/pull/1519
