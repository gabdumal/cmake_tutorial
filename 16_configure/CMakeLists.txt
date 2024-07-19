# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(processor
    LANGUAGES CXX
)

include(CMakePrintHelpers)

# Executables
add_executable(processor_info processor_info.cpp)

foreach(key IN ITEMS
    NUMBER_OF_PHYSICAL_CORES
    TOTAL_PHYSICAL_MEMORY
    OS_NAME
    OS_PLATFORM
)
    # query the item ${key} and save its value in the variable _${key}
    # i.e. the value of NUMBER_OF_LOGICAL_CORES will be saved in _NUMBER_OF_LOGICAL_CORES
    cmake_host_system_information(
        RESULT _${key}
        QUERY ${key}
    )
    cmake_print_variables("_${key}")
endforeach()

# and PROJECT_BINARY_DIR as its include directories
target_include_directories(processor_info
    PRIVATE
    ${PROJECT_BINARY_DIR}
)

# configure the file
configure_file(config.h.in config.h @ONLY)
