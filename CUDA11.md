## build with support for CUDA Compute Capability 3.5, 3/7
tested with NVIDIA Tesla K80, may also work with other ancient cards

testing environment:

NVIDIA driver 470

NVIDIA CUDA 11.8

# relevant mods:

[./discover/gpu.go]
```
(...)
var ( CudaComputeMajorMin = "3" CudaComputeMinorMin = "0" )
(...)
```

[./CMakePresets.json]
(...)
```
“name”: “CUDA 11”,
cacheVariables”:{
  “CMAKE_CUDA_ARCHITECTURES”:”35;37;50;52;53;60;61;70;75;80;86”
}
```
(...)

# build
```
mkdir build && cd build
cmake ..
make -j$(nproc)

go generate ./…
go build .
```

# run
```
./ollama serve
```
