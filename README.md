# EpiDocker

Docker image based on Alpine Linux to prepare a build and runtime environment around [Epifaster](https://github.com/lukas-sgx/Epifaster) and [Criterion](https://github.com/Snaipe/Criterion).

## Image Contents

The image installs:

- `clang20` and `clang20-rtlib`
- `make`, `build-base`, `cmake`, `meson`, `ninja`
- `gcovr`
- `libffi-dev` and `libgit2-dev`
- Criterion, built and installed from source
- Epifaster, cloned from the official GitHub repository
- the `epiclang` binary available in `/usr/bin/epiclang`
- the plugins copied to `/usr/lib/epiclang/`

## Build

```bash
docker build -t epi-docker:tek1 .
```

## Usage

The final image exposes the `epiclang` executable in the `PATH`.

Example:

```bash
docker run --rm -it epi-docker:tek1 epiclang --help
```

## Notes

- The build clones `Epifaster` and `Criterion` directly from GitHub during image construction.
- The image removes build dependencies after installation to keep the final size smaller.
- This project does not yet contain a run script or application source code outside of the `Dockerfile`.

## Project Structure

```text
.
├── Dockerfile
└── README.md
```
