# Libraries
add_library(io)

# Sources
target_sources(io
    PUBLIC
        io.hpp
    PRIVATE
        io.cpp
)

# Directories
target_include_directories(io
     PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
)
