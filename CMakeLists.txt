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

# GTK 3 dependency
FIND_PACKAGE(PkgConfig REQUIRED)
PKG_CHECK_MODULES(GTK3 REQUIRED gtk+-3.0)

# Setup CMake to use GTK+, tell the compiler where to look for headers
# and to the linker where to look for libraries
INCLUDE_DIRECTORIES(${GTK3_INCLUDE_DIRS})
LINK_DIRECTORIES(${GTK3_LIBRARY_DIRS})

# Add other flags to the compiler
ADD_DEFINITIONS(${GTK3_CFLAGS_OTHER})

# Link the target to the GTK+ libraries
TARGET_LINK_LIBRARIES(${CMAKE_PROJECT_NAME} ${GTK3_LIBRARIES})
