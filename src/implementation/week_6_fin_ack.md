# Week 6: Fin Ack

## Summary

**Date:** 2020-04-19 to 2020-04-25

* UI Coordinates / Screen Dimensions correction
* Configurable Web Logger
* Net Server and Client

### End Result

<div><iframe width="750" height="422" src="https://www.youtube.com/embed/Hc8EtqrlJsE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

## Implementation

1. Allow web logger to be configured. ([amethyst#2249], [amethyst#2250], [console_log#6])

    This was necessary as the rate of log messages was about 1000 messages per second. This meant:

    - Filtering for relevant log messages was extremely difficult.
    - The browser would lag and be unusable to work with.

2. Set canvas width/height only if unset. ([amethyst#2247], [amethyst/gfx#8537dfb], [gfx#3224], [gfx#3225])

    Quirk in this bug fix is, when setting the `"width"` attribute on the `<canvas>` element, the next read of `width()` still returns the old value. However, the updated value is returned after interacting with the canvas' WebGL2 graphics context.

3. Provide `WebSocket` transport layer implementation for `amethyst_network`. ([amethyst#2251], [amethyst#2253], [autexousious#209], [autexousious#221])

    - Use [`tungstenite`] for native targets.
    - Use `web-sys::WebSocket` for `wasm32-unknown-unknown` target.

[`tungstenite`]: https://crates.io/crates/tungstenite
[amethyst#2247]: https://github.com/amethyst/amethyst/issues/2247
[amethyst#2249]: https://github.com/amethyst/amethyst/issues/2249
[amethyst#2250]: https://github.com/amethyst/amethyst/pull/2250
[amethyst#2251]: https://github.com/amethyst/amethyst/issues/2251
[amethyst#2253]: https://github.com/amethyst/amethyst/pull/2253
[amethyst/gfx#8537dfb]: https://github.com/amethyst/gfx/commit/8537dfbe5ef742309496b7282a07653fc88f037d
[autexousious#209]: https://github.com/azriel91/autexousious/issues/209
[autexousious#221]: https://github.com/azriel91/autexousious/pull/221
[console_log#6]: https://github.com/iamcodemaker/console_log/pull/6
[gfx#3224]: https://github.com/gfx-rs/gfx/issues/3224
[gfx#3225]: https://github.com/gfx-rs/gfx/pull/3225
