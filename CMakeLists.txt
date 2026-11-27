cmake_minimum_required(VERSION 3.20)
project(ibus-unikey VERSION 0.7.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

include(GNUInstallDirs)

set(LIBEXECDIR "${CMAKE_INSTALL_FULL_LIBEXECDIR}" CACHE STRING "where to install ibus-{engine,setup}-unikey")
set(PKGDATADIR "${CMAKE_INSTALL_FULL_DATADIR}/${PROJECT_NAME}")
set(LOCALEDIR "${CMAKE_INSTALL_FULL_LOCALEDIR}")

add_compile_definitions(
    PACKAGE_NAME="${PROJECT_NAME}"
    GETTEXT_PACKAGE="${PROJECT_NAME}"
    PACKAGE_VERSION="${PROJECT_VERSION}"
    PACKAGE_BUGREPORT="https://github.com/vn-input/ibus-unikey/issues"
    LOCALEDIR="${LOCALEDIR}"
    PKGDATADIR="${PKGDATADIR}"
    LIBEXECDIR="${LIBEXECDIR}"
)

include_directories(
    "${PROJECT_SOURCE_DIR}/ukengine"
    "${PROJECT_SOURCE_DIR}/src/config"
)

add_subdirectory(ukengine)
add_subdirectory(src)
add_subdirectory(setup)
add_subdirectory(data)
add_subdirectory(po)
