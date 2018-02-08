cmake_minimum_required(VERSION 2.8.3)
project(rhoban_viewer)

find_package(catkin REQUIRED COMPONENTS eigen)

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
  LIBRARIES rhoban_viewer ${EXTRA_LIBS}
  CATKIN_DEPENDS eigen
)

###########
## Build ##
###########

# Specify additional locations of header files
# Your package locations should be listed before other locations
include_directories(
  include
  ${catkin_INCLUDE_DIRS} 
)

# Declare a C++ library
add_library(rhoban_viewer
  src/rhoban_viewer/color.cpp
  src/rhoban_viewer/viewer.cpp
)

target_link_libraries(rhoban_viewer ${catkin_LIBRARIES})