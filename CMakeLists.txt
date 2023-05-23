cmake_minimum_required(VERSION 3.15)
project(serial VERSION 0.1.0)

option(SERIAL_BUILD_EXAMPLES "Build examples" OFF)


# ==============================================================================
# Global internal configuration
# ==============================================================================

set(CMAKE_CXX_STANDARD 17)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

# ==============================================================================
# Targets
# ==============================================================================

add_subdirectory(src)

if (SERIAL_BUILD_EXAMPLES)
    add_subdirectory(examples)
endif ()


# ==============================================================================
# Exports and remaining installation
# ==============================================================================

configure_package_config_file(cmake/config.cmake.in
        ${CMAKE_CURRENT_BINARY_DIR}/serial-config.cmake
        INSTALL_DESTINATION ${CMAKE_INSTALL_DATADIR}/serial
        NO_SET_AND_CHECK_MACRO)
write_basic_package_version_file(
        ${CMAKE_CURRENT_BINARY_DIR}/serial-config-version.cmake
        VERSION ${serial_VERSION}
        COMPATIBILITY SameMajorVersion)

install(
        FILES
        ${CMAKE_CURRENT_BINARY_DIR}/serial-config.cmake
        ${CMAKE_CURRENT_BINARY_DIR}/serial-config-version.cmake
        DESTINATION
        ${CMAKE_INSTALL_DATADIR}/serial)

install(TARGETS serial EXPORT serial-targets)
install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(EXPORT serial-targets
        NAMESPACE serial::
        DESTINATION ${CMAKE_INSTALL_DATADIR}/serial)
