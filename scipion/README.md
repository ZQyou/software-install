# Install Scipion
https://scipion-em.github.io/docs/docs/scipion-modes/install-from-sources.html#

## Download Scipion
Download CentOS binary from http://scipion.i2pc.es/download_form/

## Configure Scipion
```
tar xf scipion_v2.0_2019-04-23_linux64_CentOS7.tgz
cd scipion
module load gnu/4.8.5 openmpi/3.1.4-hpcx cuda/8.0.61
./scipion config
```
The `config` option is failed to set CUDA and MATLAB. Manually changea `CUDA_LIB`, `CUDA_BIN`, `NVCC_INCLUDE` and `MATLAB_DIR` in `config/scipion.conf`
```
CUDA_LIB = /usr/local/cuda/8.0.61/lib64
CUDA_BIN = /usr/local/cuda/8.0.61/bin
NVCC_INCLUDE = /usr/local/cuda/8.0.61/include
MATLAB_DIR = /usr/local/matlab/R2018b
```
## Install
### Install basic packages
```
./scipion install -j 1
```
## Install plugins 
Install Xmipp3 and Eman2 plugins
```
./scipion installp -p scipion-em-xmipp  -j 1 -p scipion-em-eman2  -j 1
```
Install specific binaries for Xmipp3
```
./scipion installb xmippBin_Centos -j 1
```

# Test Scipion
https://scipion-em.github.io/docs/docs/developer/running-tests.html#running-tests

## Test classes and functions
```
./scipion test pyworkflow.tests.model.test_object
./scipion test pyworkflow.tests.model.test_mappers
./scipion test pyworkflow.tests.em.data.test_data
./scipion tests xmipp3.tests.test_convert_xmipp
```
All tests should be passed.

