# Week 1: Contribution Baseline

## Summary

**Date:** 2020-03-16 to 2020-03-21

* Amethyst compiles to a WASM library.
* Repository forks and branches are created.
* Contribution guide is written.
* Basic CI check is set up.

| Repository               | Commit Range          |
| ------------------------ | --------------------- |
| [`pong_wasm`]            | `9b403f69^..9f6240fe` |
| [`amethyst`]             | `8044b2a5^..0af12f84` |
| [`rendy`]                | `27e5cdc1^..757c4aa9` |
| [`glutin`] \(fork\)      | `f29d87a3`            |
| [`gfx-rs`] \(fork\)      | `3e6db5f0`            |
| [`winit`] \(fork\)       | `26e4374a^..04225a39` |
| [`builder`] \(CI agent\) | `13730efd^..2bb67aae` |

### End Result

```bash
$ wasm-pack build -- --features "wasm gl"
# ..
[INFO]: :-) Done in 37.87s
[INFO]: :-) Your wasm pkg is ready to publish at ./pkg.
```

## Implementation

Based off the [`#2040`] branch, which has the changes to use the new `winit` [event loop] introduced in `winit 0.20.0`.

1. Get amethyst to compile with `winit 0.22.0` for better WASM support. ([winit#1478])
2. Attempt to compile amethyst with `wasm-pack`.

    Instructions from <https://rustwasm.github.io/docs/book/> were followed to package the library.

    When building with:

    ```bash
    wasm-pack build --target no-modules -- --features "wasm gl"
    ```

    - If it fails due to usage of a `-sys` library, feature gate the dependency and the code that uses it.
    - If it fails and requires a code change:

        1. Fork the repository.
        2. Create a `wasm` branch.
        3. Amend the code.
        4. Point `amethyst` at the forked repository.
        5. Make a pull request back to the original repository.

    Repeat until `wasm-pack` succeeds.

3. Create end-to-end application, and make sure it compiles: [`pong_wasm`].
4. Write [contribution guidelines]. ([amethyst#2171])

    Make it easy:

    - Links to all forks and branches.
    - Cut and paste commands.
    - Setup and development instructions.

5. Create [CI job] to build amethyst as a WASM library. ([amethyst#2175])

    **Note:** [CI agent] needs `wasm32-unknown-unknown` target, and `rust-src` component.

6. Publicise the WASM effort on the [community forum] and [chat server].

[`#2040`]: https://github.com/amethyst/amethyst/pull/2040
[`amethyst`]: https://github.com/amethyst/amethyst/commits/wasm
[`builder`]: https://github.com/amethyst/builder/pull/9/files
[`gfx-rs`]: https://github.com/amethyst/gfx/commits/wasm
[`glutin`]: https://github.com/amethyst/glutin/commits/wasm
[`pong_wasm`]: https://github.com/amethyst/pong_wasm
[`rendy`]: https://github.com/amethyst/rendy/commits/wasm
[`winit`]: https://github.com/amethyst/winit/commits/wasm
[amethyst#2171]: https://github.com/amethyst/amethyst/issues/2171
[amethyst#2175]: https://github.com/amethyst/amethyst/issues/2175
[chat server]: https://discord.gg/amethyst
[CI agent]: https://github.com/amethyst/builder/pull/9/files
[CI job]: https://github.com/amethyst/amethyst/commit/76644f5ab4f6e9588f4e9ef91f92bea525c59446#diff-58231b16fdee45a03a4ee3cf94a9f2c3
[community forum]: https://community.amethyst.rs/t/wasm-effort/1336
[contribution guidelines]: https://github.com/amethyst/amethyst/blob/wasm/docs/CONTRIBUTING_WASM.md
[event loop]: https://github.com/rust-windowing/winit/blob/master/CHANGELOG.md#0200-alpha-1-2019-06-21
[winit#1478]: https://github.com/rust-windowing/winit/pull/1478
