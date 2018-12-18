# Задать минимальную версию CMake:
cmake_minimum_required(VERSION 3.0)

# Указать характеристики проекта:
project(MyProgram VERSION 1.0.0 LANGUAGES C)

# Добавить в сборку исполняемый файл "MyProgram":
add_executable(MyProgram StartProgram.c)

# Требовать обработку файла "core/CMakeFiles.txt":
add_subdirectory(core)

# Скомпоновать исполняемый файл "MyProgram" со
# скомпилированной статической библиотекой "MyProgramCore":
target_link_libraries(MyProgram MyProgramCore)

# Установить исполняемый файл "MyProgram" в директорию "bin":
install(TARGETS MyProgram DESTINATION ~/Downloads)
