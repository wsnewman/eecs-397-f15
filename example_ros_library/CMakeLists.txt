cmake_minimum_required(VERSION 2.8.3)
project(example_ros_library)

find_package(catkin_simple REQUIRED)
find_package(cmake_modules REQUIRED)
find_package(Eigen3 REQUIRED)

include_directories(${EIGEN3_INCLUDE_DIR})
add_definitions(${EIGEN_DEFINITIONS})
catkin_simple()

# example boost usage
# find_package(Boost REQUIRED COMPONENTS system thread)

# C++0x support - not quite the same as final C++11!
# SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

# Libraries
cs_add_library(plane_fitter src/plane_fitter.cpp)   

# Executables
cs_add_executable(plane_fitter_main src/plane_fitter_main.cpp)
target_link_libraries(plane_fitter_main plane_fitter ${catkin_LIBRARIES})

cs_install()
cs_export()
    
