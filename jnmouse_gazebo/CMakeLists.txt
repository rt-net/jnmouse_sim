cmake_minimum_required(VERSION 3.0.2)
project(jnmouse_gazebo)

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
)

catkin_package()

install(PROGRAMS
  scripts/download_gazebo_models.sh
  scripts/distance_sensor_simulator.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch models worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)