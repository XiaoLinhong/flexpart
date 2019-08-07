## grib_api

mkdir build; cd build
cmake  ../ -DCMAKE_INSTALL_PREFIX=/disk2/xiaolh/software/grib_api
make install

## LINPNG 1.6.29
 CPPFLAGS="-I/disk2/xiaolh/software/zlib/include" \
./configure with_zlib_prefix=/disk2/xiaolh/software/zlib --prefix=/disk2/xiaolh/software/libpng
make install

## expat 2.2.3

./configure --prefix=/disk2/xiaolh/software/expat
make install

## ncview v2.1.7  # X11
./configure --with-nc-config=/disk2/xiaolh/software/netcdf/netcdf/bin/nc-config \
 --with-png_incdir=/disk2/xiaolh/software/libpng/include --with-png_libdir=/disk2/xiaolh/software/libpng/lib \
 --with-udunits2_incdir=/disk2/xiaolh/software/udunits/include --with-udunits2_libdir=/disk2/xiaolh/software/udunits/lib \
 --prefix=/disk2/xiaolh/software/ncview
 make install
