cmake_minimum_required(VERSION 3.16)
project(Strudel VERSION 1.0.0 LANGUAGES CXX)

if (NOT DEFINED CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
  set(CMAKE_CXX_STANDARD 20)
endif()
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Link against this 'library' to use the warnings specified in cmake/compiler-warnings.cmake
add_library(compiler-warnings INTERFACE)
include(cmake/compiler-warnings.cmake)
set_project_warnings(compiler-warnings)

# Avoid warning about DOWNLOAD_EXTRACT_TIMESTAMP from FetchContent_Declare in CMake 3.24+:
if (CMAKE_VERSION VERSION_GREATER_EQUAL "3.24.0")
  cmake_policy(SET CMP0135 NEW)
endif()

message(STATUS "Using toolchain file: ${CMAKE_TOOLCHAIN_FILE}")

include(FetchContent)
FetchContent_Declare(fmt
  GIT_REPOSITORY https://github.com/fmtlib/fmt.git
  GIT_TAG 10.0.0
)
FetchContent_MakeAvailable(fmt)

FetchContent_Declare(json
  URL https://github.com/nlohmann/json/releases/download/v3.11.2/json.tar.xz)
FetchContent_MakeAvailable(json)

add_subdirectory(src)