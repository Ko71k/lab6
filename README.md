[![Build Status](https://travis-ci.com/Ko71k/lab04.svg?branch=master)](https://travis-ci.com/Ko71k/lab04)
## Laboratory work 4
# Домашнее задание
Данная лабораторная работа посвещена изучению систем автоматизации сборки проекта на примере **CMake**
Вы продолжаете проходить стажировку в "Formatter Inc." (см подробности).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы CMake.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в прошлый раз. Настройте сборочные процедуры на различных платформах:

    используйте TravisCI для сборки на операционной системе Linux с использованием компиляторов gcc и clang;
    используйте AppVeyor для сборки на операционной системе Windows.
    
Сначала подключим проект к travis: 
После этого следует настроить файл .travis.yml:
```
language: cpp

script:
- cd solver_application
- cmake .
- make
- cd ..
- cd hello_world_application
- cmake .
- make

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
      - mingw-w64
```
В процессе сборки на travis выходит ошибка. Для решения этой проблемы устанавлием стандарт языка c++ в файлах CMakeLists.txt
После всех этих действий компилятор travis завершил билд и всё заработало
