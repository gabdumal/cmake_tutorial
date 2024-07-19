# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(sys_prepoc
    LANGUAGES CXX
)

# Executables
add_executable(hello_world hello_world.cpp)

# System information
if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
    target_compile_definitions(hello_world PUBLIC "IS_LINUX")
endif()
if(CMAKE_SYSTEM_NAME STREQUAL "Darwin")
    target_compile_definitions(hello_world PUBLIC "IS_MACOS")
endif()
if(CMAKE_SYSTEM_NAME STREQUAL "Windows")
    target_compile_definitions(hello_world PUBLIC "IS_WINDOWS")
endif()
