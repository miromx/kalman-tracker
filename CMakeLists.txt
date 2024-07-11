cmake_minimum_required (VERSION 3.16.0...3.24.2)
project(app VERSION 1.0.0
                    DESCRIPTION "C++ implementation of Kalman Filter for Object Tracking"
                    LANGUAGES CXX)
get_directory_property(IS_SUBPROJECT PARENT_DIRECTORY)

# set(CMAKE_BUILD_TYPE "Debug")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_FLAGS "-pthread")

# Find OpenCV Components
find_package(OpenCV 4.7.0 REQUIRED) # version?
if(NOT OpenCV_FOUND)
    message(FATAL_ERROR "OpenCV not found")
endif()
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})

file(GLOB_RECURSE SRC  src/*.cpp src/*.hpp)
add_executable(${PROJECT_NAME} ${SRC})
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})
