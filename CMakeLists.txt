cmake_minimum_required(VERSION 3.8)
project(ros2_xbee_bridge)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

## Find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclpy REQUIRED)

## Install Python modules
ament_python_install_package(${PROJECT_NAME})
install(PROGRAMS
  scripts/xbee_bridge.py
  DESTINATION lib/${PROJECT_NAME}
)


install(DIRECTORY
  launch
  DESTINATION share/${PROJECT_NAME}/)

install(DIRECTORY
  config
  DESTINATION share/${PROJECT_NAME}/)

# rosidl_target_interfaces(sim_node
#   ${PROJECT_NAME} "rosidl_typesupport_cpp")


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
