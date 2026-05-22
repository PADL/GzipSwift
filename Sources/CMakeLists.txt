#[[
This source file is part of the GzipSwift open source project

Copyright (c) 2024 1024jp and the GzipSwift project authors
Licensed under MIT License

See https://github.com/1024jp/GzipSwift/blob/main/LICENSE for license information
#]]

if(NOT CMAKE_SYSTEM_NAME STREQUAL Darwin)
  add_subdirectory(system-zlib)
endif()
add_subdirectory(Gzip)
