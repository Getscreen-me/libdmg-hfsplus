cmake_minimum_required(VERSION 3.5)

project (libdmg-hfsplus)
list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

# We want win32 executables to build staticly by default, since it's more difficult to keep the shared libraries straight on Windows
IF(WIN32)
	SET(BUILD_STATIC ON CACHE BOOL "Force compilation with static libraries")
ELSE(WIN32)
	SET(BUILD_STATIC OFF CACHE BOOL "Force compilation with static libraries")
ENDIF(WIN32)

set(BUILD_SHARED_LIBS OFF)
set(CMAKE_FIND_LIBRARY_SUFFIXES .a)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -static")
set(CMAKE_LINKER_FLAGS "${CMAKE_LINKER_FLAGS} -static")

include_directories (${PROJECT_SOURCE_DIR}/includes)

add_subdirectory (common)
add_subdirectory (dmg)
# add_subdirectory (hdutil)
add_subdirectory (hfs)

