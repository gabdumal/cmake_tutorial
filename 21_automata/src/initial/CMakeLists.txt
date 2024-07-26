# Libraries
add_library(initial)

# Sources
target_sources(initial
    PUBLIC
        initial.hpp
    PRIVATE
        initial.cpp
)

# Directories
target_include_directories(initial
     PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
)
