### Library Level CMake
#
# Here you shoud link your libraries files
#
add_library(hello_world_lib "")

# Inform source and include directories
target_sources(
    hello_world_lib
    PRIVATE
        HelloWorld.cpp
    PUBLIC
        ${CMAKE_HOME_DIRECTORY}/include/${PROJECT_NAME}/HelloWorld.h
    )

target_include_directories(
    hello_world_lib
    PUBLIC
        ${CMAKE_HOME_DIRECTORY}/include
    )

target_link_libraries(hello_world_lib)
