cmake_minimum_required(VERSION 3.0.2)
project(jnmouse_gazebo)

find_package(catkin REQUIRED)

catkin_package()

install(PROGRAMS
  scripts/download_gazebo_models.sh
  scripts/distance_sensor_simulator.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()
