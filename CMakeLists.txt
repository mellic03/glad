cmake_minimum_required(VERSION 3.21)

# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib")
# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib")

project(glad)
add_library(
    ${PROJECT_NAME} OBJECT ${CMAKE_CURRENT_SOURCE_DIR}/src/glad.c
)
target_include_directories(
    ${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# file(
#     COPY "${CMAKE_CURRENT_SOURCE_DIR}/include"
#     DESTINATION "${CMAKE_CURRENT_BINARY_DIR}"
# )

# install(
#     DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/include"
#     DESTINATION "."
# )

# install(
#     DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib"
#     DESTINATION "."
# )
