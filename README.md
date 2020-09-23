# SpConv_mod

This is a small modification of [spconv](https://github.com/traveller59/spconv) which uses less memory.

## Install

Please refer to the install instruction of original spconv.
https://github.com/traveller59/spconv/blob/master/README.md

## Usage

Just add ```version = "mod1"``` or  ```version = "mod2"```to the subM convolution function.    
```Python
import spconv
layer = spconv.SubMConv3d(in_channels = 1,
                          out_channels = 32,
                          kernel_size = 3,
                          stride = 1,
                          padding = 1,
                          use_hash = False,
                          version = "mod1") # or "mod2"
```

#### notice
1. only support subM convolution
2. the```algo```parameter needs to be ```ConvAlgo.Native``` (default)

## Comparison

input resolution:  1600 x 1600 x 40 x 1,
sparsity 90%,
output channels: 32,
batchsize: 4

|     version     | GPU memory | imgs/s |
| :-------------: | :--------: | :----: |
| original spconv |   6473MB   |  56.3  |
|      mod1       |   4471MB   |  59.2  |
|      mod2       |   4083MB   |  43.8  |

|     version     | GPU memory | imgs/s |
| :-------------: | :--------: | :----: |
| original spconv |   3747MB   |  14.3  |
|      mod1       |   2839MB   |  14.7  |
|      mod2       |   2023MB   |   8.2  |
