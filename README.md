# flexpart安装教程

> 记住你是在编译软件！

## ZLIB v1.2.11

### 下载
``` bash
http://www.zlib.net/
wget http://www.zlib.net/zlib-1.2.11.tar.gz
```

### 安装
``` bash
mkdir -p /disk2/xiaolh/software/zlib
tar -zxvf zlib-1.2.11.tar.gz
cd zlib-1.2.11
./configure --prefix=/disk2/xiaolh/software/zlib
make install
```
### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/zlib 
/disk2/xiaolh/software/zlib
├── include
│   ├── zconf.h
│   └── zlib.h
├── lib
│   ├── libz.a
│   ├── libz.so -> libz.so.1.2.11
│   ├── libz.so.1 -> libz.so.1.2.11
│   ├── libz.so.1.2.11
│   └── pkgconfig
│       └── zlib.pc
└── share
    └── man
        └── man3
            └── zlib.3
```
### 配置环境变量
``` bash
vim ~/.bashrc
#ZLIB
export ZLIB=/disk2/xiaolh/software/zlib
export LD_LIBRARY_PATH=$ZLIB/lib:$LD_LIBRARY_PATH
```

## SZIP v2.1.1

### 下载

``` bash
https://support.hdfgroup.org/doc_resource/SZIP/
wget https://support.hdfgroup.org/ftp/lib-external/szip/2.1.1/src/szip-2.1.1.tar.gz
```
### 安装
``` bash
mkdir -p /disk2/xiaolh/software/szip
tar -zxvf szip-2.1.1.tar.gz
cd szip-2.1.1
./configure --prefix=/disk2/xiaolh/software/szip
make install
```
### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/szip
/disk2/xiaolh/software/szip
├── include
│   ├── ricehdf.h
│   ├── szip_adpt.h
│   └── szlib.h
└── lib
    ├── libsz.a
    ├── libsz.la
    ├── libsz.so -> libsz.so.2.0.0
    ├── libsz.so.2 -> libsz.so.2.0.0
    └── libsz.so.2.0.0
```

### 配置环境变量
``` bash
vim ~/.bashrc

# SZIP
export SZIP=/disk2/xiaolh/software/szip
export LD_LIBRARY_PATH=$SZIP/lib:$LD_LIBRARY_PATH
```

## HDF5 v1.10.5
依赖C++编译器

### 下载
``` bash
https://www.hdfgroup.org/downloads/hdf5/
wget https://s3.amazonaws.com/hdf-wordpress-1/wp-content/uploads/manual/HDF5/HDF5_1_10_5/source/hdf5-1.10.5.tar.gz
```
### 安装
``` bash
mkdir -p /disk2/xiaolh/software/hdf5
tar -zxvf hdf5-1.10.5.tar.gz
cd hdf5-1.10.5
./configure --with-zlib=/disk2/xiaolh/software/zlib -with-szlib=/disk2/xiaolh/software/szip --prefix=/disk2/xiaolh/software/hdf5
make install
```
### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/hdf5
/disk2/xiaolh/software/hdf5
├── bin
│   ├── gif2h5
│   ├── h52gif
├── include
│   ├── H5ACpublic.h
│   ├── H5api_adpt.h

├── lib
│   ├── libhdf5.a
│   ├── libhdf5_hl.a
│   ├── libhdf5_hl.la
│   ├── libhdf5_hl.so -> libhdf5_hl.so.100.1.2
│   ├── libhdf5_hl.so.100 -> libhdf5_hl.so.100.1.2
│   ├── libhdf5_hl.so.100.1.2
│   ├── libhdf5.la
│   ├── libhdf5.settings
│   ├── libhdf5.so -> libhdf5.so.103.1.0
│   ├── libhdf5.so.103 -> libhdf5.so.103.1.0
│   └── libhdf5.so.103.1.0
└── share
    └── hdf5_examples
        ├── c
        │   ├── h5_attribute.c
```

### 配置环境变量
``` bash
vim ~/.bashrc

# HDF5 
export HDF5=/disk2/xiaolh/software/hdf5
export PATH=$HDF5/bin:$PATH
export LD_LIBRARY_PATH=$HDF5/lib:$LD_LIBRARY_PATH
```

## netcdf-c v4.7.0
### 下载
``` bash
https://www.unidata.ucar.edu/downloads/netcdf/index.jsp
wget https://www.unidata.ucar.edu/downloads/netcdf/ftp/netcdf-c-4.7.0.tar.gz 
```
### 安装
``` bash
mkdir -p /disk2/xiaolh/software/netcdf/netcdfc
tar -zxvf netcdf-c-4.7.0.tar.gz
cd netcdf-c-4.7.0
CPPFLAGS="-I/disk2/xiaolh/software/hdf5/include -I/disk2/xiaolh/software/zlib/include"\
LDFLAGS="-L/disk2/xiaolh/software/hdf5/lib  -L/disk2/xiaolh/software/zlib/lib -L/disk2/xiaolh/software/szip/lib" \
./configure --prefix=/disk2/xiaolh/software/netcdf/netcdfc --disable-dap

make install
```
### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/netcdf/netcdfc
/disk2/xiaolh/software/netcdf/netcdfc
├── bin
│   ├── nc-config
│   ├── nccopy
│   ├── ncdump
│   ├── ncgen
│   └── ncgen3
├── include
│   ├── netcdf_aux.h
│   ├── netcdf_filter.h
│   ├── netcdf.h
│   ├── netcdf_mem.h
│   └── netcdf_meta.h
├── lib
│   ├── libh5bzip2.la
│   ├── libh5bzip2.so
│   ├── libnetcdf.a
│   ├── libnetcdf.la
│   ├── libnetcdf.settings
│   ├── libnetcdf.so -> libnetcdf.so.15.0.1
│   ├── libnetcdf.so.15 -> libnetcdf.so.15.0.1
│   ├── libnetcdf.so.15.0.1
│   └── pkgconfig
│       └── netcdf.pc
└── share
    └── man
```

### 配置环境变量
``` bash
vim ~/.bashrc

# NETCDF 
export NETCDF=/disk2/xiaolh/software/netcdfc
export PATH=$NETCDF/bin:$PATH
export LD_LIBRARY_PATH=$NETCDF/lib:$LD_LIBRARY_PATH
```

## netcdf-fortran v4.4.5
### 下载
``` bash
https://www.unidata.ucar.edu/downloads/netcdf/index.jsp
wget https://www.unidata.ucar.edu/downloads/netcdf/ftp/netcdf-fortran-4.4.5.tar.gz
```
### 安装
``` bash
mkdir -p /disk2/xiaolh/software/netcdf/netcdff
tar -zxvf netcdf-fortran-4.4.5.tar.gz
cd netcdf-fortran-4.4.5
CPPFLAGS=-I/disk2/xiaolh/software/netcdf/netcdfc/include \
LDFLAGS=-L/disk2/xiaolh/software/netcdf/netcdfc/lib \
./configure --prefix=/disk2/xiaolh/software/netcdf/netcdff

make install
```
### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/netcdf/netcdff
/disk2/xiaolh/software/netcdf/netcdff
├── bin
│   └── nf-config
├── include
│   ├── netcdf4_f03.mod
│   ├── netcdf4_nc_interfaces.mod
│   ├── netcdf4_nf_interfaces.mod
│   ├── netcdf_f03.mod
│   ├── netcdf_fortv2_c_interfaces.mod
│   ├── netcdf.inc
│   ├── netcdf.mod
│   ├── netcdf_nc_data.mod
│   ├── netcdf_nc_interfaces.mod
│   ├── netcdf_nf_data.mod
│   ├── netcdf_nf_interfaces.mod
│   └── typesizes.mod
├── lib
│   ├── libnetcdff.a
│   ├── libnetcdff.la
│   ├── libnetcdff.so -> libnetcdff.so.6.2.1
│   ├── libnetcdff.so.6 -> libnetcdff.so.6.2.1
│   ├── libnetcdff.so.6.2.1
│   └── pkgconfig
│       └── netcdf-fortran.pc
└── share
    └── man
        └── man3
            └── netcdf_fortran.3
```

### 配置环境变量
``` bash
vim ~/.bashrc

# NETCDFF
export NETCDFF=/disk2/xiaolh/software/netcdff
export LD_LIBRARY_PATH=$NETCDFF/lib:$LD_LIBRARY_PATH
```

## cmake

### 下载
``` bash
https://cmake.org/download/
wget https://github.com/Kitware/CMake/releases/download/v3.15.1/cmake-3.15.1.tar.gz
```
### 安装
``` bash
mkdir -p /disk2/xiaolh/software/cmake
tar -zxvf cmake-3.15.1.tar.gz
cd cmake-3.15.1
./configure --prefix=/disk2/xiaolh/software/cmake
make install
```
### 检查

``` bash
xiaolh@Lnode5:~/software/cmake$ tree /disk2/xiaolh/software/cmake/bin/
/disk2/xiaolh/software/cmake/bin/
├── ccmake
├── cmake
├── cpack
└── ctest
```

### 配置环境变量
``` bash
vim ~/.bashrc

# CMAKE
export CMAKE=/disk2/xiaolh/software/cmake
export PATH=$CMAKE/bin:$PATH
export LD_LIBRARY_PATH=$CMAKE/lib:$LD_LIBRARY_PATH
```

## jasper

### 下载
``` bash
https://www.ece.uvic.ca/~frodo/jasper/
wget https://www.ece.uvic.ca/~frodo/jasper/software/jasper-2.0.14.tar.gz
```
### 安装
``` bash
mkdir -p /disk2/xiaolh/software/jasper
tar -zxvf jasper-2.0.14.tar.gz
cd jasper-2.0.14
mkdir tmp ; cd tmp
cmake -G "Unix Makefiles" -H/disk2/xiaolh/software/Packages/jasper-2.0.14 \
-B/disk2/xiaolh/software/Packages/jasper-2.0.14/tmp -DCMAKE_INSTALL_PREFIX=/disk2/xiaolh/software/jasper
make install
```

### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/jasper/lib
/disk2/xiaolh/software/jasper/lib
├── libjasper.so -> libjasper.so.4
├── libjasper.so.4 -> libjasper.so.4.0.0
├── libjasper.so.4.0.0
└── pkgconfig
    └── jasper.pc
```

### 配置环境变量
``` bash
vim ~/.bashrc

# jasper
export JASPER=/disk2/xiaolh/software/jasper
export LD_LIBRARY_PATH=$JASPER/lib:$LD_LIBRARY_PATH
```

## eccodes

### 下载
``` bash
https://confluence.ecmwf.int/display/ECC/Releases
wget https://confluence.ecmwf.int/download/attachments/45757961/eccodes-2.13.0-Source.tar.gz?api=v2 -O eccodes-2.13.0-Source.tar.gz
```

### 安装
``` bash
mkdir -p /disk2/xiaolh/software/eccodes
tar -zxvf eccodes-2.13.0-Source.tar.gz
cd eccodes-2.13.0-Source
mkdir build ; cd build
cmake -DCMAKE_INSTALL_PREFIX=/disk2/xiaolh/software/eccodes ../

make install
```

### 检查

``` bash
xiaolh@Lnode5:~/software/Packages$ tree /disk2/xiaolh/software/eccodes/lib/ -L 1
/disk2/xiaolh/software/eccodes/lib/
├── cmake
├── libeccodes_f90.so
├── libeccodes.so
├── pkgconfig
└── python2.7
```

## ncl
### 下载
``` bash
https://www.earthsystemgrid.org/dataset/ncl.650.html
wget https://www.earthsystemgrid.org/dataset/ncl.650.nodap/file/ncl_ncarg-6.5.0-Debian8.11_64bit_nodap_gnu492.tar.gz
```

### 安装
``` bash
mkdir -p /disk2/xiaolh/software/ncl
mv ncl_ncarg-6.5.0-Debian8.11_64bit_nodap_gnu492.tar.gz /disk2/xiaolh/software/ncl
tar -zxvf ncarg-6.5.0-Debian8.11_64bit_nodap_gnu492.tar.gz
```

### 配置环境变量
``` bash
vim ~/.bashrc

#NCL
export NCARG_ROOT=/disk2/xiaolh/software/ncl
export PATH=$NCARG_ROOT/bin:$PATH
export LD_LIBRARY_PATH=$NCARG_ROOT/lib:$LD_LIBRARY_PATH
```





