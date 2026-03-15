cmake_minimum_required(VERSION 3.21)

project(HybridVectorSearch VERSION 0.1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(HybridVectorSearch
    src/main.cpp
)

target_include_directories(HybridVectorSearch
    PRIVATE
        ${PROJECT_SOURCE_DIR}/include
)

if(MSVC)
    target_compile_options(HybridVectorSearch PRIVATE /W4 /permissive-)
else()
    target_compile_options(HybridVectorSearch PRIVATE -Wall -Wextra -Wpedantic)
endif()