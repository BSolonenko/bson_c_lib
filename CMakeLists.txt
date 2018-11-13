cmake_minimum_required(VERSION 3.11)
project(BSON LANGUAGES C)

add_library(${PROJECT_NAME} STATIC)
add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_sources(${PROJECT_NAME}
  PRIVATE
    "${CMAKE_CURRENT_LIST_DIR}/src/bson_array.c"
    "${CMAKE_CURRENT_LIST_DIR}/include/bson/bson_array.h"
    "${CMAKE_CURRENT_LIST_DIR}/src/bson_object.c"
    "${CMAKE_CURRENT_LIST_DIR}/include/bson/bson_object.h"
    "${CMAKE_CURRENT_LIST_DIR}/src/bson_util.c"
    "${CMAKE_CURRENT_LIST_DIR}/include/bson/bson_util.h"
)

target_include_directories(${PROJECT_NAME}
  PUBLIC
    "${CMAKE_CURRENT_LIST_DIR}/include"
)

add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/emhashmap")

target_link_libraries(${PROJECT_NAME}
  PRIVATE
    emhashmap::emhashmap
)
