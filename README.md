## Задание 1
Вам поручили перейти на систему автоматизированной сборки CMake. Исходные файлы находятся в директории formatter_lib. В этой директории находятся файлы для статической библиотеки formatter. Создайте CMakeList.txt в директории formatter_lib, с помощью которого можно будет собирать статическую библиотеку formatter.
```
$ git clone https://github.com/tp-labs/lab03 // клонируем репозиторий 
$ cd lab03
$ git checkout -b laba 
$ cd formatter_lib
$ cat >>CMakeLists.txt << EOF
> EOF
$ nano CMakeLists.txt
```
Файл CmakeLists.txt:
```
cmake_minimum_required(VERSION 3.10)
project(formatter)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(formatter_lib1 STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
```
Проверка работы:
```
$ cmake -H. -B build
$ cmake --build build
```
(работает)
## Задание 2
У компании "Formatter Inc." есть перспективная библиотека, которая является расширением предыдущей библиотеки. Т.к. вы уже овладели навыком созданием CMakeList.txt для статической библиотеки formatter, ваш руководитель поручает заняться созданием CMakeList.txt для библиотеки formatter_ex, которая в свою очередь использует библиотеку formatter.

Сначала копируем папку с проектом formatter_lib в formatter_ex_lib
```
$ cd formatter_ex //переходим в другую директорию
$ cat >> CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.10)
project(formatter_ex)
include_directories(formatter_lib) //подключаем директорию с заголовочными файлами
add_subdirectory(formatter_lib) //подключаем директорию с библиотекой которая соберется сама
add_library(formatter_ex STATIC formatter_ex.h formatter_ex.cpp)
target_link_libraries(formatter_ex formatter) //подключаем библиотеку

EOF
```
Проверка работы:
```
$ cmake -H. -B build
$ cmake --build build
```
Всё работает.
## Задание 3
Конечно же ваша компания предоставляет примеры использования своих библиотек. Чтобы продемонстрировать как работать с библиотекой formatter_ex, вам необходимо создать два CMakeList.txt для двух простых приложений:

hello_world, которое использует библиотеку formatter_ex;
solver, приложение которое испольует статические библиотеки formatter_ex и solver_lib.
Удачной стажировки!

Сначала копируем библиотеку formatter_ex_lib в папку с hello_world_application
```
$ cat >> CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.10)
project(hello_world)
include_directories(formatter_ex_lib)
add_subdirectory(formatter_ex_lib)
add_executable(hello_world hello_world.cpp)
target_link_libraries(hello_world formatter_ex)
EOF
```
Проверка:
```
$ cmake -H. -B build
$ cmake --build build
```
Всё работает.

Сmake для папки solver_lib:
```
cmake_minimum_required(VERSION 3.10) 
add_library(solver_lib STATIC solver.h solver.cpp)
```
Cmake для приложения:
```
cmake_minimum_required(VERSION 3.10)
project(solver)
add_executable(solver equation.cpp)
include_directories(formatter_ex_lib)
add_subdirectory(formatter_ex_lib)
include_directories(solver_lib)
add_subdirectory(solver_lib)
target_link_libraries(solver formatter_ex)
target_link_libraries(solver solver_lib)
```
Проверка:
```
$ cmake -H. -B build
$ cmake --build build
```
Всё работает.
