# SOWFA - OpenFAST 安装说明

> [!WARNING] 
> 本文档包含我关于如何编译和安装**旧版且已弃用**的NREL/SOWFA与OpenFAST耦合的简要说明。**该软件目前未开发或维护，建议使用新版本SOWFA**。 
> 
> 更多关于SOWFA的最新版本，请访问[https://github.com/NREL/SOWFA-6](https://github.com/NREL/SOWFA-6)

## 要求

要运行SOWFA，您需要编译其三个主要组件：[**OpenFAST**](#openfast-compilation)，[**OpenFOAM 2.4.x**](#openfoam-24x-compilation)，和[**SOWFA**](#sowfa-compilation)。

但在此之前，您需要确保编译所有软件的机器具有适当的工具和额外软件。
首先，您需要几个编译器。对于OpenFOAM部分，GNU编译器集合已足够。但对于像OpenFAST这样的Fortran部分，强烈推荐使用Intel编译器套件。

此外，您还需要一些额外的工具和库：

* flex
* bison
* make
* cmake
* git
* 一种MPI库，如OpenMPI、MPICH或IntelMPI及其开发包
* 近期版本的Boost库及其开发包
* Zlib及其开发包
* libreadline及其开发包
* libgmp及其开发包
* libmpfr及其开发包
* libcurses及其开发包
* libxml2及其开发包
* libCGAL及其开发包
* HDF5及其开发包
* Python及其开发包
* Yaml-cpp
* 一种BLAS/LAPACK库。这里推荐使用Intel MKL，但也可以使用libOpenBLAS

通常，所有这些软件包都可以直接从您的Linux发行版的存储库中下载，因此无需下载和编译它们。

由于不可能涵盖所有的操作系统、软件包版本和环境组合，本文档假设用于编译代码的机器运行Ubuntu 16.04 LTS或Ubuntu 18.04 LTS。

在Ubuntu 16.04/18.04机器上，所有这些软件包都可以通过以下命令安装：

```bash
sudo apt install build-essential flex bison gfortran git cmake python python-dev \
  zlib1g-dev libreadline-dev libncurses-dev libyaml-cpp-dev libgmp-dev libmpfr-dev \
  libboost-system-dev libboost-thread-dev libopenmpi-dev openmpi-bin \
  libhdf5-dev libxml2-dev libcgal-dev libptscotch-dev libscotch-dev
