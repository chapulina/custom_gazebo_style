cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
set(CMAKE_AUTOMOC ON)

find_package(Qt5Core REQUIRED)
find_package(gazebo REQUIRED)

QT5_ADD_RESOURCES(resources_RCC resources.qrc)

include_directories(SYSTEM ${GAZEBO_INCLUDE_DIRS})
link_directories(${GAZEBO_LIBRARY_DIRS})

add_library(custom_gazebo_style SHARED
  CustomGazeboStyle.cc
  ${resources_RCC}
)
target_link_libraries(custom_gazebo_style ${GAZEBO_LIBRARIES}
    ${Qt5Core_LIBRARIES}
    ${Qt5Widgets_LIBRARIES})
