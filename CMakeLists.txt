cmake_minimum_required(VERSION 3.0.2)
project(vision)


find_package(catkin REQUIRED COMPONENTS
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
    CATKIN_DEPENDS rospy sensor_msgs message_runtime std_msgs
    DEPENDS system_lib
  )
  include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

catkin_install_python(PROGRAMS
  scripts/detection.py
  scripts/detection_usb.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
