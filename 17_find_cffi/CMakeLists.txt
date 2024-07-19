# Version
cmake_minimum_required(VERSION 3.12...3.28)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# Properties
project(find_cffi
    LANGUAGES NONE
)

find_package(Python REQUIRED)

set (_module_name "cffi")

execute_process(
    COMMAND ${Python_EXECUTABLE} "-c" "import ${_module_name}; print(${_module_name}.__version__)"
    OUTPUT_VARIABLE _stdout
    ERROR_VARIABLE _stderr
    OUTPUT_STRIP_TRAILING_WHITESPACE
    ERROR_STRIP_TRAILING_WHITESPACE
)

if(_stderr MATCHES "ModuleNotFoundError")
    message(STATUS "Module ${_module_name} not found")
else()
    message(STATUS "Found modeule ${_module_name} v${_stdout}")
endif()
