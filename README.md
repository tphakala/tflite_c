# TensorFlow Lite C API library precompiled for Linux and Windows systems

## Compile process for Linux

### Prerequisites

- bazelisk
- clang 16

```bash
$ git clone https://github.com/tensorflow/tensorflow.git
$ cd tensorflow
$ git checkout tags/v2.14.0
$ ./configure
You have bazel 6.1.0 installed.
Please specify the location of python. [Default is /usr/bin/python3]:
Found possible Python library paths:
  /usr/lib/python3/dist-packages
  /usr/local/lib/python3.9/dist-packages
Please input the desired Python library path to use.  Default is [/usr/lib/python3/dist-packages]
Do you wish to build TensorFlow with ROCm support? [y/N]:
No ROCm support will be enabled for TensorFlow.
Do you wish to build TensorFlow with CUDA support? [y/N]:
No CUDA support will be enabled for TensorFlow.
Do you want to use Clang to build TensorFlow? [Y/n]:
Clang will be used to compile TensorFlow.
Please specify the path to clang executable. [Default is /usr/lib/llvm-16/bin/clang]:
You have Clang 16.0.6 installed.
Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -Wno-sign-compare]:
Would you like to interactively configure ./WORKSPACE for Android builds? [y/N]:
Not configuring the WORKSPACE for Android builds.
Configuration finished
$ CC=clang bazelisk build -c opt //tensorflow/lite/c:libtensorflowlite_c.so
```

Compiled library is at bazel-bin/tensorflow/lite/c/
- libtensorflowlite_c.so

## Compile process for Windows

### Prerequisites

- bazelisk
- Visual Studio 2019
- msys2

```powershell
 git clone https://github.com/tensorflow/tensorflow.git
> cd tensorflow
> git checkout tags/v2.14.0
> .\configure
You have bazel 6.1.0 installed.
Please specify the location of python. [Default is C:\Users\developer\AppData\Local\Microsoft\WindowsApps\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\python.exe]:
Found possible Python library paths:
  C:\Program Files\WindowsApps\PythonSoftwareFoundation.Python.3.11_3.11.1776.0_x64__qbz5n2kfra8p0\Lib\site-packages
Please input the desired Python library path to use.  Default is [C:\Program Files\WindowsApps\PythonSoftwareFoundation.Python.3.11_3.11.1776.0_x64__qbz5n2kfra8p0\Lib\site-packages]
Do you wish to build TensorFlow with ROCm support? [y/N]:
No ROCm support will be enabled for TensorFlow.
WARNING: Cannot build with CUDA support on Windows.
Starting in TF 2.11, CUDA build is not supported for Windows. For using TensorFlow GPU on Windows, you will need to build/install TensorFlow in WSL2.
Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is /arch:AVX]:
Would you like to override eigen strong inline for some C++ compilation to reduce the compilation time? [Y/n]: N
Not overriding eigen strong inline, some compilations could take more than 20 mins.
Would you like to interactively configure ./WORKSPACE for Android builds? [y/N]:
Not configuring the WORKSPACE for Android builds.
Configuration finished
> $env:BAZEL_SH="C:/msys64/usr/bin/bash.exe"
> bazelisk.exe build --config=opt //tensorflow/lite/c:tensorflowlite_c
```

Compiled libraries are at bazel-bin\tensorflow\lite\c
  - libtensorflowlite_c.so
  - libtensorflowlite_c.dll
  - tensorflowlite_c.dll