# Locality sensitive Negative Sampling (LNS)

This repository includes the source code for two efficient negative sampling schemes proposed in the ICML 2021 paper [A Tale of Two Efficient and Informative Negative Sampling Distributions](http://proceedings.mlr.press/v139/daghaghi21a.html)

# Dataset

The dataset can be downloaded in [Amazon-670K](https://drive.google.com/file/d/0B3lPMIHmG6vGdUJwRzltS1dvUVk/view?resourcekey=0-lP9ETgM_DRMilESEUrWbHw). Note that the data is sorted by labels, so please shuffle at least the validation/testing data. 

# Build/Run LNS

## Prerequisites

CMake >= 3.0 Intel Compiler (ICC) >= 19

## Commands
```
mkdir -p bin && cd bin 
cmake .. -DCMAKE_CXX_COMPILER=icpc -DCMAKE_C_COMPILER=icc -DOPT_AVX512=1 -DOPT_AVX512_BF16=1
make -j
cd bin
OMP_NUM_THREADS=<num-of-logic-processor> KMP_HW_SUBSET=<num-of-sockets>s,<num-of-cores-per-socket>c,<num-of-logic-thread-per-core>t KMP_AFFINITY=compact,granularity=fine KMP_BLOCKTIME=200 ./runme ../SLIDE/Config_amz.csv
```
