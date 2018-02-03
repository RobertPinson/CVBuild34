# cmake needs this line
cmake_minimum_required(VERSION 2.8)

# Define project name
project(OpenCVDemo)

# Find OpenCV, you may need to set OpenCV_DIR variable
# to the absolute path to the directory containing OpenCVConfig.cmake file
# via the command line or GUI
find_package(OpenCV REQUIRED)

ocv_include_directories("${OpenCV_SOURCE_DIR}/include")
ocv_include_modules_recurse(${OPENCV_CPP_SAMPLES_REQUIRED_DEPS})

# If the package has been found, several variables will
# be set, you can find the full list with descriptions
# in the OpenCVConfig.cmake file.
# Print some message showing some of them
message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

if(CMAKE_VERSION VERSION_LESS "2.8.11")
  # Add OpenCV headers location to your include paths
  include_directories(${OpenCV_INCLUDE_DIRS})
endif()

# Declare the executable target built from your sources
add_executable(OpenCVDemo OpenCVDemo.cpp)

# Link your application with OpenCV libraries
target_link_libraries(OpenCVDemo ${OpenCV_LIBS} "${LIBRARIES_FROM_REFERENCES}")
