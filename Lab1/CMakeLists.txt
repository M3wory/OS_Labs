cmake_minimum_required(VERSION 3.10)
project(Lab1)

project ("Lab1")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Добавление подпроектов
add_subdirectory(Main)
add_subdirectory(Creator)
add_subdirectory(Reporter)