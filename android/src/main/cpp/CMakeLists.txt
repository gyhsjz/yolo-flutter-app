cmake_minimum_required(VERSION 3.10.2)
project("ultralytics")

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_library(
    ultralytics
    SHARED
    native-lib.cpp
)

# Ensure proper C++ standard library linkage
set_target_properties(ultralytics PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
    POSITION_INDEPENDENT_CODE ON
)

# Add compile options with better error handling
target_compile_options(ultralytics PRIVATE
    $<$<COMPILE_LANGUAGE:CXX>:-fexceptions>
    $<$<COMPILE_LANGUAGE:CXX>:-frtti>
)

find_library(
    log-lib
    log
)

target_link_libraries(
    ultralytics
    ${log-lib}
)

