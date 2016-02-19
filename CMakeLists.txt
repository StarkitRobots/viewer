cmake_minimum_required(VERSION 2.8.3)
project(rosban_viewer)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED
  cmake_modules
)

find_package(Eigen REQUIRED)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
    
set(EXTRA_LIBS ${EXTRA_LIBS} 
  sfml-graphics
  sfml-window
  sfml-system
  GL
  GLU
  )

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES rosban_utils ${EXTRA_LIBS}
  DEPENDS Eigen
)

###########
## Build ##
###########

# Specify additional locations of header files
# Your package locations should be listed before other locations
include_directories(
  include
  ${catkin_INCLUDE_DIRS} 
  ${Eigen_INCLUDE_DIRS}
)

# Declare a C++ library
add_library(rosban_viewer
  src/rosban_viewer/color.cpp
  src/rosban_viewer/viewer.cpp
)

target_link_libraries(rosban_viewer ${catkin_LIBRARIES})