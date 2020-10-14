cmake_minimum_required(VERSION 3.17)
project(DynDimRTree)

set(CMAKE_CXX_STANDARD 14)

include_directories(.)

add_executable(test0
        Test.cpp)

add_executable(test1
        TestBadData.cpp)

add_executable(test2
        MemoryTest.cpp)