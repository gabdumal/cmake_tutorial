# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(hello_ctest
    LANGUAGES CXX
)

# Environment
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Libraries
add_library(sum_integers sum_integers.cpp)

# Executables
add_executable(sum_up main.cpp)
target_link_libraries(sum_up PRIVATE sum_integers)

# Tests
## Binaries
add_executable(cpp_test test.cpp)
target_link_libraries(cpp_test PRIVATE sum_integers)

## Configuration
find_program(BASH_EXECUTABLE NAMES bash REQUIRED)
enable_testing()

## Defining tests
add_test(
    NAME cpp_test
    COMMAND $<TARGET_FILE:cpp_test>
)

add_test(
    NAME bash_test
    COMMAND ${BASH_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/test.sh $<TARGET_FILE:sum_up>
)
