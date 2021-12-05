cmake_minimum_required(VERSION 3.14.0)
project(moa_library
        LANGUAGES Fortran
        VERSION 0
        DESCRIPTION "Mathematics of Arrays"
)
enable_testing()

# Follow GNU conventions for installation directories
include(GNUInstallDirs)

include(${PROJECT_SOURCE_DIR}/cmake/moa.cmake)

# --- set preprocessor
set(FYPP ${python PROJECT_SOURCE_DIR}/deps/fypp/bin/fypp.py)

add_subdirectory(src)

install(EXPORT ${PROJECT_NAME}-targets
        NAMESPACE ${PROJECT_NAME}::
        DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}"
)
