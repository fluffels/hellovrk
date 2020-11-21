project(hellovrk)

cmake_minimum_required(VERSION 3.7)
set (CMAKE_CXX_STANDARD 17)

find_package(Vulkan REQUIRED)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(
    main
    hellovr_vulkan_main.cpp
    lodepng.cpp
    Matrices.cpp
    pathtools.cpp
)

message(
    STATUS
    "link ${CONAN_LIBS}"
)
target_link_libraries(
    main
    ${CONAN_LIBS}
    ${Vulkan_LIBRARIES}
)
