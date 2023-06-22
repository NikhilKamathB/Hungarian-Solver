cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

project(hungarianSolver LANGUAGES CXX)

# Make sure install paths work on all platforms.
if(NOT CMAKE_INSTALL_INCLUDEDIR)
    include(GNUInstallDirs)
endif()

find_package( Eigen3 REQUIRED )
include_directories(${EIGEN3_INCLUDE_DIR})

add_library(hungarianSolver INTERFACE)
target_include_directories(hungarianSolver
    INTERFACE
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

# add_library(${PROJECT_NAME} main.cpp ${HEADERS} ${SOURCES})

install(
    DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/hungarianSolver
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
    FILES_MATCHING # headers only
    PATTERN "*.h"
)