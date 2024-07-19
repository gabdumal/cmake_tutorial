cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

project(libraries LANGUAGES CXX)

option(USE_LIBRARY "Compile sources into a library" OFF)

message(STATUS "Compile sources into a library? ${USE_LIBRARY}")

include(CMakeDependentOption)

cmake_dependent_option(
    MAKE_STATIC_LIBRARY "Compile sources into a static library" OFF
    "USE_LIBRARY" ON  
)

cmake_dependent_option(
    MAKE_SHARED_LIBRARY "Compile sources into a shared library" OFF
    "USE_LIBRARY" ON 
)

set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)

list(APPEND _sources
    Message.hpp
    Message.cpp
)

if(USE_LIBRARY)
    message(STATUS "Compile sources into a STATIC library? ${MAKE_STATIC_LIBRARY}")

    message(STATUS "Compile sources into a SHARED library? ${MAKE_SHARED_LIBRARY}")

    add_executable(hello_world hello_world.cpp)

    if(MAKE_SHARED_LIBRARY)
        add_library(message SHARED ${_sources})
    endif()
        
    if(MAKE_STATIC_LIBRARY)
        add_library(message STATIC ${_sources})
    endif()

    target_link_libraries(hello_world PRIVATE message)

else()
    add_executable(hello_world
        hello_world.cpp
        ${_sources}
    )
endif()
