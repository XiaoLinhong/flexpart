## FLEXPART

``` bash
### 下载
https://www.flexpart.eu/

wget https://www.flexpart.eu/downloads/58 -O flexpart_wrf_3.3.2.tar.gz

wget https://www.flexpart.eu/downloads/63 -O flexpart_v10.3beta.tar.gz

### 解压
tar -zxvf flexpart_v10.3beta.tar.g
cd flexpart_v10.3beta5_348abf6/src

make -j serial ncf=yes

```
