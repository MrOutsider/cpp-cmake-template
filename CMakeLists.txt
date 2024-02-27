cmake_minimum_required(VERSION 3.22.1)
project(app)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_CXX_STANDARD 20)

#add_subdirectory()

add_executable(app src/main.cpp)
target_include_directories(app PRIVATE src include)

if (WIN32)
    #target_link_libraries(app PRIVATE)
    if (CMAKE_BUILD_TYPE STREQUAL "Release" OR CMAKE_BUILD_TYPE STREQUAL "RelWithDebInfo")
        target_link_options(app PRIVATE -mwindows -static)
    endif ()
    if (CMAKE_BUILD_TYPE STREQUAL "Debug")
        target_link_options(app PRIVATE -static)
    endif ()
endif (WIN32)

if (UNIX)
    #target_link_libraries(app PRIVATE)
endif (UNIX)
