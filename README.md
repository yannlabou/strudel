# strudel

The [fly.io Distributed Systems Challenge](https://fly.io/dist-sys/) soon to be implemented in C++.

## Building

```
mkdir -p build
cmake -GNinja -S . -B build -DCMAKE_TOOLCHAIN_FILE=cmake/gcc-toolchain.cmake
ninja -C build
```
