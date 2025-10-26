cmake_minimum_required(VERSION 3.21)


set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib")


macro(SmartNotLazy libname libtype)
    project(${libname})
    add_library(${PROJECT_NAME} ${libtype} "${CMAKE_CURRENT_SOURCE_DIR}/src/glad.c")
    add_library("mellic03::${PROJECT_NAME}" ALIAS ${PROJECT_NAME})
    set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME "glad")
    target_include_directories(${PROJECT_NAME} PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
endmacro()


SmartNotLazy(glad STATIC)
SmartNotLazy(glad-shared SHARED)

# project(glad-static)
# add_library(glad-static STATIC "${CMAKE_CURRENT_SOURCE_DIR}/src/glad.c")
# add_library(mellic03::glad ALIAS glad-static)
# set_target_properties(glad-static PROPERTIES OUTPUT_NAME "glad")
# target_include_directories(glad-static PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")

# project(glad-shared)
# add_library(${PROJECT_NAME} SHARED "${CMAKE_CURRENT_SOURCE_DIR}/src/glad.c")
# add_library("mellic03::${PROJECT_NAME}" ALIAS ${PROJECT_NAME})
# set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME "glad")
# target_include_directories(${PROJECT_NAME} PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")

file(
    COPY "${CMAKE_CURRENT_SOURCE_DIR}/include"
    DESTINATION "${CMAKE_CURRENT_BINARY_DIR}"
)

install(
    DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/include"
    DESTINATION "."
)

install(
    DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib"
    DESTINATION "."
)
