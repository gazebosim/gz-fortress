cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(ignition-fortress VERSION 1.0.3)

#============================================================================
# Find ignition-cmake
#============================================================================
# If you get an error at this line, you need to install ignition-cmake
find_package(ignition-cmake2 2.12.1 REQUIRED)

#============================================================================
# Configure the project
#============================================================================
ign_configure_project(VERSION_SUFFIX)

# all list of fortress packages

ign_find_package(ignition-common4 REQUIRED VERSION 4.5)
ign_find_package(ignition-fuel_tools7 REQUIRED VERSION 7.0)
ign_find_package(ignition-gazebo6 REQUIRED VERSION 6.9)
ign_find_package(ignition-gui6 REQUIRED VERSION 6.4)
ign_find_package(ignition-launch5 REQUIRED VERSION 5.1)
ign_find_package(ignition-math6 REQUIRED COMPONENTS eigen3 VERSION 6.10)
ign_find_package(ignition-msgs8 REQUIRED VERSION 8.4)
ign_find_package(ignition-physics5 REQUIRED VERSION 5.1)
ign_find_package(ignition-plugin1 REQUIRED VERSION 1.2.1)
ign_find_package(ignition-rendering6 REQUIRED VERSION 6.3.1)
ign_find_package(ignition-sensors6 REQUIRED VERSION 6.3)
ign_find_package(ignition-transport11 REQUIRED VERSION 11.0)
ign_find_package(ignition-utils1 REQUIRED VERSION 1.4)
ign_find_package(sdformat12 REQUIRED VERSION 12.4)

if(build_warnings)
  set(all_warnings " CONFIGURATION WARNINGS:")
  foreach (msg ${build_warnings})
    ign_string_append(all_warnings " -- ${msg}" DELIM "\n")
  endforeach ()
  message(WARNING "${all_warnings}")
endif (build_warnings)

if(build_errors)
  message(SEND_ERROR "-- BUILD ERRORS: These must be resolved before compiling.")
  foreach(msg ${build_errors})
    message(SEND_ERROR "-- ${msg}")
  endforeach()
  message(SEND_ERROR "-- END BUILD ERRORS\n")

  set(error_str "Errors encountered in build. Please see BUILD ERRORS above.")

  message(FATAL_ERROR "${error_str}")

endif()

install(DIRECTORY gazebodistro DESTINATION ${IGN_DATA_INSTALL_DIR})
