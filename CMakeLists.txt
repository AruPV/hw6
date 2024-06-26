cmake_minimum_required(VERSION 3.28)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(
	CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fcoroutines -fexceptions -O0 -std=c++20"
)

project(
	PriorityQueue
	VERSION 1.0
	LANGUAGES CXX
)

include(FetchContent)
FetchContent_Declare(
	googletest
	URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)

FetchContent_MakeAvailable(googletest)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "./bin")

enable_testing()

add_executable(
	tests
	incl/priority-queue.hpp
	src/utils.cpp
	test/priority-queue-tests.cpp
)

add_executable(
	reflection
	incl/priority-queue.hpp
	src/utils.cpp
	src/slides.cpp
)

target_link_libraries(
	tests
	GTest::gtest_main
)
