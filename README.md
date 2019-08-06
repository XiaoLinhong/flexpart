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




