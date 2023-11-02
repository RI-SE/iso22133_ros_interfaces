cmake_minimum_required(VERSION 3.8)
project(iso_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

find_package(geographic_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

set(msg_files
  "msg/CoordinateSystem.msg"
  "msg/ObjectSettings.msg"
  "msg/CartesianTrajectory.msg"
  "msg/CartesianTrajectoryPoint.msg"
  "msg/OSEMIds.msg"
  "msg/OSEMDeviations.msg"
  "msg/OSEMMonrRate.msg"
  "msg/TestMode.msg"
  "msg/OSEMTimeServer.msg"
  "msg/TrajectoryHeader.msg"
  "msg/TrajectoryInfo.msg"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES geographic_msgs builtin_interfaces
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
