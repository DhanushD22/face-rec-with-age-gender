cmake_minimum_required(VERSION 3.10)
project(FaceRecognition)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE Release)

# Include directories
include_directories(
    ${CMAKE_SOURCE_DIR}/include
    /usr/local/include/ncnn
    /usr/include/opencv4
)

# Find OpenCV
find_package(OpenCV REQUIRED)

# Source files
file(GLOB SRC_FILES ${CMAKE_SOURCE_DIR}/src/*.cpp)

# Create executable
add_executable(FaceRecognition ${SRC_FILES})

# Link libraries
target_link_libraries(FaceRecognition
    ${OpenCV_LIBS}
    ncnn
    pthread
    dl
    gomp
)
