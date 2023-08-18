# Stop if cmake version is below 3.26
cmake_minimum_required(VERSION 3.26 FATAL_ERROR)

# Give the global project a name
set(PROJECT_NAME "Template")

# ...and a version
project(${PROJECT_NAME} VERSION 0.0.2)
configure_file(src/project_conf.h.in project_conf.h)

# Some compiler specific options
set(CMAKE_C_STANDARD 23)
add_compile_options(
        -O2
        -std=c2x
        -Wall 
        -Wnested-externs 
        -Wcast-qual
        -Wshadow
        -Wunreachable-code
        -Wlogical-op 
        -Wfloat-equal 
        -Wredundant-decls
        -Wold-style-definition
        -Wno-format
        -Wno-unused-function
        -Wuninitialized
        #-Werror
        )

# Add the libraries in the libs sub-directory
add_subdirectory("libs")
MESSAGE (STATUS "Collected libraries: ${LIBRARIES}")

# Now adding the main code
add_executable(${PROJECT_NAME}
        src/main.c
        )

# Point the linker to all library entries:
target_link_libraries(${PROJECT_NAME} PUBLIC 
        ${LIBRARIES}
        )

# This way you can include them as #include "lib1/lib1.h"
target_include_directories(${PROJECT_NAME} PUBLIC
        ${PROJECT_SOURCE_DIR}/src
        ${PROJECT_SOURCE_DIR}/libs/include
        "${PROJECT_BINARY_DIR}"
        )

# Add documentation target
add_subdirectory("docs")
