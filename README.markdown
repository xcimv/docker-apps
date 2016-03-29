# Docker apps on archlinux

## Building the base image

  1. `cd archlinux/`
  2. `docker build --tag local/archlinux .`

Packages can be updated without rebuilding the entire image by setting `BUST_CACHE` on `docker build`:
```sh
docker build --build-arg "BUST_CACHE=$(date --iso-8601=s)" --tag local/archlinux .
```

## Building an app image

  1. `cd` into the directory of the app you want to build.
  2. Run `docker build --tag local/$app .`.

## Running an app

  1. Launch the app with the provided executable.

## License

Public Domain
