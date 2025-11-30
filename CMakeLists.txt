cmake_minimum_required(VERSION 3.5)
project(ex_solution)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sysmonitor_interfaces REQUIRED)

# Crea l'eseguibile
add_executable(solution_node src/solution_node.cpp)

ament_target_dependencies(solution_node 
  rclcpp 
  std_msgs 
  sysmonitor_interfaces
)

install(TARGETS
  solution_node
  DESTINATION lib/${PROJECT_NAME})

ament_package()
