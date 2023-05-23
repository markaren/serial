cmake_minimum_required(VERSION 3.15)
project(serial)

option(SERIAL_BUILD_EXAMPLES "Build examples" OFF)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(src)

if (SERIAL_BUILD_EXAMPLES)
    add_subdirectory(examples)
endif ()
