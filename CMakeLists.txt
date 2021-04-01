cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(ignition-fortress VERSION 1.0.0)

#============================================================================
# Find ignition-cmake
#============================================================================
# If you get an error at this line, you need to install ignition-cmake
find_package(ignition-cmake2 2.7.0 REQUIRED)

#============================================================================
# Configure the project
#============================================================================
ign_configure_project(VERSION_SUFFIX pre1)

# all list of fortress packages

ign_find_package(ignition-common4 REQUIRED)
ign_find_package(ignition-fuel_tools6 REQUIRED)
ign_find_package(ignition-gazebo5 REQUIRED)
ign_find_package(ignition-gui5 REQUIRED)
ign_find_package(ignition-launch4 REQUIRED)
ign_find_package(ignition-math6 REQUIRED COMPONENTS eigen3 VERSION 6.8)
ign_find_package(ignition-msgs7 REQUIRED)
ign_find_package(ignition-physics4 REQUIRED)
ign_find_package(ignition-plugin1 REQUIRED VERSION 1.2)
ign_find_package(ignition-rendering5 REQUIRED)
ign_find_package(ignition-sensors5 REQUIRED)
ign_find_package(ignition-tools REQUIRED VERSION 1.1)
ign_find_package(ignition-transport10 REQUIRED)
ign_find_package(ignition-utils1 REQUIRED)
ign_find_package(sdformat11 REQUIRED)

install(DIRECTORY gazebodistro DESTINATION ${IGN_DATA_INSTALL_DIR})
