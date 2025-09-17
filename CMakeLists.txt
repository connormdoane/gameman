cmake_minimum_required(VERSION 3.10)
project(gameman C)
set(CMAKE_C_STANDARD 99)

# Headers
include_directories(${PROJECT_SOURCE_DIR}/headers)

# Sources
file(GLOB LIB_SOURCES ${PROJECT_SOURCE_DIR}/lib/*.c)

# Find SDL2 and SDL2_ttf using pkg-config
find_package(PkgConfig REQUIRED)
pkg_check_modules(SDL2 REQUIRED sdl2)
pkg_check_modules(SDL2_TTF REQUIRED SDL2_ttf)

include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_TTF_INCLUDE_DIRS})

add_executable(gameman
  main.c
  ${LIB_SOURCES}
)

target_link_libraries(gameman
  ${SDL2_LIBRARIES}
  ${SDL2_TTF_LIBRARIES}
)
