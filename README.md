# Introduction 
This is a version of openssl 1.0.1e with Android patches that can be used to build robovm for Windows.

The files have been updated with the following patches from [Android repository](https://android.googlesource.com/platform/external/openssl/+/android-4.4.3_r1.1/patches/)
   - channelid.patch
   - alpn.patch
   - jsse.patch
   - handshake_cutthrough.patch

> Note: the applying order is important 

The patch were merged with 
```
patch -p1 -i channelid.patch
patch -p1 -i alpn.patch
patch -p1 -i jsse.patch
patch -p1 -i handshake_cutthrough.patch
```

# Binaries
Precompiled 32bits static version [is available]().

# How to build
## Prerequisites
Mingw+Msys
Get the [openssl source 1.0.1e](http://www.openssl.org/source/openssl-1.0.1e.tar.gz)

## Building 

### Shared (as dll)
```
C:\Apps\Mingw\msys\1.0\msys.bat
cd /YOUR PATH
export PATH=/C/Apps/Mingw/bin:$PATH

patch -p1 -i channelid.patch
patch -p1 -i alpn.patch
patch -p1 -i jsse.patch
patch -p1 -i handshake_cutthrough.patch

./Configure --prefix=$PWD/dist no-idea no-mdc2 no-rc5 shared mingw
make depend && make && make install
```

### Static libraries
```
C:\Apps\Mingw\msys\1.0\msys.bat
cd /YOUR PATH
export PATH=/C/Apps/Mingw/bin:$PATH

patch -p1 -i channelid.patch
patch -p1 -i alpn.patch
patch -p1 -i jsse.patch
patch -p1 -i handshake_cutthrough.patch

./Configure --prefix=$PWD/dist no-idea no-mdc2 no-rc5 no-shared mingw
make depend && make && make install
```

The result are in the `dist` folder