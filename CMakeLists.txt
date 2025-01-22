cmake_minimum_required(VERSION 3.10)
project(nlbayes VERSION 1.0.0 LANGUAGES CXX)

# Set C++ standard (upgraded to C++17 for better parallel algorithms support)
# Note: OpenMP has been removed in favor of std::async for parallelization
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Create library
file(GLOB_RECURSE SOURCES "src/*.cpp")
add_library(nlbayes STATIC ${SOURCES})

# Include directories
target_include_directories(nlbayes
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

# Installation rules
install(TARGETS nlbayes
    EXPORT nlbayes-targets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    INCLUDES DESTINATION include
)

install(DIRECTORY include/
    DESTINATION include
    FILES_MATCHING PATTERN "*.h"
)

# Export targets
install(EXPORT nlbayes-targets
    FILE nlbayes-targets.cmake
    NAMESPACE nlbayes::
    DESTINATION lib/cmake/nlbayes
)
