cmake_minimum_required(VERSION 3.8)
project(ros2_pkg)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

add_executable(hello_world_publisher src/hello_world_publisher.cpp)
ament_target_dependencies(hello_world_publisher rclcpp std_msgs)

add_executable(rpm_publisher src/rpm_publisher.cpp)
ament_target_dependencies(rpm_publisher rclcpp std_msgs)

add_executable(hello_world_subscriber src/hello_world_subscriber.cpp)
ament_target_dependencies(hello_world_subscriber rclcpp std_msgs)

add_executable(rpm_subscriber src/rpm_subscriber.cpp)
ament_target_dependencies(rpm_subscriber rclcpp std_msgs)

add_executable(speed_subscriber src/speed_subscriber.cpp)
ament_target_dependencies(speed_subscriber rclcpp std_msgs)

#add_executable(speed_subscriber src/speed_subscriber.cpp)
#ament_target_dependencies(speed_subscriber rclcpp std_msgs)

install(TARGETS 
  hello_world_publisher hello_world_subscriber rpm_publisher rpm_subscriber speed_subscriber
  DESTINATION 
  lib/${PROJECT_NAME})

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
