cmake_minimum_required(VERSION 3.5)
project(g5)

set(CMAKE_CXX_STANDARD 17)

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
  set(CMAKE_CXX_FLAGS "-fpermissive")
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  set(CMAKE_CXX_FLAGS "-fpermissive")
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
  set(CMAKE_CXX_FLAGS "/sdl-")
endif()

set(SOURCE_FILES g5compiler.cpp)
add_executable(g5 ${SOURCE_FILES})

enable_testing()
add_test(NAME test_helloworld COMMAND g5  "${PROJECT_SOURCE_DIR}/test/adhoc/helloworld.go")
add_test(NAME test_const COMMAND g5  "${PROJECT_SOURCE_DIR}/test/adhoc/constdecl.go")
add_test(NAME test_import COMMAND g5  "${PROJECT_SOURCE_DIR}/test/adhoc/importdecl.go")
add_test(NAME test_var COMMAND g5  "${PROJECT_SOURCE_DIR}/test/adhoc/vardecl.go")
add_test(NAME test_type COMMAND g5  "${PROJECT_SOURCE_DIR}/test/adhoc/typedecl.go")
add_test(NAME test_func COMMAND g5  "${PROJECT_SOURCE_DIR}/test/adhoc/funcdecl.go")
