project(MeetPie)
cmake_minimum_required(VERSION 2.4.6)

if(COMMAND cmake_policy)
  cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

find_package(PkgConfig REQUIRED)
pkg_search_module (PC_JSON-C REQUIRED json-c json)

#find_library(MATRIX_CREATOR_HAL matrix_creator_hal)

include_directories("${PROJECT_SOURCE_DIR}/include")

set (SOURCES src/MeetPie.cpp src/json_parsing.c)
set(CMAKE_BUILD_TYPE "Debug")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")
set(EXECUTABLE_OUTPUT_PATH "${PROJECT_SOURCE_DIR}/bin")

#Add base directory for includes (global)

find_path (JSON_C_INCLUDE_DIR json.h PATH_SUFFIXES json-c json)
find_library (JSON_C_LIBRARIES NAMES json-c libjson-c)
include_directories (${JSON_C_INCLUDE_DIR} ${PROJECT_SOURCE_DIR/include})


add_executable(MeetPie
    ${SOURCES}
)

target_link_libraries(MeetPie
    libc.so
    glib-2.0
    gio-2.0
    gobject-2.0
    ${JSON_C_LIBRARIES}
#    ${MATRIX_CREATOR_HAL}
    libm.so
    ~/ggk/src/libggk.a
)

install(TARGETS MeetPie DESTINATION bin)
