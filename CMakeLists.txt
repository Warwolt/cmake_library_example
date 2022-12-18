cmake_minimum_required(VERSION 3.16.0)
project(my_lib_client)
enable_language(C)

add_subdirectory(external/my_lib)

add_executable(${PROJECT_NAME}
    src/main.c
)

target_link_libraries(${PROJECT_NAME} PRIVATE my_lib)
