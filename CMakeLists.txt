cmake_minimum_required(VERSION 2.8.3)
project(speak)

find_package(catkin REQUIRED COMPONENTS roscpp message_generation)

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

add_executable(speak src/speak.cpp)
target_link_libraries(speak ${catkin_LIBRARIES})
add_dependencies(speak ${catkin_EXPORTED_TARGETS})
