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

### CMake常用指令

+ cmake_minimum_required(VERSION <min>[...<max>] [FATAL_ERROR])

	+ 指定CMake最小版本

```
cmake_minimum_required(VERSION 3.0.0)
```

+ project(<project_name>)

	+ 用於指定CMake工程名稱

```
project (test)
```

+ set(<variable> <value> [CACHE <type> <docstring> [FORCE]])

	+ 用於定義變量。可以用於定義普通變量、環境變量、緩存變量等

```
# 定義一個普通變量
set(SOURCE_FILES main.cpp foo.cpp bar.cpp)

# 定義一個環境變量
set(CMAKE_PREFIX_PATH "/path/to/dependencies")

# 定義一個緩存變量
set(MY_LIB_VERSION "1.0.0" CACHE STRING "MyLib version")
```
+ message([<mode>] " ")

	+ message命令可用於在CMake執行期間輸出自定義消息。通常用於顯示某些變量的值，調試輸出等。
	
	+ mode模式可以選擇，有STATUS、WARNING、AUTHOR_WARNING、SEND_ERROR、FATAL_ERROR、DEPRECATION，預設為STATUS

```
message(STATUS "hello world")
```

+ find_package()

	+ 用來尋找並設置所需的第三方庫的路徑和設定，以便在CMake項目中使用這些庫

```
#尋找OpenCV庫
find_package(OpenCV REQUIRED)
```

+ include_directories(path)

	+ 使用include_directories指令可以將一個目錄添加到當前項目的include路徑中，以方便在源代碼文件中包含這個目錄中的頭文件。

```
include_directories(
    /home/es912/directory1.h
    /home/es912/directory2.h
    /home/es912/directory3.h
)
```

+ add_executable(target_name source_file1 source_file2 ...)

	+ 用於建立一個可執行檔案的目標。它需要指定一個目標名稱，後面接著源文件列表，這些源文件將被編譯並連接成可執行檔案

```
#將main.cpp、foo.cpp 和 bar.cpp 這三個源文件並連接成一個名為 myapp 的可執行檔案。
add_executable(myapp main.cpp foo.cpp bar.cpp)
```

+ add_library(<name> [STATIC | SHARED | MODULE] [EXCLUDE_FROM_ALL] ssource1 [source2 ...])

	+ add_library命令可以指定靜態庫、動態庫和插件。當指定動態庫時，CMake 會生成.so文件，如果是 Windows 系統，會生成.dll文件

	+ <name>：庫的名稱；

	+ STATIC、SHARED或MODULE：可選參數，用於確定義庫的類型。默認為STATIC，即靜態庫。SHARED顯示動態庫，MODULE顯示插件。如果同時指定了SHARED和STATIC，則生成兩個庫；

	+ EXCLUDE_FROM_ALL：可選參數，表示這個庫不會被默認構造。只有顯示方式指定或被依賴時才會被構造；

	+ source1、source2等：指定庫的源文件


+ target_link_libraries(target library1 <debug | optimized> library2 ...)
	
	+  CMake 中用來將目標文件和庫文件進行連結的命令

```
target_link_libraries(yolo_ort "${ONNXRUNTIME_DIR}/lib/onnxruntime.lib")
```



