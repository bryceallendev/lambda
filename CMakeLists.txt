# @file CMakeLists.txt
# 
# CMake files for member initialization list examples

cmake_minimum_required(VERSION 3.10)

# project info
project(InitList)

# C++17
set(CMAKE_CXX_STANDARD 17)

# Turn on warnings
if (MSVC)
    # warning level 4
    add_compile_options(/W4)
else()
    # standard warnings
    add_compile_options(-Wall -Wno-unused-private-field -Wno-unused-variable)
endif()

# Assume each .cpp file is a separate application
file(GLOB APPLICATIONS "*.cpp")

# Generate executable for each .cpp file
foreach(APP ${APPLICATIONS})

    # Use basename (no path, no extension) of .cpp file for application name
    get_filename_component(APPBASENAME "${APP}" NAME_WLE)

    # Application is based on .cpp file only
    add_executable(${APPBASENAME} ${APPBASENAME}.cpp)

endforeach()
