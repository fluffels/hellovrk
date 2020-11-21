project(hellovrk)

cmake_minimum_required(VERSION 3.7)
set(CMAKE_CXX_STANDARD 17)

set(VCPKG "C:/vcpkg/")
set(CMAKE_TOOLCHAIN_FILE "${VCPKG}/scripts/buildsystems/vcpkg.cmake")
include(${CMAKE_TOOLCHAIN_FILE})
link_directories(${VCPKG}installed/x64-windows/lib)

message(STATUS "[TRACE] CMakeLists")

find_package(SDL2 REQUIRED)
find_package(Vulkan REQUIRED)

add_executable(
    main
    WIN32
    hellovr_vulkan_main.cpp
    lodepng.cpp
    Matrices.cpp
    pathtools.cpp
    strtools.cpp
)
target_link_libraries(
    main
    ${Vulkan_LIBRARIES}
    SDL2::SDL2
    openvr_api
)
