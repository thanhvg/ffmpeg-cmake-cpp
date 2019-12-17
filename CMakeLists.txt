##
# CMake minimum required version for the project.
##
cmake_minimum_required(VERSION 3.10)

##
# FFmpeg-Video-Player C Project CMakeLists.txt.
##
project(FFmpeg_Example C CXX)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
# set(CMAKE_CXX_FLAGS "-D_STDC_CONSTANT_MACROS")
##
# Include module pkg-config for CMake.
##
INCLUDE(FindPkgConfig)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/Modules)

##
# Find FFmpeg include directories and link libraries.
# define FFMPEG_LIBRARIES and FFMPEG_INCLUDE_DIRS
##
find_package(FFMPEG REQUIRED)

add_subdirectory(src)
add_executable(FFmpeg_Example ${SOURCES})

# https://stackoverflow.com/questions/50760024/cmake-configuration-for-ffmpeg-in-c-project
target_link_libraries(FFmpeg_Example PRIVATE ${FFMPEG_LIBRARIES})
# target_include_directories(FFmpeg_Example PRIVATE ${FFMPEG_INCLUDE_DIRS})
include_directories(${FFMPEG_INCLUDE_DIRS})
