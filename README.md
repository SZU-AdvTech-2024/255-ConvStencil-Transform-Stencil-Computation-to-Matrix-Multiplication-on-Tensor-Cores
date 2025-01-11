# ConvStencil

> ConvStencil: Transform Stencil Computation to Matrix Multiplication on Tensor Cores

## Prerequisites

- Hardware
    - x86-64 CPU
    - a single NVIDIA A100 GPU
- Software (attached in the docker image)
    - CUDA - 12.2 (Tested). Lower versions down to CUDA 11.0 are also supported, but it may affect the performance.
    - GCC - above 9.4.0. You may also try to use icx or clang.
    - cuDNN - above 8.0

## Getting Code
The code can be downloaded using git:
```
git clone https://github.com/microsoft/ConvStencil.git
```

## Compile

Use the following commands:
```
mkdir -p build
cd build
cmake ..
make all -j24
```

## Usage

You can run `convstencil` in the following input format.
```
convstencil_program shape input_size time_interation_size options
```
- `convstencil_program` can be chosen from `convstencil_1d`, `convstencil_2d`, and `convstencil_3d` for different dimensions.
- `shape` can be chosen by the different dimension:
    - `1d1r` and `1d2r` for 1D
    - `star2d1r`, `box2d1r`, `star2d3r` and `box2d3r` for 2D
    - `star3d1r` and `box3d1r` for 3D
- `input_size` depends on the number of dimensions; the number of inputs required is equal to the number of dimensions.
- `time_interation_size` is the iteration time.
- `options`:
    - `--help` prints the help information.
    - `--custom` inputs the custom stencil kernel weights.

