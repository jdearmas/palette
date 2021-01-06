cmake_minimum_required(VERSION 3.10)

# set the project name
project(palette VERSION 0.0.1)

# add the executable
add_executable(palette palette.c)

# specify a C standard
set(CMAKE_C_STANDARD 99)

# configure a header file to pass the version number to the source code:
configure_file(palette_config.h.in palette_config.h)

# add the binary tree to the search path for include files
target_include_directories(palette PUBLIC
                           "${PROJECT_BINARY_DIR}")

