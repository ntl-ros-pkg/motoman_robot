cmake_minimum_required(VERSION 2.8.3)
project(motoman_description)
find_package(catkin REQUIRED)
catkin_package()

###########
# Install #
###########
set(LAUNCH_DIRS
  launch/sda5
  launch/sda5/rviz
  launch/sia5
  launch/sia5/rviz
)
set(MESH_DIRS
  meshes/sda5/collision
  meshes/sda5/visual/base_link
  meshes/sda5/visual/link_b
  meshes/sda5/visual/link_e
  meshes/sda5/visual/link_l
  meshes/sda5/visual/link_r
  meshes/sda5/visual/link_s
  meshes/sda5/visual/link_t
  meshes/sda5/visual/link_u
  meshes/sda5/visual/torso_link
  meshes/sia5/collision/STL
  meshes/sia5/visual/COLLADA
  meshes/sensor/visual/COLLADA
)
set(URDF_DIRS
  robots/sda5
  robots/sia5
  robots/sia5/urdf
  urdf
  urdf/sda5
  urdf/sia5
  urdf/sensor
)

foreach(dir ${LAUNCH_DIRS} ${MESH_DIRS} ${URDF_DIRS})
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

########
# Test #
########
if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch/sda5)
  roslaunch_add_file_check(launch/sia5)
endif()

