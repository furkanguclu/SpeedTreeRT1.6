# SpeedTreeRT 1.6

SpeedTreeRT 1.6, ağaç ve bitki geometrisi üretimi için kullanılan C++ tabanlı bir runtime kütüphanesidir.  
Bu depo, **C++17 uyumlu** olacak şekilde düzenlenmiş **static** ve **shared** kütüphane çıktıları üretir.

## Features
- SpeedTreeRT 1.6 core
- Static & Shared library desteği
- CMake tabanlı build sistemi
- C++17 standardı
- Legacy kod için `std::byte` uyumluluk düzenlemeleri

## Output
build/bin/<Config>/
├─ SpeedTreeRT.dll
├─ SpeedTreeRT.lib (import library)
├─ speedtree_static.lib (static)


- `<Config>`: Debug veya Release  
- `.exp` dosyaları MSVC içindir, dağıtımda gerekmez

## How to build

> cmake -S . -B build
>
> cmake --build build

