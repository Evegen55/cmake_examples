cmake_minimum_required(VERSION 3.0)
# Задать характеристики проекта "MyProject":
project(MyProject VERSION 1.2.3.4 LANGUAGES C CXX)

message("ROOT CMakeLists file: 'VARIABLE' is equal to [${VARIABLE}]")

# Запустить скрипт `MyCMakeScript.cmake` на выполнение:
include(../cmake-example-1/CMakeLists.txt)

message("ROOT CMakeLists file: 'VARIABLE' is equal to [${VARIABLE}]")

# Добавить каталог "subLibrary" в сборку основного проекта,
# а генерируемые файлы расположить в каталоге "subLibrary/build":
add_subdirectory(subLibrary subLibrary/build)
