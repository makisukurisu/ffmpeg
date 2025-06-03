Focus on CABAC:
- ff_h264_decode_mb_cabac

https://chatgpt.com/share/6839fe61-f0b4-8009-8475-374f1ac2b401

MSYS2 Path:
```
export PATH="/c/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/bin/Hostx64/x64":"/c/ffmpeg/bin":$PATH
```

```
export PATH="/c/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.44.35207/bin/Hostx64/x64/:/c/ffmpeg/bin:/usr/local/bin:/usr/bin:/bin:/opt/bin:/c/Windows/System32:/c/Windows:/c/Windows/System32/Wbem:/c/Windows/System32/WindowsPowerShell/v1.0/:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl"
```

Debug build
```
Old:
./configure --enable-asm --enable-shared --disable-static --disable-bzlib --disable-libopenjpeg --disable-iconv --disable-zlib --prefix=/c/ffmpeg --toolchain=msvc --arch=amd64 --extra-cflags="-MDd" --extra-ldflags="/NODEFAULTLIB:libcmt" --enable-debug
./configure --enable-libx264 --enable-gpl --enable-asm --enable-shared --disable-static --disable-bzlib --disable-libopenjpeg --disable-iconv --disable-zlib --prefix=/c/ffmpeg --toolchain=msvc --arch=amd64 --extra-cflags="-MDd" --extra-ldflags="/NODEFAULTLIB:libcmt" --enable-debug
make -j6 && make install && echo -en "\007"
```

```
CC=cl PKG_CONFIG_PATH=../installed/lib/pkgconfig ./configure --prefix=../installed --toolchain=msvc --target-os=win64 --arch=x86_64 --enable-asm --disable-shared --enable-static --enable-libx264 --enable-gpl --enable-nonfree --enable-debug --disable-optimizations --extra-ldflags="-LIBPATH:../installed/lib" --extra-cxxflags="-I../installed/include/ -MTd -O1 -Z7" --extra-cflags="-I../installed/include/ -MTd -O1 -Z7"
make -j6 && make install && echo -en "\007"
```

(In ffmpeg dir)
```
../installed/bin/ffmpeg.exe -i ../Videos/real_2.mp4 -c:v h264 -c:a copy ../Videos/real_2-mod.mp4 -v trace
```