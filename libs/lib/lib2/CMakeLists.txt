# Give the current Library a name
set(CURR_LIB Library2)

# Add library specific compile options
add_compile_options(
        )

add_library(${CURR_LIB}
        lib2.c
        )

# List all include directories here:
# This way you can include them as #include "lib2/lib2.h"
target_include_directories(${CURR_LIB} PUBLIC 
        ${CMAKE_CURRENT_SOURCE_DIR}/../../include
        )

# Append the currend library to the global list anr return it to the callee
list(APPEND LIBRARIES ${CURR_LIB})
return(PROPAGATE LIBRARIES)
