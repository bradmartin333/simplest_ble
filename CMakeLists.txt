cmake_minimum_required(VERSION 3.21)

project(test_app)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(SOURCES
    common/utils.cpp
)

add_executable(test_app main.cpp ${SOURCES})

find_package(simpleble CONFIG REQUIRED)
target_link_libraries(test_app PRIVATE simpleble::simpleble simpleble::simpleble-c)
