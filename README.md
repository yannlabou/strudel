# strudel

The [fly.io Distributed Systems Challenge](https://fly.io/dist-sys/) soon to be implemented in C++.

## Building

```
mkdir -p build
cmake -GNinja -S . -B build -DCMAKE_TOOLCHAIN_FILE=cmake/gcc-toolchain.cmake

# Using mold as linker (https://github.com/rui314/mold)
cmake -GNinja -S . -B build -DCMAKE_TOOLCHAIN_FILE=cmake/gcc-toolchain.cmake -DCMAKE_C_FLAGS="-fuse-ld=mold" -DCMAKE_CXX_FLAGS="-fuse-ld=mold" 

ninja -C build
```
