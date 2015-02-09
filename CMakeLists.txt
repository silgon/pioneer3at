cmake_minimum_required(VERSION 2.4.6)
project(pioneer3at)

find_package(catkin REQUIRED)

## System dependencies are found with CMake's conventions
find_package(catkin REQUIRED COMPONENTS geometry_msgs std_msgs robot_state_publisher)

find_package(gazebo REQUIRED)
find_package(Boost REQUIRED COMPONENTS thread)

MESSAGE( STATUS "GAZEBO_INCLUDE_DIRS:         " ${GAZEBO_INCLUDE_DIRS} )
MESSAGE( STATUS "SDFormat_INCLUDE_DIRS:       " ${SDFormat_INCLUDE_DIRS} )

include_directories(include ${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${SDFormat_INCLUDE_DIRS})

add_executable(p2os_teleop src/p2os_teleop.cc)
target_link_libraries(p2os_teleop ${catkin_LIBRARIES})
add_dependencies(p2os_teleop ${catkin_EXPORTED_TARGETS})

add_executable(map_odom_tf_publisher src/map_odom_tf_publisher.cpp)
target_link_libraries(map_odom_tf_publisher ${catkin_LIBRARIES})
add_dependencies(map_odom_tf_publisher ${catkin_EXPORTED_TARGETS})
