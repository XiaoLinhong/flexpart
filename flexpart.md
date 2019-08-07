## FLEXPART

### 下载
``` bash
https://www.flexpart.eu/
wget https://www.flexpart.eu/downloads/58 -O flexpart_wrf_3.3.2.tar.gz
https://git.nilu.no/flexpart/flexpart/commits/dev
```
### 解压
tar -zxvf flexpart_v10.3beta.tar.g
cd flexpart_v10.3beta5_348abf6/src

### 修改makefile
修改库的路径

``` bash
xiaolh@Lnode5:~/software/usr$ pwd
/disk2/xiaolh/software/usr
xiaolh@Lnode5:~/software/usr$ tree
.
├── include
│?? ├── eccodes_config.h -> ../../eccodes/include/eccodes_config.h
│?? ├── eccodes_ecbuild_config.h -> ../../eccodes/include/eccodes_ecbuild_config.h
│?? ├── eccodes.h -> ../../eccodes/include/eccodes.h
│?? ├── eccodes.mod -> ../../eccodes/include/eccodes.mod
│?? ├── eccodes_version.h -> ../../eccodes/include/eccodes_version.h
│?? ├── eccodes_windef.h -> ../../eccodes/include/eccodes_windef.h
│?? ├── grib_api.h -> ../../eccodes/include/grib_api.h
│?? ├── grib_api.mod -> ../../eccodes/include/grib_api.mod
│?? ├── jasper -> ../../jasper/include/jasper
│?? ├── netcdf4_f03.mod -> ../../netcdf/netcdff/include/netcdf4_f03.mod
│?? ├── netcdf4_nc_interfaces.mod -> ../../netcdf/netcdff/include/netcdf4_nc_interfaces.mod
│?? ├── netcdf4_nf_interfaces.mod -> ../../netcdf/netcdff/include/netcdf4_nf_interfaces.mod
│?? ├── netcdf_f03.mod -> ../../netcdf/netcdff/include/netcdf_f03.mod
│?? ├── netcdf_fortv2_c_interfaces.mod -> ../../netcdf/netcdff/include/netcdf_fortv2_c_interfaces.mod
│?? ├── netcdf.inc -> ../../netcdf/netcdff/include/netcdf.inc
│?? ├── netcdf.mod -> ../../netcdf/netcdff/include/netcdf.mod
│?? ├── netcdf_nc_data.mod -> ../../netcdf/netcdff/include/netcdf_nc_data.mod
│?? ├── netcdf_nc_interfaces.mod -> ../../netcdf/netcdff/include/netcdf_nc_interfaces.mod
│?? ├── netcdf_nf_data.mod -> ../../netcdf/netcdff/include/netcdf_nf_data.mod
│?? ├── netcdf_nf_interfaces.mod -> ../../netcdf/netcdff/include/netcdf_nf_interfaces.mod
│?? └── typesizes.mod -> ../../netcdf/netcdff/include/typesizes.mod
└── lib
    ├── libeccodes_f90.so -> ../../eccodes/lib/libeccodes_f90.so
    ├── libeccodes.so -> ../../eccodes/lib/libeccodes.so
    ├── libjasper.so -> ../../jasper/lib/libjasper.so
    ├── libjasper.so.4 -> ../../jasper/lib/libjasper.so.4
    ├── libjasper.so.4.0.0 -> ../../jasper/lib/libjasper.so.4.0.0
    ├── libnetcdff.a -> ../../netcdf/netcdff/lib/libnetcdff.a
    ├── libnetcdff.la -> ../../netcdf/netcdff/lib/libnetcdff.la
    ├── libnetcdff.so -> ../../netcdf/netcdff/lib/libnetcdff.so
    ├── libnetcdff.so.6 -> ../../netcdf/netcdff/lib/libnetcdff.so.6
    └── libnetcdff.so.6.2.1 -> ../../netcdf/netcdff/lib/libnetcdff.so.6.2.1

```

## flexpart
make -j serial ncf=yes

## flexpart-wrf
make -f makefile.com serial

