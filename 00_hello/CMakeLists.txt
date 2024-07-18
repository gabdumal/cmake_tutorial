cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

project(hello 
        VERSION 1.0 
        DESCRIPTION "I am learning!" 
        LANGUAGES CXX)

add_executable(hello hello.cpp)