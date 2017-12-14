cmake_minimum_required(VERSION 2.8.3)
project(rtimulib_ros)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
)

catkin_package(
    LIBRARIES rtimulib_ros
    CATKIN_DEPENDS roscpp sensor_msgs
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(rtimulib_ros src/rtimulib_ros.cpp)

target_link_libraries(rtimulib_ros
  ${catkin_LIBRARIES}
  RTIMULib
)

# Install nodelet library
install(TARGETS ${PROJECT_NAME}
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
    )

	
# Install launch files
install(DIRECTORY launch/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
    )

# Install rviz files
install(DIRECTORY config/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config
    )

