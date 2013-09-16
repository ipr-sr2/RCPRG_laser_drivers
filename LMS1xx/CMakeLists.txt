cmake_minimum_required(VERSION 2.8.3)
project(LMS1xx)

find_package(catkin REQUIRED COMPONENTS libLMS1xx roscpp sensor_msgs)

catkin_package(
    INCLUDE_DIRS include)

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(LMS100 src/LMS1xx_node.cpp)
add_executable(set_config src/setConfig.cpp)

target_link_libraries(LMS100 ${catkin_LIBRARIES})
target_link_libraries(set_config ${catkin_LIBRARIES})


#############
## Install ##
#############

install(TARGETS LMS100 set_config
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY include
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)