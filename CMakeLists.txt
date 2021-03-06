cmake_minimum_required(VERSION 3.12)
project(moderncpp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

# Set debug build type by default
if (NOT CMAKE_BUILD_TYPE OR CMAKE_BUILD_TYPE STREQUAL "")
    set(CMAKE_BUILD_TYPE "Debug" CACHE STRING "" FORCE)
endif()

# For covering and profiling library code
if (CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(CMAKE_CXX_FLAGS "-g --coverage -fprofile-arcs -ftest-coverage")
endif()

file(GLOB SRC_LIB_FILES ${PROJECT_SOURCE_DIR}/src/*.cpp)
add_library(${PROJECT_NAME} SHARED ${SRC_LIB_FILES})

if (NOT DEFINED TEST_TYPE)
    set(TEST_TYPE "google" CACHE STRING "" FORCE)
endif()

if(${TEST_TYPE} STREQUAL "catch2")
    MESSAGE("Sets catch2 test framework")
    add_subdirectory(tests-catch2)
else()
    MESSAGE("Sets google test framework")
    add_subdirectory(tests-google)
endif()
