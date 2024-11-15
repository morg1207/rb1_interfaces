cmake_minimum_required(VERSION 3.8)
project(rb1_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)

find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(srv_files
  "srv/FindObject.srv"
  "srv/ApproachShelf.srv"
  "srv/InitLocalization.srv"
  "srv/FindNavPoses.srv"

  )
rosidl_generate_interfaces(${PROJECT_NAME}
  ${srv_files}
  DEPENDENCIES geometry_msgs
)
ament_export_dependencies(rosidl_default_runtime)

ament_package()
