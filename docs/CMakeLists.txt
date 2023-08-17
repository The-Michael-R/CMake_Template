find_package(Doxygen)
if (DOXYGEN_FOUND)

    set(DOXYGEN_PROJECT_NAME ${POJECT_NAME})
    doxygen_add_docs(docs ${PROJECT_SOURCE_DIR}
    COMMENT "Generate documentation."
    )

endif()
