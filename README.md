# Quijasi

Quijasi is an attempt to integrate Wasm3 into QuickJS to create a JavaScript + WebAssembly environment within WebAssembly and WASI. Hopefully, this will allow Emscripten builds to run on any WASI-capable runtime without extensive modifications.

## Building

To build Quijasi for the first time, or after major changes:
```
./build.sh
```

To rebuild Quijasi after minor changes:
```
cd build
make
```
