CMake
======

### CMake外部編譯和內部編譯

+ 內部編譯

```
cmake .
make
```

+ 外部編譯

```
mkdir build
cd build
cmake ..
make
```

+ 兩者差異在於內部編譯會將所有的CMake和Makefile檔案放在你原本資料夾中，而外部編譯會將CMake和Makefile檔案放在創建的build檔內部

### CMake語法

+ 變數使用以${}方式取值，如果在if判斷式內直接使用變數名稱不需要加上${}

+ 註解以#開頭

+ 指令後面加上小括號用於傳遞參數，指令名稱大小寫都可以

### CMake指令

+ cmake_minimum_required(VERSION <min>[...<max>] [FATAL_ERROR])

	+ 指定CMake最小版本

```

```
