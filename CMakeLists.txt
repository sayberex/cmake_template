cmake_minimum_required(VERSION 3.22.0) # setting this is required
project(example_project)            # this sets the project name

set(CMAKE_C_STANDARD   11)            # set c standart
set(CMAKE_C_STANDARD_REQUIRED ON)     # required or just use if available

set(CMAKE_CXX_STANDARD 17)            # set c++ standart
set(CMAKE_CXX_STANDARD_REQUIRED ON)   # required or just use if available
set(CMAKE_CXX_EXTENSIONS OFF)         #



add_executable(example)
add_executable(example::exe ALIAS example)

target_compile_options(example PUBLIC
  -std=c++1y
  -Wall
  -Wfloat-conversion
)

target_include_directories(example PUBLIC
  inc
)

target_link_libraries(example PUBLIC 
)

target_sources(example PUBLIC
  src/main.cpp
)


message(STATUS "CMAKE_BUILD_TYPE = ${CMAKE_BUILD_TYPE}")
message(STATUS "CMAKE_CONFIGURATION_TYPES = ${CMAKE_CONFIGURATION_TYPES}")

math(EXPR bitness "${CMAKE_SIZEOF_VOID_P} * 8")
message(STATUS "${bitness}-bit build")


# g cmake-init
# https://github.com/cpp-best-practices/gui_starter_template
# https://github.com/cpp-best-practices/cmake_template/blob/main/CMakePresets.json
# https://github.com/mapnik/mapnik/blob/master/CMakePresets.json
# https://sajidifti.medium.com/how-to-install-gcc-and-gdb-on-windows-using-msys2-tutorial-0fceb7e66454
# sudo apt install gcc-multilib
# sudo apt install g++-multilib