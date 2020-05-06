# Initial State

Before beginning any implementation work, some *scout* work was done to collate existing information from pre-existing attempts. The summary from each attempt is listed below.

### Jojolepro &ndash; [amethyst:wasm](https://github.com/jojolepro/amethyst/tree/wasm)

<details>

<summary>Attempt at getting `amethyst` to compile with `wasm-bindgen`.</summary>

* Top down approach &ndash; try to get `amethyst` to compile for wasm with minimal features, then incrementally enable crates.
* Partial update of winit to 0.21.
* Places crates / code behind feature toggles.

Relevant commits:

* [`f6dd55e4`]

    - removes `backtrace` from `amethyst_error`
    - places the following crates under a feature flag in `Cargo.toml`:

        + amethyst_controls
        + amethyst_input
        + amethyst_ui
        + amethyst_utils
        + amethyst_window
        + winit
        + failure

* [`2c9a78f2`]: adds `#[cfg(feature = "renderer")]` in main `amethyst` crate.
* [`ebeec5fb`]

    - Bumps `winit` to `0.21` and updates features.
    - Puts the following behind feature flags:

        + `amethyst_audio`
        + `amethyst_ui`

    - Removes `#[cfg(feature = "renderer")]` from `src/app.rs:30`

[`f6dd55e4`]: https://github.com/jojolepro/amethyst/commit/f6dd55e40745a6bac10d7ad70235e3fe8f253569
[`2c9a78f2`]: https://github.com/jojolepro/amethyst/commit/2c9a78f201716d6c0f2f6bf2de727d749efa1ede
[`ebeec5fb`]: https://github.com/jojolepro/amethyst/commit/ebeec5fbeff47be5efd23737f6ef9aecb42b9d26

</details>

### Semtexv &ndash; [`amethyst:rendy-all`](https://github.com/semtexzv/amethyst/commits/rendy-all) (based on [#2040](https://github.com/amethyst/amethyst/pull/2040))

<details>

<summary>Updates `amethyst` to use `winit 0.21` and `rendy 0.5`.</summary>

Summary:

* Updates winit to 0.21, including `Event` and screen logical / physical size changes.
* Updates rendy to 0.5.1.
* Updates most (all?) examples to properly run with `winit`'s new event loop mechanism.

Interesting diff:

```rust,ignore
/// # Examples
///
/// ~~~no_run
/// let event_loop = EventLoop::new();
/// let mut game = Application::new(assets_dir, Example::new(), game_data)?;
/// game.initialize();
/// event_loop.run(move |event, _, control_flow| {
///     #[cfg(feature = "profiler")]
///     profile_scope!("run_event_loop");
///     log::trace!("main loop run");
///     game.run_winit_loop(event, control_flow)
/// })
/// ~~~
```

</details>

### Omni-viral &ndash; [`amethyst:gl`](https://github.com/omni-viral/amethyst/tree/gl) (PR [#1877](https://github.com/amethyst/amethyst/pull/1877))

<details>

<summary>The first attempt that compiled and ran.</summary>

* Updates winit to `0.20.0-alpha2`.
* Disables the following crates:

    - `amethyst_audio`
    - `amethyst_network`

    Also for `amethyst_gltf`:

    - `mikktspace`

* Removes usage of `rayon::ThreadPool`.
* Changes shader compilation script, and recompiles all shaders.

</details>

### Jojolepro &ndash; [`web_worker`](https://github.com/jojolepro/web_worker)

Allows `rayon::ThreadPool` to be used by using a custom constructor.

### Jaynus &ndash; [`rendy:jaynus-fixes`](https://github.com/jaynus/rendy/commits/jaynus-fixes)

* Bumps `gfx-hal` to latest git master as of March 11, 2020
* Compiles `rendy/rendy` examples to WASM using `wasm-bindgen`
