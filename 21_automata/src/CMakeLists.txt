# Executables
add_executable(automata main.cpp)

# Directories
add_subdirectory(evolution)
add_subdirectory(initial)
add_subdirectory(io)
add_subdirectory(parser)

# Libraries
target_link_libraries(automata
    PRIVATE
        conversion
        evolution
        initial
        io
        parser
)
