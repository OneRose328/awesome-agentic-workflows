# Full Project Setup Example

This folder shows one way to organize multiple workflow source files before compiling them with `gh aw compile`.

## Suggested Layout

- `.github/workflows/issue-intake.md`
- `.github/workflows/pr-review-gate.md`
- `.github/workflows/release-digest.md`

This example now also includes the generated `.lock.yml` files so you can inspect the compiled output shape.

If you like the generated ASCII banner at the top of compiled files, a display copy is kept in [docs/gh-aw-banner.txt](../../docs/gh-aw-banner.txt).

In this example:

- The `.md` files are the source workflows you edit
- The `.lock.yml` files are the compiled outputs generated from those source files

Copy the source `.md` files into another repository, customize them, run `gh aw validate --dir .github/workflows`, then compile them with `gh aw compile --dir .github/workflows` to produce the matching `.lock.yml` files.

