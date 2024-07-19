# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(ctest_temeout
    LANGUAGES CXX
)

## Configuration
find_package(Python REQUIRED)
enable_testing()

## Defining tests
add_test(
    NAME example
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test.py
)

## Labels
set_tests_properties(
    example
    PROPERTIES
        TIMEOUT 10
)
