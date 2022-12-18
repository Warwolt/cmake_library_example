cmake_minimum_required(VERSION 3.16.0)
project(my_lib)
enable_language(C)

set(SRC
    src/hello.c
)

add_executable(example
    src/main.c
    ${SRC}
)

target_include_directories(example PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

add_library(${PROJECT_NAME} STATIC)

target_sources(${PROJECT_NAME}
    PRIVATE
        ${SRC}
)

target_include_directories(${PROJECT_NAME}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)
