cmake_minimum_required(VERSION 3.0.2)
project(capra_hazmat_detection)


find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  rospy
  sensor_msgs
  std_msgs
  message_generation
)

add_message_files(
  FILES
  labels_msg.msg
  )

generate_messages(
  DEPENDENCIES
  std_msgs
  sensor_msgs
  )
  
  catkin_package(
    INCLUDE_DIRS include
    LIBRARIES vision
    CATKIN_DEPENDS cv_bridge rospy sensor_msgs message_runtime std_msgs
  )
  include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

catkin_install_python(PROGRAMS
  scripts/detect.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
