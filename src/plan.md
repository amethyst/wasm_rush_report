# Plan

Because a game engine covers many complex domains -- event loop, audio, graphics, etcetera -- we want to make sure there is a "good" starting state, and be able to develop and test each domain independently. In addition, we want to encourage contribution from the community where possible.

## Jump Start

The plan to create a stable equilibrium used is:

1. Get `amethyst` to compile for the `wasm32-unknown-unknown` target.
2. Set up an end-to-end project to test usage of `amethyst`.
3. Set up automated build to ensure all contributions maintain that base quality check.
4. Make it easier for potential contributors to get into the "build, test, contribute" loop.

## Equilibrium

There are two workflows for ongoing development:

* Discovery

    1. Run end-to-end project to discover issues.
    2. Open a GitHub issue for each issue, providing any stack traces or screenshots, and the expected behaviour for the resolution of the issue.
    3. Provide some initial investigation to where the root cause of the problem lies, to make it easier to begin working on a fix.

* Implementation

    1. Contributor finds an issue they wish to do.
    2. Locally, the contributor implements a fix, and tests it against end-to-end project.
    3. The change is submitted for review, and amended if necessary.
    4. After passing review and the automated build, the contribution is merged.
