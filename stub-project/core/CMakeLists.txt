# Задать минимальную версию CMake:
cmake_minimum_required(VERSION 3.0)

# Добавить в сборку статическую библиотеку "MyProgramCore":
add_library(MyProgramCore STATIC ProcessInvoker.c SystemManager.c)
