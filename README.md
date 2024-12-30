# TensorFlow Lite C API library precompiled for Linux and Windows systems

## Compile process for Linux

### Prerequisites for Linux build

- bazelisk
- clang 18

```bash
$ git clone https://github.com/tensorflow/tensorflow.git
$ cd tensorflow
$ git checkout tags/v2.17.1
$ CC=clang bazelisk build -c opt //tensorflow/lite/c:libtensorflowlite_c.so
```

Compiled library is at bazel-bin/tensorflow/lite/c/
- libtensorflowlite_c.so

## Compile process for macOS

### Prerequisites for macOS build

- bazelisk
- xcode

```zsh
> git clone https://github.com/tensorflow/tensorflow.git
> cd tensorflow
> git checkout tags/v2.17.1
> CC=clang CXX=clang++ bazelisk build \
    -c opt \
    --copt=-O3 \
    --copt=-flto \
    --linkopt=-flto \
    --define=tflite_enable_xnnpack=true \
    --define=xnnpack_enable_subgraph_reshaping=true \
    --define=no_tensorflow_py_deps=true \
    --strip=always \
    //tensorflow/lite/c:libtensorflowlite_c.dylib
```

Compiled libraries are at bazel-bin/tensorflow/lite/c
- libtensorflowlite_c.dylib

## Compile process for Windows

### Prerequisites for Windows build

- bazelisk
- clang 18
- msys2

```powershell
> git clone https://github.com/tensorflow/tensorflow.git
> cd tensorflow
> git checkout tags/v2.17.1
> $env:BAZEL_SH="C:/msys64/usr/bin/bash.exe"
> bazelisk.exe build --config=opt //tensorflow/lite/c:tensorflowlite_c
```

Compiled libraries are at bazel-bin\tensorflow\lite\c
- tensorflowlite_c.dll

