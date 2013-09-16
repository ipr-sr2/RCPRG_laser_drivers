cmake_minimum_required(VERSION 2.8.3)
project(libLMS1xx)

find_package(catkin REQUIRED COMPONENTS roscpp)

# include_directories(include/${PROJECT_NAME} ${catkin_INCLUDE_DIRS})
catkin_package(
   LIBRARIES ${PROJECT_NAME})

include_directories(include ${catkin_INCLUDE_DIRS})

###########
## Build ##
###########

add_library(${PROJECT_NAME} src/LMS1xx.cpp)

add_executable(${PROJECT_NAME}_test src/test.cpp)

target_link_libraries(${PROJECT_NAME}_test ${PROJECT_NAME})

#############
## Install ##
#############

install(TARGETS ${PROJECT_NAME} ${PROJECT_NAME}_test
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY include
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)