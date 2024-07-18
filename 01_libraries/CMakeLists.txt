cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

project(libraries
        VERSION 1.0
        LANGUAGES CXX)

add_library(message
            Message.hpp
            Message.cpp)

add_executable(hello_world hello_world.cpp)

target_link_libraries(hello_world PRIVATE message)