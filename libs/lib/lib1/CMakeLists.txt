# Give the current Library a name
set(CURR_LIB Library1)

# Add library specific compile options
add_compile_options(
        )

add_library(${CURR_LIB}
        lib1.c
        )

# List all include directories here:
# This way you can include them as #include "lib1/lib1.h"
target_include_directories(${CURR_LIB} PUBLIC 
        ${CMAKE_CURRENT_SOURCE_DIR}/../../include
        )

# Append the currend library to the global list anr return it to the callee
list(APPEND LIBRARIES ${CURR_LIB})
return(PROPAGATE LIBRARIES)
