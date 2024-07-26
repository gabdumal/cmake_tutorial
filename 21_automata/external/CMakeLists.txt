# Libraries
add_library(conversion)

# Sources
target_sources(conversion
    PUBLIC
        conversion.hpp
    PRIVATE
        conversion.cpp
)

# Directories
target_include_directories(conversion
     PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
)
