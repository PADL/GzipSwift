#[[
This source file is part of the GzipSwift open source project

Copyright (c) 2024 1024jp and the GzipSwift project authors
Licensed under MIT License

See https://github.com/1024jp/GzipSwift/blob/main/LICENSE for license information
#]]

add_library(Gzip
  CompressionLevel.swift
  Data+Gzip.swift
  GzipError.swift
  GzipError+LocalizedError.swift)

if(NOT CMAKE_SYSTEM_NAME STREQUAL Darwin)
  target_link_libraries(Gzip PUBLIC system-zlib)
endif()

# Upcoming-features applied in Package.swift.
foreach(_feature ExistentialAny InternalImportsByDefault MemberImportVisibility
                  NonisolatedNonsendingByDefault InferIsolatedConformances)
  target_compile_options(Gzip PRIVATE
    "$<$<COMPILE_LANGUAGE:Swift>:SHELL:-enable-upcoming-feature ${_feature}>")
endforeach()

get_swift_host_os(_swift_os)
set_target_properties(Gzip PROPERTIES
  SOVERSION 0
  INTERFACE_INCLUDE_DIRECTORIES
    "$<BUILD_INTERFACE:${CMAKE_Swift_MODULE_DIRECTORY}>;$<INSTALL_INTERFACE:${CMAKE_INSTALL_LIBDIR}/swift/${_swift_os}>")

_install_target(Gzip)
set_property(GLOBAL APPEND PROPERTY GZIP_EXPORTS Gzip)
