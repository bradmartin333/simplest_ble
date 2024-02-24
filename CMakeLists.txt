cmake_minimum_required(VERSION 3.21)

project(test_app)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable(test_app main.cpp common/utils.cpp)

add_subdirectory(lib/SimpleBLE/simpleble ${CMAKE_BINARY_DIR}/simpleble)
target_link_libraries(test_app simpleble::simpleble)