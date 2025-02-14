cmake_minimum_required(VERSION 3.13)

project(Polynomial LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")

add_subdirectory(${CMAKE_SOURCE_DIR}/googletest)
include_directories(${CMAKE_SOURCE_DIR}/include)

file(GLOB POLYNOMIAL_SOURCES "${CMAKE_SOURCE_DIR}/src/*.cpp")
file(GLOB POLYNOMIAL_HEADERS "${CMAKE_SOURCE_DIR}/include/*.hpp")
file(GLOB TESTS_SOURCES "${CMAKE_SOURCE_DIR}/tests/*.cpp")

add_library(Polynomial ${POLYNOMIAL_SOURCES} ${POLYNOMIAL_HEADERS})
add_executable(tests ${TESTS_SOURCES})

target_link_libraries(tests Polynomial gtest_main)