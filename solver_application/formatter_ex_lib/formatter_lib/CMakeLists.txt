cmake_minimum_required(VERSION 3.4)
# Проверка версии CMake.
# Если версия установленой программы
# старее указаной, произайдёт аварийный выход.

add_library(formatter STATIC formatter.h formatter.cpp)
