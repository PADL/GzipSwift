#[[
This source file is part of the GzipSwift open source project

Copyright (c) 2024 1024jp and the GzipSwift project authors
Licensed under MIT License

See https://github.com/1024jp/GzipSwift/blob/main/LICENSE for license information
#]]

cmake_minimum_required(VERSION 3.16)
project(GzipSwift
  LANGUAGES Swift C)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake/modules)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_Swift_MODULE_DIRECTORY ${CMAKE_BINARY_DIR}/swift)

if(CMAKE_SYSTEM_NAME STREQUAL Windows OR CMAKE_SYSTEM_NAME STREQUAL Darwin)
  option(BUILD_SHARED_LIBS "Build shared libraries by default" YES)
endif()

include(GNUInstallDirs)
include(SwiftSupport)

add_subdirectory(Sources)
add_subdirectory(cmake/modules)
