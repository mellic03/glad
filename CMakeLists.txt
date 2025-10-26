cmake_minimum_required(VERSION 3.11)

project(mellic03_glad)

include_directories("${CMAKE_CURRENT_SOURCE_DIR}/include")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib")

add_library(glad-static STATIC "${CMAKE_CURRENT_SOURCE_DIR}/src/glad.c")
add_library(mellic03::glad ALIAS glad-static)
set_target_properties(glad-static PROPERTIES OUTPUT_NAME "glad")

add_library(glad-shared SHARED "${CMAKE_CURRENT_SOURCE_DIR}/src/glad.c")
add_library(mellic03::glad-shared ALIAS glad-shared)
set_target_properties(glad-shared PROPERTIES OUTPUT_NAME "glad")

file(
    COPY "${CMAKE_CURRENT_SOURCE_DIR}/include"
    DESTINATION "${CMAKE_CURRENT_BINARY_DIR}"
)
