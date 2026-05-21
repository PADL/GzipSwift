#[[
This source file is part of the GzipSwift open source project

Copyright (c) 2024 1024jp and the GzipSwift project authors
Licensed under MIT License

See https://github.com/1024jp/GzipSwift/blob/main/LICENSE for license information
#]]

include(CMakePackageConfigHelpers)

set(GZIP_EXPORTS_FILE
  ${CMAKE_CURRENT_BINARY_DIR}/GzipExports.cmake)

configure_file(GzipConfig.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/GzipConfig.cmake)

get_property(GZIP_EXPORTS GLOBAL PROPERTY GZIP_EXPORTS)
export(TARGETS ${GZIP_EXPORTS}
  NAMESPACE Gzip::
  FILE ${GZIP_EXPORTS_FILE}
  EXPORT_LINK_INTERFACE_LIBRARIES)

install(EXPORT GzipTargets
  FILE GzipTargets.cmake
  NAMESPACE Gzip::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/Gzip)

configure_package_config_file(
  GzipConfig.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/install/GzipConfig.cmake
  INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/Gzip)

install(FILES
  ${CMAKE_CURRENT_BINARY_DIR}/install/GzipConfig.cmake
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/Gzip)
