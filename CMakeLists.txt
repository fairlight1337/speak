cmake_minimum_required(VERSION 2.8.3)
project(speak)

find_package(catkin REQUIRED COMPONENTS roscpp std_msgs message_generation)

add_service_files(
  FILES
  Speak.srv)

generate_messages()

catkin_package(
  CATKIN_DEPENDS message_runtime espeak
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS})

add_executable(speak_service src/speak_service.cpp)
target_link_libraries(speak_service ${catkin_LIBRARIES})
add_dependencies(speak_service ${catkin_EXPORTED_TARGETS})

add_executable(speak_listener src/speak_listener.cpp)
target_link_libraries(speak_listener ${catkin_LIBRARIES})
add_dependencies(speak_listener ${catkin_EXPORTED_TARGETS})
