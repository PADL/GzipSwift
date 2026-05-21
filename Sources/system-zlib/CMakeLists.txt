#[[
This source file is part of the GzipSwift open source project

Copyright (c) 2024 1024jp and the GzipSwift project authors
Licensed under MIT License

See https://github.com/1024jp/GzipSwift/blob/main/LICENSE for license information
#]]

# INTERFACE wrapper exposing the `zlibLinux` Swift module that the Gzip
# sources import on Linux. The module.modulemap declares `link "z"`, so
# clang's module loader pulls in libz automatically.

add_library(system-zlib INTERFACE)
target_include_directories(system-zlib INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/system-zlib>)
target_link_libraries(system-zlib INTERFACE z)

install(FILES
  shim.h
  module.modulemap
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/system-zlib)

_install_target(system-zlib)
set_property(GLOBAL APPEND PROPERTY GZIP_EXPORTS system-zlib)
