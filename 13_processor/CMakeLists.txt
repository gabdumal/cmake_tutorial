# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(ctest_processor
    LANGUAGES NONE
)

# the value of NUMBER_OF_LOGICAL_CORES will be saved in _NUMBER_OF_LOGICAL_CORES
cmake_host_system_information(
    RESULT _NUMBER_OF_LOGICAL_CORES
    QUERY NUMBER_OF_LOGICAL_CORES
)
message(STATUS "Number of logical cores: ${_NUMBER_OF_LOGICAL_CORES}")
