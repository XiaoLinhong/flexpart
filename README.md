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




