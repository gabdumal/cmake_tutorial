# Libraries
add_library(parser)

# Sources
target_sources(parser
    PUBLIC
        parser.hpp
    PRIVATE
        parser.cpp
)

# Directories
target_include_directories(parser
     PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
)
