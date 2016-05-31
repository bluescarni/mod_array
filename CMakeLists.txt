cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

if(TARGET array)
  return()
endif()

enable_testing()

project(array VERSION 0.1 LANGUAGES CXX)

add_library(array src/array.cpp)

target_include_directories(array PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
  PRIVATE src)

install(TARGETS array
  ARCHIVE  DESTINATION lib
  LIBRARY  DESTINATION lib
  RUNTIME  DESTINATION bin)
install(DIRECTORY include/ DESTINATION include)

add_executable(array_test0 tests/array_test0.cpp)

target_link_libraries(array_test0 array)

add_test(array_test0 array_test0)
