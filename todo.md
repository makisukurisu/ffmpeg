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
./configure --enable-asm --enable-shared --disable-static --disable-bzlib --disable-libopenjpeg --disable-iconv --disable-zlib --prefix=/c/ffmpeg --toolchain=msvc --arch=amd64 --extra-cflags="-MDd" --extra-ldflags="/NODEFAULTLIB:libcmt" --enable-debug
make -j6 && make install && echo -en "\007"
```