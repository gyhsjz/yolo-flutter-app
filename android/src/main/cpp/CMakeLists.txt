cmake_minimum_required(VERSION 3.10.2)
project("ultralytics")

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add native library
add_library(
    ultralytics
    SHARED
    native-lib.cpp
)

# Target properties
set_target_properties(ultralytics PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
)

# Find log library
find_library(
    log-lib
    log
)

# Link libraries
target_link_libraries(
    ultralytics
    ${log-lib}
)

