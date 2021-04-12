cmake_minimum_required(VERSION 3.3)
project(project)

#cmake_utils file_functions.cmake provides the functions
#add_dependency_tree_file and get_list_from_dependency_tree
include(cmake_utils/file_functions.cmake)

#we need the full paths to the dependency tree files
get_filename_component(hdldepfile hdl/deptree.txt REALPATH)
get_filename_component(tbdepfile tb/deptree.txt REALPATH)

#placeholder1 and placeholder2 store the filepaths that are the heads of lists
add_dependency_tree_file(placeholder1 ${hdldepfile})
add_dependency_tree_file(placeholder2 ${tbdepfile})

#the value of topsynth is also in placeholder1
get_filename_component(topsynth hdl/blinky_zedboard_z7.v REALPATH)
#the value of topsim is also in placeholder2
get_filename_component(topsim tb/blinky_tb.v REALPATH)
get_list_from_dependency_tree(synthfiles ${topsynth})
get_list_from_dependency_tree(simfiles ${topsim})

message(STATUS "synth files ${synthfiles}")
message(STATUS "sim files ${simfiles}")
  


