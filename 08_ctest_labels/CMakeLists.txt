# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(ctest_labels
    LANGUAGES CXX
)

## Configuration
find_package(Python REQUIRED)
enable_testing()

## Defining tests
add_test(
    NAME feature-a
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test/feature-a.py
)

add_test(
    NAME feature-b
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test/feature-b.py
)

add_test(
    NAME feature-c
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test/feature-c.py
)

add_test(
    NAME feature-d
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test/feature-d.py
)

add_test(
    NAME benchmark-a
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test/benchmark-a.py
)

add_test(
    NAME benchmark-b
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test/benchmark-b.py
)

## Labels
set_tests_properties(
    feature-a
    feature-b
    feature-c
    PROPERTIES
        LABELS "quick"
)

set_tests_properties(
    feature-d
    benchmark-a
    benchmark-b
    PROPERTIES
        LABELS "long"
)