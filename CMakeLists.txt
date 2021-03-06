### Top Level CMake File
#
# All submodules and general project dependencies should be listed here.

# CMake Minimum Required version
cmake_minimum_required(VERSION 3.2)

# Enable C++11
set(CMAKE_CXX_STANDARD 11)

# Project name (make it yours)
project(mini_cpp_project)

# place binaries and libraries according to GNU standards
include(GNUInstallDirs)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_LIBDIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_LIBDIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_BINDIR})

# we use this to get code coverage
if(CMAKE_CXX_COMPILER_ID MATCHES GNU)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fprofile-arcs -ftest-coverage")
endif()

# better intelisense in vscode editor
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# add library source code subdirectory
add_subdirectory(src)

# add "main" application source code subdirectory
add_subdirectory(app)

# download and enable google testing
include(cmake/googletest.cmake)
fetch_googletest(
    ${PROJECT_SOURCE_DIR}/cmake
    ${PROJECT_BINARY_DIR}/extern/googletest
    )
enable_testing()

# add project tests subdirectory
add_subdirectory(test)