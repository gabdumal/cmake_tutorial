# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(ctest_cost
    LANGUAGES CXX
)

## Configuration
find_package(Python REQUIRED)
enable_testing()

## Defining tests
add_test(
    NAME a
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/a.py
)

add_test(
    NAME b
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/b.py
)

add_test(
    NAME c
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/c.py
)

add_test(
    NAME d
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/d.py
)

add_test(
    NAME e
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/e.py
)

add_test(
    NAME f
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/f.py
)

add_test(
    NAME g
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/g.py
)

add_test(
    NAME h
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/h.py
)

add_test(
    NAME i
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/i.py
)

add_test(
    NAME j
    COMMAND ${Python_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/tests/j.py
)


## Labels
set_tests_properties(
    a b c d
    PROPERTIES
        COST 0.5
)

set_tests_properties(
    a b c d
    PROPERTIES
        COST 1.5
)

set_tests_properties(
    h
    PROPERTIES
        COST 2.5
)

set_tests_properties(
    i
    PROPERTIES
        COST 3.5
)

set_tests_properties(
    j
    PROPERTIES
        COST 4.5
)