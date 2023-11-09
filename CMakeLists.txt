cmake_minimum_required(VERSION 3.21.1)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
include(CMake/JSONParser.cmake)
file(READ "info.json" jsonInfo)
sbeParseJson(info jsonInfo)

project("${info.projectName}" "VERSION" "${info.version.major}.${info.version.minor}.${info.version.patch}" "DESCRIPTION" "${info.projectDescription}" "HOMEPAGE_URL" "${info.repository}" "LANGUAGES" "C" "CXX")

add_subdirectory(UsageEnvironment)
add_subdirectory(groupsock)
add_subdirectory(liveMedia)

include(CMakePackageConfigHelpers)

set(INCLUDE_INSTALL_DIR "include")
set(CMAKE_INSTALL_DIR "cmake")
set(BIN_INSTALL_DIR "bin")
set(LIB_INSTALL_DIR "lib")
configure_package_config_file("${PROJECT_SOURCE_DIR}/CMake/libRTSPConfig.cmake.in" "${PROJECT_BINARY_DIR}/libRTSPConfig.cmake" INSTALL_DESTINATION cmake
        PATH_VARS INCLUDE_INSTALL_DIR CMAKE_INSTALL_DIR BIN_INSTALL_DIR LIB_INSTALL_DIR)

install(FILES "${PROJECT_BINARY_DIR}/libRTSPConfig.cmake" DESTINATION cmake)

