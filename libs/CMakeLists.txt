# Include each library part
add_subdirectory("lib/lib1")
add_subdirectory("lib/lib2")

# Return the collected libraries to callee
return(PROPAGATE LIBRARIES)
