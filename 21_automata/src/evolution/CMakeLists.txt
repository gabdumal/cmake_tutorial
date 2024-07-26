# Libraries
add_library(evolution)

# Sources
target_sources(evolution
    PUBLIC
        evolution.hpp
    PRIVATE
        evolution.cpp
)

# Directories
target_include_directories(evolution
     PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
)
